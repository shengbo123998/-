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


如果排序样本是纯原生的，没有广告，那么pcoc大小无所谓。但如果打分跟后面的广告在混排层作为特征，那就有关系。
