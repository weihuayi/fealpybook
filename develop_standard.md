# 开发标准



## 通用标准

NC: 单元个数
NE: 边的个数
N: 节点的个数
NF: 面的个数

网格上存储基函数值或梯度值的多维数组轴的排序约定:

* 单元编号, 单元局部自由度编号, 分量编号

后面分量编号, 可以是一维, 二维, 三维张量

如果每个单元的基函数值一样:
标量基函数 phi, 一维数组, phi[i], 第i 个局部基函数的值
向量基函数 phi, 二维数组, phi[i, j], 第 i 个基函数的第 j 个分量

如果每个单元的基函数不一样:
phi[i, j]
phi[i, j, k]

标题基基函数梯度 gradphi, 三维数组, phi[i, j, k],  第 i 个单元的第 j 个基函数关于第 k 个分量的导数值

## 网格模块

网格模块主要包含:

* TriangleMesh
* QuadrangleMesh
* TetrahedronMesh
* HexahedronMesh
* PolygonMesh
* PolyhedronMesh
* StructureQuadMesh
* StructureHexMesh
* BlockStructureQuadMesh
* BlockStructureHexMesh
* QuadtreeMesh
* OctreeMesh
* TritreeMesh
* BitreeMesh

* point: vertex coordinates 
* edge
* face
* cell 
* cell2edge
* edge2cell
* cell2face
* face2cell

## 有限元空间模块 





