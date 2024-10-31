# TempControl: Otimização de Consumo de Energia com Deep Q-Learning

## Visão Geral

Este repositório contém o código-fonte para o projeto TempControl, um sistema de gerenciamento de temperatura para data centers, utilizando Python, Streamlit e uma API RESTful, com a inclusão de Deep Q-Learning para otimizar o consumo de energia.

## Arquitetura

O TempControl utiliza uma arquitetura de microsserviços com:

1. **Frontend (Streamlit):** Interface para visualização e interação.
2. **Backend (API):** API RESTful que fornece acesso aos dados simulados do datacenter.
3. **Deep Q-Learning (DQN):** Modelo de aprendizado por reforço para otimizar o gerenciamento de temperatura do datacenter.

## Implementação

* **Frontend (Streamlit):**
    * `frontend/app.py`: Arquivo principal do dashboard, responsável por:
        * Carregar componentes do Streamlit.
        * Definir a UI com botões, sliders, gráficos e informações.
        * Realizar requisições à API do backend para obter dados e controlar o DQN.
        * Atualizar a UI com os dados recebidos.
    * `frontend/components/temperature_chart.py`: Define o componente gráfico para visualização da temperatura do servidor.
* **Backend (API):**
    * `backend/api.py`: Arquivo principal da API, responsável por:
        * Simular o comportamento do datacenter, incluindo as variáveis internas e externas.
        * Implementar lógica para receber requisições do frontend, processar os dados e retornar dados em formato JSON.
        * Interagir com o DQN para receber ações de controle de temperatura.
    * `backend/dqn.py`:  Implementa o modelo Deep Q-Learning, incluindo:
        * A rede neural que mapeia estados para valores Q.
        * A memória de experiência para guardar as experiências passadas.
        * O algoritmo de aprendizado para atualizar os pesos da rede neural.
        *  A função de recompensa que guia o aprendizado do DQN.
    * `backend/tests/test_api.py`: Arquivo para testes unitários da API.
    * `backend/requirements.txt`: Lista das dependências do projeto.

## Simulação do Datacenter

O sistema simula um datacenter do Google GCP, incluindo:

* **Variáveis Internas:** Temperatura do servidor, uso da CPU, memória, disco.
* **Variáveis Externas:** Temperatura ambiente, consumo de energia, capacidade do sistema de ar condicionado.

## Simulação Climática

O sistema simula o clima de Londres entre 2020 e 2024, com um aumento gradual da temperatura ambiente, atingindo o pico de 42.9°C em 15 de agosto de 2024.

## Mecanismos de Proteção

A simulação inclui mecanismos de proteção do Google GCP London:

* **Desligamento ou redução de capacidade dos servidores:**  Ativado quando a temperatura dos servidores ultrapassa o limite crítico.
* **Redirecionamento de tráfego:** O tráfego pode ser redirecionado para outros data centers em caso de superaquecimento generalizado.
* **Sistemas de refrigeração de emergência:** Ativados em caso de falha do sistema de ar condicionado ou temperaturas muito altas.

## Dependências

flask
requests
keras
tensorflow

## Instalação das Dependências

pip install -r requirements.txt

## Testes

pytest backend/tests

## Logs

O sistema gera logs para monitoramento e depuração, utilizando a biblioteca logging.

## Documentação

Para acessar a documentação, acesse a pasta docs/.

## Melhorias Futuras

Integração com dados reais do Google GCP London: Utilizar dados climáticos reais e informações de uso dos servidores.
Otimização do DQN: Explorar diferentes arquiteturas de rede neural, funções de recompensa e estratégias de treinamento para melhorar o desempenho do DQN.
Implementação de técnicas de inferência distribuída: Distribuir o DQN em vários servidores para acelerar o treinamento e a inferência.
Integração com sistemas de gerenciamento de infraestrutura: Integrar o TempControl com sistemas de gerenciamento de infraestrutura do Google GCP para automação do gerenciamento de temperatura.

## Observações

Validação do Deep Learning:
Certifique-se de 
