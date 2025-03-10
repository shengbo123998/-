https://zhuanlan.zhihu.com/p/13959750806
问题：
1. MMOE 专家得分分布不一致。导致expert崩溃。 方法： 使用expert内的bn层标准化，使用swish激活函数代替ReLU。
2. expert退化，有些共享专家只对某一个任务赋予很高的权重，其他很低。 方法： 加入层次掩码机制，第一层是用于抽取粗粒度的宏观元表示，分别提取:(1)时长子类别内共享知识;（2)全局共享知识; (3)互动子类目内共享知识。这里第一层是与PLE的最主要的架构差异。
   ![image](https://github.com/user-attachments/assets/e5e1d14c-4936-49ce-9bb5-295dd8ab1853)
![image](https://github.com/user-attachments/assets/fd96789f-4032-472c-9ebf-79795ea0d30a)
3. expert欠拟合，一些特定专家的权重很低，大部份权重在共享专家。因为有些任务的数据量很少，很稀疏。而共享专家学了很多样本，导致Gate门控更倾向于拟合更好的共享专家
（emb倾向于数据更多的任务学习，共享Expert可以从行为不那么稀疏的任务中感知更多的梯度更新和知识，而特定私有的Expert由于其行为稀疏容易陷入欠拟合， 所以emb输入到共享expert可以得到更有效的表示）
   方法： feature-gate。其目的是为不同的任务专家生成不同的输入特征表示，以缓解所有专家共享相同的输入特征时的潜在梯度冲突
         self-gate。self-gaet是用于确保顶层梯度可以有效地传递到底层, 并只关注其特定专家的输出。
