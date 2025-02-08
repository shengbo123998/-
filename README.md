# -

A DEEP PROBABILISTIC MODEL FOR CUSTOMER LIFETIME VALUE PREDICTION： https://arxiv.org/pdf/1912.07753

逻辑回归的本质：https://zhuanlan.zhihu.com/p/61827629 还有加权交叉熵WCE

多场景建模方法综述： https://zhuanlan.zhihu.com/p/930580173

快手直播论文：Moment&Cross: Next-Generation Real-Time Cross-Domain CTR Prediction for Live-Streaming Recommendation at Kuaishou

在交叉熵的基础上，加个Combined-pair loss :https://zhuanlan.zhihu.com/p/10542978888

在线auc跟离线auc的区别是，在线auc只用桶内的数据，即A模型打分，用的A模型的label. 而离线auc是算所有样本的auc, 即A模型打分，但是AABB模型的label。

pcoc计算： https://blog.csdn.net/pearl8899/article/details/138874217

抖音时钟兴趣，流式训练的用户时间级兴趣建模：https://arxiv.org/pdf/2404.19357。  计算用户在情绪、流派、语言等，小时级等得分，选出用户感兴趣的情绪、流派、语言等。




踩坑记录：  不要随意下线基线模型的特征，一方面是这些特征训练很久了，下线会导致模型泛化性不足。一方面是数据打分分布差异变大，影响其他模型比如重排。
