# Aprendizado de Máquina (Algoritmos de ML)

[DataSet utilizado:](https://www.kaggle.com/datasets/datacertlaboratoria/projeto-3-segmentao-de-clientes-no-ecommerce) estes dados contam com seis(6) colunas sendo elas de:
- N° da fatura
- Data da fatura
- ID Cliente
- País
- Quantidade
- Valor

retirado do site: [kaggle.com](https://www.kaggle.com/)


### Coleta de dados relevantes para o negócio proposto pela empresa:

**1. Importado os dados com pandas:**

```phyton
import pandas as pd

# importando dataframe localizado na pasta
data = pd.read_csv("/content/vendas-por-fatura.csv")
```
**2. Limpeza e pré-processamento dos dados:**

```phyton
# Removendo linhas com registro nulo na coluna 'ID_Cliente'
data = data.dropna(subset=["ID Cliente"])

# Removendo os dados duplicados do dataset, se houver
data.drop_duplicates(inplace=True)

# apresentando quantidade de linhas e colunas
data.shape

# filtrando todas as faturas que começam com 'C'
devolucao = data['N° da fatura'].str.startswith('C')

# verificando a quantidade de linhas identificadas
data[devolucao].shape

# fazendo a limpeza dos dados
data.drop(data[devolucao].index, inplace=True)

# Convertendo tipo da 'Data da Fatura' para data
data["Data da fatura"] = pd.to_datetime(data["Data da fatura"])

# alterando a separação dos valores de ',' para '.' na coluna Valor
data['Valor'] = data['Valor'].str.replace(",", ".")

# alterando o tipo da coluna 'Valor' para float
data['Valor'] = pd.to_numeric(data['Valor'])

# Obtendo Ano e Mês da data
data['Ano mes'] = data['Data da fatura'].dt.to_period('M')

# Ordenando pela Data da Fatura de maneira ascendente para facilitar nossas análises
data.sort_values(by=['Data da fatura'], inplace=True)

```

**1. Verificando a matriz confusão:**

```phyton
# Separar caracteristicas e alvo
X = data.drop(["Data da fatura", "País", "ID Cliente", "Ano mes"], axis=1)  # caracteristicas
y = data["ID Cliente"]  # alvo

# Converter a variável de destino em categórica para classificação
y = pd.cut(y, bins=3, labels=['baixo', 'médio', 'alto'])

# informações do dataset
data.info()

# Normalizar os dados
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

# Dividir o dataset em conjuntos de treinamento e validação
X_train, X_val, y_train, y_val = train_test_split(X_scaled, y, test_size=0.3, random_state=42)

# Escolher o modelo KNN para classificação
knn_cls = KNeighborsClassifier(n_neighbors=5)

# Treinar o modelo
knn_cls.fit(X_train, y_train)

# Prever as classes para o conjunto de validação
y_pred = knn_cls.predict(X_val)

# Calcular as métricas de avaliação
accuracy = accuracy_score(y_val, y_pred)
precision = precision_score(y_val, y_pred, average='weighted', zero_division='warn')
recall = recall_score(y_val, y_pred, average='weighted', zero_division='warn')
f1 = f1_score(y_val, y_pred, average='weighted', zero_division='warn')

print("Acurácia:", accuracy)
print("Precisão:", precision)
print("Recall:", recall)
print("F1-score:", f1)

# plotar a matriz confusão
cm = confusion_matrix(y_val, y_pred)
plt.figure(figsize=(8, 6))
sns.heatmap(cm, annot=True, fmt="d", cmap="Blues", cbar=False)
plt.xlabel('Predicted labels')
plt.ylabel('True labels')
plt.title('Confusion Matrix')
plt.show()
```

**Grafico gerado pela matriz confusão:**

![img](/Aprendizado%20de%20Máquina/Exploração%20de%20Dados%20e%20Pré-processamento/matriz_confusao.jpg)

Esse gráfico mostra o desempenho de compra de clientes durante um período.


**Esse é o codigo completo em phyton.**
```
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score, confusion_matrix
import matplotlib.pyplot as plt
import seaborn as sns

data = pd.read_csv("/content/vendas-por-fatura.csv")

data = data.dropna(subset=["ID Cliente"])

data.isnull().values.any()

data.drop_duplicates(inplace=True)
data.shape

devolucao = data['N° da fatura'].str.startswith('C')
data[devolucao].shape

data.drop(data[devolucao].index, inplace=True)

data["Data da fatura"] = pd.to_datetime(data["Data da fatura"])

data['Valor'] = data['Valor'].str.replace(",", ".")

data['Valor'] = pd.to_numeric(data['Valor'])

data['Ano mes'] = data['Data da fatura'].dt.to_period('M')

data.sort_values(by=['Data da fatura'], inplace=True)

X = data.drop(["Data da fatura", "País", "ID Cliente", "Ano mes"], axis=1)  
y = data["ID Cliente"]  

y = pd.cut(y, bins=3, labels=['baixo', 'médio', 'alto'])

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

X_train, X_val, y_train, y_val = train_test_split(X_scaled, y, test_size=0.3, random_state=42)

knn_cls = KNeighborsClassifier(n_neighbors=5)

knn_cls.fit(X_train, y_train)

y_pred = knn_cls.predict(X_val)

accuracy = accuracy_score(y_val, y_pred)
precision = precision_score(y_val, y_pred, average='weighted', zero_division='warn')
recall = recall_score(y_val, y_pred, average='weighted', zero_division='warn')
f1 = f1_score(y_val, y_pred, average='weighted', zero_division='warn')

print("Acurácia:", accuracy)
print("Precisão:", precision)
print("Recall:", recall)
print("F1-score:", f1)

cm = confusion_matrix(y_val, y_pred)
plt.figure(figsize=(8, 6))
sns.heatmap(cm, annot=True, fmt="d", cmap="Blues", cbar=False)
plt.xlabel('Predicted labels')
plt.ylabel('True labels')
plt.title('Confusion Matrix')
plt.show()
```