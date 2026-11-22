# 基于结构化临床指标的心脏病患病预测模型对比研究
《数据科学前沿分析研究》课程期末作业

## 研究简介
心血管疾病负担沉重，机器学习与表格深度学习为辅助筛查提供了可行方案。本研究基于多源整合心脏病临床结构化数据集，对比传统机器学习与表格专用深度学习模型在二分类预测任务上的性能，探讨TabNet、FT-Transformer这类注意力表格深度模型在中小规模临床队列上的适用性。

## 数据集
数据集来源：Kaggle heart-disease-multi-source-dataset，
数据集链接：https://www.kaggle.com/datasets/alifsathar/heart-disease-multi-source-dataset，
数据集说明：整合Cleveland、Hungary、Switzerland、VA Long Beach四个经典心脏病公开队列，经过字段对齐、去重，共2283条样本；输入包含年龄、性别、胸痛类型、静息血压、胆固醇等14项临床特征，任务为心脏病患病状态二分类。

## 对比模型清单（共8个）
传统机器学习：
- Logistic Regression（逻辑回归）
- KNN
- SVM(RBF核)
- Random Forest（随机森林）
- XGBoost

表格深度学习模型：
- MLP（多层感知机）
- TabNet
- FT-Transformer

## 实验设置
- 划分方式：训练集/测试集划分 + 5折交叉验证
- 评价指标：Accuracy、Precision、Recall、F1-score、5-fold CV AUC
- 工具：Python, scikit-learn, PyTorch, Jupyter Notebook
- 评价标准：以交叉验证AUC作为模型泛化性能主要参考指标

## 实验结果汇总
| Model             | Accuracy | Precision | Recall | F1-score | 5-fold CV AUC |
|-------------------|----------|-----------|--------|----------|---------------|
| Logistic Regression | 0.8009   | 0.80      | 0.84   | 0.82     | 0.8131 ± 0.0169 |
| KNN               | 0.7856   | 0.79      | 0.83   | 0.81     | 0.8436 ± 0.0207 |
| SVM               | 0.8337   | 0.84      | 0.87   | 0.85     | 0.8631 ± 0.0154 |
| Random Forest     | 0.8731   | 0.88      | 0.90   | 0.89     | 0.9328 ± 0.0123 |
| XGBoost           | 0.8643   | 0.87      | 0.89   | 0.88     | 0.9270 ± 0.0118 |
| MLP               | 0.8043   | 0.81      | 0.85   | 0.83     | 0.8475 ± 0.0178 |
| TabNet            | 0.7798   | 0.79      | 0.82   | 0.80     | 0.8467 ± 0.0207 |
| FT-Transformer    | 0.6652   | 0.68      | 0.70   | 0.69     | 0.7564 ± 0.0306 |

## 核心结论
在该中小规模多源临床结构化数据集上，**随机森林、XGBoost等树集成模型泛化性能最优**；TabNet、FT-Transformer等基于注意力机制的表格深度学习模型并未体现优势，FT-Transformer效果明显下降，说明这类深度模型对样本量、数据分布偏移更加敏感，不一定天然适合中小规模临床队列。

## 复现指南
1. 下载本仓库的 `heart-disease-8models-final.ipynb`
2. 下载Kaggle数据集，放入对应路径
3. 推荐在Kaggle Notebook或者本地Jupyter环境运行
4. 依赖包：numpy, pandas, scikit-learn, torch, matplotlib, seaborn

## 局限性
数据集由多中心历史队列拼接而成，存在中心间分布偏移；仅使用静态横断面结构化特征，未纳入时序、影像等多模态信息；仅为公开数据集回顾性实验，不能直接用于临床诊断。

## 论文
配套课程研究论文：heart_disease_prediction_paper.pdf
