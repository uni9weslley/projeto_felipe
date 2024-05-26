# Análise Descritiva dos Dados

A análise descritiva dos dados é uma etapa fundamental em qualquer projeto de análise de dados. Vamos explorar alguns pontos importantes para analizarção de dados:

**1. Técnicas Estatísticas Básicas para Descrever os Dados:**

- A análise descritiva envolve calcular medidas estatísticas que resumem as características dos dados. Alguns exemplos incluem:

    - Média (ou valor médio): Calcula a média dos valores em uma variável.
    - Mediana: Encontra o valor central dos dados.
    - Desvio padrão: Mede a dispersão dos dados em torno da média.
    - Quartis: Divide os dados em quartis (25%, 50% e 75%).    

Essas estatísticas nos ajudam a entender a distribuição dos dados e identificar possíveis outliers.

**2. Visualização de Dados com Matplotlib e Seaborn:**

- O Matplotlib e o Seaborn são bibliotecas populares em Python para criar gráficos e visualizações.

- Com o Matplotlib, você pode criar gráficos de linhas, barras, dispersão, histogramas e muito mais.
- O Seaborn é uma extensão do Matplotlib que oferece estilos predefinidos e funções mais simples para criar gráficos estatísticos, como gráficos de caixa e violino.
- Essas bibliotecas nos permitem visualizar padrões, tendências e relações nos dados.

**3. Identificação de Padrões e Tendências nos Dados:**
- Ao analisar os dados, procuramos por padrões e tendências que possam nos fornecer insights.
Isso pode incluir:
    - Identificar sazonalidades em séries temporais.
    - Encontrar correlações entre variáveis.
    - Detectar clusters ou agrupamentos.
    - Observar mudanças ao longo do tempo.
- Gráficos e estatísticas descritivas nos ajudam a identificar esses padrões.

Com tudo, podem acontecer alguns erros. Como por exemplo:


**overfitting**
--
Overfitting é quando, após o treino, o teste e a validação, seja feita ele demonstra padrões muito corretos, fazendo que as próximas validações tenham seus resultados sempre semelhantes ou iguais. Isso ocorre por alguns motivos tais como, poucos dados para teste, outra casa possa ser que haja muitos parâmetros  trazendo uma complexidade para tais modelos.

Para saber se o modelo está em overfitting, pode ser quando há muitos parâmetros, fazendo com que o modelo memorize padrões gerando previsões erradas, alto desempenho e baixo desempenho também é uma questão de overfitting pois também podem gerar padrões errados.

Métricas para evitar o overfitting, é ter uma boa base de dados grande o suficiente, e manter o modelo com poucos parâmetros para ser treinado, outras técnicas que podem ser utilizadas são: regularização, validação cruzada, seleção de recursos ou parar o treinamento antecipadamente.
