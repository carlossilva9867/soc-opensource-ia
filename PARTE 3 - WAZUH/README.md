# Configurações do workflow

Você também pode importar o workflow que está no projeto que já vem pré configurado

Video mostrando o processo de configuração do workflow
[![Formas de envio de log](https://img.youtube.com/vi/oRefqoTl1LI/maxresdefault.jpg)](https://youtu.be/oRefqoTl1LI?feature=shared)

### node IA_ANALISE
```
{% python %}
import requests
import re

URL = "http://IP_OLLAMA:11434/api/chat"
# Definindo o payload como um dicionário Python
instrucao = "Para a resposta, quebre as linhas utilizando '\\n' e não use nenhuma formatação de texto como negrito, itálico ou listas numeradas."
contexto = "Segue abaixo o alerta da minha ferramenta de SIEM, realize a análise e me passe as recomendações!"

# Substituindo as variáveis no alerta
alert = """
Time: $loop.timestamp
Severity: $loop.severity
Title: $loop.title
Host: $loop.all_fields.agent.name
Alert: $loop.all_fields.full_log
"""

# Criando o conteúdo a ser enviado
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
    # Remove caracteres especiais e múltiplos espaços
    formatted_message = message_content
    
    # Remove caracteres especiais, como pontuação e barras
    formatted_message = re.sub(r'[^\w\s]', '', formatted_message)
    
    # Remove espaços extras
    formatted_message = ' '.join(formatted_message.split())
    
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

### IRIS Body
```
{
  "alert_title": "$loop.title",
  "alert_description": "Alert:$loop.text\nIA\n$ia_analise",
  "alert_source": "WAZUH",
  "alert_source_ref": "Wazuh SIEM",
  "alert_source_link": "https://IP_WAZUH",
  "alert_severity_id": "1",
  "alert_status_id": "1",
  "alert_note": "TESTE",
  "alert_tags": "wazuh-siem",
  "alert_customer_id": "2",
  "alert_lassification_id": "1"
}
```
### Discord node
```
{
  "content": "**Novo alerta** - $loop.title \n$loop.timestamp\n$loop.all_fields.full_log\nanalise Ticket_iris\n$iris_v2_1.body.data.alert_description"
}
```