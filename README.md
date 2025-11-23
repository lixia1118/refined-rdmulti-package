
# Python Implementation of Multi-Cutoff RDD Analysis

本项目基于 Python 实现了多断点（Multi-Cutoff）的断点回归设计（RDD）分析及绘图功能。

## 项目背景

计量经济学家 **Matias D. Cattaneo** 在其 [Github 仓库](https://github.com/rdpackages/rdmulti) 中提供了 `rdmulti` 的 Stata、Python 和 R 三个版本。

然而，官方的 Python 版本代码尚不完善。本人在 Cattaneo 设计的代码基础上，针对核心文件 `rdmc.py` 和 `rdmcplot.py` 进行了二次开发与功能增强。

### 主要改进功能
1.  **回归结果导出**：支持将回归分析结果导出为文本文件。
2.  **绘图功能增强**：
    *   支持自定义导出图片的 DPI（分辨率）。
    *   支持自定义图片尺寸（figsize）。
    *   支持直接保存图片到指定路径。

---

## 安装与配置

由于本项目是对现有库的“补丁”式更新，请按照以下步骤进行配置：

### 第一步：安装原始库
请在 **Anaconda Prompt** 或终端中运行以下命令：

```bash
pip install rdmulti
```

### 第二步：替换文件
安装完成后，需要使用本项目 `refine` 文件夹中的文件替换原始库文件。

1.  找到 Python 环境下的库安装路径。
    *   *示例路径*：`D:\Anaconda\Lib\site-packages\rdmulti`（具体路径因用户设定而异）
    *   该文件夹内应包含 `rdmc.py`, `rdmcplot.py`, `rdms.py` 等文件。
2.  将本项目 **`refine`** 文件夹中的所有文件复制。
3.  粘贴到上述示例路径的 `rdmulti` 文件夹中，并选择 **覆盖/替换** 原始文件。

完成替换后，即可使用增强版功能。

---

## 快速开始

演示代码请参考项目中的 Jupyter Notebook 文件：
**`multi-cutoff.ipynb`**

---

## 参数说明

以下是经过完善后的函数接口及其新增参数说明。

### 1. `rdmc` (回归分析)

位于 `rdmc.py` 中。

```python
def rdmc(Y, X, C, 
         fuzzy=None, derivvec=None, pooled_opt=None, verbose=False,
         pvec=None, qvec=None, hmat=None, bmat=None, rhovec=None,
         covs_mat=None, covs_list=None, covs_dropvec=None, kernelvec=None, weightsvec=None,
         bwselectvec=None, scaleparvec=None, scaleregulvec=None,
         masspointsvec=None, bwcheckvec=None, bwrestrictvec=None,
         stdvarsvec=None, vcevec=None, nnmatchvec=None, cluster=None,
         level=95, plot=False, conventional=False, 
         # --- 新增/修改参数 ---
         dpi=300,             # 图片分辨率
         output_path=None,    # 回归结果文本导出路径
         plot_path=None,      # 图片保存路径
         figsize=(12, 5)      # 图片尺寸
         ):
```

### 2. `rdmcplot` (绘图)

位于 `rdmcplot.py` 中。

```python
def rdmcplot(Y, X, C, 
             nbinsmat=None, binselectvec=None, scalevec=None,
             supportmat=None, pvec=None, hmat=None, kernelvec=None,
             weightsvec=None, covs_mat=None, covs_list=None, covs_evalvec=None,
             covs_dropvec=None, ci=None, col_bins=None, pch_bins=None,
             col_poly=None, lty_poly=None, col_xline=None, lty_xline=None,
             nobins=False, nopoly=False, noxline=False, nodraw=False,
             title=None, xlabel=None, ylabel=None, legend_labels=None,
             # --- 新增/修改参数 ---
             figsize=(10, 6),     # 图片尺寸
             dpi=300,             # 图片分辨率
             grid=False,          # 是否显示网格
             save_path=None,      # 图片保存路径
             legend_loc='best',   # 图例位置
             font_size=10,        # 字体大小
             marker_size=4,       # 散点大小
             line_width=1,        # 线条宽度
             show_legend=True     # 是否显示图例
             ):
```

---
**注意**：请确保在使用前已正确覆盖原始库文件，否则新增参数将无法生效并报错。
