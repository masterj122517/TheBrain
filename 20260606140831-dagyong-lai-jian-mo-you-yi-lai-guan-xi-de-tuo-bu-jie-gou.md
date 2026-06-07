# DAG用来建模有依赖关系的拓扑结构

Tags: #algorithm

---

由于DAG有两个特性 
Directed(有向): 说明存在依赖结构 like u -> y, 说明必须先完成u才有y

Acyclic(无环): 没有路径能让节点返回自己

这个特性让something like build system, package manager, autograd engine 能够利用到

他们的特性就是，我需要找到依赖关系，并且，我自己不能依赖自己


## References
-
