# Binary classification: ADME(PAMPA_NCATS) dataset

This tutorial illustrates how to predict the PAMPA permeability assay based on the SMILES string of a compound, using the supervised graph neural networks, the classical tree models, and the transformer models.

Following is a summary of the time spent on the project:
| Activity| Time (hrs) |
|-----------------|-------------|
| Familiarity with drug discovery datasets| 2-3 |
| Learning about GNN frameworks | 3-4|
| Programming  | 2-3 | 
| The documentation| 2-3|
| Learning PyG| 1 day|
| Total | 1 day & 9-13 (hrs)|

A dataset used in this project is [PAMPA](https://tdcommons.ai/single_pred_tasks/adme/#pampa-permeability-ncats)(one of the ADME subset databases). Here is a summary of the information related to this database:
| **PAMPA Dataset**| **info**|
|-----------------|-------------|
| **Dataset Description**| PAMPA (parallel artificial membrane permeability assay) is a commonly employed assay to evaluate drug permeability across the cellular membrane. PAMPA is a non-cell-based, low-cost and high-throughput alternative to cellular models. Although PAMPA does not model active and efflux transporters, it still provides permeability values that are useful for absorption prediction because the majority of drugs are absorbed by passive diffusion through the membrane. |
| **Dataset Statistics:** | NCATS set - 2035 compounds; Approved drugs set - 142 drugs.|
| **References** | [1] Siramshetty, V.B., Shah, P., et al. “Validating ADME QSAR Models Using Marketed Drugs.” SLAS Discovery 2021 Dec;26(10):1326-1336. doi: 10.1177/24725552211017520. | 
| **Dataset License**| Not Specified. CC BY 4.0.|

There are different frameworks to model GNN algorithms including **PyG, DGL, DeepPurpose, Tf-gnn**, etc. In this project, we will use **PyG and DeepPurpose** as two of the best and most common gnn-ML frameworks in the field of drug discovery. 

**In total, 18 potential algorithms were evaluated in order to find the best combination of algorithms. Following are the steps taken for this project. A detailed description of each step is included in the project files.**

![ss](https://user-images.githubusercontent.com/62473531/208411413-3ac6f89d-8e73-4760-9714-90a7d448ec31.png)

Here is a summary of the final results:
| **Framework**| **Algorithms**| **F1_score** | **ROC-AUC** | **PR-AUC** |
|-------------|-------------|-------------|-------------|-------------|
|**xgboost+scikit-learn**| **XGBClassifier_results**| 92% | 0.57 | 0.85 |
|**DeepPurpose**| **DGL_GIN_ContextPred_results**| 91% | 0.76 | 0.92 |
|**DeepPurpose**| **Transformer_results**| 91% | 0.57 | 0.87 |
|**PyG**| **GCN-GraphConv**| 91.3% | 0.75 | 0.90 |

The metrics used for this project include:
* **[F1_Score](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html):** The F1 score can be interpreted as a harmonic mean of the precision and recall, where an F1 score reaches its **best value at 1 and worst score at 0**. 
* **[ROC-AUC](https://deepchecks.com/question/what-is-a-good-roc-curve-score/):** The area under the ROC curve (AUC) results were considered **excellent** for AUC values between **0.9-1**, **good** for AUC values between **0.8-0.9**, **fair** for AUC values between **0.7-0.8**, **poor** for AUC values between **0.6-0.7** and **failed** for AUC values between **0.5-0.6**.
* **[PR-AUC](https://neptune.ai/blog/f1-score-accuracy-roc-auc-pr-auc):** It is a curve that combines precision (PPV) and Recall (TPR) in a single visualization. In a perfect classifier, AUC-PR =1.The higher on y-axis your curve is the better your model performance.

According to the results, the best algorithms in order of performance are:
* **1)DGL_GIN_ContextPred**
* **2)GCN-GraphConv**
* **3)Transformer models** 
* **4)XGBClassifier**


**NOTE:** All the files have been designed end-to-end to run on Colab + GPU
