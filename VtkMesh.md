# VtkMesh (>9.0)

## 数据结构

### vtkPolyData

vtkPolyData 是 VTK 中用于表示 多边形网格（Polygonal Mesh） 的基本数据类型，包含以下几类几何数据：

- 顶点（Points）
- 拓扑（Cells）：点集（Vertex Cells）、线段（Line Cells）、多边形/多边形单元（Polygons / Triangle Strips）
- 属性：标量、向量、纹理坐标、点法线、单元法线、颜色数组

**本质上，vtkPolyData 是一种包含点和连接这些点的单元的拓扑结构，并将几何数据和拓扑数据分开存储。**

#### 主要数据组成

- 几何坐标(Points): 存储真实的顶点坐标，内部实际以vtkDataArray形式存储
- 拓扑单元存储(Cell Arrays): 存储vertices\lines\polygons\strips，内部实际以vtkCellArray存储，具体在下一节中展开

```c++
vtkPolyData
├── Points: vtkPoints (Array of 3d vectors)
├── Vertices: vtkCellArray
├── Lines: vtkCellArray
├── Polygons: vtkCellArray
├── Strips: vtkCellArray
├── PointData: field arrays & attributes
├── CellData: field arrays & attributes
└── (optional) link/edge structures
```

#### 数据访问接口

- 遍历points

```c++
auto pts = polydata->GetPoints();
for (vtkIdType i = 0; i < pts->GetNumberOfPoints(); ++i) {
    double p[3];
    pts->GetPoint(i, p);
}
```

- 遍历cells

```c++
for (vtkIdType cellId=0; cellId < polydata->GetNumberOfCells(); ++cellId) {
    vtkIdList* ids;
    polydata->GetCellPoints(cellId, ids);
}
```

- 访问CellArray (更快)

```c++
for (vtkIdType cellId=0; cellId < polydata->GetNumberOfCells(); ++cellId) {
    vtkIdList* ids;
    polydata->GetCellPoints(cellId, ids);
}
```
