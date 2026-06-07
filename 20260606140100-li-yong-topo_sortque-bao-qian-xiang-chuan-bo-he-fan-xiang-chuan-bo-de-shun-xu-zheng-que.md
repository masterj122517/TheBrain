# 利用topo_sort确保前向传播和反向传播的顺序正确

Tags: #ML

---

我们知道，要计算梯度，就是用链式法则
$$\frac{\partial L}{\partial Y} = \frac{\partial L}{\partial Z_1} \frac{\partial Z_1}{\partial Y} + \frac{\partial L}{\partial Z_2} \frac{\partial Z_2}{\partial Y}$$ 

如果要计算某个 node 的梯度，根据 Chain Rule，必须先拿到所有以该 node 作为输入（即依赖它）的后续节点的梯度。

因此，反向传播的实质是将前向传播建立的 DAG [[20260606140831-dagyong-lai-jian-mo-you-yi-lai-guan-xi-de-tuo-bu-jie-gou]] 进行**反向拓扑排序（Reverse Topological Sort）**并依序计算。

topo sort 的原理是 DFS + 一个visted[] 用来记录这个node有没有被遍历过，如果有意味着被多次依赖了，不能放进topo[] for more than once




## References
-
