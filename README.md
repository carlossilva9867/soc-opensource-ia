
## Visão Geral do Projeto

Neste projeto, os alertas gerados pela ferramenta de segurança SIEM são enviados para uma plataforma de gerenciamento de incidentes (DFIR-IRIS), onde uma IA faz uma análise inicial.

Com o tempo, playbooks e runbooks alinhados ao modelo de IA podem ajudar muito na tomada de decisões em cenários específicos, dependendo de como a IA foi treinada.

### Funcionalidades Úteis para um SOC

- **Tomada de decisão** baseada em playbooks e runbooks.
- **Classificação do nível de ameaça** considerando vários fatores, como usuário, IP e correlação com ferramentas de CTI.

Com um ambiente orquestrado e inteligente, você pode focar sua criatividade e tempo em tarefas mais estratégicas, aumentando a eficiência e a eficácia das operações de segurança.


### Arquitetura do Projeto
![Workflow](https://github.com/carlossilva9867/soc-opensource-ia/blob/main/IMG/diagrama.png)

A arquitetura do projeto foi planejada para maximizar a eficiência e a segurança. A inteligência artificial é treinada localmente para garantir que dados sensíveis sejam protegidos, ao mesmo tempo em que se aproveita ao máximo as capacidades de orquestração e automação.

### Requisitos
- 4x Máquinas virtuais para rodar o ambiente
- Acesso à internet para atualização de pacotes e comunicação com plataformas externas

### [Parte I: Instalação](https://github.com/carlossilva9867/soc-opensource-ia/tree/main/PARTE%201%20-%20INSTALACAO)

Nesta seção, detalharemos os passos necessários para instalar todas as ferramentas e configurar o ambiente.

### Parte II: Construção [EM DESENVOLVIMENTO]
Aqui, construiremos a solução integrada, conectando o SIEM, a IA e a plataforma de gerenciamento de incidentes. Também discutiremos como personalizar e expandir as funcionalidades para atender a diferentes necessidades.

---

Este projeto é ideal para equipes de segurança que desejam implementar uma solução poderosa de SOC utilizando apenas ferramentas de código aberto, combinando o poder da inteligência artificial com práticas avançadas de gerenciamento de incidentes.
