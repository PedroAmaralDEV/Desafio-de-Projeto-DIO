# Desafio-de-Projeto-DIO
Repositório para conclusão de desafio de código do Bootcamp DIO
🍦 Projeto Gelato Mágico: Previsão de Demandas com Azure Automated ML
"Machine Learning sem código, resultados rápidos e eficientes na nuvem."

Este repositório documenta o desenvolvimento de uma solução de Inteligência Artificial para a sorveteria "Gelato Mágico". O objetivo é prever o volume de vendas diárias de sorvete com base na previsão da temperatura, permitindo um planejamento de estoque mais inteligente, reduzindo desperdícios e maximizando lucros.

A solução foi construída integralmente utilizando a abordagem No-Code (sem código) através do recurso de Automated Machine Learning (AutoML) do Microsoft Azure.

🎯 O Desafio de Negócio
A "Gelato Mágico", localizada em uma cidade litorânea, enfrenta o desafio clássico de produtos perecíveis: a demanda varia drasticamente com o clima.

Problema: Produzir sorvete demais em dias frios gera desperdício; produzir de menos em dias quentes gera perda de receita.

Solução: Criar um modelo preditivo que, dado a temperatura prevista para o dia seguinte, estime a quantidade de vendas.

Abordagem Técnica: Utilizar o poder da nuvem Azure para testar automaticamente múltiplos algoritmos de IA e encontrar o melhor modelo para nossos dados, sem necessidade de programação manual.

🛠️ Tecnologias Utilizadas
Microsoft Azure Machine Learning Studio

Azure Automated ML: Para treinamento e seleção automática de modelos.

Azure Data Assets: Para gerenciamento do conjunto de dados na nuvem.

Managed Online Endpoints (Opcional): Para implantação do modelo em tempo real.

🚀 O Processo de Desenvolvimento no Azure
O fluxo de trabalho foi realizado inteiramente na interface visual do Azure ML Studio, seguindo as etapas abaixo:

1. Preparação dos Dados (Data Asset)
O primeiro passo foi carregar o histórico de vendas e temperaturas (dados_sorvete.csv) para a nuvem, criando um "Ativo de Dados" registrado no Azure ML. Isso garante que os dados estejam versionados e acessíveis para o treinamento.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7a207770-4b04-4509-9598-bc685bd40a87" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/920d953e-377e-4835-b405-34e4778cb504" />




2. Configuração do Automated ML
Um novo trabalho de Automated ML foi configurado com os seguintes parâmetros chave:

Tipo de Tarefa: Regressão (pois queremos prever um valor numérico contínuo: a quantidade de vendas).

Conjunto de Dados: O ativo de dados criado na etapa anterior.

Coluna Alvo (Target Column): Vendas (o valor que queremos prever).

Métrica Primária: [Insira a métrica que você escolheu, ex: Normalized Root Mean Squared Error (NRMSE) ou R2 Score].

Configuração de Computação: Utilizado um cluster de computação serverless para processar o treinamento.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/afc6a3bc-9e7f-42b7-ad4b-4f2798bbc135" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c9bcd7a8-d1cd-428a-9a6c-f8a6ce1ab46d" />

3. Treinamento e Seleção do Melhor Modelo
O Azure Automated ML testou dezenas de algoritmos diferentes (como Regressão Linear, LightGBM, Random Forest, etc.) e aplicou diferentes técnicas de normalização de dados automaticamente.

Ao final do processo, o Azure gerou um ranking (leaderboard) dos modelos que tiveram melhor desempenho com base na métrica escolhida.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ebc1da51-b6ed-4729-975e-e796f2ccc3a9" />


4. Análise dos Resultados e Interpretabilidade
O melhor modelo identificado foi um VotingEnsemble
Métricas Alcançadas:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/77108045-956b-4fd2-9636-ddb7b6934de8" />


Interpretabilidade (Feature Importance): Uma vantagem do Azure AutoML é a capacidade de explicar por que o modelo toma suas decisões. O gráfico de importância de atributos abaixo confirma nossa hipótese de negócio: a Temperatura é, de longe, o fator mais determinante para prever as Vendas.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5fde95b5-12a4-454e-ab19-a43a408789a1" />


5. Implantação (Deployment)

Com apenas um clique na interface do Azure ML, o melhor modelo foi implantado em um Managed Online Endpoint. Isso criou uma API REST em tempo real. Agora, o sistema da sorveteria pode enviar a temperatura prevista e receber instantaneamente a previsão de vendas.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c75057af-3448-4284-9a61-325b02cbebe5" />


🧠 Conclusão e Aprendizados
Este projeto demonstrou a eficácia do Automated ML para resolver problemas de negócios reais rapidamente.

Velocidade: Em poucos minutos, foi possível testar modelos que levariam horas ou dias para serem codificados e ajustados manualmente.

Qualidade: O recurso de "Ensemble" (combinação de modelos) do Azure geralmente supera modelos individuais criados manualmente por iniciantes.

Foco no Negócio: A abordagem No-Code permite que o profissional foque na qualidade dos dados e na interpretação dos resultados para a tomada de decisão, abstraindo a complexidade do código de treinamento.

📂 Estrutura de Arquivos
/data: Contém o arquivo CSV original utilizado para o upload no Azure.

/inputs: (Requisito de estrutura do desafio).

README.md: Este documento com o relatório do projeto.
