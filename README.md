# heart-disease-prediction，《数据科学前沿分析研究》课程期末作业

心脏病预测多模型对比实验，作业如下：


# 基于结构化临床指标的心脏病患病预测模型对比研究
本研究在心脏病结构化数据集上，对比传统机器学习与表格深度学习模型的预测效果，包含逻辑回归、KNN、SVM、随机森林、XGBoost、MLP、TabNet、FT-Transformer共8种模型。

## 实验结果汇总
| Model               | Accuracy | 5-fold CV AUC |
|---------------------|----------|---------------|
| Logistic Regression | 0.8009   | 0.8131 ± 0.0169 |
| KNN                 | 0.7856   | 0.8436 ± 0.0207 |
| SVM                 | 0.8337   | 0.8631 ± 0.0154 |
| Random Forest       | 0.8731   | 0.9328 ± 0.0123 |
| XGBoost             | 0.8643   | 0.9270 ± 0.0118 |
| MLP                 | 0.8043   | 0.8475 ± 0.0178 |
| TabNet              | 0.7798   | 0.8467 ± 0.0207 |
| FT-Transformer      | 0.6652   | 0.7564 ± 0.0306 |

## 文件说明
- `paper.pdf`：完整课程论文，包含研究背景、方法、结果、讨论、参考文献
- `results/roc_all_models.png`：8个模型ROC对比图
- `src/heart-disease-8models-final.ipynb`：完整实验源代码。代码适配Kaggle Notebook环境，依赖Kaggle平台数据集。
> 所有结果已经导出静态图表，**无需运行代码即可查看全部结果**
