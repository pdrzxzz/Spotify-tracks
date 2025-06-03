# Relatório: Otimização de Hiperparâmetros e Comparação de Modelos - Spotify Tracks

**Professor:** Leandro Maciel Almeida  
**Aluno:** Emanuel Salgado Pedroza  

---

## Objetivo

Treinar, otimizar e avaliar os modelos **K-NN**, **LVQ** e **SVM** usando o dataset **Spotify Tracks**, compreendendo o impacto da escolha de hiperparâmetros no desempenho e comparando os modelos para determinar o mais eficiente.

---

## 1. Tratamento dos Dados

### 1.1. Carregamento

- Dataset importado da HuggingFace: `spotify-tracks-dataset`.

### 1.2. Limpeza

- Colunas removidas: `Unnamed: 0`, `track_id`, `artists`, `album_name`, `track_name`.

### 1.3. Valores Ausentes

- O dataset **não apresenta valores ausentes**.

### 1.4. Codificação de Variáveis Categóricas

- Todas as variáveis categóricas foram codificadas usando `LabelEncoder`.

### 1.5. Divisão dos Dados

- Atributos numéricos foram padronizados com `StandardScaler` (Z-score), respeitando a separação de treino, validação e teste para evitar **data leakage**.

### 1.6. Normalização

- Treino: **70%**  
- Validação: **15%**  
- Teste: **15%**

---

## 2. Busca por Hiperparâmetros (Grid Search)

### 2.1. K-Nearest Neighbors (K-NN)

- **Hiperparâmetros testados**:
  - `n_neighbors = [1, 3, 7, 13, 21, 30]`
  - `weights = ['uniform', 'distance']`
  - `metric = ['euclidean', 'manhattan', 'minkowski']`

- **Melhor configuração**:
  - `n_neighbors = 30`
  - `weights = 'distance'`
  - `metric = 'manhattan'`

### 2.2. Learning Vector Quantization (LVQ)

- Implementação manual via **Programação Orientada a Objetos**.
- **Hiperparâmetros testados**:
  - `n_prototypes = [1, 2]`
  - `initial_lr = [10, 1, 0.1]`

- **Melhor configuração**:
  - `n_prototypes = 1`
  - `initial_lr = 0.1`

### 2.3. Support Vector Machine (SVM)

- **Hiperparâmetros testados**:
  - `C = [0.1, 1, 10]`
  - `kernel = ['linear', 'rbf']`
  - `gamma = ['scale']`

- **Melhor configuração**:
  - `C = 1`
  - `kernel = 'rbf'`
  - `gamma = 'scale'`

---

## 3. Avaliação e Comparação dos Modelos

> As métricas completas (incluindo matriz de confusão) foram geradas com `classification_report` e `confusion_matrix`.

---

## 4. Conclusões

- **SVM** apresentou o **melhor desempenho geral**, especialmente na **acurácia** e **F1-score**, sendo mais robusto para classificação multiclasse.
- O **K-NN** teve desempenho intermediário, com bons resultados e **baixa complexidade computacional**.
- O **LVQ**, apesar da implementação manual, teve **valor didático** e desempenho competitivo, mas inferior aos outros modelos.
- A escolha dos hiperparâmetros teve **impacto claro na performance**, reforçando a importância da **validação cruzada**.

### Considerações Finais

No contexto da classificação de gêneros musicais com base nos atributos numéricos do dataset **Spotify Track Genre**:

- **SVM** se destacou como o modelo mais eficaz, especialmente em cenários com múltiplas classes e dados padronizados.
- **K-NN** mostrou-se uma opção viável quando se busca simplicidade e interpretabilidade.
- **LVQ**, embora com menor desempenho global, pode ser útil em contextos com distribuição clara de classes e quando se deseja controle direto sobre protótipos.

Para aplicações práticas como **recomendação, categorização** ou **análise musical**, o **SVM** é o mais indicado, enquanto o **K-NN** é uma alternativa leve e o **LVQ** serve como ferramenta exploratória ou educacional.
