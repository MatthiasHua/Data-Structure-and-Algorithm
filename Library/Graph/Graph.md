# 图

---

操作集:

void initGraph (Graph &graph, int numVertex) // 初始化一个空图
void DFS_recursive(Graph &graph, int numVertex, int startVertex, int visited[]) // DFS遍历 递归实现

输入:
void inputGraph1 (Graph &graph) // 输入有权重的无向图
数据格式:
第一行numVertex,表示有numVertex,后面numVertex行，每行三个数分别是两个顶点和边的权重。
3
1 2 3
2 5 4
3 1 2

输出:
void printMatrix(int G[MaxVertexNum][MaxVertexNum], int numVertex) // 输出邻接矩阵