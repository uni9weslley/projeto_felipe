# Implementação de Modelos de Aprendizado de Máquina

### Escolha de algoritmos de ML adequados ao problema:
Nesta etapa foi escolhido o algoritimo do  KMeans, para verificação de vendas em um determinado periodo. Utilizando os filtros de limpeza que foram utilizados na Matriz confusão.  

**1. importando as bibliotecas utilizadas.**
```phyton
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler 
```
```
# importando dataframe localizado na pasta
data = pd.read_csv('/content/sample_data/vendas-por-fatura.csv')
```
### Implementação dos modelos escolhidos utilizando bibliotecas como Scikit-learn

**2.Aqui é o treinamento do modelo escolhido.**

````phyton
# Selecionando as características para clustering
X = data.drop(['Data da fatura','País','Ano mes'], axis=1)
# Normalizando os dados
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
# Escolhendo o número de clusters (neste caso, vamos escolher 2)
n_clusters = 2
# Adicionando os rótulos dos clusters ao conjunto de dados
data['cluster'] = kmeans.labels_
````

### Avaliação da performance dos modelos com métricas apropriadas:
**3.Aqui o resultado gerado pelo modelo.**

````phyton
# Visualizando os centros dos clusters
print("Centros dos Clusters:")
print(scaler.inverse_transform(kmeans.cluster_centers_))
````

**Resultado dos centros de clusters.**

Centros dos Clusters:

[[5.59906978e+05 1.38506283e+04 3.05965948e+02 5.19171920e+02
  2.03293352e-04]
  
 [5.59072329e+05 1.68616147e+04 2.48808776e+02 4.35815141e+02
  2.00000000e+00]]

**E por fim o grafíco gerado.**

````phyton
# Plotando os clusters
plt.figure(figsize=(10, 6))

for cluster in range(n_clusters):
    cluster_data = data[data['cluster'] == cluster]
    plt.scatter(cluster_data['ID Cliente'], cluster_data['Valor'], label=f'Cluster {cluster}')

plt.title('Valor de venda feita por fatura\n determinado periodo ')
plt.xlabel('ID Cliente')
plt.ylabel('Valor')
plt.legend()
plt.show()
````

![img](/Aprendizado%20de%20Máquina/2.Modelos%20de%20Aprendizado%20de%20Máquina/tabela_vendas.png)

Essa tabela mostra as vendas no começo de 2024