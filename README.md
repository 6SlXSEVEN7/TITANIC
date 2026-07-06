# TITANIC
Titanic - Machine Learning from Disaster

Kaggle 竞赛：[Titanic - Machine Learning from Disaster](https://www.kaggle.com/competitions/titanic)
课程作业 · 华南师范大学 数据科学与工程学院 大数据4班

## 项目简介

基于 Kaggle Titanic问题的数据集，通过数据清洗、特征工程与随机森林模型，预测乘客生还情况。
最终 Kaggle 得分 0.78229，排名 3153 / 12668。

## 文件说明

| 文件 | 内容 |
|---|---|
| `getdata.ipynb` | 读取原始数据，做探索性数据分析（EDA） |
| `feature.ipynb` | 处理缺失值与进行特征工程 |
| `models.ipynb` | 模型训练、交叉验证对比与最终预测 |
| `train.csv` / `test.csv` / `gender_submission.csv` | Kaggle 官方提供的原始数据 |

## 运行顺序

`getdata.ipynb` → `feature.ipynb` → `models.ipynb`

## 方法概述
EDA分析》预处理策略》特征工程》模型对比》最终结果

首先对test.csv的891行训练数据进行了可视化与统计分析，核心发现如下：
1.性别因素： 女性乘客的生存率高达74%，而男性乘客仅有19%。
社会阶级： 舱位等级越高，生存率越高。一等舱的生存率超过60%，而三等舱的生存率不足 25%。
年龄与甲板：儿童的生存率明显更高。
Cabin（船舱号）的缺失率高达 77%，但分析数据得出，有船舱记录的乘客生存率明显更高。
亲属关系： 孤身一人的乘客生存率较低，拥有1-3名亲属的乘客生存率最高，而4人以上亲属的大家庭的生存率反而下降。

Embarked（登船港口）填充： 缺失2条数据。通过分析这两名乘客的舱位等级（一等舱）和票价（$80），发现其与从 S港 (南安普顿) 登船的同类乘客特征最吻合，故填充为S。
Fare（票价）填充： 测试集缺失1条数据。使用该乘客所属 Pclass=3 且 Embarked=S 的中位数票价进行填充。

Title（头衔）： 从 Name 中提取 Mr, Miss, Mrs, Master 等。将 Don, Lady, Countess 等稀有称呼统一归类为 Rare。

对三种模型进行对比： Baseline模型的准确率约为79.5%，决策树的准确率约为81.8%，随机树的准确率最高为82.4%，因为其抗过拟合能力强，能很好地捕捉特征间的非线性关系，故使用随机树。

## 结果
Kaggle Score: 0.78229
Leaderboard: 3153 / 12668
