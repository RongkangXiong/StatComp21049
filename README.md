
# StatComp21049

<!-- badges: start -->
<!-- badges: end -->

StatComp21049 is a R package developed to present the homework of statistic computing course by author StatComp21049 and reconstruct the Phase space for worm behavior.


<center>This is the Phase space reconstruction theory </center>
![](https://cdn.jsdelivr.net/gh/RongkangXiong/pic-bed/blog/img/202112201851366.png)



## Installation

You can install the development version of StatComp21049 from [GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("RongkangXiong/StatComp21049",build_vignettes = TRUE, force = T)
```

You can access the project's home page query help documentation from
[StatComp21049](https://rongkangxiong.github.io/StatComp21049)

## Example

This is a basic example which shows you how to solve a common problem:

``` r
library(StatComp21049)
## basic example code

data("curve_data", "time_Elapsed", "w")
## you can use your data to Proceed to the steps below
rec <- Downsample(time_Elapsed, curve_data, 16)
time_downsampled <- rec$time_downsampled
data_downsampled <- rec$data_downsampled
ev <- Get_Matrix_Eigens(data_downsampled)
eigenvalues <- ev$values
eigenvectors <- ev$vectors
PCAmode <- 5
K_delay <- 12
Xeigenvector <- eigenvectors[, 1:PCAmode]
X_PCA <- data_downsampled %*% Xeigenvector
test_CurveFilter_embeddingdelay <- Embedding_delay(X_PCA, PCAmode, K_delay)
X <- test_CurveFilter_embeddingdelay %*% w
## Plot the projection
plot(X[, 3], X[, 4], type = "l")
plot(X[, 6], X[, 7], type = "l")
```

# This is the results in MATLAB
![](https://cdn.jsdelivr.net/gh/RongkangXiong/pic-bed/blog/img/202112201901769.png)
![](https://cdn.jsdelivr.net/gh/RongkangXiong/pic-bed/blog/img/202112201907918.png)

# This is the results in R

The dataset is only one-tenth of that of MATLAB due to its size limitations


![](https://cdn.jsdelivr.net/gh/RongkangXiong/pic-bed/blog/img/202112201856062.png)
![](https://cdn.jsdelivr.net/gh/RongkangXiong/pic-bed/blog/img/202112201855871.png)



