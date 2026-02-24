# BandUP 仓库功能概览

BandUP 是一个用于**平面波 DFT 超胞能带展开（band unfolding）**的工具，核心用途是把超胞计算得到的能带投影回原胞布里渊区，便于与理想晶体能带对照。

## 核心功能（通过 `bandup <task>` 调用）

- `kpts-sc-get`：生成用于超胞能带计算的 k 点路径（展开前准备）。
- `unfold`：执行能带展开，生成 unfolded EBS 数据。
- `plot`：对展开结果进行可视化，可命令行绘图，也可 GUI（依赖 PyQt）。
- `projected-unfold`：原子/轨道分解的展开能带（当前仅 VASP）。

## 支持的第一性原理程序

- VASP
- Quantum ESPRESSO
- ABINIT
- CASTEP（README 标注为按需提供）

## 教程/示例体现的典型工作流

示例目录（`tutorial/`）基本都遵循同一套 4~5 步流程：

1. 先做电荷密度自洽计算（step_1）。
2. 生成将用于超胞能带计算的 k 点（step_2，对应 `kpts-sc-get`）。
3. 计算超胞波函数/能带（step_3）。
4. 用 BandUP 做展开并绘图（step_4，对应 `unfold` + `plot`）。
5. （部分示例）对展开后的谱函数做带中心/展宽分析（step_5）。

## 从示例能看出的适用场景

- 二维体系（如石墨烯超胞）
- 三维体材料（如 Si）
- 异质结构（如 graphene on Cu）
- 同一物理流程可迁移到不同 DFT 后端（VASP / QE / ABINIT）

