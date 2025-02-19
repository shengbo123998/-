# -

A DEEP PROBABILISTIC MODEL FOR CUSTOMER LIFETIME VALUE PREDICTION： https://arxiv.org/pdf/1912.07753

逻辑回归的本质：https://zhuanlan.zhihu.com/p/61827629 还有加权交叉熵WCE

多场景建模方法综述： https://zhuanlan.zhihu.com/p/930580173

快手直播论文：Moment&Cross: Next-Generation Real-Time Cross-Domain CTR Prediction for Live-Streaming Recommendation at Kuaishou

在交叉熵的基础上，加个Combined-pair loss :https://zhuanlan.zhihu.com/p/10542978888

在线auc跟离线auc的区别是，在线auc只用桶内的数据，即A模型打分，用的A模型的label. 而离线auc是算所有样本的auc, 即A模型打分，但是AABB模型的label。

pcoc计算： https://blog.csdn.net/pearl8899/article/details/138874217

抖音时钟兴趣，流式训练的用户时间级兴趣建模：https://arxiv.org/pdf/2404.19357。  计算用户在情绪、流派、语言等，小时级等得分，选出用户感兴趣的情绪、流派、语言等。建模高斯分布，因为用户兴趣变化是连续的，不可能是突变的。

快手HMoE, 快手主场景都已推全 https://zhuanlan.zhihu.com/p/13959750806



踩坑记录：  
          - 不要随意下线基线模型的特征，一方面是这些特征训练很久了，下线会导致模型泛化性不足。一方面是数据打分分布差异变大，影响其他模型比如重排。

          - 新加特征后，发现ego平台上没有配置特征，导致很多特征缺失。所以AB实验跟线下不一致，有可能是开发特征的原因。
          
          - 上线cvr精排模型后，部分地区出现广告曝光大量减少，因此会影响订单量跟时长，结果不可信。需要移到混排层实验，有广告自适应的调控策略。

          - 做AB测试的过程中，要保证广告的曝光跟收入是平的，cvr模型推荐的是直播视频。但是总指标计算的是广告+视频，所以要保证广告一致性，所以现在遇到的问题是，广告不平，广告曝光减少，vv减少。需要移到混排桶，混排桶有广告流量调控策略。

          - 基于第四点放到混排层，现在有新的问题，广告正常了，但是时长涨，订单持平。时长为什么会涨，因为混排层有广告流量调控，影响了整体的数据分布。导致融合参更偏向于时长模型。
          - 现在时长跟订单都涨了。到时候反转还是在混排桶。推全的时候在季度桶，季度桶会有单独的广告流控。控制广告流量。AB测试会出现广告不平，是因为四个桶用同一套广告流控，会有倾向于哪个桶。
          




