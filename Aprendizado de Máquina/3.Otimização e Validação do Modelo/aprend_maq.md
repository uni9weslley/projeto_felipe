# Otimização e Validação do Modelo

**1.Otimização dos hiperparâmetros dos modelos para melhorar a performance:**

Nesta etapa, foi utilizado o algoritimo de "LinearRegression", para fazer a prevenção de vendas de acordo com os valores vendidos. Utilizando os filtros de limpeza que foram utilizados na Matriz confusão.

**Bibliotecas utilizadas.**
````phyton
# importação das bibliotecas.
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
from sklearn.model_selection import cross_val_score
````
**Treinando o modelo de previsoes**
````phyton
# definindo as variaveis de entrada e de saida.
X = data.drop(columns=['Valor', 'ID Cliente','Data da fatura', 'País','Ano mes'])
y = data['Valor']

# dividindo os conjuntos para treinar.
X_train, X_val, y_train, y_val = train_test_split(X, y, test_size=0.3, random_state=42)

# Criando uma instância do modelo de regressão linear
model = LinearRegression()

# trinando o modelo e fazendo as previsões,
model.fit(X_train, y_train)
predictions = model.predict(X_val)


````
**Calculo das métricas**

````phyton
# calculando as metricas.
mae = mean_absolute_error(y_val, predictions)
mse = mean_squared_error(y_val, predictions)
rmse = mean_squared_error(y_val, predictions, squared=False)  
r2 = r2_score(y_val, predictions)

# Exibindo as métricas
print("Erro Médio Absoluto (MAE):", mae)
print("Erro Quadrático Médio (MSE):", mse)
print("Raiz do Erro Quadrático Médio (RMSE):", rmse)
print("R-quadrado (R²):", r2)
````
#### Resultado do calculo das métricas

- Erro Médio Absoluto (MAE): 209.5681814796844
- Erro Quadrático Médio (MSE): 1134665.2307438026
- Raiz do Erro Quadrático Médio (RMSE): 1065.206661049302
- R-quadrado (R²): 0.5115444142576595

## Grafíco gerado da previsão

**Grafíco do modelo**
![img](/Aprendizado%20de%20Máquina/3.Otimização%20e%20Validação%20do%20Modelo/baixados.png)

Esta grafíco mostra a previsão de vendas de acordo com o valor. 

### Validação cruzada.

````phyton
cv_pred = cross_val_score(model, X, y)
print("\nValidação cruzada: \n{0} ".format(cv_knn))
````
**Resultado da validação**

Validação cruzada:

[0.53619067 , 0.680733  , 0.57093758 , 0.6932718 , 0.81977309] 