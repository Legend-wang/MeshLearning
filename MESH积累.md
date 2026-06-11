# mesh积累

## 常用三方库

### ACVD

ACVD（Approximate Centroidal Voronoi Diagrams）是一个由开发者 Sébastien Valette 开发的、用于 3D 表面网格快速简化与重新划分（Remeshing）的开源库。它与 VTK（Visualization Toolkit）有着极深的渊源，是基于 VTK 进行扩展实现的，常被医学图形处理及 3D 图形渲染领域的开发者使用。

ACVD 的核心是一种基于近似质心 Voronoi 图的高效 3D 三角网格简化算法。在 3D 图形处理中，它主要用于对复杂的网格模型进行**重新划分（Remeshing）**，从而优化网格拓扑结构并提升渲染或后续处理的性能。

由于 ACVD 是作为 VTK 的扩展存在的，VTK 是其不可或缺的核心依赖项。由于VTK在9.0版本更改了底层polydata的数据结构，因此编译时要选择正确的版本。

### CAGL

### VMTK


