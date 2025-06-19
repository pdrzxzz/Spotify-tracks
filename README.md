# Report: Hyperparameter Optimization and Model Comparison - Spotify Tracks 🎵📊  

**Professor:** Leandro Maciel Almeida  
**Student:** Emanuel Pedroza  

---  

## Objective 🎯  

Train, optimize, and evaluate **K-NN**, **LVQ**, and **SVM** models using the **Spotify Tracks** dataset, analyzing the impact of hyperparameter selection on performance and comparing models to determine the most efficient one.  

---  

## 1. Data Preprocessing 🛠️  

### 1.1. Loading  
- Dataset imported from HuggingFace: `spotify-tracks-dataset`.  

### 1.2. Cleaning  
- Removed columns: `Unnamed: 0`, `track_id`, `artists`, `album_name`, `track_name`.  

### 1.3. Missing Values  
- The dataset **contains no missing values**. ✅  

### 1.4. Categorical Encoding  
- Categorical variables encoded using `LabelEncoder`.  

### 1.5. Data Splitting  
- Numerical features standardized with `StandardScaler` (Z-score), ensuring no **data leakage** between train/validation/test sets.  

### 1.6. Normalization  
- **Train**: 70%  
- **Validation**: 15%  
- **Test**: 15%  

---  

## 2. Hyperparameter Tuning (Grid Search) ⚙️  

### 2.1. K-Nearest Neighbors (K-NN)  
- **Tested Hyperparameters**:  
  - `n_neighbors = [1, 3, 7, 13, 21, 30]`  
  - `weights = ['uniform', 'distance']`  
  - `metric = ['euclidean', 'manhattan', 'minkowski']`  

- **Best Configuration**:  
  - `n_neighbors = 30`  
  - `weights = 'distance'`  
  - `metric = 'manhattan'`  

### 2.2. Learning Vector Quantization (LVQ)  
- Implemented manually via **Object-Oriented Programming**.  
- **Tested Hyperparameters**:  
  - `n_prototypes = [1, 2]`  
  - `initial_lr = [10, 1, 0.1]`  

- **Best Configuration**:  
  - `n_prototypes = 1`  
  - `initial_lr = 0.1`  

### 2.3. Support Vector Machine (SVM)  
- **Tested Hyperparameters**:  
  - `C = [0.1, 1, 10]`  
  - `kernel = ['linear', 'rbf']`  
  - `gamma = ['scale']`  

- **Best Configuration**:  
  - `C = 1`  
  - `kernel = 'rbf'`  
  - `gamma = 'scale'`  

---  

## 3. Model Evaluation & Comparison 📈  

> Full metrics (including confusion matrices) generated using `classification_report` and `confusion_matrix`.  

---  

## 4. Key Findings & Conclusions 🏆  

- **SVM** achieved the **highest overall performance** (accuracy & F1-score), excelling in **multi-class classification**.  
- **K-NN** showed **moderate performance** with **low computational complexity**, making it a simple yet effective choice.  
- **LVQ**, despite its educational value, underperformed compared to SVM/K-NN but provided insights into prototype-based learning.  
- Hyperparameter tuning **significantly impacted results**, reinforcing the need for **cross-validation**.  

### Final Recommendations 🚀  

For **music genre classification** in the **Spotify Track Genre** dataset:  
- **SVM** is the **top choice** for high accuracy and robustness.  
- **K-NN** is ideal for **lightweight, interpretable** solutions.  
- **LVQ** remains useful for **educational purposes** or prototype analysis.  

---  
