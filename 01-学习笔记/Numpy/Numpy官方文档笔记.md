##  定位
-  NumPy 是什么：Python 科学计算的基础库，核心对象是 `ndarray`——**同类型数据的 n 维数组**，运算在编译好的 C 代码里执行。
- 和 Python 列表的 4 个区别（官方原话）：
    - 数组创建时大小固定，改大小等于创建新数组、删掉旧的（列表能动态增长）；
    - 元素必须同类型，因此内存中每个元素等大（列表可以混装）；
    - 大规模数学运算更快、代码更少；
    - 整个科学生态（scipy、matplotlib、pandas、PyTorch…）都以它为交换格式。
- 相比C和python计算更快

## quickstart
1. `*` 逐元素乘，`@` 矩阵乘   ```
```
A = np.array([[1,1],[0,1]]); B = np.array([[2,0],[3,4]])
A * B        # [[2 0] [0 4]]    逐元素
A @ B        # [[5 4] [3 4]]    矩阵乘
A.dot(B)     # 同上,矩阵乘
```
2. 原地运算 `+=` 有类型限制
```
a = np.ones((2,3), dtype=np.int64)
b = np.random.default_rng(1).random((2,3))     # float64
a *= 3        # 可以
a += b        # 报错，原地写回 a 的内存，而 a 的内存是 int64，装不下 float64 的结果
a = a + b     # 正确，创建一个新的 float64 数组再让 a 指向它
```
3.  `reshape / ravel` 不改原数组，`resize` 才改
```
a = np.arange(12).reshape(3,4)
a.ravel()        # (12,)   原数组 a 还是 (3,4)  
a.reshape(6,2)   # (6,2)   原数组 a 还是 (3,4)
a.T              # (4,3)   原数组 a 还是 (3,4)
a.resize((2,6))  #   a 变为（2，6）
```
