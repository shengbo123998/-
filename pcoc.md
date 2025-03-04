假设有以下数据：

user_id	r_cvr (预测 CVR)	order_coa (实际转化)
1	0.1	0
2	0.3	1
3	0.2	0
4	0.4	1
计算：

Sum of Predicted CVR = 0.1 + 0.3 + 0.2 + 0.4 = 1.0
Sum of Observed CVR = 0 + 1 + 0 + 1 = 2
PCOC = 1.0 / 2 = 0.5

精排模型也有广告。
如果排序样本是纯原生的，没有广告，那么pcoc大小无所谓。但如果打分跟后面的广告在混排层作为特征，那就有关系。

预估值大小准确性在Auction服务中的重要性，广告中，需要考虑广告的价格和广告的CTR预估，所以CTR预估虽然排序不变，但是准度会影响推哪个广告。

总的来说，预估值大小准确性直接影响Auction机制的公平性，下面用两个例子来说明
纯直投广告场景

广告	price	pCTR	eCPM	rank
ad1	1.5	0.8%	12	1
ad2	0.6	1.8%	11	2
ad3	1.0	1.0%	10	3
ad4	0.5	1.4%	7	4
对于ad3: pCTR 1.0%->1.3%:

绝对值高估30%，AUC不变
eCPM从10变为13，获得更加优质的广告展示机会
ad3的拿量能力变大，平台期望收入降低。 

calibration-N(cal-N)

cal-N将样本集合按照自定义规则划分出多个簇分别计算PCOC，并计算与1的偏差作为标准误差。举个例子，将pctr根据值大小划分为多个桶，每个桶为一个簇，计算每个簇的PCOC及其与1的偏差 数学公式:

![image](https://github.com/user-attachments/assets/ba6eba07-1cb9-4f52-947a-e667821d4c13)


https://zhuanlan.zhihu.com/p/460061332


重点理解这句话：正负样本不均衡的情况下，负采样通常可以提升模型的AUC精度，但是pctr值会发生变化，与真实ctr差距扩大。 多国家多场景cvr建模中，不同国家不同场景的后验cvr是不一样的，如果没有加入消偏，pcvr值会趋近于所有国家所有场景的真实cvr值，但是没有对不同国家不同场景做区分。

![image](https://github.com/user-attachments/assets/4d30402f-f673-4ba2-a59e-ab27199a12ef)

