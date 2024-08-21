# SOC Open Source com IA

Neste projeto, o alerta gerado pela ferramenta de segurança SIEM é enviado para uma plataforma de gerenciamento de incidentes (DFIR-IRIS), onde já passou por uma análise primária realizada por uma inteligência artificial. Essa abordagem traz benefícios significativos para projetos futuros, como a definição de criticidade com base em padrões analisados pela IA.

No futuro, com playbooks e runbooks alinhados ao modelo de IA, essa tecnologia pode auxiliar na tomada de decisões em cenários específicos, conforme o treinamento que recebeu. É possível, por exemplo, executar ações como isolar um host da rede, redefinir senhas ou bloquear um usuário. Uma vez que você possui um ambiente orquestrado e inteligente, a criatividade e o tempo se tornam os únicos limites para explorar as inúmeras possibilidades.

### Arquitetura do Projeto
![Workflow](https://github.com/carlossilva9867/soc-opensource-ia/IMG/diagrama.png)

A arquitetura do projeto foi planejada para maximizar a eficiência e a segurança. A inteligência artificial é treinada localmente para garantir que dados sensíveis sejam protegidos, ao mesmo tempo em que se aproveita ao máximo as capacidades de orquestração e automação.

### Requisitos
- 4x Máquinas virtuais para rodar o ambiente
- Acesso à internet para atualização de pacotes e comunicação com plataformas externas

### Parte I: Instalação
Nesta seção, detalharemos os passos necessários para instalar todas as ferramentas e configurar o ambiente.

### Parte II: Construção [EM DESENVOLVIMENTO]
Aqui, construiremos a solução integrada, conectando o SIEM, a IA e a plataforma de gerenciamento de incidentes. Também discutiremos como personalizar e expandir as funcionalidades para atender a diferentes necessidades.

---

Este projeto é ideal para equipes de segurança que desejam implementar uma solução poderosa de SOC utilizando apenas ferramentas de código aberto, combinando o poder da inteligência artificial com práticas avançadas de gerenciamento de incidentes.
