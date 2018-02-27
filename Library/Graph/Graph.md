# 图

---

操作集:
```cpp
void initGraph (Graph &graph) // 初始化一个空图
void DFS_recursive(Graph &graph, int startVertex, int visited[]) // DFS遍历 递归实现
void DFS_nonrecursive(Graph &graph, int startVertex) // DFS遍历 非递归实现
void BFS(Graph &graph, int startVertex) // BFS遍历 非递归实现
void unweightShortPath(Graph & graph, int Source, int dict[], int path[]) // 无权图的单源最短路
void Dijkstra(Graph &graph, int Source, int dict[], int path[]) // 有权图的单源最短路
```

输入:
```cpp
void inputGraph1 (Graph &graph) // 输入有权重的无向图
数据格式:
第一行numVertex,表示有numVertex,后面numVertex行，每行三个数分别是两个顶点和边的权重。
3
1 2 3
2 5 4
3 1 2
```

输出:
```cpp
void printMatrix(Graph &graph) // 输出邻接矩阵
```