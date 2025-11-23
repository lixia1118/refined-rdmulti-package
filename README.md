本代码实现的功能是使用Python进行多断点的RDD回归分析及绘图
首先，在**Anaconda Prompt**输入*pip install rdmulti*，随后在"D:\Anaconda\Lib\site-packages"会发现以**rdmulti**为名的文件夹，里面有3个py文件，分别是rdmc.py、rdmcplot.py、rdms.py. 
实际上，计量经济学家Matias D. Cattaneo在[自己的Github库](https://github.com/rdpackages/rdmulti)给出了Stata/Python/R三个版本的rdmulti代码，然而，python版本的代码尚不完善。
本人在Cattaneo设计的代码基础上，针对rdmc.py、rdmcplot.py增添了一些功能，例如，对回归结果的文本导出、图片dpi和尺寸调整及导出，演示代码是multi-cutoff.ipynb。
唯一的操作是将**refine**文件夹中的文件复制粘贴至上述提及路径中的rdmulti文件夹中，即可完成对原始代码的替换。

完善后的rdmc.py中的函数参数如下：
def rdmc(Y, X, C, fuzzy=None, derivvec=None, pooled_opt=None, verbose=False,
         pvec=None, qvec=None, hmat=None, bmat=None, rhovec=None,
         covs_mat=None, covs_list=None, covs_dropvec=None, kernelvec=None, weightsvec=None,
         bwselectvec=None, scaleparvec=None, scaleregulvec=None,
         masspointsvec=None, bwcheckvec=None, bwrestrictvec=None,
         stdvarsvec=None, vcevec=None, nnmatchvec=None, cluster=None,
         level=95, plot=False, conventional=False,dpi=300,
         output_path=None,
         plot_path=None,
         figsize=(12, 5))
         
完善后的rdmcplot.py中的函数参数如下：
def rdmcplot(Y, X, C, nbinsmat=None, binselectvec=None, scalevec=None,
             supportmat=None, pvec=None, hmat=None, kernelvec=None,
             weightsvec=None, covs_mat=None, covs_list=None, covs_evalvec=None,
             covs_dropvec=None, ci=None, col_bins=None, pch_bins=None,
             col_poly=None, lty_poly=None, col_xline=None, lty_xline=None,
             nobins=False, nopoly=False, noxline=False, nodraw=False,
             title=None, xlabel=None, ylabel=None, legend_labels=None,
             figsize=(10, 6), dpi=300, grid=False, save_path=None,
             legend_loc='best', font_size=10, marker_size=4, line_width=1,
             show_legend=True)
