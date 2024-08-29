# Construindo um Laboratório de SOC Open Source com IA

## Visão Geral
Este repositório documenta o processo de construção de um laboratório de Security Operations Center (SOC) open source, com foco na automatização da análise de alertas utilizando inteligência artificial.

## Parte II: Configuração do SIEM

### Introdução
Nesta parte, abordamos a configuração do Elastic SIEM para o envio e análise de logs.

### Objetivos
* Configurar o envio de logs para o elasticsearch
* Criar regras de detecção personalizadas

### Pré-requisitos
* Instância do Elastic Stack (Elasticsearch, Kibana) instalada
* Conhecimento básico de SIEM e Elastic Stack

## Teoria
1. **Introdução:**
      [![Introdução sobre o projeto](https://img.youtube.com/vi/p9bnK8c76_U/maxresdefault.jpg)](https://youtu.be/p9bnK8c76_U?feature=shared)
---
2. **Formas de envio de log:**
   - **Beats**: Agentes leves instalados em diversas máquinas para coletar e enviar logs para o sistema centralizado.
   - **Fleet server**: Um servidor que gerencia e configura os Beats em diferentes máquinas.
   - **Fluentd**: Um agente de coleta de logs que pode ser configurado para enviar logs para diversos destinos, incluindo o sistema centralizado.

   [![Formas de envio de log](https://img.youtube.com/vi/v1Wrn_CwStk/maxresdefault.jpg)](https://youtu.be/p9bnK8c76_U?feature=shared)
--- 
3. **Instalação dos agentes (beat)**
   - [Auditbeat](https://github.com/carlossilva9867/soc-opensource-ia/blob/main/PARTE%202%20-%20CONFIGURA%C3%87%C3%83O/SIEM/002%20-%20Instala%C3%A7%C3%A3o%20-%20auditbeat.md)
   - [Winlogbeat](https://github.com/carlossilva9867/soc-opensource-ia/blob/main/PARTE%202%20-%20CONFIGURA%C3%87%C3%83O/SIEM/003%20-%20Instala%C3%A7%C3%A3o%20-%20winlogbeat.md)
---
## Prática
3. **Consumo de alertas:**
   [![OLLAMA](https://img.youtube.com/vi/_pajqTdyLkU/maxresdefault.jpg)](https://youtu.be/_pajqTdyLkU)
4. **Integração com IA:**
   [![OLLAMA](https://img.youtube.com/vi/_UNTCAl4pio/maxresdefault.jpg)](https://www.youtube.com/watch?v=_UNTCAl4pio)
5. **Geração de tickets no DFIR-IRIS:**
   [![OLLAMA](https://img.youtube.com/vi/hzK9muP8ST4/maxresdefault.jpg)](https://youtu.be/hzK9muP8ST4)
6. **Notificações:**
   (EM BREVE)


## Contribuições
Contribuições são bem-vindas! Por favor, abra um issue para discutir novas ideias ou funcionalidades.
