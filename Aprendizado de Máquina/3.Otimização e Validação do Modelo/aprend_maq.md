# Otimização e Validação do Modelo

**1.Otimização dos hiperparâmetros dos modelos para melhorar a performance:**

Nesta etapa foi feita a validação do modelo escolhido, as técnicas utilizadas foram a Grid Search e a validação cruzada para avaliar o desempenho.

**Bibliotecas utilizadas.**
````phyton
# importação das bibliotecas.
from sklearn.model_selection import cross_val_score
from sklearn.model_selection import GridSearchCV
````
### Grid Search
````phyton
parametros = {'n_estimators': [50, 100, 150], 'max_depth': [None, 10, 20]}
grid_search = GridSearchCV(RandomForestClassifier(), parametros, cv=5)`
````

### Validação cruzada.

````phyton
pontuacoes = cross_val_score(grid_search, X, y, cv=5)
print(pontuacoes)

# resultado da validação cruzada
[0.99865374 0.99973068 1.         1.         1.        ]
````