Este é o objeto contém um codigo em python que realiza a consulta no ollama, ferramenta utilizada com inteligencia artificial do projeto 
  
![Node_OLLAMA](https://github.com/carlossilva9867/soc-opensource-ia/blob/main/IMG/node_ollma_shuffle.png?raw=true)

**Nome do objeto**: IA_ANALYSIS\
**Find actions**: repeat back to me
  
```
{% python %}
import requests

URL = "http://IP_DO_SERVIDOR_OLLAMA:11434/api/chat"

# Definindo o payload como um dicionário Python
instrucao = "Para a resposta, quebre as linhas utilizando '\\n' e não use nenhuma formatação de texto como negrito, itálico ou listas numeradas."
contexto = "Segue abaixo o alerta da minha ferramenta de SIEM, realize a análise e me passe as recomendações!"
alert = "$loop.#._source.kibana.alert.reason"

content = instrucao + "\n" + contexto + "\n" + alert
payload = {
    "model": "ALIENTELLIGENCE/cybersecuritymonitoring:latest",
    "messages": [
        {
            "role": "user",
            "content": content
        }
    ],
    "temperature": 0.1,  # Reduz a criatividade para acelerar a resposta
    "max_tokens": 200,   # Ajustado para permitir uma resposta mais completa
    "stream": False
}

# Função para formatar a resposta
def format_message(message_content):
    # Remove os caracteres '**'
    formatted_message = message_content.replace('**', '')
    
    # Substitui múltiplos espaços por um único espaço e remove espaços extras no início e no fim
    formatted_message = ' '.join(formatted_message.split())
    
    # Substitui linhas em branco por '\n'
    lines = formatted_message.split('\n')
    formatted_message = '\n'.join([line.strip() for line in lines])
    
    return formatted_message

# Usando uma sessão persistente
with requests.Session() as session:
    try:
        response = session.post(URL, json=payload)
        if response.status_code == 200:
            response_json = response.json()
            message_content = response_json.get('message', {}).get('content', 'Conteúdo não encontrado')
            
            # Formatar o conteúdo da mensagem
            formatted_message = format_message(message_content)
            print(formatted_message)
            
        else:
            print(f"Erro {response.status_code}: {response.text}")
    except requests.exceptions.Timeout:
        print("A requisição demorou muito para ser processada.")
    except requests.exceptions.RequestException as e:
        print(f"Ocorreu um erro na requisição: {e}")

{% endpython %}
```