# Hiperparametros.

Hiperparâmetros são configurações que controlam o processo de treinamento e o comportamento de modelos de machine learning. Ao contrário dos parâmetros do modelo que são aprendidos durante o treinamento, os hiperparâmetros devem ser definidos antes que o treinamento comece.

Alguns exemplos comuns de hiperparâmetros incluem:

Número de árvores em um modelo Random Forest
Taxa de aprendizado em redes neurais
Profundidade máxima de árvores de decisão
Penalidade de regularização em regressões

Ajustar adequadamente os hiperparâmetros permite que os cientistas de dados controlem o treinamento do modelo e melhorem seu desempenho. Modelos com hiperparâmetros bem calibrados tendem a ter menor overfitting e maior acurácia nos dados de teste.


Por que otimizar hiperparâmetros?

A otimização de hiperparâmetros é importante por alguns motivos:


Melhora o desempenho do modelo em dados não vistos anteriormente, aumentando a acurácia nos dados de teste.
Reduz o overfitting, fazendo com que o modelo generalize melhor para novas amostras de dados.
Faz o modelo se comportar mais próximo do ideal para o problema que está sendo modelado.
Diminui o erro na predição, tanto o viés quanto a variância.
Encontra o equilíbrio certo entre viés e variância para um bom desempenho.

Modelos com hiperparâmetros otimizados tendem a ter melhor acurácia, menor overfitting e maior robustez. Por isso, é uma etapa crucial no desenvolvimento de qualquer solução de machine learning.

Técnicas de otimização de hiperparâmetros

Existem várias abordagens que podem ser utilizadas para encontrar os melhores valores de hiperparâmetros para um determinado modelo e conjunto de dados. As principais são:


Grid Search
Random Search
Bayesian Optimization
Hyperband
Genetic Algorithms

Neste ebook, vamos focar nas duas primeiras, que são as mais simples e amplamente utilizadas: Grid Search e Random Search.

Grid Search

O Grid Search realiza uma busca exaustiva dos melhores parâmetros em uma grade (grid) pré-definida de valores. É um método simples, porém computacionalmente caro.

O processo consiste em:


Definir os hiperparâmetros que serão otimizados e seus respectivos valores que serão testados.
Criar todas as combinações possíveis desses parâmetros.
Treinar um modelo com cada combinação de hiperparâmetros.
Avaliar o desempenho de cada modelo treinado.
Escolher a combinação de hiperparâmetros que obteve o melhor desempenho.

O desempenho de cada modelo é avaliado com uma métrica como acurácia, erro quadrático médio, área sob a curva ROC etc. Escolhe-se os hiperparâmetros do modelo que otimizou esta métrica.

Por testar exaustivamente todas as combinações, o Grid Search garante que os melhores hiperparâmetros serão encontrados dentro dos valores fornecidos. Porém, tem um custo computacional muito alto.

Exemplo de Grid Search com dois hiperparâmetros, cada um com dois valores possíveis:

Hiperparâmetro 1:
- Valor 1
- Valor 2

Hiperparâmetro 2:
- Valor A
- Valor B

Combinações testadas:
- Valor 1 + Valor A
- Valor 1 + Valor B
- Valor 2 + Valor A
- Valor 2 + Valor B


Neste caso simples já são necessários 4 treinamentos. Conforme mais hiperparâmetros e valores são adicionados, o número de combinações cresce exponencialmente.

Random Search:

O Random Search resolve o problema de alto custo computacional do Grid Search fazendo uma busca aleatória pelos hiperparâmetros.

Ao invés de testar todas as combinações possíveis, o Random Search testa um subconjunto aleatório delas dentro das faixas definidas para cada parâmetro.

O processo é:

Definir os hiperparâmetros e faixas de valores para busca.
Gerar aleatoriamente várias combinações de valores dentro das faixas.
Treinar modelos com as combinações aleatórias de hiperparâmetros.
Avaliar o desempenho de cada modelo.
Escolher os hiperparâmetros do modelo com melhor desempenho.

O Random Search encontra uma solução suficientemente boa em um tempo muito menor do que o Grid Search. Porém, não garante que os hiperparâmetros globais ótimos serão encontrados.

Geralmente o Random Search é executado várias vezes, intercalando com o treinamento de modelos para melhorar gradativamente a solução.

Grid Search no Scikit-Learn

O Scikit-Learn possui a classe GridSearchCV que automatiza o processo de Grid Search.

Os principais parâmetros do GridSearchCV são:


estimator - O modelo que será otimizado.
param_grid - Dicionário com os nomes dos hiperparâmetros e lista de valores para busca.
scoring - Métrica para avaliar o desempenho nos conjuntos de validação.
cv - Número de folds para validação cruzada.
n_jobs - Número de cores de CPU para paralelização.
