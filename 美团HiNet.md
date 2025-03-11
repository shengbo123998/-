https://tech.meituan.com/2023/03/23/recommendation-multi-scenario-task.html

相关方法往往是将多场景推荐做为一个多任务学习（Multi-Task Learning，MTL）问题进行建模，并且此类方法大多使用多门控混合专家（Multi-gate Mixture-of-Experts，MMoE）网络框架作为模型改进的基础来学习场景之间的共性和特性。然而，这种基于MTL的方法往往将多个场景的数据信息投影到同一个特征空间进行优化，这很难充分捕捉到具有多个任务的众多场景之间的复杂关系，因此也无法进一步提升多场景多任务学习模型的性能。

在场景抽取层（Scenario Extraction Layer），HiNet能够通过单独的专家模块提取场景共享信息和场景特有信息。为了进一步加强对当前场景的表示学习，我们设计了场景感知注意力网络（Scenario-aware Attentive Network，SAN），显式学习其他场景对当前场景的信息表征贡献程度。

场景抽取层相当于将不同场景的数据映射到不同的特征空间。
