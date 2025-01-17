<p align="center"> <a href="https://github.com/logpai"> <img src="https://github.com/logpai/logpai.github.io/blob/master/img/logpai_logo.jpg" width="425"></a></p>


# loglizer


**Loglizer is a machine learning-based log analysis toolkit for automated anomaly detection**. 
> Loglizer是一款基于AI的日志大数据分析工具, 能用于自动异常检测、智能故障诊断等场景
  

Logs are imperative in the development and maintenance process of many software systems. They record detailed
runtime information during system operation that allows developers and support engineers to monitor their systems and track abnormal behaviors and errors. Loglizer provides a toolkit that implements a number of machine-learning based log analysis techniques for automated anomaly detection. 

:telescope: If you use loglizer in your research for publication, please kindly cite the following paper.
+ Shilin He, Jieming Zhu, Pinjia He, Michael R. Lyu. [Experience Report: System Log Analysis for Anomaly Detection](https://jiemingzhu.github.io/pub/slhe_issre2016.pdf), *IEEE International Symposium on Software Reliability Engineering (ISSRE)*, 2016. [[Bibtex](https://dblp.org/rec/bibtex/conf/issre/HeZHL16)][[中文版本](https://github.com/AmateurEvents/article/issues/2)]

## Framework

![Framework of Anomaly Detection](/docs/img/framework.png)

The log analysis framework for anomaly detection usually comprises the following components:

1. **Log collection:** Logs are generated at runtime and aggregated into a centralized place with a data streaming pipeline, such as Flume and Kafka. 
2. **Log parsing:** The goal of log parsing is to convert unstructured log messages into a map of structured events, based on which sophisticated machine learning models can be applied. The details of log parsing can be found at [our logparser project](https://github.com/logpai/logparser).
3. **Feature extraction:** Structured logs can be sliced into short log sequences through interval window, sliding window, or session window. Then, feature extraction is performed to vectorize each log sequence, for example, using an event counting vector. 
4. **Anomaly detection:** Anomaly detection models are trained to check whether a given feature vector is an anomaly or not.


## Models

Anomaly detection models currently available:

| Model | Paper reference |
| :--- | :--- |
| **Supervised models** |
| LR | [**EuroSys'10**] [Fingerprinting the Datacenter: Automated Classification of Performance Crises](https://www.microsoft.com/en-us/research/wp-content/uploads/2009/07/hiLighter.pdf), by Peter Bodík, Moises Goldszmidt, Armando Fox, Hans Andersen. [**Microsoft**] |
| Decision Tree | [**ICAC'04**] [Failure Diagnosis Using Decision Trees](http://www.cs.berkeley.edu/~brewer/papers/icac2004_chen_diagnosis.pdf), by Mike Chen, Alice X. Zheng, Jim Lloyd, Michael I. Jordan, Eric Brewer. [**eBay**] |
| SVM | [**ICDM'07**] [Failure Prediction in IBM BlueGene/L Event Logs](https://www.researchgate.net/publication/4324148_Failure_Prediction_in_IBM_BlueGeneL_Event_Logs), by Yinglung Liang, Yanyong Zhang, Hui Xiong, Ramendra Sahoo. [**IBM**]|
| **Unsupervised models** |
| LOF (coming)| [**SIGMOD'00**] [LOF: Identifying Density-Based Local Outliers](), by Markus M. Breunig, Hans-Peter Kriegel, Raymond T. Ng, Jörg Sander. |
| One-Class SVM (coming)| [**Neural Computation'01**] [Estimating the Support of a High-Dimensional Distribution](), by John Platt, Bernhard Schölkopf, John Shawe-Taylor, Alex J. Smola, Robert C. Williamson. |
| Isolation Forest (coming)| [**ICDM'08**] [Isolation Forest](https://cs.nju.edu.cn/zhouzh/zhouzh.files/publication/icdm08b.pdf), by Fei Tony Liu, Kai Ming Ting, Zhi-Hua Zhou. |
| PCA | [**SOSP'09**] [Large-Scale System Problems Detection by Mining Console Logs](http://iiis.tsinghua.edu.cn/~weixu/files/sosp09.pdf), by Wei Xu, Ling Huang, Armando Fox, David Patterson, Michael I. Jordan. [**Intel**] |
| Invariants Mining | [**ATC'10**] [Mining Invariants from Console Logs for System Problem Detection](https://www.usenix.org/legacy/event/atc10/tech/full_papers/Lou.pdf), by Jian-Guang Lou, Qiang Fu, Shengqi Yang, Ye Xu, Jiang Li. [**Microsoft**]|
| Clustering | [**ICSE'16**] [Log Clustering based Problem Identification for Online Service Systems](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/07/ICSE-2016-2-Log-Clustering-based-Problem-Identification-for-Online-Service-Systems.pdf), by Qingwei Lin, Hongyu Zhang, Jian-Guang Lou, Yu Zhang, Xuewei Chen. [**Microsoft**]|
| DeepLog (coming)| [**CCS'17**] [DeepLog: Anomaly Detection and Diagnosis from System Logs through Deep Learning](https://www.cs.utah.edu/~lifeifei/papers/deeplog.pdf), by Min Du, Feifei Li, Guineng Zheng, Vivek Srikumar. |
| AutoEncoder (coming)| [**Arxiv'18**] [Anomaly Detection using Autoencoders in High Performance Computing Systems](https://arxiv.org/abs/1811.05269), by Andrea Borghesi, Andrea Bartolini, Michele Lombardi, Michela Milano, Luca Benini. |


## Log data
We have collected a set of labeled log datasets in [loghub](https://github.com/logpai/loghub) for research purposes. If you are interested in the datasets, please follow the link to submit your access request.

## Demo
Please follow [the demo](./docs/demo.md) in the docs to get started.

## Benchmarking results
|       |            | HDFS |     |
| :----:|:----:|:----:|:----:|
| **Model** | **Precision** | **Recall** | **F1** |
| LR| 0.955 |	0.911 |	0.933 |
| Decision Tree | 0.998 |	0.998 |	0.998 |
| SVM| 0.959 |	0.970 |	0.965 |
| Clustering | 1.000 | 0.720 | 0.837 |
| PCA | 0.975 | 0.635 | 0.769|
| Invariants Mining | 0.888 | 0.945 | 0.915|


## Contributors
+ [Shilin He](https://shilinhe.github.io), The Chinese University of Hong Kong
+ [Jieming Zhu](https://jiemingzhu.github.io), The Chinese University of Hong Kong, currently at Huawei Noah's Ark Lab
+ [Pinjia He](https://pinjiahe.github.io/), The Chinese University of Hong Kong, currently at ETH Zurich


## Feedback
For any questions or feedback, please post to [the issue page](https://github.com/logpai/loglizer/issues/new). 


## History
* May 14, 2016: initial commit 
* Sep 21, 2017: update code and readme 
* Mar 21, 2018: rewrite most of the code and add detailed comments
* Feb 18, 2019: restructure the repository with hands-on demo
