# scHCL

####  A tool defines cell types in human based on single-cell digital expression


At first scHCL  is a breif R package for large scale data(large DGE) from scHCL online function [Human Cell Landscape](http://bis.zju.edu.cn/HCL)  ,to alleviate burdens of our main Server. 


Now we add a UI for visulizing the scHCL reuslt. 
### Installation

```R
#This require devtools  
install.packages('devtools')
library(devtools)
# scHCL requires ggplot2/reshape2/plotly/shiny/shinythemes/shiny
install_github("ggjlab/scHCL")

```

### Quick Start

```R
library(scHCL)
# hcl_lung is an example expression matrix from HCL project.
> data(hcl_lung)
> dim(hcl_lung)
[1] 2884   160

# scHCL has two parameters , single cell expression matrix(scdata) and 
# the number of most similar cell types
> hcl_result <- scHCL(scdata = hcl_lung, numbers_plot = 3)

```
The return of scHCL() is a list which contains 4 parts.
* cors_matrix: Pearson correlation coefficient matrix of each cell and cell type.
* top_cors: equals to numbers_plot 
* scHCL: the most relevant cell type for each query cell
* scHCL_probility: the top n relevant cell types for each query cell

```R
# open shiny for visualize result for scHCL

scHCL_vis(hcl_result)
```

scHCL_vis() provides a bref function for visualizing and downloading of scHCL results
![scHCL_vis](http://bis.zju.edu.cn/HCL/assets/img/scHCL.png)
