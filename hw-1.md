Assignment 1
================
Rachel Cardarelli
9/19/2019

``` r
#install.packages('tinytex')
#tinytex::install_tinytex()
```

Question 1
----------

``` r
x = c(1:2019)
S1 = print(sum(x))
```

    ## [1] 2039190

``` r
S2 = print(sum(x^2))
```

    ## [1] 2745429470

``` r
S3 = print(sum(x^x))
```

    ## [1] Inf

``` r
y <- c(1,-1)
S4 = print(sum((x^x)*y))
```

    ## Warning in (x^x) * y: longer object length is not a multiple of shorter
    ## object length

    ## [1] NaN

``` r
S5 = print(sum(x^-2))
```

    ## [1] 1.644439

``` r
S6 = print(sum(x^-1))
```

    ## [1] 8.187821

``` r
S7 = print(sum(x^-3))
```

    ## [1] 1.202057

``` r
S8 = print(sum((x^-1)*y))
```

    ## Warning in (x^-1) * y: longer object length is not a multiple of shorter
    ## object length

    ## [1] 0.6933948

Question 2
----------

``` r
x <- rnorm(1000,mean=10,sd=1)
print(mean(x))
```

    ## [1] 9.992815

``` r
print(sd(x))
```

    ## [1] 1.006304

``` r
print(sum(x>10))
```

    ## [1] 499

``` r
hist(x)
```

![](hw-1_files/figure-markdown_github/unnamed-chunk-3-1.png)

``` r
x <- rnorm(1000,mean=2,sd=1)
print(sum(x>1)/1000)
```

    ## [1] 0.825

Question 3
----------

``` r
x <- sample(c(1:6),1000,replace = TRUE)
mean(x)
```

    ## [1] 3.523

``` r
sd(x)
```

    ## [1] 1.691843

``` r
sum(x==6)
```

    ## [1] 167

``` r
table(x)
```

    ## x
    ##   1   2   3   4   5   6 
    ## 160 162 169 180 162 167

``` r
prop.table(table(x))
```

    ## x
    ##     1     2     3     4     5     6 
    ## 0.160 0.162 0.169 0.180 0.162 0.167

``` r
hist(x)
```

![](hw-1_files/figure-markdown_github/unnamed-chunk-4-1.png)

Question 4a
-----------

``` r
x1 = sample(c(1:6), 1000, replace=TRUE)
x2 = sample(c(1:6), 1000, replace=TRUE)
x3 = sample(c(1:6), 1000, replace=TRUE)

sum(x1 > x2 +x3)/1000
```

    ## [1] 0.105

Question 4b
-----------

``` r
sum(x1^2 > x2^2 +x3^2)/ 1000
```

    ## [1] 0.234

Question 5
----------

``` r
m <- matrix(sample(c(0,1),3000, replace = TRUE), ncol = 3)
sum(rowSums(m)==3)/3000
```

    ## [1] 0.04366667

Question 6
----------

``` r
m <- matrix(sample(c(0,1),10000, replace = TRUE), ncol = 10)
for (n in 1000){
for (i in 8){
 if(sum(m[n,i:(i+2)])==0){
  t = t + 1
  i = i + 1 #trying to make sure it's exactly three in a row
 }}}
#t/1000
```

Question 7
----------

``` r
m <- matrix(rep(runif(1000, min = 0, max = 1),100), nrow = 100)
x <- rowMeans(m,na.rm = FALSE, dims = 1)
hist(x)
```

![](hw-1_files/figure-markdown_github/unnamed-chunk-9-1.png)

``` r
n <- matrix(rep(rpois(1000,lambda = 12),100),nrow = 100)
y <-  rowMeans(n,na.rm = FALSE, dims = 1)
hist(y)
```

![](hw-1_files/figure-markdown_github/unnamed-chunk-9-2.png)

``` r
o <- matrix(rep(rbinom(1000,1000,.5),100),nrow = 100)
z <-  rowMeans(o,na.rm = FALSE, dims = 1)
hist(z)
```

![](hw-1_files/figure-markdown_github/unnamed-chunk-9-3.png)

Question 7
----------

``` r
library(readr)
library(stringr)

titanic <- read.csv("C:/Users/student/Documents/Honors Thesis/titanic.csv")
str(titanic)
```

    ## 'data.frame':    891 obs. of  12 variables:
    ##  $ PassengerId: int  1 2 3 4 5 6 7 8 9 10 ...
    ##  $ Survived   : int  0 1 1 1 0 0 0 0 1 1 ...
    ##  $ Pclass     : int  3 1 3 1 3 3 1 3 3 2 ...
    ##  $ Name       : Factor w/ 891 levels "Abbing, Mr. Anthony",..: 109 191 358 277 16 559 520 629 417 581 ...
    ##  $ Sex        : Factor w/ 2 levels "female","male": 2 1 1 1 2 2 2 2 1 1 ...
    ##  $ Age        : num  22 38 26 35 35 NA 54 2 27 14 ...
    ##  $ SibSp      : int  1 1 0 1 0 0 0 3 0 1 ...
    ##  $ Parch      : int  0 0 0 0 0 0 0 1 2 0 ...
    ##  $ Ticket     : Factor w/ 681 levels "110152","110413",..: 524 597 670 50 473 276 86 396 345 133 ...
    ##  $ Fare       : num  7.25 71.28 7.92 53.1 8.05 ...
    ##  $ Cabin      : Factor w/ 148 levels "","A10","A14",..: 1 83 1 57 1 1 131 1 1 1 ...
    ##  $ Embarked   : Factor w/ 4 levels "","C","Q","S": 4 2 4 4 4 3 4 4 4 2 ...

Question 8
----------

``` r
knitr::kable(titanic[1:10,], format = 'markdown')
```

<table>
<colgroup>
<col width="8%" />
<col width="6%" />
<col width="5%" />
<col width="34%" />
<col width="5%" />
<col width="3%" />
<col width="4%" />
<col width="4%" />
<col width="11%" />
<col width="5%" />
<col width="4%" />
<col width="6%" />
</colgroup>
<thead>
<tr class="header">
<th align="right">PassengerId</th>
<th align="right">Survived</th>
<th align="right">Pclass</th>
<th align="left">Name</th>
<th align="left">Sex</th>
<th align="right">Age</th>
<th align="right">SibSp</th>
<th align="right">Parch</th>
<th align="left">Ticket</th>
<th align="right">Fare</th>
<th align="left">Cabin</th>
<th align="left">Embarked</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="right">1</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="left">Braund, Mr. Owen Harris</td>
<td align="left">male</td>
<td align="right">22</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="left">A/5 21171</td>
<td align="right">7.2500</td>
<td align="left"></td>
<td align="left">S</td>
</tr>
<tr class="even">
<td align="right">2</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="left">Cumings, Mrs. John Bradley (Florence Briggs Thayer)</td>
<td align="left">female</td>
<td align="right">38</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="left">PC 17599</td>
<td align="right">71.2833</td>
<td align="left">C85</td>
<td align="left">C</td>
</tr>
<tr class="odd">
<td align="right">3</td>
<td align="right">1</td>
<td align="right">3</td>
<td align="left">Heikkinen, Miss. Laina</td>
<td align="left">female</td>
<td align="right">26</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="left">STON/O2. 3101282</td>
<td align="right">7.9250</td>
<td align="left"></td>
<td align="left">S</td>
</tr>
<tr class="even">
<td align="right">4</td>
<td align="right">1</td>
<td align="right">1</td>
<td align="left">Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
<td align="left">female</td>
<td align="right">35</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="left">113803</td>
<td align="right">53.1000</td>
<td align="left">C123</td>
<td align="left">S</td>
</tr>
<tr class="odd">
<td align="right">5</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="left">Allen, Mr. William Henry</td>
<td align="left">male</td>
<td align="right">35</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="left">373450</td>
<td align="right">8.0500</td>
<td align="left"></td>
<td align="left">S</td>
</tr>
<tr class="even">
<td align="right">6</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="left">Moran, Mr. James</td>
<td align="left">male</td>
<td align="right">NA</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="left">330877</td>
<td align="right">8.4583</td>
<td align="left"></td>
<td align="left">Q</td>
</tr>
<tr class="odd">
<td align="right">7</td>
<td align="right">0</td>
<td align="right">1</td>
<td align="left">McCarthy, Mr. Timothy J</td>
<td align="left">male</td>
<td align="right">54</td>
<td align="right">0</td>
<td align="right">0</td>
<td align="left">17463</td>
<td align="right">51.8625</td>
<td align="left">E46</td>
<td align="left">S</td>
</tr>
<tr class="even">
<td align="right">8</td>
<td align="right">0</td>
<td align="right">3</td>
<td align="left">Palsson, Master. Gosta Leonard</td>
<td align="left">male</td>
<td align="right">2</td>
<td align="right">3</td>
<td align="right">1</td>
<td align="left">349909</td>
<td align="right">21.0750</td>
<td align="left"></td>
<td align="left">S</td>
</tr>
<tr class="odd">
<td align="right">9</td>
<td align="right">1</td>
<td align="right">3</td>
<td align="left">Johnson, Mrs. Oscar W (Elisabeth Vilhelmina Berg)</td>
<td align="left">female</td>
<td align="right">27</td>
<td align="right">0</td>
<td align="right">2</td>
<td align="left">347742</td>
<td align="right">11.1333</td>
<td align="left"></td>
<td align="left">S</td>
</tr>
<tr class="even">
<td align="right">10</td>
<td align="right">1</td>
<td align="right">2</td>
<td align="left">Nasser, Mrs. Nicholas (Adele Achem)</td>
<td align="left">female</td>
<td align="right">14</td>
<td align="right">1</td>
<td align="right">0</td>
<td align="left">237736</td>
<td align="right">30.0708</td>
<td align="left"></td>
<td align="left">C</td>
</tr>
</tbody>
</table>

Question 9
----------

``` r
#Missing entries in data
sum(is.na(titanic))
```

    ## [1] 177

``` r
#Missing entries in each column
colSums(is.na(titanic))
```

    ## PassengerId    Survived      Pclass        Name         Sex         Age 
    ##           0           0           0           0           0         177 
    ##       SibSp       Parch      Ticket        Fare       Cabin    Embarked 
    ##           0           0           0           0           0           0

Question 10
-----------

``` r
mean(titanic$Age, na.rm = TRUE)
```

    ## [1] 29.69912

Question 11
-----------

``` r
mean_age <- mean(titanic$Age, na.rm = TRUE)
missing_Age = which(is.na(titanic$Age))
titanic$Age[missing_Age] = mean_age
```

Question 12
-----------

``` r
titanic <- subset(titanic, select = -c(Name, PassengerId, Ticket, Cabin))
```

Question 13
-----------

``` r
mean(titanic$Age[titanic$Sex == "female"], na.rm = TRUE)
```

    ## [1] 28.21673

Question 14
-----------

``` r
median(titanic$Fare[titanic$Pclass==1], na.rm = TRUE)
```

    ## [1] 60.2875

``` r
median(subset(titanic, (Pclass == 1))$Fare, na.rm = TRUE)
```

    ## [1] 60.2875

``` r
median(titanic[titanic$Pclass==1,"Fare"], na.rm = TRUE)
```

    ## [1] 60.2875

Question 15
-----------

``` r
median(titanic$Fare[titanic$Sex == "female" & titanic$Pclass != 1], na.rm = TRUE)
```

    ## [1] 14.45625

Question 16
-----------

``` r
median(subset(titanic, (Survived == 1) & (Sex == "female") & (Pclass != 3))$Age, na.rm=TRUE)
```

    ## [1] 30

Question 17
-----------

``` r
teenager = c(13:19)
mean(titanic$Fare[titanic$Sex == 'female' & titanic$Survived == 1 & match(titanic$Age, teenager)], na.rm = TRUE)
```

    ## [1] 49.17966

Question 18
-----------

``` r
mean(titanic$Fare[titanic$Sex == 'female' & titanic$Survived == 1 & match(titanic$Age, teenager)& titanic$Pclass == 1], na.rm = TRUE)
```

    ## [1] 107.5407

``` r
mean(titanic$Fare[titanic$Sex == 'female' & titanic$Survived == 1 & match(titanic$Age, teenager)& titanic$Pclass == 2], na.rm = TRUE)
```

    ## [1] 20.00885

``` r
mean(titanic$Fare[titanic$Sex == 'female' & titanic$Survived == 1 & match(titanic$Age, teenager)& titanic$Pclass == 3], na.rm = TRUE)
```

    ## [1] 8.769885

Question 19
-----------

``` r
subset1 <- subset(titanic, titanic$Fare > mean(titanic$Fare))
sum(subset1$Survived == 1)/sum(subset1$Survived==0)
```

    ## [1] 1.482353

Question 20
-----------

``` r
sfare <- (titanic$Fare - mean(titanic$Fare))/sd(titanic$Fare)
cbind(titanic, sfare)
```

    ##     Survived Pclass    Sex      Age SibSp Parch     Fare Embarked
    ## 1          0      3   male 22.00000     1     0   7.2500        S
    ## 2          1      1 female 38.00000     1     0  71.2833        C
    ## 3          1      3 female 26.00000     0     0   7.9250        S
    ## 4          1      1 female 35.00000     1     0  53.1000        S
    ## 5          0      3   male 35.00000     0     0   8.0500        S
    ## 6          0      3   male 29.69912     0     0   8.4583        Q
    ## 7          0      1   male 54.00000     0     0  51.8625        S
    ## 8          0      3   male  2.00000     3     1  21.0750        S
    ## 9          1      3 female 27.00000     0     2  11.1333        S
    ## 10         1      2 female 14.00000     1     0  30.0708        C
    ## 11         1      3 female  4.00000     1     1  16.7000        S
    ## 12         1      1 female 58.00000     0     0  26.5500        S
    ## 13         0      3   male 20.00000     0     0   8.0500        S
    ## 14         0      3   male 39.00000     1     5  31.2750        S
    ## 15         0      3 female 14.00000     0     0   7.8542        S
    ## 16         1      2 female 55.00000     0     0  16.0000        S
    ## 17         0      3   male  2.00000     4     1  29.1250        Q
    ## 18         1      2   male 29.69912     0     0  13.0000        S
    ## 19         0      3 female 31.00000     1     0  18.0000        S
    ## 20         1      3 female 29.69912     0     0   7.2250        C
    ## 21         0      2   male 35.00000     0     0  26.0000        S
    ## 22         1      2   male 34.00000     0     0  13.0000        S
    ## 23         1      3 female 15.00000     0     0   8.0292        Q
    ## 24         1      1   male 28.00000     0     0  35.5000        S
    ## 25         0      3 female  8.00000     3     1  21.0750        S
    ## 26         1      3 female 38.00000     1     5  31.3875        S
    ## 27         0      3   male 29.69912     0     0   7.2250        C
    ## 28         0      1   male 19.00000     3     2 263.0000        S
    ## 29         1      3 female 29.69912     0     0   7.8792        Q
    ## 30         0      3   male 29.69912     0     0   7.8958        S
    ## 31         0      1   male 40.00000     0     0  27.7208        C
    ## 32         1      1 female 29.69912     1     0 146.5208        C
    ## 33         1      3 female 29.69912     0     0   7.7500        Q
    ## 34         0      2   male 66.00000     0     0  10.5000        S
    ## 35         0      1   male 28.00000     1     0  82.1708        C
    ## 36         0      1   male 42.00000     1     0  52.0000        S
    ## 37         1      3   male 29.69912     0     0   7.2292        C
    ## 38         0      3   male 21.00000     0     0   8.0500        S
    ## 39         0      3 female 18.00000     2     0  18.0000        S
    ## 40         1      3 female 14.00000     1     0  11.2417        C
    ## 41         0      3 female 40.00000     1     0   9.4750        S
    ## 42         0      2 female 27.00000     1     0  21.0000        S
    ## 43         0      3   male 29.69912     0     0   7.8958        C
    ## 44         1      2 female  3.00000     1     2  41.5792        C
    ## 45         1      3 female 19.00000     0     0   7.8792        Q
    ## 46         0      3   male 29.69912     0     0   8.0500        S
    ## 47         0      3   male 29.69912     1     0  15.5000        Q
    ## 48         1      3 female 29.69912     0     0   7.7500        Q
    ## 49         0      3   male 29.69912     2     0  21.6792        C
    ## 50         0      3 female 18.00000     1     0  17.8000        S
    ## 51         0      3   male  7.00000     4     1  39.6875        S
    ## 52         0      3   male 21.00000     0     0   7.8000        S
    ## 53         1      1 female 49.00000     1     0  76.7292        C
    ## 54         1      2 female 29.00000     1     0  26.0000        S
    ## 55         0      1   male 65.00000     0     1  61.9792        C
    ## 56         1      1   male 29.69912     0     0  35.5000        S
    ## 57         1      2 female 21.00000     0     0  10.5000        S
    ## 58         0      3   male 28.50000     0     0   7.2292        C
    ## 59         1      2 female  5.00000     1     2  27.7500        S
    ## 60         0      3   male 11.00000     5     2  46.9000        S
    ## 61         0      3   male 22.00000     0     0   7.2292        C
    ## 62         1      1 female 38.00000     0     0  80.0000         
    ## 63         0      1   male 45.00000     1     0  83.4750        S
    ## 64         0      3   male  4.00000     3     2  27.9000        S
    ## 65         0      1   male 29.69912     0     0  27.7208        C
    ## 66         1      3   male 29.69912     1     1  15.2458        C
    ## 67         1      2 female 29.00000     0     0  10.5000        S
    ## 68         0      3   male 19.00000     0     0   8.1583        S
    ## 69         1      3 female 17.00000     4     2   7.9250        S
    ## 70         0      3   male 26.00000     2     0   8.6625        S
    ## 71         0      2   male 32.00000     0     0  10.5000        S
    ## 72         0      3 female 16.00000     5     2  46.9000        S
    ## 73         0      2   male 21.00000     0     0  73.5000        S
    ## 74         0      3   male 26.00000     1     0  14.4542        C
    ## 75         1      3   male 32.00000     0     0  56.4958        S
    ## 76         0      3   male 25.00000     0     0   7.6500        S
    ## 77         0      3   male 29.69912     0     0   7.8958        S
    ## 78         0      3   male 29.69912     0     0   8.0500        S
    ## 79         1      2   male  0.83000     0     2  29.0000        S
    ## 80         1      3 female 30.00000     0     0  12.4750        S
    ## 81         0      3   male 22.00000     0     0   9.0000        S
    ## 82         1      3   male 29.00000     0     0   9.5000        S
    ## 83         1      3 female 29.69912     0     0   7.7875        Q
    ## 84         0      1   male 28.00000     0     0  47.1000        S
    ## 85         1      2 female 17.00000     0     0  10.5000        S
    ## 86         1      3 female 33.00000     3     0  15.8500        S
    ## 87         0      3   male 16.00000     1     3  34.3750        S
    ## 88         0      3   male 29.69912     0     0   8.0500        S
    ## 89         1      1 female 23.00000     3     2 263.0000        S
    ## 90         0      3   male 24.00000     0     0   8.0500        S
    ## 91         0      3   male 29.00000     0     0   8.0500        S
    ## 92         0      3   male 20.00000     0     0   7.8542        S
    ## 93         0      1   male 46.00000     1     0  61.1750        S
    ## 94         0      3   male 26.00000     1     2  20.5750        S
    ## 95         0      3   male 59.00000     0     0   7.2500        S
    ## 96         0      3   male 29.69912     0     0   8.0500        S
    ## 97         0      1   male 71.00000     0     0  34.6542        C
    ## 98         1      1   male 23.00000     0     1  63.3583        C
    ## 99         1      2 female 34.00000     0     1  23.0000        S
    ## 100        0      2   male 34.00000     1     0  26.0000        S
    ## 101        0      3 female 28.00000     0     0   7.8958        S
    ## 102        0      3   male 29.69912     0     0   7.8958        S
    ## 103        0      1   male 21.00000     0     1  77.2875        S
    ## 104        0      3   male 33.00000     0     0   8.6542        S
    ## 105        0      3   male 37.00000     2     0   7.9250        S
    ## 106        0      3   male 28.00000     0     0   7.8958        S
    ## 107        1      3 female 21.00000     0     0   7.6500        S
    ## 108        1      3   male 29.69912     0     0   7.7750        S
    ## 109        0      3   male 38.00000     0     0   7.8958        S
    ## 110        1      3 female 29.69912     1     0  24.1500        Q
    ## 111        0      1   male 47.00000     0     0  52.0000        S
    ## 112        0      3 female 14.50000     1     0  14.4542        C
    ## 113        0      3   male 22.00000     0     0   8.0500        S
    ## 114        0      3 female 20.00000     1     0   9.8250        S
    ## 115        0      3 female 17.00000     0     0  14.4583        C
    ## 116        0      3   male 21.00000     0     0   7.9250        S
    ## 117        0      3   male 70.50000     0     0   7.7500        Q
    ## 118        0      2   male 29.00000     1     0  21.0000        S
    ## 119        0      1   male 24.00000     0     1 247.5208        C
    ## 120        0      3 female  2.00000     4     2  31.2750        S
    ## 121        0      2   male 21.00000     2     0  73.5000        S
    ## 122        0      3   male 29.69912     0     0   8.0500        S
    ## 123        0      2   male 32.50000     1     0  30.0708        C
    ## 124        1      2 female 32.50000     0     0  13.0000        S
    ## 125        0      1   male 54.00000     0     1  77.2875        S
    ## 126        1      3   male 12.00000     1     0  11.2417        C
    ## 127        0      3   male 29.69912     0     0   7.7500        Q
    ## 128        1      3   male 24.00000     0     0   7.1417        S
    ## 129        1      3 female 29.69912     1     1  22.3583        C
    ## 130        0      3   male 45.00000     0     0   6.9750        S
    ## 131        0      3   male 33.00000     0     0   7.8958        C
    ## 132        0      3   male 20.00000     0     0   7.0500        S
    ## 133        0      3 female 47.00000     1     0  14.5000        S
    ## 134        1      2 female 29.00000     1     0  26.0000        S
    ## 135        0      2   male 25.00000     0     0  13.0000        S
    ## 136        0      2   male 23.00000     0     0  15.0458        C
    ## 137        1      1 female 19.00000     0     2  26.2833        S
    ## 138        0      1   male 37.00000     1     0  53.1000        S
    ## 139        0      3   male 16.00000     0     0   9.2167        S
    ## 140        0      1   male 24.00000     0     0  79.2000        C
    ## 141        0      3 female 29.69912     0     2  15.2458        C
    ## 142        1      3 female 22.00000     0     0   7.7500        S
    ## 143        1      3 female 24.00000     1     0  15.8500        S
    ## 144        0      3   male 19.00000     0     0   6.7500        Q
    ## 145        0      2   male 18.00000     0     0  11.5000        S
    ## 146        0      2   male 19.00000     1     1  36.7500        S
    ## 147        1      3   male 27.00000     0     0   7.7958        S
    ## 148        0      3 female  9.00000     2     2  34.3750        S
    ## 149        0      2   male 36.50000     0     2  26.0000        S
    ## 150        0      2   male 42.00000     0     0  13.0000        S
    ## 151        0      2   male 51.00000     0     0  12.5250        S
    ## 152        1      1 female 22.00000     1     0  66.6000        S
    ## 153        0      3   male 55.50000     0     0   8.0500        S
    ## 154        0      3   male 40.50000     0     2  14.5000        S
    ## 155        0      3   male 29.69912     0     0   7.3125        S
    ## 156        0      1   male 51.00000     0     1  61.3792        C
    ## 157        1      3 female 16.00000     0     0   7.7333        Q
    ## 158        0      3   male 30.00000     0     0   8.0500        S
    ## 159        0      3   male 29.69912     0     0   8.6625        S
    ## 160        0      3   male 29.69912     8     2  69.5500        S
    ## 161        0      3   male 44.00000     0     1  16.1000        S
    ## 162        1      2 female 40.00000     0     0  15.7500        S
    ## 163        0      3   male 26.00000     0     0   7.7750        S
    ## 164        0      3   male 17.00000     0     0   8.6625        S
    ## 165        0      3   male  1.00000     4     1  39.6875        S
    ## 166        1      3   male  9.00000     0     2  20.5250        S
    ## 167        1      1 female 29.69912     0     1  55.0000        S
    ## 168        0      3 female 45.00000     1     4  27.9000        S
    ## 169        0      1   male 29.69912     0     0  25.9250        S
    ## 170        0      3   male 28.00000     0     0  56.4958        S
    ## 171        0      1   male 61.00000     0     0  33.5000        S
    ## 172        0      3   male  4.00000     4     1  29.1250        Q
    ## 173        1      3 female  1.00000     1     1  11.1333        S
    ## 174        0      3   male 21.00000     0     0   7.9250        S
    ## 175        0      1   male 56.00000     0     0  30.6958        C
    ## 176        0      3   male 18.00000     1     1   7.8542        S
    ## 177        0      3   male 29.69912     3     1  25.4667        S
    ## 178        0      1 female 50.00000     0     0  28.7125        C
    ## 179        0      2   male 30.00000     0     0  13.0000        S
    ## 180        0      3   male 36.00000     0     0   0.0000        S
    ## 181        0      3 female 29.69912     8     2  69.5500        S
    ## 182        0      2   male 29.69912     0     0  15.0500        C
    ## 183        0      3   male  9.00000     4     2  31.3875        S
    ## 184        1      2   male  1.00000     2     1  39.0000        S
    ## 185        1      3 female  4.00000     0     2  22.0250        S
    ## 186        0      1   male 29.69912     0     0  50.0000        S
    ## 187        1      3 female 29.69912     1     0  15.5000        Q
    ## 188        1      1   male 45.00000     0     0  26.5500        S
    ## 189        0      3   male 40.00000     1     1  15.5000        Q
    ## 190        0      3   male 36.00000     0     0   7.8958        S
    ## 191        1      2 female 32.00000     0     0  13.0000        S
    ## 192        0      2   male 19.00000     0     0  13.0000        S
    ## 193        1      3 female 19.00000     1     0   7.8542        S
    ## 194        1      2   male  3.00000     1     1  26.0000        S
    ## 195        1      1 female 44.00000     0     0  27.7208        C
    ## 196        1      1 female 58.00000     0     0 146.5208        C
    ## 197        0      3   male 29.69912     0     0   7.7500        Q
    ## 198        0      3   male 42.00000     0     1   8.4042        S
    ## 199        1      3 female 29.69912     0     0   7.7500        Q
    ## 200        0      2 female 24.00000     0     0  13.0000        S
    ## 201        0      3   male 28.00000     0     0   9.5000        S
    ## 202        0      3   male 29.69912     8     2  69.5500        S
    ## 203        0      3   male 34.00000     0     0   6.4958        S
    ## 204        0      3   male 45.50000     0     0   7.2250        C
    ## 205        1      3   male 18.00000     0     0   8.0500        S
    ## 206        0      3 female  2.00000     0     1  10.4625        S
    ## 207        0      3   male 32.00000     1     0  15.8500        S
    ## 208        1      3   male 26.00000     0     0  18.7875        C
    ## 209        1      3 female 16.00000     0     0   7.7500        Q
    ## 210        1      1   male 40.00000     0     0  31.0000        C
    ## 211        0      3   male 24.00000     0     0   7.0500        S
    ## 212        1      2 female 35.00000     0     0  21.0000        S
    ## 213        0      3   male 22.00000     0     0   7.2500        S
    ## 214        0      2   male 30.00000     0     0  13.0000        S
    ## 215        0      3   male 29.69912     1     0   7.7500        Q
    ## 216        1      1 female 31.00000     1     0 113.2750        C
    ## 217        1      3 female 27.00000     0     0   7.9250        S
    ## 218        0      2   male 42.00000     1     0  27.0000        S
    ## 219        1      1 female 32.00000     0     0  76.2917        C
    ## 220        0      2   male 30.00000     0     0  10.5000        S
    ## 221        1      3   male 16.00000     0     0   8.0500        S
    ## 222        0      2   male 27.00000     0     0  13.0000        S
    ## 223        0      3   male 51.00000     0     0   8.0500        S
    ## 224        0      3   male 29.69912     0     0   7.8958        S
    ## 225        1      1   male 38.00000     1     0  90.0000        S
    ## 226        0      3   male 22.00000     0     0   9.3500        S
    ## 227        1      2   male 19.00000     0     0  10.5000        S
    ## 228        0      3   male 20.50000     0     0   7.2500        S
    ## 229        0      2   male 18.00000     0     0  13.0000        S
    ## 230        0      3 female 29.69912     3     1  25.4667        S
    ## 231        1      1 female 35.00000     1     0  83.4750        S
    ## 232        0      3   male 29.00000     0     0   7.7750        S
    ## 233        0      2   male 59.00000     0     0  13.5000        S
    ## 234        1      3 female  5.00000     4     2  31.3875        S
    ## 235        0      2   male 24.00000     0     0  10.5000        S
    ## 236        0      3 female 29.69912     0     0   7.5500        S
    ## 237        0      2   male 44.00000     1     0  26.0000        S
    ## 238        1      2 female  8.00000     0     2  26.2500        S
    ## 239        0      2   male 19.00000     0     0  10.5000        S
    ## 240        0      2   male 33.00000     0     0  12.2750        S
    ## 241        0      3 female 29.69912     1     0  14.4542        C
    ## 242        1      3 female 29.69912     1     0  15.5000        Q
    ## 243        0      2   male 29.00000     0     0  10.5000        S
    ## 244        0      3   male 22.00000     0     0   7.1250        S
    ## 245        0      3   male 30.00000     0     0   7.2250        C
    ## 246        0      1   male 44.00000     2     0  90.0000        Q
    ## 247        0      3 female 25.00000     0     0   7.7750        S
    ## 248        1      2 female 24.00000     0     2  14.5000        S
    ## 249        1      1   male 37.00000     1     1  52.5542        S
    ## 250        0      2   male 54.00000     1     0  26.0000        S
    ## 251        0      3   male 29.69912     0     0   7.2500        S
    ## 252        0      3 female 29.00000     1     1  10.4625        S
    ## 253        0      1   male 62.00000     0     0  26.5500        S
    ## 254        0      3   male 30.00000     1     0  16.1000        S
    ## 255        0      3 female 41.00000     0     2  20.2125        S
    ## 256        1      3 female 29.00000     0     2  15.2458        C
    ## 257        1      1 female 29.69912     0     0  79.2000        C
    ## 258        1      1 female 30.00000     0     0  86.5000        S
    ## 259        1      1 female 35.00000     0     0 512.3292        C
    ## 260        1      2 female 50.00000     0     1  26.0000        S
    ## 261        0      3   male 29.69912     0     0   7.7500        Q
    ## 262        1      3   male  3.00000     4     2  31.3875        S
    ## 263        0      1   male 52.00000     1     1  79.6500        S
    ## 264        0      1   male 40.00000     0     0   0.0000        S
    ## 265        0      3 female 29.69912     0     0   7.7500        Q
    ## 266        0      2   male 36.00000     0     0  10.5000        S
    ## 267        0      3   male 16.00000     4     1  39.6875        S
    ## 268        1      3   male 25.00000     1     0   7.7750        S
    ## 269        1      1 female 58.00000     0     1 153.4625        S
    ## 270        1      1 female 35.00000     0     0 135.6333        S
    ## 271        0      1   male 29.69912     0     0  31.0000        S
    ## 272        1      3   male 25.00000     0     0   0.0000        S
    ## 273        1      2 female 41.00000     0     1  19.5000        S
    ## 274        0      1   male 37.00000     0     1  29.7000        C
    ## 275        1      3 female 29.69912     0     0   7.7500        Q
    ## 276        1      1 female 63.00000     1     0  77.9583        S
    ## 277        0      3 female 45.00000     0     0   7.7500        S
    ## 278        0      2   male 29.69912     0     0   0.0000        S
    ## 279        0      3   male  7.00000     4     1  29.1250        Q
    ## 280        1      3 female 35.00000     1     1  20.2500        S
    ## 281        0      3   male 65.00000     0     0   7.7500        Q
    ## 282        0      3   male 28.00000     0     0   7.8542        S
    ## 283        0      3   male 16.00000     0     0   9.5000        S
    ## 284        1      3   male 19.00000     0     0   8.0500        S
    ## 285        0      1   male 29.69912     0     0  26.0000        S
    ## 286        0      3   male 33.00000     0     0   8.6625        C
    ## 287        1      3   male 30.00000     0     0   9.5000        S
    ## 288        0      3   male 22.00000     0     0   7.8958        S
    ## 289        1      2   male 42.00000     0     0  13.0000        S
    ## 290        1      3 female 22.00000     0     0   7.7500        Q
    ## 291        1      1 female 26.00000     0     0  78.8500        S
    ## 292        1      1 female 19.00000     1     0  91.0792        C
    ## 293        0      2   male 36.00000     0     0  12.8750        C
    ## 294        0      3 female 24.00000     0     0   8.8500        S
    ## 295        0      3   male 24.00000     0     0   7.8958        S
    ## 296        0      1   male 29.69912     0     0  27.7208        C
    ## 297        0      3   male 23.50000     0     0   7.2292        C
    ## 298        0      1 female  2.00000     1     2 151.5500        S
    ## 299        1      1   male 29.69912     0     0  30.5000        S
    ## 300        1      1 female 50.00000     0     1 247.5208        C
    ## 301        1      3 female 29.69912     0     0   7.7500        Q
    ## 302        1      3   male 29.69912     2     0  23.2500        Q
    ## 303        0      3   male 19.00000     0     0   0.0000        S
    ## 304        1      2 female 29.69912     0     0  12.3500        Q
    ## 305        0      3   male 29.69912     0     0   8.0500        S
    ## 306        1      1   male  0.92000     1     2 151.5500        S
    ## 307        1      1 female 29.69912     0     0 110.8833        C
    ## 308        1      1 female 17.00000     1     0 108.9000        C
    ## 309        0      2   male 30.00000     1     0  24.0000        C
    ## 310        1      1 female 30.00000     0     0  56.9292        C
    ## 311        1      1 female 24.00000     0     0  83.1583        C
    ## 312        1      1 female 18.00000     2     2 262.3750        C
    ## 313        0      2 female 26.00000     1     1  26.0000        S
    ## 314        0      3   male 28.00000     0     0   7.8958        S
    ## 315        0      2   male 43.00000     1     1  26.2500        S
    ## 316        1      3 female 26.00000     0     0   7.8542        S
    ## 317        1      2 female 24.00000     1     0  26.0000        S
    ## 318        0      2   male 54.00000     0     0  14.0000        S
    ## 319        1      1 female 31.00000     0     2 164.8667        S
    ## 320        1      1 female 40.00000     1     1 134.5000        C
    ## 321        0      3   male 22.00000     0     0   7.2500        S
    ## 322        0      3   male 27.00000     0     0   7.8958        S
    ## 323        1      2 female 30.00000     0     0  12.3500        Q
    ## 324        1      2 female 22.00000     1     1  29.0000        S
    ## 325        0      3   male 29.69912     8     2  69.5500        S
    ## 326        1      1 female 36.00000     0     0 135.6333        C
    ## 327        0      3   male 61.00000     0     0   6.2375        S
    ## 328        1      2 female 36.00000     0     0  13.0000        S
    ## 329        1      3 female 31.00000     1     1  20.5250        S
    ## 330        1      1 female 16.00000     0     1  57.9792        C
    ## 331        1      3 female 29.69912     2     0  23.2500        Q
    ## 332        0      1   male 45.50000     0     0  28.5000        S
    ## 333        0      1   male 38.00000     0     1 153.4625        S
    ## 334        0      3   male 16.00000     2     0  18.0000        S
    ## 335        1      1 female 29.69912     1     0 133.6500        S
    ## 336        0      3   male 29.69912     0     0   7.8958        S
    ## 337        0      1   male 29.00000     1     0  66.6000        S
    ## 338        1      1 female 41.00000     0     0 134.5000        C
    ## 339        1      3   male 45.00000     0     0   8.0500        S
    ## 340        0      1   male 45.00000     0     0  35.5000        S
    ## 341        1      2   male  2.00000     1     1  26.0000        S
    ## 342        1      1 female 24.00000     3     2 263.0000        S
    ## 343        0      2   male 28.00000     0     0  13.0000        S
    ## 344        0      2   male 25.00000     0     0  13.0000        S
    ## 345        0      2   male 36.00000     0     0  13.0000        S
    ## 346        1      2 female 24.00000     0     0  13.0000        S
    ## 347        1      2 female 40.00000     0     0  13.0000        S
    ## 348        1      3 female 29.69912     1     0  16.1000        S
    ## 349        1      3   male  3.00000     1     1  15.9000        S
    ## 350        0      3   male 42.00000     0     0   8.6625        S
    ## 351        0      3   male 23.00000     0     0   9.2250        S
    ## 352        0      1   male 29.69912     0     0  35.0000        S
    ## 353        0      3   male 15.00000     1     1   7.2292        C
    ## 354        0      3   male 25.00000     1     0  17.8000        S
    ## 355        0      3   male 29.69912     0     0   7.2250        C
    ## 356        0      3   male 28.00000     0     0   9.5000        S
    ## 357        1      1 female 22.00000     0     1  55.0000        S
    ## 358        0      2 female 38.00000     0     0  13.0000        S
    ## 359        1      3 female 29.69912     0     0   7.8792        Q
    ## 360        1      3 female 29.69912     0     0   7.8792        Q
    ## 361        0      3   male 40.00000     1     4  27.9000        S
    ## 362        0      2   male 29.00000     1     0  27.7208        C
    ## 363        0      3 female 45.00000     0     1  14.4542        C
    ## 364        0      3   male 35.00000     0     0   7.0500        S
    ## 365        0      3   male 29.69912     1     0  15.5000        Q
    ## 366        0      3   male 30.00000     0     0   7.2500        S
    ## 367        1      1 female 60.00000     1     0  75.2500        C
    ## 368        1      3 female 29.69912     0     0   7.2292        C
    ## 369        1      3 female 29.69912     0     0   7.7500        Q
    ## 370        1      1 female 24.00000     0     0  69.3000        C
    ## 371        1      1   male 25.00000     1     0  55.4417        C
    ## 372        0      3   male 18.00000     1     0   6.4958        S
    ## 373        0      3   male 19.00000     0     0   8.0500        S
    ## 374        0      1   male 22.00000     0     0 135.6333        C
    ## 375        0      3 female  3.00000     3     1  21.0750        S
    ## 376        1      1 female 29.69912     1     0  82.1708        C
    ## 377        1      3 female 22.00000     0     0   7.2500        S
    ## 378        0      1   male 27.00000     0     2 211.5000        C
    ## 379        0      3   male 20.00000     0     0   4.0125        C
    ## 380        0      3   male 19.00000     0     0   7.7750        S
    ## 381        1      1 female 42.00000     0     0 227.5250        C
    ## 382        1      3 female  1.00000     0     2  15.7417        C
    ## 383        0      3   male 32.00000     0     0   7.9250        S
    ## 384        1      1 female 35.00000     1     0  52.0000        S
    ## 385        0      3   male 29.69912     0     0   7.8958        S
    ## 386        0      2   male 18.00000     0     0  73.5000        S
    ## 387        0      3   male  1.00000     5     2  46.9000        S
    ## 388        1      2 female 36.00000     0     0  13.0000        S
    ## 389        0      3   male 29.69912     0     0   7.7292        Q
    ## 390        1      2 female 17.00000     0     0  12.0000        C
    ## 391        1      1   male 36.00000     1     2 120.0000        S
    ## 392        1      3   male 21.00000     0     0   7.7958        S
    ## 393        0      3   male 28.00000     2     0   7.9250        S
    ## 394        1      1 female 23.00000     1     0 113.2750        C
    ## 395        1      3 female 24.00000     0     2  16.7000        S
    ## 396        0      3   male 22.00000     0     0   7.7958        S
    ## 397        0      3 female 31.00000     0     0   7.8542        S
    ## 398        0      2   male 46.00000     0     0  26.0000        S
    ## 399        0      2   male 23.00000     0     0  10.5000        S
    ## 400        1      2 female 28.00000     0     0  12.6500        S
    ## 401        1      3   male 39.00000     0     0   7.9250        S
    ## 402        0      3   male 26.00000     0     0   8.0500        S
    ## 403        0      3 female 21.00000     1     0   9.8250        S
    ## 404        0      3   male 28.00000     1     0  15.8500        S
    ## 405        0      3 female 20.00000     0     0   8.6625        S
    ## 406        0      2   male 34.00000     1     0  21.0000        S
    ## 407        0      3   male 51.00000     0     0   7.7500        S
    ## 408        1      2   male  3.00000     1     1  18.7500        S
    ## 409        0      3   male 21.00000     0     0   7.7750        S
    ## 410        0      3 female 29.69912     3     1  25.4667        S
    ## 411        0      3   male 29.69912     0     0   7.8958        S
    ## 412        0      3   male 29.69912     0     0   6.8583        Q
    ## 413        1      1 female 33.00000     1     0  90.0000        Q
    ## 414        0      2   male 29.69912     0     0   0.0000        S
    ## 415        1      3   male 44.00000     0     0   7.9250        S
    ## 416        0      3 female 29.69912     0     0   8.0500        S
    ## 417        1      2 female 34.00000     1     1  32.5000        S
    ## 418        1      2 female 18.00000     0     2  13.0000        S
    ## 419        0      2   male 30.00000     0     0  13.0000        S
    ## 420        0      3 female 10.00000     0     2  24.1500        S
    ## 421        0      3   male 29.69912     0     0   7.8958        C
    ## 422        0      3   male 21.00000     0     0   7.7333        Q
    ## 423        0      3   male 29.00000     0     0   7.8750        S
    ## 424        0      3 female 28.00000     1     1  14.4000        S
    ## 425        0      3   male 18.00000     1     1  20.2125        S
    ## 426        0      3   male 29.69912     0     0   7.2500        S
    ## 427        1      2 female 28.00000     1     0  26.0000        S
    ## 428        1      2 female 19.00000     0     0  26.0000        S
    ## 429        0      3   male 29.69912     0     0   7.7500        Q
    ## 430        1      3   male 32.00000     0     0   8.0500        S
    ## 431        1      1   male 28.00000     0     0  26.5500        S
    ## 432        1      3 female 29.69912     1     0  16.1000        S
    ## 433        1      2 female 42.00000     1     0  26.0000        S
    ## 434        0      3   male 17.00000     0     0   7.1250        S
    ## 435        0      1   male 50.00000     1     0  55.9000        S
    ## 436        1      1 female 14.00000     1     2 120.0000        S
    ## 437        0      3 female 21.00000     2     2  34.3750        S
    ## 438        1      2 female 24.00000     2     3  18.7500        S
    ## 439        0      1   male 64.00000     1     4 263.0000        S
    ## 440        0      2   male 31.00000     0     0  10.5000        S
    ## 441        1      2 female 45.00000     1     1  26.2500        S
    ## 442        0      3   male 20.00000     0     0   9.5000        S
    ## 443        0      3   male 25.00000     1     0   7.7750        S
    ## 444        1      2 female 28.00000     0     0  13.0000        S
    ## 445        1      3   male 29.69912     0     0   8.1125        S
    ## 446        1      1   male  4.00000     0     2  81.8583        S
    ## 447        1      2 female 13.00000     0     1  19.5000        S
    ## 448        1      1   male 34.00000     0     0  26.5500        S
    ## 449        1      3 female  5.00000     2     1  19.2583        C
    ## 450        1      1   male 52.00000     0     0  30.5000        S
    ## 451        0      2   male 36.00000     1     2  27.7500        S
    ## 452        0      3   male 29.69912     1     0  19.9667        S
    ## 453        0      1   male 30.00000     0     0  27.7500        C
    ## 454        1      1   male 49.00000     1     0  89.1042        C
    ## 455        0      3   male 29.69912     0     0   8.0500        S
    ## 456        1      3   male 29.00000     0     0   7.8958        C
    ## 457        0      1   male 65.00000     0     0  26.5500        S
    ## 458        1      1 female 29.69912     1     0  51.8625        S
    ## 459        1      2 female 50.00000     0     0  10.5000        S
    ## 460        0      3   male 29.69912     0     0   7.7500        Q
    ## 461        1      1   male 48.00000     0     0  26.5500        S
    ## 462        0      3   male 34.00000     0     0   8.0500        S
    ## 463        0      1   male 47.00000     0     0  38.5000        S
    ## 464        0      2   male 48.00000     0     0  13.0000        S
    ## 465        0      3   male 29.69912     0     0   8.0500        S
    ## 466        0      3   male 38.00000     0     0   7.0500        S
    ## 467        0      2   male 29.69912     0     0   0.0000        S
    ## 468        0      1   male 56.00000     0     0  26.5500        S
    ## 469        0      3   male 29.69912     0     0   7.7250        Q
    ## 470        1      3 female  0.75000     2     1  19.2583        C
    ## 471        0      3   male 29.69912     0     0   7.2500        S
    ## 472        0      3   male 38.00000     0     0   8.6625        S
    ## 473        1      2 female 33.00000     1     2  27.7500        S
    ## 474        1      2 female 23.00000     0     0  13.7917        C
    ## 475        0      3 female 22.00000     0     0   9.8375        S
    ## 476        0      1   male 29.69912     0     0  52.0000        S
    ## 477        0      2   male 34.00000     1     0  21.0000        S
    ## 478        0      3   male 29.00000     1     0   7.0458        S
    ## 479        0      3   male 22.00000     0     0   7.5208        S
    ## 480        1      3 female  2.00000     0     1  12.2875        S
    ## 481        0      3   male  9.00000     5     2  46.9000        S
    ## 482        0      2   male 29.69912     0     0   0.0000        S
    ## 483        0      3   male 50.00000     0     0   8.0500        S
    ## 484        1      3 female 63.00000     0     0   9.5875        S
    ## 485        1      1   male 25.00000     1     0  91.0792        C
    ## 486        0      3 female 29.69912     3     1  25.4667        S
    ## 487        1      1 female 35.00000     1     0  90.0000        S
    ## 488        0      1   male 58.00000     0     0  29.7000        C
    ## 489        0      3   male 30.00000     0     0   8.0500        S
    ## 490        1      3   male  9.00000     1     1  15.9000        S
    ## 491        0      3   male 29.69912     1     0  19.9667        S
    ## 492        0      3   male 21.00000     0     0   7.2500        S
    ## 493        0      1   male 55.00000     0     0  30.5000        S
    ## 494        0      1   male 71.00000     0     0  49.5042        C
    ## 495        0      3   male 21.00000     0     0   8.0500        S
    ## 496        0      3   male 29.69912     0     0  14.4583        C
    ## 497        1      1 female 54.00000     1     0  78.2667        C
    ## 498        0      3   male 29.69912     0     0  15.1000        S
    ## 499        0      1 female 25.00000     1     2 151.5500        S
    ## 500        0      3   male 24.00000     0     0   7.7958        S
    ## 501        0      3   male 17.00000     0     0   8.6625        S
    ## 502        0      3 female 21.00000     0     0   7.7500        Q
    ## 503        0      3 female 29.69912     0     0   7.6292        Q
    ## 504        0      3 female 37.00000     0     0   9.5875        S
    ## 505        1      1 female 16.00000     0     0  86.5000        S
    ## 506        0      1   male 18.00000     1     0 108.9000        C
    ## 507        1      2 female 33.00000     0     2  26.0000        S
    ## 508        1      1   male 29.69912     0     0  26.5500        S
    ## 509        0      3   male 28.00000     0     0  22.5250        S
    ## 510        1      3   male 26.00000     0     0  56.4958        S
    ## 511        1      3   male 29.00000     0     0   7.7500        Q
    ## 512        0      3   male 29.69912     0     0   8.0500        S
    ## 513        1      1   male 36.00000     0     0  26.2875        S
    ## 514        1      1 female 54.00000     1     0  59.4000        C
    ## 515        0      3   male 24.00000     0     0   7.4958        S
    ## 516        0      1   male 47.00000     0     0  34.0208        S
    ## 517        1      2 female 34.00000     0     0  10.5000        S
    ## 518        0      3   male 29.69912     0     0  24.1500        Q
    ## 519        1      2 female 36.00000     1     0  26.0000        S
    ## 520        0      3   male 32.00000     0     0   7.8958        S
    ## 521        1      1 female 30.00000     0     0  93.5000        S
    ## 522        0      3   male 22.00000     0     0   7.8958        S
    ## 523        0      3   male 29.69912     0     0   7.2250        C
    ## 524        1      1 female 44.00000     0     1  57.9792        C
    ## 525        0      3   male 29.69912     0     0   7.2292        C
    ## 526        0      3   male 40.50000     0     0   7.7500        Q
    ## 527        1      2 female 50.00000     0     0  10.5000        S
    ## 528        0      1   male 29.69912     0     0 221.7792        S
    ## 529        0      3   male 39.00000     0     0   7.9250        S
    ## 530        0      2   male 23.00000     2     1  11.5000        S
    ## 531        1      2 female  2.00000     1     1  26.0000        S
    ## 532        0      3   male 29.69912     0     0   7.2292        C
    ## 533        0      3   male 17.00000     1     1   7.2292        C
    ## 534        1      3 female 29.69912     0     2  22.3583        C
    ## 535        0      3 female 30.00000     0     0   8.6625        S
    ## 536        1      2 female  7.00000     0     2  26.2500        S
    ## 537        0      1   male 45.00000     0     0  26.5500        S
    ## 538        1      1 female 30.00000     0     0 106.4250        C
    ## 539        0      3   male 29.69912     0     0  14.5000        S
    ## 540        1      1 female 22.00000     0     2  49.5000        C
    ## 541        1      1 female 36.00000     0     2  71.0000        S
    ## 542        0      3 female  9.00000     4     2  31.2750        S
    ## 543        0      3 female 11.00000     4     2  31.2750        S
    ## 544        1      2   male 32.00000     1     0  26.0000        S
    ## 545        0      1   male 50.00000     1     0 106.4250        C
    ## 546        0      1   male 64.00000     0     0  26.0000        S
    ## 547        1      2 female 19.00000     1     0  26.0000        S
    ## 548        1      2   male 29.69912     0     0  13.8625        C
    ## 549        0      3   male 33.00000     1     1  20.5250        S
    ## 550        1      2   male  8.00000     1     1  36.7500        S
    ## 551        1      1   male 17.00000     0     2 110.8833        C
    ## 552        0      2   male 27.00000     0     0  26.0000        S
    ## 553        0      3   male 29.69912     0     0   7.8292        Q
    ## 554        1      3   male 22.00000     0     0   7.2250        C
    ## 555        1      3 female 22.00000     0     0   7.7750        S
    ## 556        0      1   male 62.00000     0     0  26.5500        S
    ## 557        1      1 female 48.00000     1     0  39.6000        C
    ## 558        0      1   male 29.69912     0     0 227.5250        C
    ## 559        1      1 female 39.00000     1     1  79.6500        S
    ## 560        1      3 female 36.00000     1     0  17.4000        S
    ## 561        0      3   male 29.69912     0     0   7.7500        Q
    ## 562        0      3   male 40.00000     0     0   7.8958        S
    ## 563        0      2   male 28.00000     0     0  13.5000        S
    ## 564        0      3   male 29.69912     0     0   8.0500        S
    ## 565        0      3 female 29.69912     0     0   8.0500        S
    ## 566        0      3   male 24.00000     2     0  24.1500        S
    ## 567        0      3   male 19.00000     0     0   7.8958        S
    ## 568        0      3 female 29.00000     0     4  21.0750        S
    ## 569        0      3   male 29.69912     0     0   7.2292        C
    ## 570        1      3   male 32.00000     0     0   7.8542        S
    ## 571        1      2   male 62.00000     0     0  10.5000        S
    ## 572        1      1 female 53.00000     2     0  51.4792        S
    ## 573        1      1   male 36.00000     0     0  26.3875        S
    ## 574        1      3 female 29.69912     0     0   7.7500        Q
    ## 575        0      3   male 16.00000     0     0   8.0500        S
    ## 576        0      3   male 19.00000     0     0  14.5000        S
    ## 577        1      2 female 34.00000     0     0  13.0000        S
    ## 578        1      1 female 39.00000     1     0  55.9000        S
    ## 579        0      3 female 29.69912     1     0  14.4583        C
    ## 580        1      3   male 32.00000     0     0   7.9250        S
    ## 581        1      2 female 25.00000     1     1  30.0000        S
    ## 582        1      1 female 39.00000     1     1 110.8833        C
    ## 583        0      2   male 54.00000     0     0  26.0000        S
    ## 584        0      1   male 36.00000     0     0  40.1250        C
    ## 585        0      3   male 29.69912     0     0   8.7125        C
    ## 586        1      1 female 18.00000     0     2  79.6500        S
    ## 587        0      2   male 47.00000     0     0  15.0000        S
    ## 588        1      1   male 60.00000     1     1  79.2000        C
    ## 589        0      3   male 22.00000     0     0   8.0500        S
    ## 590        0      3   male 29.69912     0     0   8.0500        S
    ## 591        0      3   male 35.00000     0     0   7.1250        S
    ## 592        1      1 female 52.00000     1     0  78.2667        C
    ## 593        0      3   male 47.00000     0     0   7.2500        S
    ## 594        0      3 female 29.69912     0     2   7.7500        Q
    ## 595        0      2   male 37.00000     1     0  26.0000        S
    ## 596        0      3   male 36.00000     1     1  24.1500        S
    ## 597        1      2 female 29.69912     0     0  33.0000        S
    ## 598        0      3   male 49.00000     0     0   0.0000        S
    ## 599        0      3   male 29.69912     0     0   7.2250        C
    ## 600        1      1   male 49.00000     1     0  56.9292        C
    ## 601        1      2 female 24.00000     2     1  27.0000        S
    ## 602        0      3   male 29.69912     0     0   7.8958        S
    ## 603        0      1   male 29.69912     0     0  42.4000        S
    ## 604        0      3   male 44.00000     0     0   8.0500        S
    ## 605        1      1   male 35.00000     0     0  26.5500        C
    ## 606        0      3   male 36.00000     1     0  15.5500        S
    ## 607        0      3   male 30.00000     0     0   7.8958        S
    ## 608        1      1   male 27.00000     0     0  30.5000        S
    ## 609        1      2 female 22.00000     1     2  41.5792        C
    ## 610        1      1 female 40.00000     0     0 153.4625        S
    ## 611        0      3 female 39.00000     1     5  31.2750        S
    ## 612        0      3   male 29.69912     0     0   7.0500        S
    ## 613        1      3 female 29.69912     1     0  15.5000        Q
    ## 614        0      3   male 29.69912     0     0   7.7500        Q
    ## 615        0      3   male 35.00000     0     0   8.0500        S
    ## 616        1      2 female 24.00000     1     2  65.0000        S
    ## 617        0      3   male 34.00000     1     1  14.4000        S
    ## 618        0      3 female 26.00000     1     0  16.1000        S
    ## 619        1      2 female  4.00000     2     1  39.0000        S
    ## 620        0      2   male 26.00000     0     0  10.5000        S
    ## 621        0      3   male 27.00000     1     0  14.4542        C
    ## 622        1      1   male 42.00000     1     0  52.5542        S
    ## 623        1      3   male 20.00000     1     1  15.7417        C
    ## 624        0      3   male 21.00000     0     0   7.8542        S
    ## 625        0      3   male 21.00000     0     0  16.1000        S
    ## 626        0      1   male 61.00000     0     0  32.3208        S
    ## 627        0      2   male 57.00000     0     0  12.3500        Q
    ## 628        1      1 female 21.00000     0     0  77.9583        S
    ## 629        0      3   male 26.00000     0     0   7.8958        S
    ## 630        0      3   male 29.69912     0     0   7.7333        Q
    ## 631        1      1   male 80.00000     0     0  30.0000        S
    ## 632        0      3   male 51.00000     0     0   7.0542        S
    ## 633        1      1   male 32.00000     0     0  30.5000        C
    ## 634        0      1   male 29.69912     0     0   0.0000        S
    ## 635        0      3 female  9.00000     3     2  27.9000        S
    ## 636        1      2 female 28.00000     0     0  13.0000        S
    ## 637        0      3   male 32.00000     0     0   7.9250        S
    ## 638        0      2   male 31.00000     1     1  26.2500        S
    ## 639        0      3 female 41.00000     0     5  39.6875        S
    ## 640        0      3   male 29.69912     1     0  16.1000        S
    ## 641        0      3   male 20.00000     0     0   7.8542        S
    ## 642        1      1 female 24.00000     0     0  69.3000        C
    ## 643        0      3 female  2.00000     3     2  27.9000        S
    ## 644        1      3   male 29.69912     0     0  56.4958        S
    ## 645        1      3 female  0.75000     2     1  19.2583        C
    ## 646        1      1   male 48.00000     1     0  76.7292        C
    ## 647        0      3   male 19.00000     0     0   7.8958        S
    ## 648        1      1   male 56.00000     0     0  35.5000        C
    ## 649        0      3   male 29.69912     0     0   7.5500        S
    ## 650        1      3 female 23.00000     0     0   7.5500        S
    ## 651        0      3   male 29.69912     0     0   7.8958        S
    ## 652        1      2 female 18.00000     0     1  23.0000        S
    ## 653        0      3   male 21.00000     0     0   8.4333        S
    ## 654        1      3 female 29.69912     0     0   7.8292        Q
    ## 655        0      3 female 18.00000     0     0   6.7500        Q
    ## 656        0      2   male 24.00000     2     0  73.5000        S
    ## 657        0      3   male 29.69912     0     0   7.8958        S
    ## 658        0      3 female 32.00000     1     1  15.5000        Q
    ## 659        0      2   male 23.00000     0     0  13.0000        S
    ## 660        0      1   male 58.00000     0     2 113.2750        C
    ## 661        1      1   male 50.00000     2     0 133.6500        S
    ## 662        0      3   male 40.00000     0     0   7.2250        C
    ## 663        0      1   male 47.00000     0     0  25.5875        S
    ## 664        0      3   male 36.00000     0     0   7.4958        S
    ## 665        1      3   male 20.00000     1     0   7.9250        S
    ## 666        0      2   male 32.00000     2     0  73.5000        S
    ## 667        0      2   male 25.00000     0     0  13.0000        S
    ## 668        0      3   male 29.69912     0     0   7.7750        S
    ## 669        0      3   male 43.00000     0     0   8.0500        S
    ## 670        1      1 female 29.69912     1     0  52.0000        S
    ## 671        1      2 female 40.00000     1     1  39.0000        S
    ## 672        0      1   male 31.00000     1     0  52.0000        S
    ## 673        0      2   male 70.00000     0     0  10.5000        S
    ## 674        1      2   male 31.00000     0     0  13.0000        S
    ## 675        0      2   male 29.69912     0     0   0.0000        S
    ## 676        0      3   male 18.00000     0     0   7.7750        S
    ## 677        0      3   male 24.50000     0     0   8.0500        S
    ## 678        1      3 female 18.00000     0     0   9.8417        S
    ## 679        0      3 female 43.00000     1     6  46.9000        S
    ## 680        1      1   male 36.00000     0     1 512.3292        C
    ## 681        0      3 female 29.69912     0     0   8.1375        Q
    ## 682        1      1   male 27.00000     0     0  76.7292        C
    ## 683        0      3   male 20.00000     0     0   9.2250        S
    ## 684        0      3   male 14.00000     5     2  46.9000        S
    ## 685        0      2   male 60.00000     1     1  39.0000        S
    ## 686        0      2   male 25.00000     1     2  41.5792        C
    ## 687        0      3   male 14.00000     4     1  39.6875        S
    ## 688        0      3   male 19.00000     0     0  10.1708        S
    ## 689        0      3   male 18.00000     0     0   7.7958        S
    ## 690        1      1 female 15.00000     0     1 211.3375        S
    ## 691        1      1   male 31.00000     1     0  57.0000        S
    ## 692        1      3 female  4.00000     0     1  13.4167        C
    ## 693        1      3   male 29.69912     0     0  56.4958        S
    ## 694        0      3   male 25.00000     0     0   7.2250        C
    ## 695        0      1   male 60.00000     0     0  26.5500        S
    ## 696        0      2   male 52.00000     0     0  13.5000        S
    ## 697        0      3   male 44.00000     0     0   8.0500        S
    ## 698        1      3 female 29.69912     0     0   7.7333        Q
    ## 699        0      1   male 49.00000     1     1 110.8833        C
    ## 700        0      3   male 42.00000     0     0   7.6500        S
    ## 701        1      1 female 18.00000     1     0 227.5250        C
    ## 702        1      1   male 35.00000     0     0  26.2875        S
    ## 703        0      3 female 18.00000     0     1  14.4542        C
    ## 704        0      3   male 25.00000     0     0   7.7417        Q
    ## 705        0      3   male 26.00000     1     0   7.8542        S
    ## 706        0      2   male 39.00000     0     0  26.0000        S
    ## 707        1      2 female 45.00000     0     0  13.5000        S
    ## 708        1      1   male 42.00000     0     0  26.2875        S
    ## 709        1      1 female 22.00000     0     0 151.5500        S
    ## 710        1      3   male 29.69912     1     1  15.2458        C
    ## 711        1      1 female 24.00000     0     0  49.5042        C
    ## 712        0      1   male 29.69912     0     0  26.5500        S
    ## 713        1      1   male 48.00000     1     0  52.0000        S
    ## 714        0      3   male 29.00000     0     0   9.4833        S
    ## 715        0      2   male 52.00000     0     0  13.0000        S
    ## 716        0      3   male 19.00000     0     0   7.6500        S
    ## 717        1      1 female 38.00000     0     0 227.5250        C
    ## 718        1      2 female 27.00000     0     0  10.5000        S
    ## 719        0      3   male 29.69912     0     0  15.5000        Q
    ## 720        0      3   male 33.00000     0     0   7.7750        S
    ## 721        1      2 female  6.00000     0     1  33.0000        S
    ## 722        0      3   male 17.00000     1     0   7.0542        S
    ## 723        0      2   male 34.00000     0     0  13.0000        S
    ## 724        0      2   male 50.00000     0     0  13.0000        S
    ## 725        1      1   male 27.00000     1     0  53.1000        S
    ## 726        0      3   male 20.00000     0     0   8.6625        S
    ## 727        1      2 female 30.00000     3     0  21.0000        S
    ## 728        1      3 female 29.69912     0     0   7.7375        Q
    ## 729        0      2   male 25.00000     1     0  26.0000        S
    ## 730        0      3 female 25.00000     1     0   7.9250        S
    ## 731        1      1 female 29.00000     0     0 211.3375        S
    ## 732        0      3   male 11.00000     0     0  18.7875        C
    ## 733        0      2   male 29.69912     0     0   0.0000        S
    ## 734        0      2   male 23.00000     0     0  13.0000        S
    ## 735        0      2   male 23.00000     0     0  13.0000        S
    ## 736        0      3   male 28.50000     0     0  16.1000        S
    ## 737        0      3 female 48.00000     1     3  34.3750        S
    ## 738        1      1   male 35.00000     0     0 512.3292        C
    ## 739        0      3   male 29.69912     0     0   7.8958        S
    ## 740        0      3   male 29.69912     0     0   7.8958        S
    ## 741        1      1   male 29.69912     0     0  30.0000        S
    ## 742        0      1   male 36.00000     1     0  78.8500        S
    ## 743        1      1 female 21.00000     2     2 262.3750        C
    ## 744        0      3   male 24.00000     1     0  16.1000        S
    ## 745        1      3   male 31.00000     0     0   7.9250        S
    ## 746        0      1   male 70.00000     1     1  71.0000        S
    ## 747        0      3   male 16.00000     1     1  20.2500        S
    ## 748        1      2 female 30.00000     0     0  13.0000        S
    ## 749        0      1   male 19.00000     1     0  53.1000        S
    ## 750        0      3   male 31.00000     0     0   7.7500        Q
    ## 751        1      2 female  4.00000     1     1  23.0000        S
    ## 752        1      3   male  6.00000     0     1  12.4750        S
    ## 753        0      3   male 33.00000     0     0   9.5000        S
    ## 754        0      3   male 23.00000     0     0   7.8958        S
    ## 755        1      2 female 48.00000     1     2  65.0000        S
    ## 756        1      2   male  0.67000     1     1  14.5000        S
    ## 757        0      3   male 28.00000     0     0   7.7958        S
    ## 758        0      2   male 18.00000     0     0  11.5000        S
    ## 759        0      3   male 34.00000     0     0   8.0500        S
    ## 760        1      1 female 33.00000     0     0  86.5000        S
    ## 761        0      3   male 29.69912     0     0  14.5000        S
    ## 762        0      3   male 41.00000     0     0   7.1250        S
    ## 763        1      3   male 20.00000     0     0   7.2292        C
    ## 764        1      1 female 36.00000     1     2 120.0000        S
    ## 765        0      3   male 16.00000     0     0   7.7750        S
    ## 766        1      1 female 51.00000     1     0  77.9583        S
    ## 767        0      1   male 29.69912     0     0  39.6000        C
    ## 768        0      3 female 30.50000     0     0   7.7500        Q
    ## 769        0      3   male 29.69912     1     0  24.1500        Q
    ## 770        0      3   male 32.00000     0     0   8.3625        S
    ## 771        0      3   male 24.00000     0     0   9.5000        S
    ## 772        0      3   male 48.00000     0     0   7.8542        S
    ## 773        0      2 female 57.00000     0     0  10.5000        S
    ## 774        0      3   male 29.69912     0     0   7.2250        C
    ## 775        1      2 female 54.00000     1     3  23.0000        S
    ## 776        0      3   male 18.00000     0     0   7.7500        S
    ## 777        0      3   male 29.69912     0     0   7.7500        Q
    ## 778        1      3 female  5.00000     0     0  12.4750        S
    ## 779        0      3   male 29.69912     0     0   7.7375        Q
    ## 780        1      1 female 43.00000     0     1 211.3375        S
    ## 781        1      3 female 13.00000     0     0   7.2292        C
    ## 782        1      1 female 17.00000     1     0  57.0000        S
    ## 783        0      1   male 29.00000     0     0  30.0000        S
    ## 784        0      3   male 29.69912     1     2  23.4500        S
    ## 785        0      3   male 25.00000     0     0   7.0500        S
    ## 786        0      3   male 25.00000     0     0   7.2500        S
    ## 787        1      3 female 18.00000     0     0   7.4958        S
    ## 788        0      3   male  8.00000     4     1  29.1250        Q
    ## 789        1      3   male  1.00000     1     2  20.5750        S
    ## 790        0      1   male 46.00000     0     0  79.2000        C
    ## 791        0      3   male 29.69912     0     0   7.7500        Q
    ## 792        0      2   male 16.00000     0     0  26.0000        S
    ## 793        0      3 female 29.69912     8     2  69.5500        S
    ## 794        0      1   male 29.69912     0     0  30.6958        C
    ## 795        0      3   male 25.00000     0     0   7.8958        S
    ## 796        0      2   male 39.00000     0     0  13.0000        S
    ## 797        1      1 female 49.00000     0     0  25.9292        S
    ## 798        1      3 female 31.00000     0     0   8.6833        S
    ## 799        0      3   male 30.00000     0     0   7.2292        C
    ## 800        0      3 female 30.00000     1     1  24.1500        S
    ## 801        0      2   male 34.00000     0     0  13.0000        S
    ## 802        1      2 female 31.00000     1     1  26.2500        S
    ## 803        1      1   male 11.00000     1     2 120.0000        S
    ## 804        1      3   male  0.42000     0     1   8.5167        C
    ## 805        1      3   male 27.00000     0     0   6.9750        S
    ## 806        0      3   male 31.00000     0     0   7.7750        S
    ## 807        0      1   male 39.00000     0     0   0.0000        S
    ## 808        0      3 female 18.00000     0     0   7.7750        S
    ## 809        0      2   male 39.00000     0     0  13.0000        S
    ## 810        1      1 female 33.00000     1     0  53.1000        S
    ## 811        0      3   male 26.00000     0     0   7.8875        S
    ## 812        0      3   male 39.00000     0     0  24.1500        S
    ## 813        0      2   male 35.00000     0     0  10.5000        S
    ## 814        0      3 female  6.00000     4     2  31.2750        S
    ## 815        0      3   male 30.50000     0     0   8.0500        S
    ## 816        0      1   male 29.69912     0     0   0.0000        S
    ## 817        0      3 female 23.00000     0     0   7.9250        S
    ## 818        0      2   male 31.00000     1     1  37.0042        C
    ## 819        0      3   male 43.00000     0     0   6.4500        S
    ## 820        0      3   male 10.00000     3     2  27.9000        S
    ## 821        1      1 female 52.00000     1     1  93.5000        S
    ## 822        1      3   male 27.00000     0     0   8.6625        S
    ## 823        0      1   male 38.00000     0     0   0.0000        S
    ## 824        1      3 female 27.00000     0     1  12.4750        S
    ## 825        0      3   male  2.00000     4     1  39.6875        S
    ## 826        0      3   male 29.69912     0     0   6.9500        Q
    ## 827        0      3   male 29.69912     0     0  56.4958        S
    ## 828        1      2   male  1.00000     0     2  37.0042        C
    ## 829        1      3   male 29.69912     0     0   7.7500        Q
    ## 830        1      1 female 62.00000     0     0  80.0000         
    ## 831        1      3 female 15.00000     1     0  14.4542        C
    ## 832        1      2   male  0.83000     1     1  18.7500        S
    ## 833        0      3   male 29.69912     0     0   7.2292        C
    ## 834        0      3   male 23.00000     0     0   7.8542        S
    ## 835        0      3   male 18.00000     0     0   8.3000        S
    ## 836        1      1 female 39.00000     1     1  83.1583        C
    ## 837        0      3   male 21.00000     0     0   8.6625        S
    ## 838        0      3   male 29.69912     0     0   8.0500        S
    ## 839        1      3   male 32.00000     0     0  56.4958        S
    ## 840        1      1   male 29.69912     0     0  29.7000        C
    ## 841        0      3   male 20.00000     0     0   7.9250        S
    ## 842        0      2   male 16.00000     0     0  10.5000        S
    ## 843        1      1 female 30.00000     0     0  31.0000        C
    ## 844        0      3   male 34.50000     0     0   6.4375        C
    ## 845        0      3   male 17.00000     0     0   8.6625        S
    ## 846        0      3   male 42.00000     0     0   7.5500        S
    ## 847        0      3   male 29.69912     8     2  69.5500        S
    ## 848        0      3   male 35.00000     0     0   7.8958        C
    ## 849        0      2   male 28.00000     0     1  33.0000        S
    ## 850        1      1 female 29.69912     1     0  89.1042        C
    ## 851        0      3   male  4.00000     4     2  31.2750        S
    ## 852        0      3   male 74.00000     0     0   7.7750        S
    ## 853        0      3 female  9.00000     1     1  15.2458        C
    ## 854        1      1 female 16.00000     0     1  39.4000        S
    ## 855        0      2 female 44.00000     1     0  26.0000        S
    ## 856        1      3 female 18.00000     0     1   9.3500        S
    ## 857        1      1 female 45.00000     1     1 164.8667        S
    ## 858        1      1   male 51.00000     0     0  26.5500        S
    ## 859        1      3 female 24.00000     0     3  19.2583        C
    ## 860        0      3   male 29.69912     0     0   7.2292        C
    ## 861        0      3   male 41.00000     2     0  14.1083        S
    ## 862        0      2   male 21.00000     1     0  11.5000        S
    ## 863        1      1 female 48.00000     0     0  25.9292        S
    ## 864        0      3 female 29.69912     8     2  69.5500        S
    ## 865        0      2   male 24.00000     0     0  13.0000        S
    ## 866        1      2 female 42.00000     0     0  13.0000        S
    ## 867        1      2 female 27.00000     1     0  13.8583        C
    ## 868        0      1   male 31.00000     0     0  50.4958        S
    ## 869        0      3   male 29.69912     0     0   9.5000        S
    ## 870        1      3   male  4.00000     1     1  11.1333        S
    ## 871        0      3   male 26.00000     0     0   7.8958        S
    ## 872        1      1 female 47.00000     1     1  52.5542        S
    ## 873        0      1   male 33.00000     0     0   5.0000        S
    ## 874        0      3   male 47.00000     0     0   9.0000        S
    ## 875        1      2 female 28.00000     1     0  24.0000        C
    ## 876        1      3 female 15.00000     0     0   7.2250        C
    ## 877        0      3   male 20.00000     0     0   9.8458        S
    ## 878        0      3   male 19.00000     0     0   7.8958        S
    ## 879        0      3   male 29.69912     0     0   7.8958        S
    ## 880        1      1 female 56.00000     0     1  83.1583        C
    ## 881        1      2 female 25.00000     0     1  26.0000        S
    ## 882        0      3   male 33.00000     0     0   7.8958        S
    ## 883        0      3 female 22.00000     0     0  10.5167        S
    ## 884        0      2   male 28.00000     0     0  10.5000        S
    ## 885        0      3   male 25.00000     0     0   7.0500        S
    ## 886        0      3 female 39.00000     0     5  29.1250        Q
    ## 887        0      2   male 27.00000     0     0  13.0000        S
    ## 888        1      1 female 19.00000     0     0  30.0000        S
    ## 889        0      3 female 29.69912     1     2  23.4500        S
    ## 890        1      1   male 26.00000     0     0  30.0000        C
    ## 891        0      3   male 32.00000     0     0   7.7500        Q
    ##            sfare
    ## 1   -0.502163137
    ## 2    0.786403618
    ## 3   -0.488579852
    ## 4    0.420494070
    ## 5   -0.486064428
    ## 6   -0.477848050
    ## 7    0.395591381
    ## 8   -0.223957338
    ## 9   -0.424017995
    ## 10  -0.042931390
    ## 11  -0.311997147
    ## 12  -0.113781804
    ## 13  -0.486064428
    ## 14  -0.018698810
    ## 15  -0.490004587
    ## 16  -0.326083517
    ## 17  -0.061964088
    ## 18  -0.386453672
    ## 19  -0.285836747
    ## 20  -0.502666221
    ## 21  -0.124849666
    ## 22  -0.386453672
    ## 23  -0.486482995
    ## 24   0.066322492
    ## 25  -0.223957338
    ## 26  -0.016434929
    ## 27  -0.502666221
    ## 28   4.644392600
    ## 29  -0.489501503
    ## 30  -0.489167454
    ## 31  -0.090221345
    ## 32   2.300436803
    ## 33  -0.492101444
    ## 34  -0.436762135
    ## 35   1.005496973
    ## 36   0.398358346
    ## 37  -0.502581703
    ## 38  -0.486064428
    ## 39  -0.285836747
    ## 40  -0.421836620
    ## 41  -0.457388605
    ## 42  -0.225466592
    ## 43  -0.489167454
    ## 44   0.188656575
    ## 45  -0.489501503
    ## 46  -0.486064428
    ## 47  -0.336145210
    ## 48  -0.492101444
    ## 49  -0.211798788
    ## 50  -0.289861424
    ## 51   0.150589167
    ## 52  -0.491095275
    ## 53   0.895993561
    ## 54  -0.124849666
    ## 55   0.599173631
    ## 56   0.066322492
    ## 57  -0.436762135
    ## 58  -0.502581703
    ## 59  -0.089633742
    ## 60   0.295729082
    ## 61  -0.502581703
    ## 62   0.961813129
    ## 63   1.031741892
    ## 64  -0.086615234
    ## 65  -0.090221345
    ## 66  -0.341260574
    ## 67  -0.436762135
    ## 68  -0.483885066
    ## 69  -0.488579852
    ## 70  -0.473738855
    ## 71  -0.436762135
    ## 72   0.295729082
    ## 73   0.831011126
    ## 74  -0.357190246
    ## 75   0.488829061
    ## 76  -0.494113782
    ## 77  -0.489167454
    ## 78  -0.486064428
    ## 79  -0.064479511
    ## 80  -0.397018449
    ## 81  -0.466947213
    ## 82  -0.456885520
    ## 83  -0.491346817
    ## 84   0.299753759
    ## 85  -0.436762135
    ## 86  -0.329102025
    ## 87   0.043683684
    ## 88  -0.486064428
    ## 89   4.644392600
    ## 90  -0.486064428
    ## 91  -0.486064428
    ## 92  -0.490004587
    ## 93   0.582990404
    ## 94  -0.234019030
    ## 95  -0.502163137
    ## 96  -0.486064428
    ## 97   0.049302133
    ## 98   0.626925791
    ## 99  -0.185219821
    ## 100 -0.124849666
    ## 101 -0.489167454
    ## 102 -0.489167454
    ## 103  0.907228447
    ## 104 -0.473905879
    ## 105 -0.488579852
    ## 106 -0.489167454
    ## 107 -0.494113782
    ## 108 -0.491598359
    ## 109 -0.489167454
    ## 110 -0.162077929
    ## 111  0.398358346
    ## 112 -0.357190246
    ## 113 -0.486064428
    ## 114 -0.450345420
    ## 115 -0.357107740
    ## 116 -0.488579852
    ## 117 -0.492101444
    ## 118 -0.225466592
    ## 119  4.332898697
    ## 120 -0.018698810
    ## 121  0.831011126
    ## 122 -0.486064428
    ## 123 -0.042931390
    ## 124 -0.386453672
    ## 125  0.907228447
    ## 126 -0.421836620
    ## 127 -0.492101444
    ## 128 -0.504342499
    ## 129 -0.198132998
    ## 130 -0.507697067
    ## 131 -0.489167454
    ## 132 -0.506187814
    ## 133 -0.356268595
    ## 134 -0.124849666
    ## 135 -0.386453672
    ## 136 -0.345285251
    ## 137 -0.119148711
    ## 138  0.420494070
    ## 139 -0.462586475
    ## 140  0.945714421
    ## 141 -0.341260574
    ## 142 -0.492101444
    ## 143 -0.329102025
    ## 144 -0.512224829
    ## 145 -0.416638750
    ## 146  0.091476724
    ## 147 -0.491179793
    ## 148  0.043683684
    ## 149 -0.124849666
    ## 150 -0.386453672
    ## 151 -0.396012280
    ## 152  0.692159768
    ## 153 -0.486064428
    ## 154 -0.356268595
    ## 155 -0.500905425
    ## 156  0.587099600
    ## 157 -0.492437505
    ## 158 -0.486064428
    ## 159 -0.473738855
    ## 160  0.751523754
    ## 161 -0.324071178
    ## 162 -0.331114363
    ## 163 -0.491598359
    ## 164 -0.473738855
    ## 165  0.150589167
    ## 166 -0.235025199
    ## 167  0.458728501
    ## 168 -0.086615234
    ## 169 -0.126358920
    ## 170  0.488829061
    ## 171  0.026075722
    ## 172 -0.061964088
    ## 173 -0.424017995
    ## 174 -0.488579852
    ## 175 -0.030354274
    ## 176 -0.490004587
    ## 177 -0.135581467
    ## 178 -0.070264984
    ## 179 -0.386453672
    ## 180 -0.648057678
    ## 181  0.751523754
    ## 182 -0.345200733
    ## 183 -0.016434929
    ## 184  0.136754340
    ## 185 -0.204840122
    ## 186  0.358111576
    ## 187 -0.336145210
    ## 188 -0.113781804
    ## 189 -0.336145210
    ## 190 -0.489167454
    ## 191 -0.386453672
    ## 192 -0.386453672
    ## 193 -0.490004587
    ## 194 -0.124849666
    ## 195 -0.090221345
    ## 196  2.300436803
    ## 197 -0.492101444
    ## 198 -0.478936725
    ## 199 -0.492101444
    ## 200 -0.386453672
    ## 201 -0.456885520
    ## 202  0.751523754
    ## 203 -0.517340194
    ## 204 -0.502666221
    ## 205 -0.486064428
    ## 206 -0.437516762
    ## 207 -0.329102025
    ## 208 -0.269989581
    ## 209 -0.492101444
    ## 210 -0.024232741
    ## 211 -0.506187814
    ## 212 -0.225466592
    ## 213 -0.502163137
    ## 214 -0.386453672
    ## 215 -0.492101444
    ## 216  1.631418767
    ## 217 -0.488579852
    ## 218 -0.104726281
    ## 219  0.887189580
    ## 220 -0.436762135
    ## 221 -0.486064428
    ## 222 -0.386453672
    ## 223 -0.486064428
    ## 224 -0.489167454
    ## 225  1.163046980
    ## 226 -0.459904028
    ## 227 -0.436762135
    ## 228 -0.502163137
    ## 229 -0.386453672
    ## 230 -0.135581467
    ## 231  1.031741892
    ## 232 -0.491598359
    ## 233 -0.376391980
    ## 234 -0.016434929
    ## 235 -0.436762135
    ## 236 -0.496126121
    ## 237 -0.124849666
    ## 238 -0.119818820
    ## 239 -0.436762135
    ## 240 -0.401043126
    ## 241 -0.357190246
    ## 242 -0.336145210
    ## 243 -0.436762135
    ## 244 -0.504678560
    ## 245 -0.502666221
    ## 246  1.163046980
    ## 247 -0.491598359
    ## 248 -0.356268595
    ## 249  0.409510726
    ## 250 -0.124849666
    ## 251 -0.502163137
    ## 252 -0.437516762
    ## 253 -0.113781804
    ## 254 -0.324071178
    ## 255 -0.241313757
    ## 256 -0.341260574
    ## 257  0.945714421
    ## 258  1.092615132
    ## 259  9.661740105
    ## 260 -0.124849666
    ## 261 -0.492101444
    ## 262 -0.016434929
    ## 263  0.954769944
    ## 264 -0.648057678
    ## 265 -0.492101444
    ## 266 -0.436762135
    ## 267  0.150589167
    ## 268 -0.491598359
    ## 269  2.440127306
    ## 270  2.081343448
    ## 271 -0.024232741
    ## 272 -0.648057678
    ## 273 -0.255651669
    ## 274 -0.050393141
    ## 275 -0.492101444
    ## 276  0.920727213
    ## 277 -0.492101444
    ## 278 -0.648057678
    ## 279 -0.061964088
    ## 280 -0.240559130
    ## 281 -0.492101444
    ## 282 -0.490004587
    ## 283 -0.456885520
    ## 284 -0.486064428
    ## 285 -0.124849666
    ## 286 -0.473738855
    ## 287 -0.456885520
    ## 288 -0.489167454
    ## 289 -0.386453672
    ## 290 -0.492101444
    ## 291  0.938671236
    ## 292  1.184764137
    ## 293 -0.388969095
    ## 294 -0.469965720
    ## 295 -0.489167454
    ## 296 -0.090221345
    ## 297 -0.502581703
    ## 298  2.401641332
    ## 299 -0.034294433
    ## 300  4.332898697
    ## 301 -0.492101444
    ## 302 -0.180188975
    ## 303 -0.648057678
    ## 304 -0.399533873
    ## 305 -0.486064428
    ## 306  2.401641332
    ## 307  1.583289667
    ## 308  1.543378958
    ## 309 -0.165096436
    ## 310  0.497550536
    ## 311  1.025368816
    ## 312  4.631815484
    ## 313 -0.124849666
    ## 314 -0.489167454
    ## 315 -0.119818820
    ## 316 -0.490004587
    ## 317 -0.124849666
    ## 318 -0.366330287
    ## 319  2.669618414
    ## 320  2.058537616
    ## 321 -0.502163137
    ## 322 -0.489167454
    ## 323 -0.399533873
    ## 324 -0.064479511
    ## 325  0.751523754
    ## 326  2.081343448
    ## 327 -0.522538064
    ## 328 -0.386453672
    ## 329 -0.235025199
    ## 330  0.518680090
    ## 331 -0.180188975
    ## 332 -0.074541203
    ## 333  2.440127306
    ## 334 -0.285836747
    ## 335  2.041432739
    ## 336 -0.489167454
    ## 337  0.692159768
    ## 338  2.058537616
    ## 339 -0.486064428
    ## 340  0.066322492
    ## 341 -0.124849666
    ## 342  4.644392600
    ## 343 -0.386453672
    ## 344 -0.386453672
    ## 345 -0.386453672
    ## 346 -0.386453672
    ## 347 -0.386453672
    ## 348 -0.324071178
    ## 349 -0.328095856
    ## 350 -0.473738855
    ## 351 -0.462419451
    ## 352  0.056260800
    ## 353 -0.502581703
    ## 354 -0.289861424
    ## 355 -0.502666221
    ## 356 -0.456885520
    ## 357  0.458728501
    ## 358 -0.386453672
    ## 359 -0.489501503
    ## 360 -0.489501503
    ## 361 -0.086615234
    ## 362 -0.090221345
    ## 363 -0.357190246
    ## 364 -0.506187814
    ## 365 -0.336145210
    ## 366 -0.502163137
    ## 367  0.866227049
    ## 368 -0.502581703
    ## 369 -0.492101444
    ## 370  0.746492908
    ## 371  0.467617001
    ## 372 -0.517340194
    ## 373 -0.486064428
    ## 374  2.081343448
    ## 375 -0.223957338
    ## 376  1.005496973
    ## 377 -0.502163137
    ## 378  3.608038268
    ## 379 -0.567312596
    ## 380 -0.491598359
    ## 381  3.930515514
    ## 382 -0.331281387
    ## 383 -0.488579852
    ## 384  0.398358346
    ## 385 -0.489167454
    ## 386  0.831011126
    ## 387  0.295729082
    ## 388 -0.386453672
    ## 389 -0.492520010
    ## 390 -0.406577057
    ## 391  1.766748532
    ## 392 -0.491179793
    ## 393 -0.488579852
    ## 394  1.631418767
    ## 395 -0.311997147
    ## 396 -0.491179793
    ## 397 -0.490004587
    ## 398 -0.124849666
    ## 399 -0.436762135
    ## 400 -0.393496857
    ## 401 -0.488579852
    ## 402 -0.486064428
    ## 403 -0.450345420
    ## 404 -0.329102025
    ## 405 -0.473738855
    ## 406 -0.225466592
    ## 407 -0.492101444
    ## 408 -0.270744208
    ## 409 -0.491598359
    ## 410 -0.135581467
    ## 411 -0.489167454
    ## 412 -0.510045466
    ## 413  1.163046980
    ## 414 -0.648057678
    ## 415 -0.488579852
    ## 416 -0.486064428
    ## 417  0.005952337
    ## 418 -0.386453672
    ## 419 -0.386453672
    ## 420 -0.162077929
    ## 421 -0.489167454
    ## 422 -0.492437505
    ## 423 -0.489586021
    ## 424 -0.358280933
    ## 425 -0.241313757
    ## 426 -0.502163137
    ## 427 -0.124849666
    ## 428 -0.124849666
    ## 429 -0.492101444
    ## 430 -0.486064428
    ## 431 -0.113781804
    ## 432 -0.324071178
    ## 433 -0.124849666
    ## 434 -0.504678560
    ## 435  0.476839548
    ## 436  1.766748532
    ## 437  0.043683684
    ## 438 -0.270744208
    ## 439  4.644392600
    ## 440 -0.436762135
    ## 441 -0.119818820
    ## 442 -0.456885520
    ## 443 -0.491598359
    ## 444 -0.386453672
    ## 445 -0.484806717
    ## 446  0.999208415
    ## 447 -0.255651669
    ## 448 -0.113781804
    ## 449 -0.260515491
    ## 450 -0.034294433
    ## 451 -0.089633742
    ## 452 -0.246260085
    ## 453 -0.089633742
    ## 454  1.145020451
    ## 455 -0.486064428
    ## 456 -0.489167454
    ## 457 -0.113781804
    ## 458  0.395591381
    ## 459 -0.436762135
    ## 460 -0.492101444
    ## 461 -0.113781804
    ## 462 -0.486064428
    ## 463  0.126692647
    ## 464 -0.386453672
    ## 465 -0.486064428
    ## 466 -0.506187814
    ## 467 -0.648057678
    ## 468 -0.113781804
    ## 469 -0.492604529
    ## 470 -0.260515491
    ## 471 -0.502163137
    ## 472 -0.473738855
    ## 473 -0.089633742
    ## 474 -0.370521988
    ## 475 -0.450093878
    ## 476  0.398358346
    ## 477 -0.225466592
    ## 478 -0.506272332
    ## 479 -0.496713724
    ## 480 -0.400791584
    ## 481  0.295729082
    ## 482 -0.648057678
    ## 483 -0.486064428
    ## 484 -0.455124724
    ## 485  1.184764137
    ## 486 -0.135581467
    ## 487  1.163046980
    ## 488 -0.050393141
    ## 489 -0.486064428
    ## 490 -0.328095856
    ## 491 -0.246260085
    ## 492 -0.502163137
    ## 493 -0.034294433
    ## 494  0.348134402
    ## 495 -0.486064428
    ## 496 -0.357107740
    ## 497  0.926933265
    ## 498 -0.344194564
    ## 499  2.401641332
    ## 500 -0.491179793
    ## 501 -0.473738855
    ## 502 -0.492101444
    ## 503 -0.494532349
    ## 504 -0.455124724
    ## 505  1.092615132
    ## 506  1.543378958
    ## 507 -0.124849666
    ## 508 -0.113781804
    ## 509 -0.194778429
    ## 510  0.488829061
    ## 511 -0.492101444
    ## 512 -0.486064428
    ## 513 -0.119064193
    ## 514  0.547271396
    ## 515 -0.497216808
    ## 516  0.036555981
    ## 517 -0.436762135
    ## 518 -0.162077929
    ## 519 -0.124849666
    ## 520 -0.489167454
    ## 521  1.233478827
    ## 522 -0.489167454
    ## 523 -0.502666221
    ## 524  0.518680090
    ## 525 -0.502581703
    ## 526 -0.492101444
    ## 527 -0.436762135
    ## 528  3.814890568
    ## 529 -0.488579852
    ## 530 -0.416638750
    ## 531 -0.124849666
    ## 532 -0.502581703
    ## 533 -0.502581703
    ## 534 -0.198132998
    ## 535 -0.473738855
    ## 536 -0.119818820
    ## 537 -0.113781804
    ## 538  1.493573580
    ## 539 -0.356268595
    ## 540  0.348049883
    ## 541  0.780702663
    ## 542 -0.018698810
    ## 543 -0.018698810
    ## 544 -0.124849666
    ## 545  1.493573580
    ## 546 -0.124849666
    ## 547 -0.124849666
    ## 548 -0.369097253
    ## 549 -0.235025199
    ## 550  0.091476724
    ## 551  1.583289667
    ## 552 -0.124849666
    ## 553 -0.490507672
    ## 554 -0.502666221
    ## 555 -0.491598359
    ## 556 -0.113781804
    ## 557  0.148828371
    ## 558  3.930515514
    ## 559  0.954769944
    ## 560 -0.297910778
    ## 561 -0.492101444
    ## 562 -0.489167454
    ## 563 -0.376391980
    ## 564 -0.486064428
    ## 565 -0.486064428
    ## 566 -0.162077929
    ## 567 -0.489167454
    ## 568 -0.223957338
    ## 569 -0.502581703
    ## 570 -0.490004587
    ## 571 -0.436762135
    ## 572  0.387878087
    ## 573 -0.117051854
    ## 574 -0.492101444
    ## 575 -0.486064428
    ## 576 -0.356268595
    ## 577 -0.386453672
    ## 578  0.476839548
    ## 579 -0.357107740
    ## 580 -0.488579852
    ## 581 -0.044356126
    ## 582  1.583289667
    ## 583 -0.124849666
    ## 584  0.159393148
    ## 585 -0.472732686
    ## 586  0.954769944
    ## 587 -0.346206902
    ## 588  0.945714421
    ## 589 -0.486064428
    ## 590 -0.486064428
    ## 591 -0.504678560
    ## 592  0.926933265
    ## 593 -0.502163137
    ## 594 -0.492101444
    ## 595 -0.124849666
    ## 596 -0.162077929
    ## 597  0.016014029
    ## 598 -0.648057678
    ## 599 -0.502666221
    ## 600  0.497550536
    ## 601 -0.104726281
    ## 602 -0.489167454
    ## 603  0.205173849
    ## 604 -0.486064428
    ## 605 -0.113781804
    ## 606 -0.335139040
    ## 607 -0.489167454
    ## 608 -0.034294433
    ## 609  0.188656575
    ## 610  2.440127306
    ## 611 -0.018698810
    ## 612 -0.506187814
    ## 613 -0.336145210
    ## 614 -0.492101444
    ## 615 -0.486064428
    ## 616  0.659962352
    ## 617 -0.358280933
    ## 618 -0.324071178
    ## 619  0.136754340
    ## 620 -0.436762135
    ## 621 -0.357190246
    ## 622  0.409510726
    ## 623 -0.331281387
    ## 624 -0.490004587
    ## 625 -0.324071178
    ## 626  0.002346226
    ## 627 -0.399533873
    ## 628  0.920727213
    ## 629 -0.489167454
    ## 630 -0.492437505
    ## 631 -0.044356126
    ## 632 -0.506103295
    ## 633 -0.034294433
    ## 634 -0.648057678
    ## 635 -0.086615234
    ## 636 -0.386453672
    ## 637 -0.488579852
    ## 638 -0.119818820
    ## 639  0.150589167
    ## 640 -0.324071178
    ## 641 -0.490004587
    ## 642  0.746492908
    ## 643 -0.086615234
    ## 644  0.488829061
    ## 645 -0.260515491
    ## 646  0.895993561
    ## 647 -0.489167454
    ## 648  0.066322492
    ## 649 -0.496126121
    ## 650 -0.496126121
    ## 651 -0.489167454
    ## 652 -0.185219821
    ## 653 -0.478351135
    ## 654 -0.490507672
    ## 655 -0.512224829
    ## 656  0.831011126
    ## 657 -0.489167454
    ## 658 -0.336145210
    ## 659 -0.386453672
    ## 660  1.631418767
    ## 661  2.041432739
    ## 662 -0.502666221
    ## 663 -0.133150562
    ## 664 -0.497216808
    ## 665 -0.488579852
    ## 666  0.831011126
    ## 667 -0.386453672
    ## 668 -0.491598359
    ## 669 -0.486064428
    ## 670  0.398358346
    ## 671  0.136754340
    ## 672  0.398358346
    ## 673 -0.436762135
    ## 674 -0.386453672
    ## 675 -0.648057678
    ## 676 -0.491598359
    ## 677 -0.486064428
    ## 678 -0.450009359
    ## 679  0.295729082
    ## 680  9.661740105
    ## 681 -0.484303632
    ## 682  0.895993561
    ## 683 -0.462419451
    ## 684  0.295729082
    ## 685  0.136754340
    ## 686  0.188656575
    ## 687  0.150589167
    ## 688 -0.443386753
    ## 689 -0.491179793
    ## 690  3.604768218
    ## 691  0.498975272
    ## 692 -0.378068258
    ## 693  0.488829061
    ## 694 -0.502666221
    ## 695 -0.113781804
    ## 696 -0.376391980
    ## 697 -0.486064428
    ## 698 -0.492437505
    ## 699  1.583289667
    ## 700 -0.494113782
    ## 701  3.930515514
    ## 702 -0.119064193
    ## 703 -0.357190246
    ## 704 -0.492268468
    ## 705 -0.490004587
    ## 706 -0.124849666
    ## 707 -0.376391980
    ## 708 -0.119064193
    ## 709  2.401641332
    ## 710 -0.341260574
    ## 711  0.348134402
    ## 712 -0.113781804
    ## 713  0.398358346
    ## 714 -0.457221581
    ## 715 -0.386453672
    ## 716 -0.494113782
    ## 717  3.930515514
    ## 718 -0.436762135
    ## 719 -0.336145210
    ## 720 -0.491598359
    ## 721  0.016014029
    ## 722 -0.506103295
    ## 723 -0.386453672
    ## 724 -0.386453672
    ## 725  0.420494070
    ## 726 -0.473738855
    ## 727 -0.225466592
    ## 728 -0.492352986
    ## 729 -0.124849666
    ## 730 -0.488579852
    ## 731  3.604768218
    ## 732 -0.269989581
    ## 733 -0.648057678
    ## 734 -0.386453672
    ## 735 -0.386453672
    ## 736 -0.324071178
    ## 737  0.043683684
    ## 738  9.661740105
    ## 739 -0.489167454
    ## 740 -0.489167454
    ## 741 -0.044356126
    ## 742  0.938671236
    ## 743  4.631815484
    ## 744 -0.324071178
    ## 745 -0.488579852
    ## 746  0.780702663
    ## 747 -0.240559130
    ## 748 -0.386453672
    ## 749  0.420494070
    ## 750 -0.492101444
    ## 751 -0.185219821
    ## 752 -0.397018449
    ## 753 -0.456885520
    ## 754 -0.489167454
    ## 755  0.659962352
    ## 756 -0.356268595
    ## 757 -0.491179793
    ## 758 -0.416638750
    ## 759 -0.486064428
    ## 760  1.092615132
    ## 761 -0.356268595
    ## 762 -0.504678560
    ## 763 -0.502581703
    ## 764  1.766748532
    ## 765 -0.491598359
    ## 766  0.920727213
    ## 767  0.148828371
    ## 768 -0.492101444
    ## 769 -0.162077929
    ## 770 -0.479775871
    ## 771 -0.456885520
    ## 772 -0.490004587
    ## 773 -0.436762135
    ## 774 -0.502666221
    ## 775 -0.185219821
    ## 776 -0.492101444
    ## 777 -0.492101444
    ## 778 -0.397018449
    ## 779 -0.492352986
    ## 780  3.604768218
    ## 781 -0.502581703
    ## 782  0.498975272
    ## 783 -0.044356126
    ## 784 -0.176164298
    ## 785 -0.506187814
    ## 786 -0.502163137
    ## 787 -0.497216808
    ## 788 -0.061964088
    ## 789 -0.234019030
    ## 790  0.945714421
    ## 791 -0.492101444
    ## 792 -0.124849666
    ## 793  0.751523754
    ## 794 -0.030354274
    ## 795 -0.489167454
    ## 796 -0.386453672
    ## 797 -0.126274402
    ## 798 -0.473320289
    ## 799 -0.502581703
    ## 800 -0.162077929
    ## 801 -0.386453672
    ## 802 -0.119818820
    ## 803  1.766748532
    ## 804 -0.476672845
    ## 805 -0.507697067
    ## 806 -0.491598359
    ## 807 -0.648057678
    ## 808 -0.491598359
    ## 809 -0.386453672
    ## 810  0.420494070
    ## 811 -0.489334479
    ## 812 -0.162077929
    ## 813 -0.436762135
    ## 814 -0.018698810
    ## 815 -0.486064428
    ## 816 -0.648057678
    ## 817 -0.488579852
    ## 818  0.096592088
    ## 819 -0.518261845
    ## 820 -0.086615234
    ## 821  1.233478827
    ## 822 -0.473738855
    ## 823 -0.648057678
    ## 824 -0.397018449
    ## 825  0.150589167
    ## 826 -0.508200152
    ## 827  0.488829061
    ## 828  0.096592088
    ## 829 -0.492101444
    ## 830  0.961813129
    ## 831 -0.357190246
    ## 832 -0.270744208
    ## 833 -0.502581703
    ## 834 -0.490004587
    ## 835 -0.481033582
    ## 836  1.025368816
    ## 837 -0.473738855
    ## 838 -0.486064428
    ## 839  0.488829061
    ## 840 -0.050393141
    ## 841 -0.488579852
    ## 842 -0.436762135
    ## 843 -0.024232741
    ## 844 -0.518513387
    ## 845 -0.473738855
    ## 846 -0.496126121
    ## 847  0.751523754
    ## 848 -0.489167454
    ## 849  0.016014029
    ## 850  1.145020451
    ## 851 -0.018698810
    ## 852 -0.491598359
    ## 853 -0.341260574
    ## 854  0.144803694
    ## 855 -0.124849666
    ## 856 -0.459904028
    ## 857  2.669618414
    ## 858 -0.113781804
    ## 859 -0.260515491
    ## 860 -0.502581703
    ## 861 -0.364150925
    ## 862 -0.416638750
    ## 863 -0.126274402
    ## 864  0.751523754
    ## 865 -0.386453672
    ## 866 -0.386453672
    ## 867 -0.369181771
    ## 868  0.368088750
    ## 869 -0.456885520
    ## 870 -0.424017995
    ## 871 -0.489167454
    ## 872  0.409510726
    ## 873 -0.547440753
    ## 874 -0.466947213
    ## 875 -0.165096436
    ## 876 -0.502666221
    ## 877 -0.449926854
    ## 878 -0.489167454
    ## 879 -0.489167454
    ## 880  1.025368816
    ## 881 -0.124849666
    ## 882 -0.489167454
    ## 883 -0.436426074
    ## 884 -0.436762135
    ## 885 -0.506187814
    ## 886 -0.061964088
    ## 887 -0.386453672
    ## 888 -0.044356126
    ## 889 -0.176164298
    ## 890 -0.044356126
    ## 891 -0.492101444

Question 21
-----------

``` r
cfare <- ifelse(titanic$Fare < mean(titanic$Fare), c("cheap"), c("expensive"))
cbind(titanic, cfare)
```

    ##     Survived Pclass    Sex      Age SibSp Parch     Fare Embarked
    ## 1          0      3   male 22.00000     1     0   7.2500        S
    ## 2          1      1 female 38.00000     1     0  71.2833        C
    ## 3          1      3 female 26.00000     0     0   7.9250        S
    ## 4          1      1 female 35.00000     1     0  53.1000        S
    ## 5          0      3   male 35.00000     0     0   8.0500        S
    ## 6          0      3   male 29.69912     0     0   8.4583        Q
    ## 7          0      1   male 54.00000     0     0  51.8625        S
    ## 8          0      3   male  2.00000     3     1  21.0750        S
    ## 9          1      3 female 27.00000     0     2  11.1333        S
    ## 10         1      2 female 14.00000     1     0  30.0708        C
    ## 11         1      3 female  4.00000     1     1  16.7000        S
    ## 12         1      1 female 58.00000     0     0  26.5500        S
    ## 13         0      3   male 20.00000     0     0   8.0500        S
    ## 14         0      3   male 39.00000     1     5  31.2750        S
    ## 15         0      3 female 14.00000     0     0   7.8542        S
    ## 16         1      2 female 55.00000     0     0  16.0000        S
    ## 17         0      3   male  2.00000     4     1  29.1250        Q
    ## 18         1      2   male 29.69912     0     0  13.0000        S
    ## 19         0      3 female 31.00000     1     0  18.0000        S
    ## 20         1      3 female 29.69912     0     0   7.2250        C
    ## 21         0      2   male 35.00000     0     0  26.0000        S
    ## 22         1      2   male 34.00000     0     0  13.0000        S
    ## 23         1      3 female 15.00000     0     0   8.0292        Q
    ## 24         1      1   male 28.00000     0     0  35.5000        S
    ## 25         0      3 female  8.00000     3     1  21.0750        S
    ## 26         1      3 female 38.00000     1     5  31.3875        S
    ## 27         0      3   male 29.69912     0     0   7.2250        C
    ## 28         0      1   male 19.00000     3     2 263.0000        S
    ## 29         1      3 female 29.69912     0     0   7.8792        Q
    ## 30         0      3   male 29.69912     0     0   7.8958        S
    ## 31         0      1   male 40.00000     0     0  27.7208        C
    ## 32         1      1 female 29.69912     1     0 146.5208        C
    ## 33         1      3 female 29.69912     0     0   7.7500        Q
    ## 34         0      2   male 66.00000     0     0  10.5000        S
    ## 35         0      1   male 28.00000     1     0  82.1708        C
    ## 36         0      1   male 42.00000     1     0  52.0000        S
    ## 37         1      3   male 29.69912     0     0   7.2292        C
    ## 38         0      3   male 21.00000     0     0   8.0500        S
    ## 39         0      3 female 18.00000     2     0  18.0000        S
    ## 40         1      3 female 14.00000     1     0  11.2417        C
    ## 41         0      3 female 40.00000     1     0   9.4750        S
    ## 42         0      2 female 27.00000     1     0  21.0000        S
    ## 43         0      3   male 29.69912     0     0   7.8958        C
    ## 44         1      2 female  3.00000     1     2  41.5792        C
    ## 45         1      3 female 19.00000     0     0   7.8792        Q
    ## 46         0      3   male 29.69912     0     0   8.0500        S
    ## 47         0      3   male 29.69912     1     0  15.5000        Q
    ## 48         1      3 female 29.69912     0     0   7.7500        Q
    ## 49         0      3   male 29.69912     2     0  21.6792        C
    ## 50         0      3 female 18.00000     1     0  17.8000        S
    ## 51         0      3   male  7.00000     4     1  39.6875        S
    ## 52         0      3   male 21.00000     0     0   7.8000        S
    ## 53         1      1 female 49.00000     1     0  76.7292        C
    ## 54         1      2 female 29.00000     1     0  26.0000        S
    ## 55         0      1   male 65.00000     0     1  61.9792        C
    ## 56         1      1   male 29.69912     0     0  35.5000        S
    ## 57         1      2 female 21.00000     0     0  10.5000        S
    ## 58         0      3   male 28.50000     0     0   7.2292        C
    ## 59         1      2 female  5.00000     1     2  27.7500        S
    ## 60         0      3   male 11.00000     5     2  46.9000        S
    ## 61         0      3   male 22.00000     0     0   7.2292        C
    ## 62         1      1 female 38.00000     0     0  80.0000         
    ## 63         0      1   male 45.00000     1     0  83.4750        S
    ## 64         0      3   male  4.00000     3     2  27.9000        S
    ## 65         0      1   male 29.69912     0     0  27.7208        C
    ## 66         1      3   male 29.69912     1     1  15.2458        C
    ## 67         1      2 female 29.00000     0     0  10.5000        S
    ## 68         0      3   male 19.00000     0     0   8.1583        S
    ## 69         1      3 female 17.00000     4     2   7.9250        S
    ## 70         0      3   male 26.00000     2     0   8.6625        S
    ## 71         0      2   male 32.00000     0     0  10.5000        S
    ## 72         0      3 female 16.00000     5     2  46.9000        S
    ## 73         0      2   male 21.00000     0     0  73.5000        S
    ## 74         0      3   male 26.00000     1     0  14.4542        C
    ## 75         1      3   male 32.00000     0     0  56.4958        S
    ## 76         0      3   male 25.00000     0     0   7.6500        S
    ## 77         0      3   male 29.69912     0     0   7.8958        S
    ## 78         0      3   male 29.69912     0     0   8.0500        S
    ## 79         1      2   male  0.83000     0     2  29.0000        S
    ## 80         1      3 female 30.00000     0     0  12.4750        S
    ## 81         0      3   male 22.00000     0     0   9.0000        S
    ## 82         1      3   male 29.00000     0     0   9.5000        S
    ## 83         1      3 female 29.69912     0     0   7.7875        Q
    ## 84         0      1   male 28.00000     0     0  47.1000        S
    ## 85         1      2 female 17.00000     0     0  10.5000        S
    ## 86         1      3 female 33.00000     3     0  15.8500        S
    ## 87         0      3   male 16.00000     1     3  34.3750        S
    ## 88         0      3   male 29.69912     0     0   8.0500        S
    ## 89         1      1 female 23.00000     3     2 263.0000        S
    ## 90         0      3   male 24.00000     0     0   8.0500        S
    ## 91         0      3   male 29.00000     0     0   8.0500        S
    ## 92         0      3   male 20.00000     0     0   7.8542        S
    ## 93         0      1   male 46.00000     1     0  61.1750        S
    ## 94         0      3   male 26.00000     1     2  20.5750        S
    ## 95         0      3   male 59.00000     0     0   7.2500        S
    ## 96         0      3   male 29.69912     0     0   8.0500        S
    ## 97         0      1   male 71.00000     0     0  34.6542        C
    ## 98         1      1   male 23.00000     0     1  63.3583        C
    ## 99         1      2 female 34.00000     0     1  23.0000        S
    ## 100        0      2   male 34.00000     1     0  26.0000        S
    ## 101        0      3 female 28.00000     0     0   7.8958        S
    ## 102        0      3   male 29.69912     0     0   7.8958        S
    ## 103        0      1   male 21.00000     0     1  77.2875        S
    ## 104        0      3   male 33.00000     0     0   8.6542        S
    ## 105        0      3   male 37.00000     2     0   7.9250        S
    ## 106        0      3   male 28.00000     0     0   7.8958        S
    ## 107        1      3 female 21.00000     0     0   7.6500        S
    ## 108        1      3   male 29.69912     0     0   7.7750        S
    ## 109        0      3   male 38.00000     0     0   7.8958        S
    ## 110        1      3 female 29.69912     1     0  24.1500        Q
    ## 111        0      1   male 47.00000     0     0  52.0000        S
    ## 112        0      3 female 14.50000     1     0  14.4542        C
    ## 113        0      3   male 22.00000     0     0   8.0500        S
    ## 114        0      3 female 20.00000     1     0   9.8250        S
    ## 115        0      3 female 17.00000     0     0  14.4583        C
    ## 116        0      3   male 21.00000     0     0   7.9250        S
    ## 117        0      3   male 70.50000     0     0   7.7500        Q
    ## 118        0      2   male 29.00000     1     0  21.0000        S
    ## 119        0      1   male 24.00000     0     1 247.5208        C
    ## 120        0      3 female  2.00000     4     2  31.2750        S
    ## 121        0      2   male 21.00000     2     0  73.5000        S
    ## 122        0      3   male 29.69912     0     0   8.0500        S
    ## 123        0      2   male 32.50000     1     0  30.0708        C
    ## 124        1      2 female 32.50000     0     0  13.0000        S
    ## 125        0      1   male 54.00000     0     1  77.2875        S
    ## 126        1      3   male 12.00000     1     0  11.2417        C
    ## 127        0      3   male 29.69912     0     0   7.7500        Q
    ## 128        1      3   male 24.00000     0     0   7.1417        S
    ## 129        1      3 female 29.69912     1     1  22.3583        C
    ## 130        0      3   male 45.00000     0     0   6.9750        S
    ## 131        0      3   male 33.00000     0     0   7.8958        C
    ## 132        0      3   male 20.00000     0     0   7.0500        S
    ## 133        0      3 female 47.00000     1     0  14.5000        S
    ## 134        1      2 female 29.00000     1     0  26.0000        S
    ## 135        0      2   male 25.00000     0     0  13.0000        S
    ## 136        0      2   male 23.00000     0     0  15.0458        C
    ## 137        1      1 female 19.00000     0     2  26.2833        S
    ## 138        0      1   male 37.00000     1     0  53.1000        S
    ## 139        0      3   male 16.00000     0     0   9.2167        S
    ## 140        0      1   male 24.00000     0     0  79.2000        C
    ## 141        0      3 female 29.69912     0     2  15.2458        C
    ## 142        1      3 female 22.00000     0     0   7.7500        S
    ## 143        1      3 female 24.00000     1     0  15.8500        S
    ## 144        0      3   male 19.00000     0     0   6.7500        Q
    ## 145        0      2   male 18.00000     0     0  11.5000        S
    ## 146        0      2   male 19.00000     1     1  36.7500        S
    ## 147        1      3   male 27.00000     0     0   7.7958        S
    ## 148        0      3 female  9.00000     2     2  34.3750        S
    ## 149        0      2   male 36.50000     0     2  26.0000        S
    ## 150        0      2   male 42.00000     0     0  13.0000        S
    ## 151        0      2   male 51.00000     0     0  12.5250        S
    ## 152        1      1 female 22.00000     1     0  66.6000        S
    ## 153        0      3   male 55.50000     0     0   8.0500        S
    ## 154        0      3   male 40.50000     0     2  14.5000        S
    ## 155        0      3   male 29.69912     0     0   7.3125        S
    ## 156        0      1   male 51.00000     0     1  61.3792        C
    ## 157        1      3 female 16.00000     0     0   7.7333        Q
    ## 158        0      3   male 30.00000     0     0   8.0500        S
    ## 159        0      3   male 29.69912     0     0   8.6625        S
    ## 160        0      3   male 29.69912     8     2  69.5500        S
    ## 161        0      3   male 44.00000     0     1  16.1000        S
    ## 162        1      2 female 40.00000     0     0  15.7500        S
    ## 163        0      3   male 26.00000     0     0   7.7750        S
    ## 164        0      3   male 17.00000     0     0   8.6625        S
    ## 165        0      3   male  1.00000     4     1  39.6875        S
    ## 166        1      3   male  9.00000     0     2  20.5250        S
    ## 167        1      1 female 29.69912     0     1  55.0000        S
    ## 168        0      3 female 45.00000     1     4  27.9000        S
    ## 169        0      1   male 29.69912     0     0  25.9250        S
    ## 170        0      3   male 28.00000     0     0  56.4958        S
    ## 171        0      1   male 61.00000     0     0  33.5000        S
    ## 172        0      3   male  4.00000     4     1  29.1250        Q
    ## 173        1      3 female  1.00000     1     1  11.1333        S
    ## 174        0      3   male 21.00000     0     0   7.9250        S
    ## 175        0      1   male 56.00000     0     0  30.6958        C
    ## 176        0      3   male 18.00000     1     1   7.8542        S
    ## 177        0      3   male 29.69912     3     1  25.4667        S
    ## 178        0      1 female 50.00000     0     0  28.7125        C
    ## 179        0      2   male 30.00000     0     0  13.0000        S
    ## 180        0      3   male 36.00000     0     0   0.0000        S
    ## 181        0      3 female 29.69912     8     2  69.5500        S
    ## 182        0      2   male 29.69912     0     0  15.0500        C
    ## 183        0      3   male  9.00000     4     2  31.3875        S
    ## 184        1      2   male  1.00000     2     1  39.0000        S
    ## 185        1      3 female  4.00000     0     2  22.0250        S
    ## 186        0      1   male 29.69912     0     0  50.0000        S
    ## 187        1      3 female 29.69912     1     0  15.5000        Q
    ## 188        1      1   male 45.00000     0     0  26.5500        S
    ## 189        0      3   male 40.00000     1     1  15.5000        Q
    ## 190        0      3   male 36.00000     0     0   7.8958        S
    ## 191        1      2 female 32.00000     0     0  13.0000        S
    ## 192        0      2   male 19.00000     0     0  13.0000        S
    ## 193        1      3 female 19.00000     1     0   7.8542        S
    ## 194        1      2   male  3.00000     1     1  26.0000        S
    ## 195        1      1 female 44.00000     0     0  27.7208        C
    ## 196        1      1 female 58.00000     0     0 146.5208        C
    ## 197        0      3   male 29.69912     0     0   7.7500        Q
    ## 198        0      3   male 42.00000     0     1   8.4042        S
    ## 199        1      3 female 29.69912     0     0   7.7500        Q
    ## 200        0      2 female 24.00000     0     0  13.0000        S
    ## 201        0      3   male 28.00000     0     0   9.5000        S
    ## 202        0      3   male 29.69912     8     2  69.5500        S
    ## 203        0      3   male 34.00000     0     0   6.4958        S
    ## 204        0      3   male 45.50000     0     0   7.2250        C
    ## 205        1      3   male 18.00000     0     0   8.0500        S
    ## 206        0      3 female  2.00000     0     1  10.4625        S
    ## 207        0      3   male 32.00000     1     0  15.8500        S
    ## 208        1      3   male 26.00000     0     0  18.7875        C
    ## 209        1      3 female 16.00000     0     0   7.7500        Q
    ## 210        1      1   male 40.00000     0     0  31.0000        C
    ## 211        0      3   male 24.00000     0     0   7.0500        S
    ## 212        1      2 female 35.00000     0     0  21.0000        S
    ## 213        0      3   male 22.00000     0     0   7.2500        S
    ## 214        0      2   male 30.00000     0     0  13.0000        S
    ## 215        0      3   male 29.69912     1     0   7.7500        Q
    ## 216        1      1 female 31.00000     1     0 113.2750        C
    ## 217        1      3 female 27.00000     0     0   7.9250        S
    ## 218        0      2   male 42.00000     1     0  27.0000        S
    ## 219        1      1 female 32.00000     0     0  76.2917        C
    ## 220        0      2   male 30.00000     0     0  10.5000        S
    ## 221        1      3   male 16.00000     0     0   8.0500        S
    ## 222        0      2   male 27.00000     0     0  13.0000        S
    ## 223        0      3   male 51.00000     0     0   8.0500        S
    ## 224        0      3   male 29.69912     0     0   7.8958        S
    ## 225        1      1   male 38.00000     1     0  90.0000        S
    ## 226        0      3   male 22.00000     0     0   9.3500        S
    ## 227        1      2   male 19.00000     0     0  10.5000        S
    ## 228        0      3   male 20.50000     0     0   7.2500        S
    ## 229        0      2   male 18.00000     0     0  13.0000        S
    ## 230        0      3 female 29.69912     3     1  25.4667        S
    ## 231        1      1 female 35.00000     1     0  83.4750        S
    ## 232        0      3   male 29.00000     0     0   7.7750        S
    ## 233        0      2   male 59.00000     0     0  13.5000        S
    ## 234        1      3 female  5.00000     4     2  31.3875        S
    ## 235        0      2   male 24.00000     0     0  10.5000        S
    ## 236        0      3 female 29.69912     0     0   7.5500        S
    ## 237        0      2   male 44.00000     1     0  26.0000        S
    ## 238        1      2 female  8.00000     0     2  26.2500        S
    ## 239        0      2   male 19.00000     0     0  10.5000        S
    ## 240        0      2   male 33.00000     0     0  12.2750        S
    ## 241        0      3 female 29.69912     1     0  14.4542        C
    ## 242        1      3 female 29.69912     1     0  15.5000        Q
    ## 243        0      2   male 29.00000     0     0  10.5000        S
    ## 244        0      3   male 22.00000     0     0   7.1250        S
    ## 245        0      3   male 30.00000     0     0   7.2250        C
    ## 246        0      1   male 44.00000     2     0  90.0000        Q
    ## 247        0      3 female 25.00000     0     0   7.7750        S
    ## 248        1      2 female 24.00000     0     2  14.5000        S
    ## 249        1      1   male 37.00000     1     1  52.5542        S
    ## 250        0      2   male 54.00000     1     0  26.0000        S
    ## 251        0      3   male 29.69912     0     0   7.2500        S
    ## 252        0      3 female 29.00000     1     1  10.4625        S
    ## 253        0      1   male 62.00000     0     0  26.5500        S
    ## 254        0      3   male 30.00000     1     0  16.1000        S
    ## 255        0      3 female 41.00000     0     2  20.2125        S
    ## 256        1      3 female 29.00000     0     2  15.2458        C
    ## 257        1      1 female 29.69912     0     0  79.2000        C
    ## 258        1      1 female 30.00000     0     0  86.5000        S
    ## 259        1      1 female 35.00000     0     0 512.3292        C
    ## 260        1      2 female 50.00000     0     1  26.0000        S
    ## 261        0      3   male 29.69912     0     0   7.7500        Q
    ## 262        1      3   male  3.00000     4     2  31.3875        S
    ## 263        0      1   male 52.00000     1     1  79.6500        S
    ## 264        0      1   male 40.00000     0     0   0.0000        S
    ## 265        0      3 female 29.69912     0     0   7.7500        Q
    ## 266        0      2   male 36.00000     0     0  10.5000        S
    ## 267        0      3   male 16.00000     4     1  39.6875        S
    ## 268        1      3   male 25.00000     1     0   7.7750        S
    ## 269        1      1 female 58.00000     0     1 153.4625        S
    ## 270        1      1 female 35.00000     0     0 135.6333        S
    ## 271        0      1   male 29.69912     0     0  31.0000        S
    ## 272        1      3   male 25.00000     0     0   0.0000        S
    ## 273        1      2 female 41.00000     0     1  19.5000        S
    ## 274        0      1   male 37.00000     0     1  29.7000        C
    ## 275        1      3 female 29.69912     0     0   7.7500        Q
    ## 276        1      1 female 63.00000     1     0  77.9583        S
    ## 277        0      3 female 45.00000     0     0   7.7500        S
    ## 278        0      2   male 29.69912     0     0   0.0000        S
    ## 279        0      3   male  7.00000     4     1  29.1250        Q
    ## 280        1      3 female 35.00000     1     1  20.2500        S
    ## 281        0      3   male 65.00000     0     0   7.7500        Q
    ## 282        0      3   male 28.00000     0     0   7.8542        S
    ## 283        0      3   male 16.00000     0     0   9.5000        S
    ## 284        1      3   male 19.00000     0     0   8.0500        S
    ## 285        0      1   male 29.69912     0     0  26.0000        S
    ## 286        0      3   male 33.00000     0     0   8.6625        C
    ## 287        1      3   male 30.00000     0     0   9.5000        S
    ## 288        0      3   male 22.00000     0     0   7.8958        S
    ## 289        1      2   male 42.00000     0     0  13.0000        S
    ## 290        1      3 female 22.00000     0     0   7.7500        Q
    ## 291        1      1 female 26.00000     0     0  78.8500        S
    ## 292        1      1 female 19.00000     1     0  91.0792        C
    ## 293        0      2   male 36.00000     0     0  12.8750        C
    ## 294        0      3 female 24.00000     0     0   8.8500        S
    ## 295        0      3   male 24.00000     0     0   7.8958        S
    ## 296        0      1   male 29.69912     0     0  27.7208        C
    ## 297        0      3   male 23.50000     0     0   7.2292        C
    ## 298        0      1 female  2.00000     1     2 151.5500        S
    ## 299        1      1   male 29.69912     0     0  30.5000        S
    ## 300        1      1 female 50.00000     0     1 247.5208        C
    ## 301        1      3 female 29.69912     0     0   7.7500        Q
    ## 302        1      3   male 29.69912     2     0  23.2500        Q
    ## 303        0      3   male 19.00000     0     0   0.0000        S
    ## 304        1      2 female 29.69912     0     0  12.3500        Q
    ## 305        0      3   male 29.69912     0     0   8.0500        S
    ## 306        1      1   male  0.92000     1     2 151.5500        S
    ## 307        1      1 female 29.69912     0     0 110.8833        C
    ## 308        1      1 female 17.00000     1     0 108.9000        C
    ## 309        0      2   male 30.00000     1     0  24.0000        C
    ## 310        1      1 female 30.00000     0     0  56.9292        C
    ## 311        1      1 female 24.00000     0     0  83.1583        C
    ## 312        1      1 female 18.00000     2     2 262.3750        C
    ## 313        0      2 female 26.00000     1     1  26.0000        S
    ## 314        0      3   male 28.00000     0     0   7.8958        S
    ## 315        0      2   male 43.00000     1     1  26.2500        S
    ## 316        1      3 female 26.00000     0     0   7.8542        S
    ## 317        1      2 female 24.00000     1     0  26.0000        S
    ## 318        0      2   male 54.00000     0     0  14.0000        S
    ## 319        1      1 female 31.00000     0     2 164.8667        S
    ## 320        1      1 female 40.00000     1     1 134.5000        C
    ## 321        0      3   male 22.00000     0     0   7.2500        S
    ## 322        0      3   male 27.00000     0     0   7.8958        S
    ## 323        1      2 female 30.00000     0     0  12.3500        Q
    ## 324        1      2 female 22.00000     1     1  29.0000        S
    ## 325        0      3   male 29.69912     8     2  69.5500        S
    ## 326        1      1 female 36.00000     0     0 135.6333        C
    ## 327        0      3   male 61.00000     0     0   6.2375        S
    ## 328        1      2 female 36.00000     0     0  13.0000        S
    ## 329        1      3 female 31.00000     1     1  20.5250        S
    ## 330        1      1 female 16.00000     0     1  57.9792        C
    ## 331        1      3 female 29.69912     2     0  23.2500        Q
    ## 332        0      1   male 45.50000     0     0  28.5000        S
    ## 333        0      1   male 38.00000     0     1 153.4625        S
    ## 334        0      3   male 16.00000     2     0  18.0000        S
    ## 335        1      1 female 29.69912     1     0 133.6500        S
    ## 336        0      3   male 29.69912     0     0   7.8958        S
    ## 337        0      1   male 29.00000     1     0  66.6000        S
    ## 338        1      1 female 41.00000     0     0 134.5000        C
    ## 339        1      3   male 45.00000     0     0   8.0500        S
    ## 340        0      1   male 45.00000     0     0  35.5000        S
    ## 341        1      2   male  2.00000     1     1  26.0000        S
    ## 342        1      1 female 24.00000     3     2 263.0000        S
    ## 343        0      2   male 28.00000     0     0  13.0000        S
    ## 344        0      2   male 25.00000     0     0  13.0000        S
    ## 345        0      2   male 36.00000     0     0  13.0000        S
    ## 346        1      2 female 24.00000     0     0  13.0000        S
    ## 347        1      2 female 40.00000     0     0  13.0000        S
    ## 348        1      3 female 29.69912     1     0  16.1000        S
    ## 349        1      3   male  3.00000     1     1  15.9000        S
    ## 350        0      3   male 42.00000     0     0   8.6625        S
    ## 351        0      3   male 23.00000     0     0   9.2250        S
    ## 352        0      1   male 29.69912     0     0  35.0000        S
    ## 353        0      3   male 15.00000     1     1   7.2292        C
    ## 354        0      3   male 25.00000     1     0  17.8000        S
    ## 355        0      3   male 29.69912     0     0   7.2250        C
    ## 356        0      3   male 28.00000     0     0   9.5000        S
    ## 357        1      1 female 22.00000     0     1  55.0000        S
    ## 358        0      2 female 38.00000     0     0  13.0000        S
    ## 359        1      3 female 29.69912     0     0   7.8792        Q
    ## 360        1      3 female 29.69912     0     0   7.8792        Q
    ## 361        0      3   male 40.00000     1     4  27.9000        S
    ## 362        0      2   male 29.00000     1     0  27.7208        C
    ## 363        0      3 female 45.00000     0     1  14.4542        C
    ## 364        0      3   male 35.00000     0     0   7.0500        S
    ## 365        0      3   male 29.69912     1     0  15.5000        Q
    ## 366        0      3   male 30.00000     0     0   7.2500        S
    ## 367        1      1 female 60.00000     1     0  75.2500        C
    ## 368        1      3 female 29.69912     0     0   7.2292        C
    ## 369        1      3 female 29.69912     0     0   7.7500        Q
    ## 370        1      1 female 24.00000     0     0  69.3000        C
    ## 371        1      1   male 25.00000     1     0  55.4417        C
    ## 372        0      3   male 18.00000     1     0   6.4958        S
    ## 373        0      3   male 19.00000     0     0   8.0500        S
    ## 374        0      1   male 22.00000     0     0 135.6333        C
    ## 375        0      3 female  3.00000     3     1  21.0750        S
    ## 376        1      1 female 29.69912     1     0  82.1708        C
    ## 377        1      3 female 22.00000     0     0   7.2500        S
    ## 378        0      1   male 27.00000     0     2 211.5000        C
    ## 379        0      3   male 20.00000     0     0   4.0125        C
    ## 380        0      3   male 19.00000     0     0   7.7750        S
    ## 381        1      1 female 42.00000     0     0 227.5250        C
    ## 382        1      3 female  1.00000     0     2  15.7417        C
    ## 383        0      3   male 32.00000     0     0   7.9250        S
    ## 384        1      1 female 35.00000     1     0  52.0000        S
    ## 385        0      3   male 29.69912     0     0   7.8958        S
    ## 386        0      2   male 18.00000     0     0  73.5000        S
    ## 387        0      3   male  1.00000     5     2  46.9000        S
    ## 388        1      2 female 36.00000     0     0  13.0000        S
    ## 389        0      3   male 29.69912     0     0   7.7292        Q
    ## 390        1      2 female 17.00000     0     0  12.0000        C
    ## 391        1      1   male 36.00000     1     2 120.0000        S
    ## 392        1      3   male 21.00000     0     0   7.7958        S
    ## 393        0      3   male 28.00000     2     0   7.9250        S
    ## 394        1      1 female 23.00000     1     0 113.2750        C
    ## 395        1      3 female 24.00000     0     2  16.7000        S
    ## 396        0      3   male 22.00000     0     0   7.7958        S
    ## 397        0      3 female 31.00000     0     0   7.8542        S
    ## 398        0      2   male 46.00000     0     0  26.0000        S
    ## 399        0      2   male 23.00000     0     0  10.5000        S
    ## 400        1      2 female 28.00000     0     0  12.6500        S
    ## 401        1      3   male 39.00000     0     0   7.9250        S
    ## 402        0      3   male 26.00000     0     0   8.0500        S
    ## 403        0      3 female 21.00000     1     0   9.8250        S
    ## 404        0      3   male 28.00000     1     0  15.8500        S
    ## 405        0      3 female 20.00000     0     0   8.6625        S
    ## 406        0      2   male 34.00000     1     0  21.0000        S
    ## 407        0      3   male 51.00000     0     0   7.7500        S
    ## 408        1      2   male  3.00000     1     1  18.7500        S
    ## 409        0      3   male 21.00000     0     0   7.7750        S
    ## 410        0      3 female 29.69912     3     1  25.4667        S
    ## 411        0      3   male 29.69912     0     0   7.8958        S
    ## 412        0      3   male 29.69912     0     0   6.8583        Q
    ## 413        1      1 female 33.00000     1     0  90.0000        Q
    ## 414        0      2   male 29.69912     0     0   0.0000        S
    ## 415        1      3   male 44.00000     0     0   7.9250        S
    ## 416        0      3 female 29.69912     0     0   8.0500        S
    ## 417        1      2 female 34.00000     1     1  32.5000        S
    ## 418        1      2 female 18.00000     0     2  13.0000        S
    ## 419        0      2   male 30.00000     0     0  13.0000        S
    ## 420        0      3 female 10.00000     0     2  24.1500        S
    ## 421        0      3   male 29.69912     0     0   7.8958        C
    ## 422        0      3   male 21.00000     0     0   7.7333        Q
    ## 423        0      3   male 29.00000     0     0   7.8750        S
    ## 424        0      3 female 28.00000     1     1  14.4000        S
    ## 425        0      3   male 18.00000     1     1  20.2125        S
    ## 426        0      3   male 29.69912     0     0   7.2500        S
    ## 427        1      2 female 28.00000     1     0  26.0000        S
    ## 428        1      2 female 19.00000     0     0  26.0000        S
    ## 429        0      3   male 29.69912     0     0   7.7500        Q
    ## 430        1      3   male 32.00000     0     0   8.0500        S
    ## 431        1      1   male 28.00000     0     0  26.5500        S
    ## 432        1      3 female 29.69912     1     0  16.1000        S
    ## 433        1      2 female 42.00000     1     0  26.0000        S
    ## 434        0      3   male 17.00000     0     0   7.1250        S
    ## 435        0      1   male 50.00000     1     0  55.9000        S
    ## 436        1      1 female 14.00000     1     2 120.0000        S
    ## 437        0      3 female 21.00000     2     2  34.3750        S
    ## 438        1      2 female 24.00000     2     3  18.7500        S
    ## 439        0      1   male 64.00000     1     4 263.0000        S
    ## 440        0      2   male 31.00000     0     0  10.5000        S
    ## 441        1      2 female 45.00000     1     1  26.2500        S
    ## 442        0      3   male 20.00000     0     0   9.5000        S
    ## 443        0      3   male 25.00000     1     0   7.7750        S
    ## 444        1      2 female 28.00000     0     0  13.0000        S
    ## 445        1      3   male 29.69912     0     0   8.1125        S
    ## 446        1      1   male  4.00000     0     2  81.8583        S
    ## 447        1      2 female 13.00000     0     1  19.5000        S
    ## 448        1      1   male 34.00000     0     0  26.5500        S
    ## 449        1      3 female  5.00000     2     1  19.2583        C
    ## 450        1      1   male 52.00000     0     0  30.5000        S
    ## 451        0      2   male 36.00000     1     2  27.7500        S
    ## 452        0      3   male 29.69912     1     0  19.9667        S
    ## 453        0      1   male 30.00000     0     0  27.7500        C
    ## 454        1      1   male 49.00000     1     0  89.1042        C
    ## 455        0      3   male 29.69912     0     0   8.0500        S
    ## 456        1      3   male 29.00000     0     0   7.8958        C
    ## 457        0      1   male 65.00000     0     0  26.5500        S
    ## 458        1      1 female 29.69912     1     0  51.8625        S
    ## 459        1      2 female 50.00000     0     0  10.5000        S
    ## 460        0      3   male 29.69912     0     0   7.7500        Q
    ## 461        1      1   male 48.00000     0     0  26.5500        S
    ## 462        0      3   male 34.00000     0     0   8.0500        S
    ## 463        0      1   male 47.00000     0     0  38.5000        S
    ## 464        0      2   male 48.00000     0     0  13.0000        S
    ## 465        0      3   male 29.69912     0     0   8.0500        S
    ## 466        0      3   male 38.00000     0     0   7.0500        S
    ## 467        0      2   male 29.69912     0     0   0.0000        S
    ## 468        0      1   male 56.00000     0     0  26.5500        S
    ## 469        0      3   male 29.69912     0     0   7.7250        Q
    ## 470        1      3 female  0.75000     2     1  19.2583        C
    ## 471        0      3   male 29.69912     0     0   7.2500        S
    ## 472        0      3   male 38.00000     0     0   8.6625        S
    ## 473        1      2 female 33.00000     1     2  27.7500        S
    ## 474        1      2 female 23.00000     0     0  13.7917        C
    ## 475        0      3 female 22.00000     0     0   9.8375        S
    ## 476        0      1   male 29.69912     0     0  52.0000        S
    ## 477        0      2   male 34.00000     1     0  21.0000        S
    ## 478        0      3   male 29.00000     1     0   7.0458        S
    ## 479        0      3   male 22.00000     0     0   7.5208        S
    ## 480        1      3 female  2.00000     0     1  12.2875        S
    ## 481        0      3   male  9.00000     5     2  46.9000        S
    ## 482        0      2   male 29.69912     0     0   0.0000        S
    ## 483        0      3   male 50.00000     0     0   8.0500        S
    ## 484        1      3 female 63.00000     0     0   9.5875        S
    ## 485        1      1   male 25.00000     1     0  91.0792        C
    ## 486        0      3 female 29.69912     3     1  25.4667        S
    ## 487        1      1 female 35.00000     1     0  90.0000        S
    ## 488        0      1   male 58.00000     0     0  29.7000        C
    ## 489        0      3   male 30.00000     0     0   8.0500        S
    ## 490        1      3   male  9.00000     1     1  15.9000        S
    ## 491        0      3   male 29.69912     1     0  19.9667        S
    ## 492        0      3   male 21.00000     0     0   7.2500        S
    ## 493        0      1   male 55.00000     0     0  30.5000        S
    ## 494        0      1   male 71.00000     0     0  49.5042        C
    ## 495        0      3   male 21.00000     0     0   8.0500        S
    ## 496        0      3   male 29.69912     0     0  14.4583        C
    ## 497        1      1 female 54.00000     1     0  78.2667        C
    ## 498        0      3   male 29.69912     0     0  15.1000        S
    ## 499        0      1 female 25.00000     1     2 151.5500        S
    ## 500        0      3   male 24.00000     0     0   7.7958        S
    ## 501        0      3   male 17.00000     0     0   8.6625        S
    ## 502        0      3 female 21.00000     0     0   7.7500        Q
    ## 503        0      3 female 29.69912     0     0   7.6292        Q
    ## 504        0      3 female 37.00000     0     0   9.5875        S
    ## 505        1      1 female 16.00000     0     0  86.5000        S
    ## 506        0      1   male 18.00000     1     0 108.9000        C
    ## 507        1      2 female 33.00000     0     2  26.0000        S
    ## 508        1      1   male 29.69912     0     0  26.5500        S
    ## 509        0      3   male 28.00000     0     0  22.5250        S
    ## 510        1      3   male 26.00000     0     0  56.4958        S
    ## 511        1      3   male 29.00000     0     0   7.7500        Q
    ## 512        0      3   male 29.69912     0     0   8.0500        S
    ## 513        1      1   male 36.00000     0     0  26.2875        S
    ## 514        1      1 female 54.00000     1     0  59.4000        C
    ## 515        0      3   male 24.00000     0     0   7.4958        S
    ## 516        0      1   male 47.00000     0     0  34.0208        S
    ## 517        1      2 female 34.00000     0     0  10.5000        S
    ## 518        0      3   male 29.69912     0     0  24.1500        Q
    ## 519        1      2 female 36.00000     1     0  26.0000        S
    ## 520        0      3   male 32.00000     0     0   7.8958        S
    ## 521        1      1 female 30.00000     0     0  93.5000        S
    ## 522        0      3   male 22.00000     0     0   7.8958        S
    ## 523        0      3   male 29.69912     0     0   7.2250        C
    ## 524        1      1 female 44.00000     0     1  57.9792        C
    ## 525        0      3   male 29.69912     0     0   7.2292        C
    ## 526        0      3   male 40.50000     0     0   7.7500        Q
    ## 527        1      2 female 50.00000     0     0  10.5000        S
    ## 528        0      1   male 29.69912     0     0 221.7792        S
    ## 529        0      3   male 39.00000     0     0   7.9250        S
    ## 530        0      2   male 23.00000     2     1  11.5000        S
    ## 531        1      2 female  2.00000     1     1  26.0000        S
    ## 532        0      3   male 29.69912     0     0   7.2292        C
    ## 533        0      3   male 17.00000     1     1   7.2292        C
    ## 534        1      3 female 29.69912     0     2  22.3583        C
    ## 535        0      3 female 30.00000     0     0   8.6625        S
    ## 536        1      2 female  7.00000     0     2  26.2500        S
    ## 537        0      1   male 45.00000     0     0  26.5500        S
    ## 538        1      1 female 30.00000     0     0 106.4250        C
    ## 539        0      3   male 29.69912     0     0  14.5000        S
    ## 540        1      1 female 22.00000     0     2  49.5000        C
    ## 541        1      1 female 36.00000     0     2  71.0000        S
    ## 542        0      3 female  9.00000     4     2  31.2750        S
    ## 543        0      3 female 11.00000     4     2  31.2750        S
    ## 544        1      2   male 32.00000     1     0  26.0000        S
    ## 545        0      1   male 50.00000     1     0 106.4250        C
    ## 546        0      1   male 64.00000     0     0  26.0000        S
    ## 547        1      2 female 19.00000     1     0  26.0000        S
    ## 548        1      2   male 29.69912     0     0  13.8625        C
    ## 549        0      3   male 33.00000     1     1  20.5250        S
    ## 550        1      2   male  8.00000     1     1  36.7500        S
    ## 551        1      1   male 17.00000     0     2 110.8833        C
    ## 552        0      2   male 27.00000     0     0  26.0000        S
    ## 553        0      3   male 29.69912     0     0   7.8292        Q
    ## 554        1      3   male 22.00000     0     0   7.2250        C
    ## 555        1      3 female 22.00000     0     0   7.7750        S
    ## 556        0      1   male 62.00000     0     0  26.5500        S
    ## 557        1      1 female 48.00000     1     0  39.6000        C
    ## 558        0      1   male 29.69912     0     0 227.5250        C
    ## 559        1      1 female 39.00000     1     1  79.6500        S
    ## 560        1      3 female 36.00000     1     0  17.4000        S
    ## 561        0      3   male 29.69912     0     0   7.7500        Q
    ## 562        0      3   male 40.00000     0     0   7.8958        S
    ## 563        0      2   male 28.00000     0     0  13.5000        S
    ## 564        0      3   male 29.69912     0     0   8.0500        S
    ## 565        0      3 female 29.69912     0     0   8.0500        S
    ## 566        0      3   male 24.00000     2     0  24.1500        S
    ## 567        0      3   male 19.00000     0     0   7.8958        S
    ## 568        0      3 female 29.00000     0     4  21.0750        S
    ## 569        0      3   male 29.69912     0     0   7.2292        C
    ## 570        1      3   male 32.00000     0     0   7.8542        S
    ## 571        1      2   male 62.00000     0     0  10.5000        S
    ## 572        1      1 female 53.00000     2     0  51.4792        S
    ## 573        1      1   male 36.00000     0     0  26.3875        S
    ## 574        1      3 female 29.69912     0     0   7.7500        Q
    ## 575        0      3   male 16.00000     0     0   8.0500        S
    ## 576        0      3   male 19.00000     0     0  14.5000        S
    ## 577        1      2 female 34.00000     0     0  13.0000        S
    ## 578        1      1 female 39.00000     1     0  55.9000        S
    ## 579        0      3 female 29.69912     1     0  14.4583        C
    ## 580        1      3   male 32.00000     0     0   7.9250        S
    ## 581        1      2 female 25.00000     1     1  30.0000        S
    ## 582        1      1 female 39.00000     1     1 110.8833        C
    ## 583        0      2   male 54.00000     0     0  26.0000        S
    ## 584        0      1   male 36.00000     0     0  40.1250        C
    ## 585        0      3   male 29.69912     0     0   8.7125        C
    ## 586        1      1 female 18.00000     0     2  79.6500        S
    ## 587        0      2   male 47.00000     0     0  15.0000        S
    ## 588        1      1   male 60.00000     1     1  79.2000        C
    ## 589        0      3   male 22.00000     0     0   8.0500        S
    ## 590        0      3   male 29.69912     0     0   8.0500        S
    ## 591        0      3   male 35.00000     0     0   7.1250        S
    ## 592        1      1 female 52.00000     1     0  78.2667        C
    ## 593        0      3   male 47.00000     0     0   7.2500        S
    ## 594        0      3 female 29.69912     0     2   7.7500        Q
    ## 595        0      2   male 37.00000     1     0  26.0000        S
    ## 596        0      3   male 36.00000     1     1  24.1500        S
    ## 597        1      2 female 29.69912     0     0  33.0000        S
    ## 598        0      3   male 49.00000     0     0   0.0000        S
    ## 599        0      3   male 29.69912     0     0   7.2250        C
    ## 600        1      1   male 49.00000     1     0  56.9292        C
    ## 601        1      2 female 24.00000     2     1  27.0000        S
    ## 602        0      3   male 29.69912     0     0   7.8958        S
    ## 603        0      1   male 29.69912     0     0  42.4000        S
    ## 604        0      3   male 44.00000     0     0   8.0500        S
    ## 605        1      1   male 35.00000     0     0  26.5500        C
    ## 606        0      3   male 36.00000     1     0  15.5500        S
    ## 607        0      3   male 30.00000     0     0   7.8958        S
    ## 608        1      1   male 27.00000     0     0  30.5000        S
    ## 609        1      2 female 22.00000     1     2  41.5792        C
    ## 610        1      1 female 40.00000     0     0 153.4625        S
    ## 611        0      3 female 39.00000     1     5  31.2750        S
    ## 612        0      3   male 29.69912     0     0   7.0500        S
    ## 613        1      3 female 29.69912     1     0  15.5000        Q
    ## 614        0      3   male 29.69912     0     0   7.7500        Q
    ## 615        0      3   male 35.00000     0     0   8.0500        S
    ## 616        1      2 female 24.00000     1     2  65.0000        S
    ## 617        0      3   male 34.00000     1     1  14.4000        S
    ## 618        0      3 female 26.00000     1     0  16.1000        S
    ## 619        1      2 female  4.00000     2     1  39.0000        S
    ## 620        0      2   male 26.00000     0     0  10.5000        S
    ## 621        0      3   male 27.00000     1     0  14.4542        C
    ## 622        1      1   male 42.00000     1     0  52.5542        S
    ## 623        1      3   male 20.00000     1     1  15.7417        C
    ## 624        0      3   male 21.00000     0     0   7.8542        S
    ## 625        0      3   male 21.00000     0     0  16.1000        S
    ## 626        0      1   male 61.00000     0     0  32.3208        S
    ## 627        0      2   male 57.00000     0     0  12.3500        Q
    ## 628        1      1 female 21.00000     0     0  77.9583        S
    ## 629        0      3   male 26.00000     0     0   7.8958        S
    ## 630        0      3   male 29.69912     0     0   7.7333        Q
    ## 631        1      1   male 80.00000     0     0  30.0000        S
    ## 632        0      3   male 51.00000     0     0   7.0542        S
    ## 633        1      1   male 32.00000     0     0  30.5000        C
    ## 634        0      1   male 29.69912     0     0   0.0000        S
    ## 635        0      3 female  9.00000     3     2  27.9000        S
    ## 636        1      2 female 28.00000     0     0  13.0000        S
    ## 637        0      3   male 32.00000     0     0   7.9250        S
    ## 638        0      2   male 31.00000     1     1  26.2500        S
    ## 639        0      3 female 41.00000     0     5  39.6875        S
    ## 640        0      3   male 29.69912     1     0  16.1000        S
    ## 641        0      3   male 20.00000     0     0   7.8542        S
    ## 642        1      1 female 24.00000     0     0  69.3000        C
    ## 643        0      3 female  2.00000     3     2  27.9000        S
    ## 644        1      3   male 29.69912     0     0  56.4958        S
    ## 645        1      3 female  0.75000     2     1  19.2583        C
    ## 646        1      1   male 48.00000     1     0  76.7292        C
    ## 647        0      3   male 19.00000     0     0   7.8958        S
    ## 648        1      1   male 56.00000     0     0  35.5000        C
    ## 649        0      3   male 29.69912     0     0   7.5500        S
    ## 650        1      3 female 23.00000     0     0   7.5500        S
    ## 651        0      3   male 29.69912     0     0   7.8958        S
    ## 652        1      2 female 18.00000     0     1  23.0000        S
    ## 653        0      3   male 21.00000     0     0   8.4333        S
    ## 654        1      3 female 29.69912     0     0   7.8292        Q
    ## 655        0      3 female 18.00000     0     0   6.7500        Q
    ## 656        0      2   male 24.00000     2     0  73.5000        S
    ## 657        0      3   male 29.69912     0     0   7.8958        S
    ## 658        0      3 female 32.00000     1     1  15.5000        Q
    ## 659        0      2   male 23.00000     0     0  13.0000        S
    ## 660        0      1   male 58.00000     0     2 113.2750        C
    ## 661        1      1   male 50.00000     2     0 133.6500        S
    ## 662        0      3   male 40.00000     0     0   7.2250        C
    ## 663        0      1   male 47.00000     0     0  25.5875        S
    ## 664        0      3   male 36.00000     0     0   7.4958        S
    ## 665        1      3   male 20.00000     1     0   7.9250        S
    ## 666        0      2   male 32.00000     2     0  73.5000        S
    ## 667        0      2   male 25.00000     0     0  13.0000        S
    ## 668        0      3   male 29.69912     0     0   7.7750        S
    ## 669        0      3   male 43.00000     0     0   8.0500        S
    ## 670        1      1 female 29.69912     1     0  52.0000        S
    ## 671        1      2 female 40.00000     1     1  39.0000        S
    ## 672        0      1   male 31.00000     1     0  52.0000        S
    ## 673        0      2   male 70.00000     0     0  10.5000        S
    ## 674        1      2   male 31.00000     0     0  13.0000        S
    ## 675        0      2   male 29.69912     0     0   0.0000        S
    ## 676        0      3   male 18.00000     0     0   7.7750        S
    ## 677        0      3   male 24.50000     0     0   8.0500        S
    ## 678        1      3 female 18.00000     0     0   9.8417        S
    ## 679        0      3 female 43.00000     1     6  46.9000        S
    ## 680        1      1   male 36.00000     0     1 512.3292        C
    ## 681        0      3 female 29.69912     0     0   8.1375        Q
    ## 682        1      1   male 27.00000     0     0  76.7292        C
    ## 683        0      3   male 20.00000     0     0   9.2250        S
    ## 684        0      3   male 14.00000     5     2  46.9000        S
    ## 685        0      2   male 60.00000     1     1  39.0000        S
    ## 686        0      2   male 25.00000     1     2  41.5792        C
    ## 687        0      3   male 14.00000     4     1  39.6875        S
    ## 688        0      3   male 19.00000     0     0  10.1708        S
    ## 689        0      3   male 18.00000     0     0   7.7958        S
    ## 690        1      1 female 15.00000     0     1 211.3375        S
    ## 691        1      1   male 31.00000     1     0  57.0000        S
    ## 692        1      3 female  4.00000     0     1  13.4167        C
    ## 693        1      3   male 29.69912     0     0  56.4958        S
    ## 694        0      3   male 25.00000     0     0   7.2250        C
    ## 695        0      1   male 60.00000     0     0  26.5500        S
    ## 696        0      2   male 52.00000     0     0  13.5000        S
    ## 697        0      3   male 44.00000     0     0   8.0500        S
    ## 698        1      3 female 29.69912     0     0   7.7333        Q
    ## 699        0      1   male 49.00000     1     1 110.8833        C
    ## 700        0      3   male 42.00000     0     0   7.6500        S
    ## 701        1      1 female 18.00000     1     0 227.5250        C
    ## 702        1      1   male 35.00000     0     0  26.2875        S
    ## 703        0      3 female 18.00000     0     1  14.4542        C
    ## 704        0      3   male 25.00000     0     0   7.7417        Q
    ## 705        0      3   male 26.00000     1     0   7.8542        S
    ## 706        0      2   male 39.00000     0     0  26.0000        S
    ## 707        1      2 female 45.00000     0     0  13.5000        S
    ## 708        1      1   male 42.00000     0     0  26.2875        S
    ## 709        1      1 female 22.00000     0     0 151.5500        S
    ## 710        1      3   male 29.69912     1     1  15.2458        C
    ## 711        1      1 female 24.00000     0     0  49.5042        C
    ## 712        0      1   male 29.69912     0     0  26.5500        S
    ## 713        1      1   male 48.00000     1     0  52.0000        S
    ## 714        0      3   male 29.00000     0     0   9.4833        S
    ## 715        0      2   male 52.00000     0     0  13.0000        S
    ## 716        0      3   male 19.00000     0     0   7.6500        S
    ## 717        1      1 female 38.00000     0     0 227.5250        C
    ## 718        1      2 female 27.00000     0     0  10.5000        S
    ## 719        0      3   male 29.69912     0     0  15.5000        Q
    ## 720        0      3   male 33.00000     0     0   7.7750        S
    ## 721        1      2 female  6.00000     0     1  33.0000        S
    ## 722        0      3   male 17.00000     1     0   7.0542        S
    ## 723        0      2   male 34.00000     0     0  13.0000        S
    ## 724        0      2   male 50.00000     0     0  13.0000        S
    ## 725        1      1   male 27.00000     1     0  53.1000        S
    ## 726        0      3   male 20.00000     0     0   8.6625        S
    ## 727        1      2 female 30.00000     3     0  21.0000        S
    ## 728        1      3 female 29.69912     0     0   7.7375        Q
    ## 729        0      2   male 25.00000     1     0  26.0000        S
    ## 730        0      3 female 25.00000     1     0   7.9250        S
    ## 731        1      1 female 29.00000     0     0 211.3375        S
    ## 732        0      3   male 11.00000     0     0  18.7875        C
    ## 733        0      2   male 29.69912     0     0   0.0000        S
    ## 734        0      2   male 23.00000     0     0  13.0000        S
    ## 735        0      2   male 23.00000     0     0  13.0000        S
    ## 736        0      3   male 28.50000     0     0  16.1000        S
    ## 737        0      3 female 48.00000     1     3  34.3750        S
    ## 738        1      1   male 35.00000     0     0 512.3292        C
    ## 739        0      3   male 29.69912     0     0   7.8958        S
    ## 740        0      3   male 29.69912     0     0   7.8958        S
    ## 741        1      1   male 29.69912     0     0  30.0000        S
    ## 742        0      1   male 36.00000     1     0  78.8500        S
    ## 743        1      1 female 21.00000     2     2 262.3750        C
    ## 744        0      3   male 24.00000     1     0  16.1000        S
    ## 745        1      3   male 31.00000     0     0   7.9250        S
    ## 746        0      1   male 70.00000     1     1  71.0000        S
    ## 747        0      3   male 16.00000     1     1  20.2500        S
    ## 748        1      2 female 30.00000     0     0  13.0000        S
    ## 749        0      1   male 19.00000     1     0  53.1000        S
    ## 750        0      3   male 31.00000     0     0   7.7500        Q
    ## 751        1      2 female  4.00000     1     1  23.0000        S
    ## 752        1      3   male  6.00000     0     1  12.4750        S
    ## 753        0      3   male 33.00000     0     0   9.5000        S
    ## 754        0      3   male 23.00000     0     0   7.8958        S
    ## 755        1      2 female 48.00000     1     2  65.0000        S
    ## 756        1      2   male  0.67000     1     1  14.5000        S
    ## 757        0      3   male 28.00000     0     0   7.7958        S
    ## 758        0      2   male 18.00000     0     0  11.5000        S
    ## 759        0      3   male 34.00000     0     0   8.0500        S
    ## 760        1      1 female 33.00000     0     0  86.5000        S
    ## 761        0      3   male 29.69912     0     0  14.5000        S
    ## 762        0      3   male 41.00000     0     0   7.1250        S
    ## 763        1      3   male 20.00000     0     0   7.2292        C
    ## 764        1      1 female 36.00000     1     2 120.0000        S
    ## 765        0      3   male 16.00000     0     0   7.7750        S
    ## 766        1      1 female 51.00000     1     0  77.9583        S
    ## 767        0      1   male 29.69912     0     0  39.6000        C
    ## 768        0      3 female 30.50000     0     0   7.7500        Q
    ## 769        0      3   male 29.69912     1     0  24.1500        Q
    ## 770        0      3   male 32.00000     0     0   8.3625        S
    ## 771        0      3   male 24.00000     0     0   9.5000        S
    ## 772        0      3   male 48.00000     0     0   7.8542        S
    ## 773        0      2 female 57.00000     0     0  10.5000        S
    ## 774        0      3   male 29.69912     0     0   7.2250        C
    ## 775        1      2 female 54.00000     1     3  23.0000        S
    ## 776        0      3   male 18.00000     0     0   7.7500        S
    ## 777        0      3   male 29.69912     0     0   7.7500        Q
    ## 778        1      3 female  5.00000     0     0  12.4750        S
    ## 779        0      3   male 29.69912     0     0   7.7375        Q
    ## 780        1      1 female 43.00000     0     1 211.3375        S
    ## 781        1      3 female 13.00000     0     0   7.2292        C
    ## 782        1      1 female 17.00000     1     0  57.0000        S
    ## 783        0      1   male 29.00000     0     0  30.0000        S
    ## 784        0      3   male 29.69912     1     2  23.4500        S
    ## 785        0      3   male 25.00000     0     0   7.0500        S
    ## 786        0      3   male 25.00000     0     0   7.2500        S
    ## 787        1      3 female 18.00000     0     0   7.4958        S
    ## 788        0      3   male  8.00000     4     1  29.1250        Q
    ## 789        1      3   male  1.00000     1     2  20.5750        S
    ## 790        0      1   male 46.00000     0     0  79.2000        C
    ## 791        0      3   male 29.69912     0     0   7.7500        Q
    ## 792        0      2   male 16.00000     0     0  26.0000        S
    ## 793        0      3 female 29.69912     8     2  69.5500        S
    ## 794        0      1   male 29.69912     0     0  30.6958        C
    ## 795        0      3   male 25.00000     0     0   7.8958        S
    ## 796        0      2   male 39.00000     0     0  13.0000        S
    ## 797        1      1 female 49.00000     0     0  25.9292        S
    ## 798        1      3 female 31.00000     0     0   8.6833        S
    ## 799        0      3   male 30.00000     0     0   7.2292        C
    ## 800        0      3 female 30.00000     1     1  24.1500        S
    ## 801        0      2   male 34.00000     0     0  13.0000        S
    ## 802        1      2 female 31.00000     1     1  26.2500        S
    ## 803        1      1   male 11.00000     1     2 120.0000        S
    ## 804        1      3   male  0.42000     0     1   8.5167        C
    ## 805        1      3   male 27.00000     0     0   6.9750        S
    ## 806        0      3   male 31.00000     0     0   7.7750        S
    ## 807        0      1   male 39.00000     0     0   0.0000        S
    ## 808        0      3 female 18.00000     0     0   7.7750        S
    ## 809        0      2   male 39.00000     0     0  13.0000        S
    ## 810        1      1 female 33.00000     1     0  53.1000        S
    ## 811        0      3   male 26.00000     0     0   7.8875        S
    ## 812        0      3   male 39.00000     0     0  24.1500        S
    ## 813        0      2   male 35.00000     0     0  10.5000        S
    ## 814        0      3 female  6.00000     4     2  31.2750        S
    ## 815        0      3   male 30.50000     0     0   8.0500        S
    ## 816        0      1   male 29.69912     0     0   0.0000        S
    ## 817        0      3 female 23.00000     0     0   7.9250        S
    ## 818        0      2   male 31.00000     1     1  37.0042        C
    ## 819        0      3   male 43.00000     0     0   6.4500        S
    ## 820        0      3   male 10.00000     3     2  27.9000        S
    ## 821        1      1 female 52.00000     1     1  93.5000        S
    ## 822        1      3   male 27.00000     0     0   8.6625        S
    ## 823        0      1   male 38.00000     0     0   0.0000        S
    ## 824        1      3 female 27.00000     0     1  12.4750        S
    ## 825        0      3   male  2.00000     4     1  39.6875        S
    ## 826        0      3   male 29.69912     0     0   6.9500        Q
    ## 827        0      3   male 29.69912     0     0  56.4958        S
    ## 828        1      2   male  1.00000     0     2  37.0042        C
    ## 829        1      3   male 29.69912     0     0   7.7500        Q
    ## 830        1      1 female 62.00000     0     0  80.0000         
    ## 831        1      3 female 15.00000     1     0  14.4542        C
    ## 832        1      2   male  0.83000     1     1  18.7500        S
    ## 833        0      3   male 29.69912     0     0   7.2292        C
    ## 834        0      3   male 23.00000     0     0   7.8542        S
    ## 835        0      3   male 18.00000     0     0   8.3000        S
    ## 836        1      1 female 39.00000     1     1  83.1583        C
    ## 837        0      3   male 21.00000     0     0   8.6625        S
    ## 838        0      3   male 29.69912     0     0   8.0500        S
    ## 839        1      3   male 32.00000     0     0  56.4958        S
    ## 840        1      1   male 29.69912     0     0  29.7000        C
    ## 841        0      3   male 20.00000     0     0   7.9250        S
    ## 842        0      2   male 16.00000     0     0  10.5000        S
    ## 843        1      1 female 30.00000     0     0  31.0000        C
    ## 844        0      3   male 34.50000     0     0   6.4375        C
    ## 845        0      3   male 17.00000     0     0   8.6625        S
    ## 846        0      3   male 42.00000     0     0   7.5500        S
    ## 847        0      3   male 29.69912     8     2  69.5500        S
    ## 848        0      3   male 35.00000     0     0   7.8958        C
    ## 849        0      2   male 28.00000     0     1  33.0000        S
    ## 850        1      1 female 29.69912     1     0  89.1042        C
    ## 851        0      3   male  4.00000     4     2  31.2750        S
    ## 852        0      3   male 74.00000     0     0   7.7750        S
    ## 853        0      3 female  9.00000     1     1  15.2458        C
    ## 854        1      1 female 16.00000     0     1  39.4000        S
    ## 855        0      2 female 44.00000     1     0  26.0000        S
    ## 856        1      3 female 18.00000     0     1   9.3500        S
    ## 857        1      1 female 45.00000     1     1 164.8667        S
    ## 858        1      1   male 51.00000     0     0  26.5500        S
    ## 859        1      3 female 24.00000     0     3  19.2583        C
    ## 860        0      3   male 29.69912     0     0   7.2292        C
    ## 861        0      3   male 41.00000     2     0  14.1083        S
    ## 862        0      2   male 21.00000     1     0  11.5000        S
    ## 863        1      1 female 48.00000     0     0  25.9292        S
    ## 864        0      3 female 29.69912     8     2  69.5500        S
    ## 865        0      2   male 24.00000     0     0  13.0000        S
    ## 866        1      2 female 42.00000     0     0  13.0000        S
    ## 867        1      2 female 27.00000     1     0  13.8583        C
    ## 868        0      1   male 31.00000     0     0  50.4958        S
    ## 869        0      3   male 29.69912     0     0   9.5000        S
    ## 870        1      3   male  4.00000     1     1  11.1333        S
    ## 871        0      3   male 26.00000     0     0   7.8958        S
    ## 872        1      1 female 47.00000     1     1  52.5542        S
    ## 873        0      1   male 33.00000     0     0   5.0000        S
    ## 874        0      3   male 47.00000     0     0   9.0000        S
    ## 875        1      2 female 28.00000     1     0  24.0000        C
    ## 876        1      3 female 15.00000     0     0   7.2250        C
    ## 877        0      3   male 20.00000     0     0   9.8458        S
    ## 878        0      3   male 19.00000     0     0   7.8958        S
    ## 879        0      3   male 29.69912     0     0   7.8958        S
    ## 880        1      1 female 56.00000     0     1  83.1583        C
    ## 881        1      2 female 25.00000     0     1  26.0000        S
    ## 882        0      3   male 33.00000     0     0   7.8958        S
    ## 883        0      3 female 22.00000     0     0  10.5167        S
    ## 884        0      2   male 28.00000     0     0  10.5000        S
    ## 885        0      3   male 25.00000     0     0   7.0500        S
    ## 886        0      3 female 39.00000     0     5  29.1250        Q
    ## 887        0      2   male 27.00000     0     0  13.0000        S
    ## 888        1      1 female 19.00000     0     0  30.0000        S
    ## 889        0      3 female 29.69912     1     2  23.4500        S
    ## 890        1      1   male 26.00000     0     0  30.0000        C
    ## 891        0      3   male 32.00000     0     0   7.7500        Q
    ##         cfare
    ## 1       cheap
    ## 2   expensive
    ## 3       cheap
    ## 4   expensive
    ## 5       cheap
    ## 6       cheap
    ## 7   expensive
    ## 8       cheap
    ## 9       cheap
    ## 10      cheap
    ## 11      cheap
    ## 12      cheap
    ## 13      cheap
    ## 14      cheap
    ## 15      cheap
    ## 16      cheap
    ## 17      cheap
    ## 18      cheap
    ## 19      cheap
    ## 20      cheap
    ## 21      cheap
    ## 22      cheap
    ## 23      cheap
    ## 24  expensive
    ## 25      cheap
    ## 26      cheap
    ## 27      cheap
    ## 28  expensive
    ## 29      cheap
    ## 30      cheap
    ## 31      cheap
    ## 32  expensive
    ## 33      cheap
    ## 34      cheap
    ## 35  expensive
    ## 36  expensive
    ## 37      cheap
    ## 38      cheap
    ## 39      cheap
    ## 40      cheap
    ## 41      cheap
    ## 42      cheap
    ## 43      cheap
    ## 44  expensive
    ## 45      cheap
    ## 46      cheap
    ## 47      cheap
    ## 48      cheap
    ## 49      cheap
    ## 50      cheap
    ## 51  expensive
    ## 52      cheap
    ## 53  expensive
    ## 54      cheap
    ## 55  expensive
    ## 56  expensive
    ## 57      cheap
    ## 58      cheap
    ## 59      cheap
    ## 60  expensive
    ## 61      cheap
    ## 62  expensive
    ## 63  expensive
    ## 64      cheap
    ## 65      cheap
    ## 66      cheap
    ## 67      cheap
    ## 68      cheap
    ## 69      cheap
    ## 70      cheap
    ## 71      cheap
    ## 72  expensive
    ## 73  expensive
    ## 74      cheap
    ## 75  expensive
    ## 76      cheap
    ## 77      cheap
    ## 78      cheap
    ## 79      cheap
    ## 80      cheap
    ## 81      cheap
    ## 82      cheap
    ## 83      cheap
    ## 84  expensive
    ## 85      cheap
    ## 86      cheap
    ## 87  expensive
    ## 88      cheap
    ## 89  expensive
    ## 90      cheap
    ## 91      cheap
    ## 92      cheap
    ## 93  expensive
    ## 94      cheap
    ## 95      cheap
    ## 96      cheap
    ## 97  expensive
    ## 98  expensive
    ## 99      cheap
    ## 100     cheap
    ## 101     cheap
    ## 102     cheap
    ## 103 expensive
    ## 104     cheap
    ## 105     cheap
    ## 106     cheap
    ## 107     cheap
    ## 108     cheap
    ## 109     cheap
    ## 110     cheap
    ## 111 expensive
    ## 112     cheap
    ## 113     cheap
    ## 114     cheap
    ## 115     cheap
    ## 116     cheap
    ## 117     cheap
    ## 118     cheap
    ## 119 expensive
    ## 120     cheap
    ## 121 expensive
    ## 122     cheap
    ## 123     cheap
    ## 124     cheap
    ## 125 expensive
    ## 126     cheap
    ## 127     cheap
    ## 128     cheap
    ## 129     cheap
    ## 130     cheap
    ## 131     cheap
    ## 132     cheap
    ## 133     cheap
    ## 134     cheap
    ## 135     cheap
    ## 136     cheap
    ## 137     cheap
    ## 138 expensive
    ## 139     cheap
    ## 140 expensive
    ## 141     cheap
    ## 142     cheap
    ## 143     cheap
    ## 144     cheap
    ## 145     cheap
    ## 146 expensive
    ## 147     cheap
    ## 148 expensive
    ## 149     cheap
    ## 150     cheap
    ## 151     cheap
    ## 152 expensive
    ## 153     cheap
    ## 154     cheap
    ## 155     cheap
    ## 156 expensive
    ## 157     cheap
    ## 158     cheap
    ## 159     cheap
    ## 160 expensive
    ## 161     cheap
    ## 162     cheap
    ## 163     cheap
    ## 164     cheap
    ## 165 expensive
    ## 166     cheap
    ## 167 expensive
    ## 168     cheap
    ## 169     cheap
    ## 170 expensive
    ## 171 expensive
    ## 172     cheap
    ## 173     cheap
    ## 174     cheap
    ## 175     cheap
    ## 176     cheap
    ## 177     cheap
    ## 178     cheap
    ## 179     cheap
    ## 180     cheap
    ## 181 expensive
    ## 182     cheap
    ## 183     cheap
    ## 184 expensive
    ## 185     cheap
    ## 186 expensive
    ## 187     cheap
    ## 188     cheap
    ## 189     cheap
    ## 190     cheap
    ## 191     cheap
    ## 192     cheap
    ## 193     cheap
    ## 194     cheap
    ## 195     cheap
    ## 196 expensive
    ## 197     cheap
    ## 198     cheap
    ## 199     cheap
    ## 200     cheap
    ## 201     cheap
    ## 202 expensive
    ## 203     cheap
    ## 204     cheap
    ## 205     cheap
    ## 206     cheap
    ## 207     cheap
    ## 208     cheap
    ## 209     cheap
    ## 210     cheap
    ## 211     cheap
    ## 212     cheap
    ## 213     cheap
    ## 214     cheap
    ## 215     cheap
    ## 216 expensive
    ## 217     cheap
    ## 218     cheap
    ## 219 expensive
    ## 220     cheap
    ## 221     cheap
    ## 222     cheap
    ## 223     cheap
    ## 224     cheap
    ## 225 expensive
    ## 226     cheap
    ## 227     cheap
    ## 228     cheap
    ## 229     cheap
    ## 230     cheap
    ## 231 expensive
    ## 232     cheap
    ## 233     cheap
    ## 234     cheap
    ## 235     cheap
    ## 236     cheap
    ## 237     cheap
    ## 238     cheap
    ## 239     cheap
    ## 240     cheap
    ## 241     cheap
    ## 242     cheap
    ## 243     cheap
    ## 244     cheap
    ## 245     cheap
    ## 246 expensive
    ## 247     cheap
    ## 248     cheap
    ## 249 expensive
    ## 250     cheap
    ## 251     cheap
    ## 252     cheap
    ## 253     cheap
    ## 254     cheap
    ## 255     cheap
    ## 256     cheap
    ## 257 expensive
    ## 258 expensive
    ## 259 expensive
    ## 260     cheap
    ## 261     cheap
    ## 262     cheap
    ## 263 expensive
    ## 264     cheap
    ## 265     cheap
    ## 266     cheap
    ## 267 expensive
    ## 268     cheap
    ## 269 expensive
    ## 270 expensive
    ## 271     cheap
    ## 272     cheap
    ## 273     cheap
    ## 274     cheap
    ## 275     cheap
    ## 276 expensive
    ## 277     cheap
    ## 278     cheap
    ## 279     cheap
    ## 280     cheap
    ## 281     cheap
    ## 282     cheap
    ## 283     cheap
    ## 284     cheap
    ## 285     cheap
    ## 286     cheap
    ## 287     cheap
    ## 288     cheap
    ## 289     cheap
    ## 290     cheap
    ## 291 expensive
    ## 292 expensive
    ## 293     cheap
    ## 294     cheap
    ## 295     cheap
    ## 296     cheap
    ## 297     cheap
    ## 298 expensive
    ## 299     cheap
    ## 300 expensive
    ## 301     cheap
    ## 302     cheap
    ## 303     cheap
    ## 304     cheap
    ## 305     cheap
    ## 306 expensive
    ## 307 expensive
    ## 308 expensive
    ## 309     cheap
    ## 310 expensive
    ## 311 expensive
    ## 312 expensive
    ## 313     cheap
    ## 314     cheap
    ## 315     cheap
    ## 316     cheap
    ## 317     cheap
    ## 318     cheap
    ## 319 expensive
    ## 320 expensive
    ## 321     cheap
    ## 322     cheap
    ## 323     cheap
    ## 324     cheap
    ## 325 expensive
    ## 326 expensive
    ## 327     cheap
    ## 328     cheap
    ## 329     cheap
    ## 330 expensive
    ## 331     cheap
    ## 332     cheap
    ## 333 expensive
    ## 334     cheap
    ## 335 expensive
    ## 336     cheap
    ## 337 expensive
    ## 338 expensive
    ## 339     cheap
    ## 340 expensive
    ## 341     cheap
    ## 342 expensive
    ## 343     cheap
    ## 344     cheap
    ## 345     cheap
    ## 346     cheap
    ## 347     cheap
    ## 348     cheap
    ## 349     cheap
    ## 350     cheap
    ## 351     cheap
    ## 352 expensive
    ## 353     cheap
    ## 354     cheap
    ## 355     cheap
    ## 356     cheap
    ## 357 expensive
    ## 358     cheap
    ## 359     cheap
    ## 360     cheap
    ## 361     cheap
    ## 362     cheap
    ## 363     cheap
    ## 364     cheap
    ## 365     cheap
    ## 366     cheap
    ## 367 expensive
    ## 368     cheap
    ## 369     cheap
    ## 370 expensive
    ## 371 expensive
    ## 372     cheap
    ## 373     cheap
    ## 374 expensive
    ## 375     cheap
    ## 376 expensive
    ## 377     cheap
    ## 378 expensive
    ## 379     cheap
    ## 380     cheap
    ## 381 expensive
    ## 382     cheap
    ## 383     cheap
    ## 384 expensive
    ## 385     cheap
    ## 386 expensive
    ## 387 expensive
    ## 388     cheap
    ## 389     cheap
    ## 390     cheap
    ## 391 expensive
    ## 392     cheap
    ## 393     cheap
    ## 394 expensive
    ## 395     cheap
    ## 396     cheap
    ## 397     cheap
    ## 398     cheap
    ## 399     cheap
    ## 400     cheap
    ## 401     cheap
    ## 402     cheap
    ## 403     cheap
    ## 404     cheap
    ## 405     cheap
    ## 406     cheap
    ## 407     cheap
    ## 408     cheap
    ## 409     cheap
    ## 410     cheap
    ## 411     cheap
    ## 412     cheap
    ## 413 expensive
    ## 414     cheap
    ## 415     cheap
    ## 416     cheap
    ## 417 expensive
    ## 418     cheap
    ## 419     cheap
    ## 420     cheap
    ## 421     cheap
    ## 422     cheap
    ## 423     cheap
    ## 424     cheap
    ## 425     cheap
    ## 426     cheap
    ## 427     cheap
    ## 428     cheap
    ## 429     cheap
    ## 430     cheap
    ## 431     cheap
    ## 432     cheap
    ## 433     cheap
    ## 434     cheap
    ## 435 expensive
    ## 436 expensive
    ## 437 expensive
    ## 438     cheap
    ## 439 expensive
    ## 440     cheap
    ## 441     cheap
    ## 442     cheap
    ## 443     cheap
    ## 444     cheap
    ## 445     cheap
    ## 446 expensive
    ## 447     cheap
    ## 448     cheap
    ## 449     cheap
    ## 450     cheap
    ## 451     cheap
    ## 452     cheap
    ## 453     cheap
    ## 454 expensive
    ## 455     cheap
    ## 456     cheap
    ## 457     cheap
    ## 458 expensive
    ## 459     cheap
    ## 460     cheap
    ## 461     cheap
    ## 462     cheap
    ## 463 expensive
    ## 464     cheap
    ## 465     cheap
    ## 466     cheap
    ## 467     cheap
    ## 468     cheap
    ## 469     cheap
    ## 470     cheap
    ## 471     cheap
    ## 472     cheap
    ## 473     cheap
    ## 474     cheap
    ## 475     cheap
    ## 476 expensive
    ## 477     cheap
    ## 478     cheap
    ## 479     cheap
    ## 480     cheap
    ## 481 expensive
    ## 482     cheap
    ## 483     cheap
    ## 484     cheap
    ## 485 expensive
    ## 486     cheap
    ## 487 expensive
    ## 488     cheap
    ## 489     cheap
    ## 490     cheap
    ## 491     cheap
    ## 492     cheap
    ## 493     cheap
    ## 494 expensive
    ## 495     cheap
    ## 496     cheap
    ## 497 expensive
    ## 498     cheap
    ## 499 expensive
    ## 500     cheap
    ## 501     cheap
    ## 502     cheap
    ## 503     cheap
    ## 504     cheap
    ## 505 expensive
    ## 506 expensive
    ## 507     cheap
    ## 508     cheap
    ## 509     cheap
    ## 510 expensive
    ## 511     cheap
    ## 512     cheap
    ## 513     cheap
    ## 514 expensive
    ## 515     cheap
    ## 516 expensive
    ## 517     cheap
    ## 518     cheap
    ## 519     cheap
    ## 520     cheap
    ## 521 expensive
    ## 522     cheap
    ## 523     cheap
    ## 524 expensive
    ## 525     cheap
    ## 526     cheap
    ## 527     cheap
    ## 528 expensive
    ## 529     cheap
    ## 530     cheap
    ## 531     cheap
    ## 532     cheap
    ## 533     cheap
    ## 534     cheap
    ## 535     cheap
    ## 536     cheap
    ## 537     cheap
    ## 538 expensive
    ## 539     cheap
    ## 540 expensive
    ## 541 expensive
    ## 542     cheap
    ## 543     cheap
    ## 544     cheap
    ## 545 expensive
    ## 546     cheap
    ## 547     cheap
    ## 548     cheap
    ## 549     cheap
    ## 550 expensive
    ## 551 expensive
    ## 552     cheap
    ## 553     cheap
    ## 554     cheap
    ## 555     cheap
    ## 556     cheap
    ## 557 expensive
    ## 558 expensive
    ## 559 expensive
    ## 560     cheap
    ## 561     cheap
    ## 562     cheap
    ## 563     cheap
    ## 564     cheap
    ## 565     cheap
    ## 566     cheap
    ## 567     cheap
    ## 568     cheap
    ## 569     cheap
    ## 570     cheap
    ## 571     cheap
    ## 572 expensive
    ## 573     cheap
    ## 574     cheap
    ## 575     cheap
    ## 576     cheap
    ## 577     cheap
    ## 578 expensive
    ## 579     cheap
    ## 580     cheap
    ## 581     cheap
    ## 582 expensive
    ## 583     cheap
    ## 584 expensive
    ## 585     cheap
    ## 586 expensive
    ## 587     cheap
    ## 588 expensive
    ## 589     cheap
    ## 590     cheap
    ## 591     cheap
    ## 592 expensive
    ## 593     cheap
    ## 594     cheap
    ## 595     cheap
    ## 596     cheap
    ## 597 expensive
    ## 598     cheap
    ## 599     cheap
    ## 600 expensive
    ## 601     cheap
    ## 602     cheap
    ## 603 expensive
    ## 604     cheap
    ## 605     cheap
    ## 606     cheap
    ## 607     cheap
    ## 608     cheap
    ## 609 expensive
    ## 610 expensive
    ## 611     cheap
    ## 612     cheap
    ## 613     cheap
    ## 614     cheap
    ## 615     cheap
    ## 616 expensive
    ## 617     cheap
    ## 618     cheap
    ## 619 expensive
    ## 620     cheap
    ## 621     cheap
    ## 622 expensive
    ## 623     cheap
    ## 624     cheap
    ## 625     cheap
    ## 626 expensive
    ## 627     cheap
    ## 628 expensive
    ## 629     cheap
    ## 630     cheap
    ## 631     cheap
    ## 632     cheap
    ## 633     cheap
    ## 634     cheap
    ## 635     cheap
    ## 636     cheap
    ## 637     cheap
    ## 638     cheap
    ## 639 expensive
    ## 640     cheap
    ## 641     cheap
    ## 642 expensive
    ## 643     cheap
    ## 644 expensive
    ## 645     cheap
    ## 646 expensive
    ## 647     cheap
    ## 648 expensive
    ## 649     cheap
    ## 650     cheap
    ## 651     cheap
    ## 652     cheap
    ## 653     cheap
    ## 654     cheap
    ## 655     cheap
    ## 656 expensive
    ## 657     cheap
    ## 658     cheap
    ## 659     cheap
    ## 660 expensive
    ## 661 expensive
    ## 662     cheap
    ## 663     cheap
    ## 664     cheap
    ## 665     cheap
    ## 666 expensive
    ## 667     cheap
    ## 668     cheap
    ## 669     cheap
    ## 670 expensive
    ## 671 expensive
    ## 672 expensive
    ## 673     cheap
    ## 674     cheap
    ## 675     cheap
    ## 676     cheap
    ## 677     cheap
    ## 678     cheap
    ## 679 expensive
    ## 680 expensive
    ## 681     cheap
    ## 682 expensive
    ## 683     cheap
    ## 684 expensive
    ## 685 expensive
    ## 686 expensive
    ## 687 expensive
    ## 688     cheap
    ## 689     cheap
    ## 690 expensive
    ## 691 expensive
    ## 692     cheap
    ## 693 expensive
    ## 694     cheap
    ## 695     cheap
    ## 696     cheap
    ## 697     cheap
    ## 698     cheap
    ## 699 expensive
    ## 700     cheap
    ## 701 expensive
    ## 702     cheap
    ## 703     cheap
    ## 704     cheap
    ## 705     cheap
    ## 706     cheap
    ## 707     cheap
    ## 708     cheap
    ## 709 expensive
    ## 710     cheap
    ## 711 expensive
    ## 712     cheap
    ## 713 expensive
    ## 714     cheap
    ## 715     cheap
    ## 716     cheap
    ## 717 expensive
    ## 718     cheap
    ## 719     cheap
    ## 720     cheap
    ## 721 expensive
    ## 722     cheap
    ## 723     cheap
    ## 724     cheap
    ## 725 expensive
    ## 726     cheap
    ## 727     cheap
    ## 728     cheap
    ## 729     cheap
    ## 730     cheap
    ## 731 expensive
    ## 732     cheap
    ## 733     cheap
    ## 734     cheap
    ## 735     cheap
    ## 736     cheap
    ## 737 expensive
    ## 738 expensive
    ## 739     cheap
    ## 740     cheap
    ## 741     cheap
    ## 742 expensive
    ## 743 expensive
    ## 744     cheap
    ## 745     cheap
    ## 746 expensive
    ## 747     cheap
    ## 748     cheap
    ## 749 expensive
    ## 750     cheap
    ## 751     cheap
    ## 752     cheap
    ## 753     cheap
    ## 754     cheap
    ## 755 expensive
    ## 756     cheap
    ## 757     cheap
    ## 758     cheap
    ## 759     cheap
    ## 760 expensive
    ## 761     cheap
    ## 762     cheap
    ## 763     cheap
    ## 764 expensive
    ## 765     cheap
    ## 766 expensive
    ## 767 expensive
    ## 768     cheap
    ## 769     cheap
    ## 770     cheap
    ## 771     cheap
    ## 772     cheap
    ## 773     cheap
    ## 774     cheap
    ## 775     cheap
    ## 776     cheap
    ## 777     cheap
    ## 778     cheap
    ## 779     cheap
    ## 780 expensive
    ## 781     cheap
    ## 782 expensive
    ## 783     cheap
    ## 784     cheap
    ## 785     cheap
    ## 786     cheap
    ## 787     cheap
    ## 788     cheap
    ## 789     cheap
    ## 790 expensive
    ## 791     cheap
    ## 792     cheap
    ## 793 expensive
    ## 794     cheap
    ## 795     cheap
    ## 796     cheap
    ## 797     cheap
    ## 798     cheap
    ## 799     cheap
    ## 800     cheap
    ## 801     cheap
    ## 802     cheap
    ## 803 expensive
    ## 804     cheap
    ## 805     cheap
    ## 806     cheap
    ## 807     cheap
    ## 808     cheap
    ## 809     cheap
    ## 810 expensive
    ## 811     cheap
    ## 812     cheap
    ## 813     cheap
    ## 814     cheap
    ## 815     cheap
    ## 816     cheap
    ## 817     cheap
    ## 818 expensive
    ## 819     cheap
    ## 820     cheap
    ## 821 expensive
    ## 822     cheap
    ## 823     cheap
    ## 824     cheap
    ## 825 expensive
    ## 826     cheap
    ## 827 expensive
    ## 828 expensive
    ## 829     cheap
    ## 830 expensive
    ## 831     cheap
    ## 832     cheap
    ## 833     cheap
    ## 834     cheap
    ## 835     cheap
    ## 836 expensive
    ## 837     cheap
    ## 838     cheap
    ## 839 expensive
    ## 840     cheap
    ## 841     cheap
    ## 842     cheap
    ## 843     cheap
    ## 844     cheap
    ## 845     cheap
    ## 846     cheap
    ## 847 expensive
    ## 848     cheap
    ## 849 expensive
    ## 850 expensive
    ## 851     cheap
    ## 852     cheap
    ## 853     cheap
    ## 854 expensive
    ## 855     cheap
    ## 856     cheap
    ## 857 expensive
    ## 858     cheap
    ## 859     cheap
    ## 860     cheap
    ## 861     cheap
    ## 862     cheap
    ## 863     cheap
    ## 864 expensive
    ## 865     cheap
    ## 866     cheap
    ## 867     cheap
    ## 868 expensive
    ## 869     cheap
    ## 870     cheap
    ## 871     cheap
    ## 872 expensive
    ## 873     cheap
    ## 874     cheap
    ## 875     cheap
    ## 876     cheap
    ## 877     cheap
    ## 878     cheap
    ## 879     cheap
    ## 880 expensive
    ## 881     cheap
    ## 882     cheap
    ## 883     cheap
    ## 884     cheap
    ## 885     cheap
    ## 886     cheap
    ## 887     cheap
    ## 888     cheap
    ## 889     cheap
    ## 890     cheap
    ## 891     cheap

Question 22
-----------

``` r
attach(titanic)
titanic$cage[titanic$Age <= 10] <- 0
titanic$cage[titanic$Age > 10 & titanic$Age <= 20] <- 1
titanic$cage[titanic$Age > 20 & titanic$Age <= 30] <- 2
titanic$cage[titanic$Age > 30 & titanic$Age <= 40] <- 3
titanic$cage[titanic$Age > 40 & titanic$Age <= 50] <- 4
titanic$cage[titanic$Age > 50 & titanic$Age <= 60] <- 5
titanic$cage[titanic$Age > 60 & titanic$Age <= 70] <- 6
titanic$cage[titanic$Age > 70 & titanic$Age <= 80] <- 7
detach(titanic)
titanic
```

    ##     Survived Pclass    Sex      Age SibSp Parch     Fare Embarked cage
    ## 1          0      3   male 22.00000     1     0   7.2500        S    2
    ## 2          1      1 female 38.00000     1     0  71.2833        C    3
    ## 3          1      3 female 26.00000     0     0   7.9250        S    2
    ## 4          1      1 female 35.00000     1     0  53.1000        S    3
    ## 5          0      3   male 35.00000     0     0   8.0500        S    3
    ## 6          0      3   male 29.69912     0     0   8.4583        Q    2
    ## 7          0      1   male 54.00000     0     0  51.8625        S    5
    ## 8          0      3   male  2.00000     3     1  21.0750        S    0
    ## 9          1      3 female 27.00000     0     2  11.1333        S    2
    ## 10         1      2 female 14.00000     1     0  30.0708        C    1
    ## 11         1      3 female  4.00000     1     1  16.7000        S    0
    ## 12         1      1 female 58.00000     0     0  26.5500        S    5
    ## 13         0      3   male 20.00000     0     0   8.0500        S    1
    ## 14         0      3   male 39.00000     1     5  31.2750        S    3
    ## 15         0      3 female 14.00000     0     0   7.8542        S    1
    ## 16         1      2 female 55.00000     0     0  16.0000        S    5
    ## 17         0      3   male  2.00000     4     1  29.1250        Q    0
    ## 18         1      2   male 29.69912     0     0  13.0000        S    2
    ## 19         0      3 female 31.00000     1     0  18.0000        S    3
    ## 20         1      3 female 29.69912     0     0   7.2250        C    2
    ## 21         0      2   male 35.00000     0     0  26.0000        S    3
    ## 22         1      2   male 34.00000     0     0  13.0000        S    3
    ## 23         1      3 female 15.00000     0     0   8.0292        Q    1
    ## 24         1      1   male 28.00000     0     0  35.5000        S    2
    ## 25         0      3 female  8.00000     3     1  21.0750        S    0
    ## 26         1      3 female 38.00000     1     5  31.3875        S    3
    ## 27         0      3   male 29.69912     0     0   7.2250        C    2
    ## 28         0      1   male 19.00000     3     2 263.0000        S    1
    ## 29         1      3 female 29.69912     0     0   7.8792        Q    2
    ## 30         0      3   male 29.69912     0     0   7.8958        S    2
    ## 31         0      1   male 40.00000     0     0  27.7208        C    3
    ## 32         1      1 female 29.69912     1     0 146.5208        C    2
    ## 33         1      3 female 29.69912     0     0   7.7500        Q    2
    ## 34         0      2   male 66.00000     0     0  10.5000        S    6
    ## 35         0      1   male 28.00000     1     0  82.1708        C    2
    ## 36         0      1   male 42.00000     1     0  52.0000        S    4
    ## 37         1      3   male 29.69912     0     0   7.2292        C    2
    ## 38         0      3   male 21.00000     0     0   8.0500        S    2
    ## 39         0      3 female 18.00000     2     0  18.0000        S    1
    ## 40         1      3 female 14.00000     1     0  11.2417        C    1
    ## 41         0      3 female 40.00000     1     0   9.4750        S    3
    ## 42         0      2 female 27.00000     1     0  21.0000        S    2
    ## 43         0      3   male 29.69912     0     0   7.8958        C    2
    ## 44         1      2 female  3.00000     1     2  41.5792        C    0
    ## 45         1      3 female 19.00000     0     0   7.8792        Q    1
    ## 46         0      3   male 29.69912     0     0   8.0500        S    2
    ## 47         0      3   male 29.69912     1     0  15.5000        Q    2
    ## 48         1      3 female 29.69912     0     0   7.7500        Q    2
    ## 49         0      3   male 29.69912     2     0  21.6792        C    2
    ## 50         0      3 female 18.00000     1     0  17.8000        S    1
    ## 51         0      3   male  7.00000     4     1  39.6875        S    0
    ## 52         0      3   male 21.00000     0     0   7.8000        S    2
    ## 53         1      1 female 49.00000     1     0  76.7292        C    4
    ## 54         1      2 female 29.00000     1     0  26.0000        S    2
    ## 55         0      1   male 65.00000     0     1  61.9792        C    6
    ## 56         1      1   male 29.69912     0     0  35.5000        S    2
    ## 57         1      2 female 21.00000     0     0  10.5000        S    2
    ## 58         0      3   male 28.50000     0     0   7.2292        C    2
    ## 59         1      2 female  5.00000     1     2  27.7500        S    0
    ## 60         0      3   male 11.00000     5     2  46.9000        S    1
    ## 61         0      3   male 22.00000     0     0   7.2292        C    2
    ## 62         1      1 female 38.00000     0     0  80.0000             3
    ## 63         0      1   male 45.00000     1     0  83.4750        S    4
    ## 64         0      3   male  4.00000     3     2  27.9000        S    0
    ## 65         0      1   male 29.69912     0     0  27.7208        C    2
    ## 66         1      3   male 29.69912     1     1  15.2458        C    2
    ## 67         1      2 female 29.00000     0     0  10.5000        S    2
    ## 68         0      3   male 19.00000     0     0   8.1583        S    1
    ## 69         1      3 female 17.00000     4     2   7.9250        S    1
    ## 70         0      3   male 26.00000     2     0   8.6625        S    2
    ## 71         0      2   male 32.00000     0     0  10.5000        S    3
    ## 72         0      3 female 16.00000     5     2  46.9000        S    1
    ## 73         0      2   male 21.00000     0     0  73.5000        S    2
    ## 74         0      3   male 26.00000     1     0  14.4542        C    2
    ## 75         1      3   male 32.00000     0     0  56.4958        S    3
    ## 76         0      3   male 25.00000     0     0   7.6500        S    2
    ## 77         0      3   male 29.69912     0     0   7.8958        S    2
    ## 78         0      3   male 29.69912     0     0   8.0500        S    2
    ## 79         1      2   male  0.83000     0     2  29.0000        S    0
    ## 80         1      3 female 30.00000     0     0  12.4750        S    2
    ## 81         0      3   male 22.00000     0     0   9.0000        S    2
    ## 82         1      3   male 29.00000     0     0   9.5000        S    2
    ## 83         1      3 female 29.69912     0     0   7.7875        Q    2
    ## 84         0      1   male 28.00000     0     0  47.1000        S    2
    ## 85         1      2 female 17.00000     0     0  10.5000        S    1
    ## 86         1      3 female 33.00000     3     0  15.8500        S    3
    ## 87         0      3   male 16.00000     1     3  34.3750        S    1
    ## 88         0      3   male 29.69912     0     0   8.0500        S    2
    ## 89         1      1 female 23.00000     3     2 263.0000        S    2
    ## 90         0      3   male 24.00000     0     0   8.0500        S    2
    ## 91         0      3   male 29.00000     0     0   8.0500        S    2
    ## 92         0      3   male 20.00000     0     0   7.8542        S    1
    ## 93         0      1   male 46.00000     1     0  61.1750        S    4
    ## 94         0      3   male 26.00000     1     2  20.5750        S    2
    ## 95         0      3   male 59.00000     0     0   7.2500        S    5
    ## 96         0      3   male 29.69912     0     0   8.0500        S    2
    ## 97         0      1   male 71.00000     0     0  34.6542        C    7
    ## 98         1      1   male 23.00000     0     1  63.3583        C    2
    ## 99         1      2 female 34.00000     0     1  23.0000        S    3
    ## 100        0      2   male 34.00000     1     0  26.0000        S    3
    ## 101        0      3 female 28.00000     0     0   7.8958        S    2
    ## 102        0      3   male 29.69912     0     0   7.8958        S    2
    ## 103        0      1   male 21.00000     0     1  77.2875        S    2
    ## 104        0      3   male 33.00000     0     0   8.6542        S    3
    ## 105        0      3   male 37.00000     2     0   7.9250        S    3
    ## 106        0      3   male 28.00000     0     0   7.8958        S    2
    ## 107        1      3 female 21.00000     0     0   7.6500        S    2
    ## 108        1      3   male 29.69912     0     0   7.7750        S    2
    ## 109        0      3   male 38.00000     0     0   7.8958        S    3
    ## 110        1      3 female 29.69912     1     0  24.1500        Q    2
    ## 111        0      1   male 47.00000     0     0  52.0000        S    4
    ## 112        0      3 female 14.50000     1     0  14.4542        C    1
    ## 113        0      3   male 22.00000     0     0   8.0500        S    2
    ## 114        0      3 female 20.00000     1     0   9.8250        S    1
    ## 115        0      3 female 17.00000     0     0  14.4583        C    1
    ## 116        0      3   male 21.00000     0     0   7.9250        S    2
    ## 117        0      3   male 70.50000     0     0   7.7500        Q    7
    ## 118        0      2   male 29.00000     1     0  21.0000        S    2
    ## 119        0      1   male 24.00000     0     1 247.5208        C    2
    ## 120        0      3 female  2.00000     4     2  31.2750        S    0
    ## 121        0      2   male 21.00000     2     0  73.5000        S    2
    ## 122        0      3   male 29.69912     0     0   8.0500        S    2
    ## 123        0      2   male 32.50000     1     0  30.0708        C    3
    ## 124        1      2 female 32.50000     0     0  13.0000        S    3
    ## 125        0      1   male 54.00000     0     1  77.2875        S    5
    ## 126        1      3   male 12.00000     1     0  11.2417        C    1
    ## 127        0      3   male 29.69912     0     0   7.7500        Q    2
    ## 128        1      3   male 24.00000     0     0   7.1417        S    2
    ## 129        1      3 female 29.69912     1     1  22.3583        C    2
    ## 130        0      3   male 45.00000     0     0   6.9750        S    4
    ## 131        0      3   male 33.00000     0     0   7.8958        C    3
    ## 132        0      3   male 20.00000     0     0   7.0500        S    1
    ## 133        0      3 female 47.00000     1     0  14.5000        S    4
    ## 134        1      2 female 29.00000     1     0  26.0000        S    2
    ## 135        0      2   male 25.00000     0     0  13.0000        S    2
    ## 136        0      2   male 23.00000     0     0  15.0458        C    2
    ## 137        1      1 female 19.00000     0     2  26.2833        S    1
    ## 138        0      1   male 37.00000     1     0  53.1000        S    3
    ## 139        0      3   male 16.00000     0     0   9.2167        S    1
    ## 140        0      1   male 24.00000     0     0  79.2000        C    2
    ## 141        0      3 female 29.69912     0     2  15.2458        C    2
    ## 142        1      3 female 22.00000     0     0   7.7500        S    2
    ## 143        1      3 female 24.00000     1     0  15.8500        S    2
    ## 144        0      3   male 19.00000     0     0   6.7500        Q    1
    ## 145        0      2   male 18.00000     0     0  11.5000        S    1
    ## 146        0      2   male 19.00000     1     1  36.7500        S    1
    ## 147        1      3   male 27.00000     0     0   7.7958        S    2
    ## 148        0      3 female  9.00000     2     2  34.3750        S    0
    ## 149        0      2   male 36.50000     0     2  26.0000        S    3
    ## 150        0      2   male 42.00000     0     0  13.0000        S    4
    ## 151        0      2   male 51.00000     0     0  12.5250        S    5
    ## 152        1      1 female 22.00000     1     0  66.6000        S    2
    ## 153        0      3   male 55.50000     0     0   8.0500        S    5
    ## 154        0      3   male 40.50000     0     2  14.5000        S    4
    ## 155        0      3   male 29.69912     0     0   7.3125        S    2
    ## 156        0      1   male 51.00000     0     1  61.3792        C    5
    ## 157        1      3 female 16.00000     0     0   7.7333        Q    1
    ## 158        0      3   male 30.00000     0     0   8.0500        S    2
    ## 159        0      3   male 29.69912     0     0   8.6625        S    2
    ## 160        0      3   male 29.69912     8     2  69.5500        S    2
    ## 161        0      3   male 44.00000     0     1  16.1000        S    4
    ## 162        1      2 female 40.00000     0     0  15.7500        S    3
    ## 163        0      3   male 26.00000     0     0   7.7750        S    2
    ## 164        0      3   male 17.00000     0     0   8.6625        S    1
    ## 165        0      3   male  1.00000     4     1  39.6875        S    0
    ## 166        1      3   male  9.00000     0     2  20.5250        S    0
    ## 167        1      1 female 29.69912     0     1  55.0000        S    2
    ## 168        0      3 female 45.00000     1     4  27.9000        S    4
    ## 169        0      1   male 29.69912     0     0  25.9250        S    2
    ## 170        0      3   male 28.00000     0     0  56.4958        S    2
    ## 171        0      1   male 61.00000     0     0  33.5000        S    6
    ## 172        0      3   male  4.00000     4     1  29.1250        Q    0
    ## 173        1      3 female  1.00000     1     1  11.1333        S    0
    ## 174        0      3   male 21.00000     0     0   7.9250        S    2
    ## 175        0      1   male 56.00000     0     0  30.6958        C    5
    ## 176        0      3   male 18.00000     1     1   7.8542        S    1
    ## 177        0      3   male 29.69912     3     1  25.4667        S    2
    ## 178        0      1 female 50.00000     0     0  28.7125        C    4
    ## 179        0      2   male 30.00000     0     0  13.0000        S    2
    ## 180        0      3   male 36.00000     0     0   0.0000        S    3
    ## 181        0      3 female 29.69912     8     2  69.5500        S    2
    ## 182        0      2   male 29.69912     0     0  15.0500        C    2
    ## 183        0      3   male  9.00000     4     2  31.3875        S    0
    ## 184        1      2   male  1.00000     2     1  39.0000        S    0
    ## 185        1      3 female  4.00000     0     2  22.0250        S    0
    ## 186        0      1   male 29.69912     0     0  50.0000        S    2
    ## 187        1      3 female 29.69912     1     0  15.5000        Q    2
    ## 188        1      1   male 45.00000     0     0  26.5500        S    4
    ## 189        0      3   male 40.00000     1     1  15.5000        Q    3
    ## 190        0      3   male 36.00000     0     0   7.8958        S    3
    ## 191        1      2 female 32.00000     0     0  13.0000        S    3
    ## 192        0      2   male 19.00000     0     0  13.0000        S    1
    ## 193        1      3 female 19.00000     1     0   7.8542        S    1
    ## 194        1      2   male  3.00000     1     1  26.0000        S    0
    ## 195        1      1 female 44.00000     0     0  27.7208        C    4
    ## 196        1      1 female 58.00000     0     0 146.5208        C    5
    ## 197        0      3   male 29.69912     0     0   7.7500        Q    2
    ## 198        0      3   male 42.00000     0     1   8.4042        S    4
    ## 199        1      3 female 29.69912     0     0   7.7500        Q    2
    ## 200        0      2 female 24.00000     0     0  13.0000        S    2
    ## 201        0      3   male 28.00000     0     0   9.5000        S    2
    ## 202        0      3   male 29.69912     8     2  69.5500        S    2
    ## 203        0      3   male 34.00000     0     0   6.4958        S    3
    ## 204        0      3   male 45.50000     0     0   7.2250        C    4
    ## 205        1      3   male 18.00000     0     0   8.0500        S    1
    ## 206        0      3 female  2.00000     0     1  10.4625        S    0
    ## 207        0      3   male 32.00000     1     0  15.8500        S    3
    ## 208        1      3   male 26.00000     0     0  18.7875        C    2
    ## 209        1      3 female 16.00000     0     0   7.7500        Q    1
    ## 210        1      1   male 40.00000     0     0  31.0000        C    3
    ## 211        0      3   male 24.00000     0     0   7.0500        S    2
    ## 212        1      2 female 35.00000     0     0  21.0000        S    3
    ## 213        0      3   male 22.00000     0     0   7.2500        S    2
    ## 214        0      2   male 30.00000     0     0  13.0000        S    2
    ## 215        0      3   male 29.69912     1     0   7.7500        Q    2
    ## 216        1      1 female 31.00000     1     0 113.2750        C    3
    ## 217        1      3 female 27.00000     0     0   7.9250        S    2
    ## 218        0      2   male 42.00000     1     0  27.0000        S    4
    ## 219        1      1 female 32.00000     0     0  76.2917        C    3
    ## 220        0      2   male 30.00000     0     0  10.5000        S    2
    ## 221        1      3   male 16.00000     0     0   8.0500        S    1
    ## 222        0      2   male 27.00000     0     0  13.0000        S    2
    ## 223        0      3   male 51.00000     0     0   8.0500        S    5
    ## 224        0      3   male 29.69912     0     0   7.8958        S    2
    ## 225        1      1   male 38.00000     1     0  90.0000        S    3
    ## 226        0      3   male 22.00000     0     0   9.3500        S    2
    ## 227        1      2   male 19.00000     0     0  10.5000        S    1
    ## 228        0      3   male 20.50000     0     0   7.2500        S    2
    ## 229        0      2   male 18.00000     0     0  13.0000        S    1
    ## 230        0      3 female 29.69912     3     1  25.4667        S    2
    ## 231        1      1 female 35.00000     1     0  83.4750        S    3
    ## 232        0      3   male 29.00000     0     0   7.7750        S    2
    ## 233        0      2   male 59.00000     0     0  13.5000        S    5
    ## 234        1      3 female  5.00000     4     2  31.3875        S    0
    ## 235        0      2   male 24.00000     0     0  10.5000        S    2
    ## 236        0      3 female 29.69912     0     0   7.5500        S    2
    ## 237        0      2   male 44.00000     1     0  26.0000        S    4
    ## 238        1      2 female  8.00000     0     2  26.2500        S    0
    ## 239        0      2   male 19.00000     0     0  10.5000        S    1
    ## 240        0      2   male 33.00000     0     0  12.2750        S    3
    ## 241        0      3 female 29.69912     1     0  14.4542        C    2
    ## 242        1      3 female 29.69912     1     0  15.5000        Q    2
    ## 243        0      2   male 29.00000     0     0  10.5000        S    2
    ## 244        0      3   male 22.00000     0     0   7.1250        S    2
    ## 245        0      3   male 30.00000     0     0   7.2250        C    2
    ## 246        0      1   male 44.00000     2     0  90.0000        Q    4
    ## 247        0      3 female 25.00000     0     0   7.7750        S    2
    ## 248        1      2 female 24.00000     0     2  14.5000        S    2
    ## 249        1      1   male 37.00000     1     1  52.5542        S    3
    ## 250        0      2   male 54.00000     1     0  26.0000        S    5
    ## 251        0      3   male 29.69912     0     0   7.2500        S    2
    ## 252        0      3 female 29.00000     1     1  10.4625        S    2
    ## 253        0      1   male 62.00000     0     0  26.5500        S    6
    ## 254        0      3   male 30.00000     1     0  16.1000        S    2
    ## 255        0      3 female 41.00000     0     2  20.2125        S    4
    ## 256        1      3 female 29.00000     0     2  15.2458        C    2
    ## 257        1      1 female 29.69912     0     0  79.2000        C    2
    ## 258        1      1 female 30.00000     0     0  86.5000        S    2
    ## 259        1      1 female 35.00000     0     0 512.3292        C    3
    ## 260        1      2 female 50.00000     0     1  26.0000        S    4
    ## 261        0      3   male 29.69912     0     0   7.7500        Q    2
    ## 262        1      3   male  3.00000     4     2  31.3875        S    0
    ## 263        0      1   male 52.00000     1     1  79.6500        S    5
    ## 264        0      1   male 40.00000     0     0   0.0000        S    3
    ## 265        0      3 female 29.69912     0     0   7.7500        Q    2
    ## 266        0      2   male 36.00000     0     0  10.5000        S    3
    ## 267        0      3   male 16.00000     4     1  39.6875        S    1
    ## 268        1      3   male 25.00000     1     0   7.7750        S    2
    ## 269        1      1 female 58.00000     0     1 153.4625        S    5
    ## 270        1      1 female 35.00000     0     0 135.6333        S    3
    ## 271        0      1   male 29.69912     0     0  31.0000        S    2
    ## 272        1      3   male 25.00000     0     0   0.0000        S    2
    ## 273        1      2 female 41.00000     0     1  19.5000        S    4
    ## 274        0      1   male 37.00000     0     1  29.7000        C    3
    ## 275        1      3 female 29.69912     0     0   7.7500        Q    2
    ## 276        1      1 female 63.00000     1     0  77.9583        S    6
    ## 277        0      3 female 45.00000     0     0   7.7500        S    4
    ## 278        0      2   male 29.69912     0     0   0.0000        S    2
    ## 279        0      3   male  7.00000     4     1  29.1250        Q    0
    ## 280        1      3 female 35.00000     1     1  20.2500        S    3
    ## 281        0      3   male 65.00000     0     0   7.7500        Q    6
    ## 282        0      3   male 28.00000     0     0   7.8542        S    2
    ## 283        0      3   male 16.00000     0     0   9.5000        S    1
    ## 284        1      3   male 19.00000     0     0   8.0500        S    1
    ## 285        0      1   male 29.69912     0     0  26.0000        S    2
    ## 286        0      3   male 33.00000     0     0   8.6625        C    3
    ## 287        1      3   male 30.00000     0     0   9.5000        S    2
    ## 288        0      3   male 22.00000     0     0   7.8958        S    2
    ## 289        1      2   male 42.00000     0     0  13.0000        S    4
    ## 290        1      3 female 22.00000     0     0   7.7500        Q    2
    ## 291        1      1 female 26.00000     0     0  78.8500        S    2
    ## 292        1      1 female 19.00000     1     0  91.0792        C    1
    ## 293        0      2   male 36.00000     0     0  12.8750        C    3
    ## 294        0      3 female 24.00000     0     0   8.8500        S    2
    ## 295        0      3   male 24.00000     0     0   7.8958        S    2
    ## 296        0      1   male 29.69912     0     0  27.7208        C    2
    ## 297        0      3   male 23.50000     0     0   7.2292        C    2
    ## 298        0      1 female  2.00000     1     2 151.5500        S    0
    ## 299        1      1   male 29.69912     0     0  30.5000        S    2
    ## 300        1      1 female 50.00000     0     1 247.5208        C    4
    ## 301        1      3 female 29.69912     0     0   7.7500        Q    2
    ## 302        1      3   male 29.69912     2     0  23.2500        Q    2
    ## 303        0      3   male 19.00000     0     0   0.0000        S    1
    ## 304        1      2 female 29.69912     0     0  12.3500        Q    2
    ## 305        0      3   male 29.69912     0     0   8.0500        S    2
    ## 306        1      1   male  0.92000     1     2 151.5500        S    0
    ## 307        1      1 female 29.69912     0     0 110.8833        C    2
    ## 308        1      1 female 17.00000     1     0 108.9000        C    1
    ## 309        0      2   male 30.00000     1     0  24.0000        C    2
    ## 310        1      1 female 30.00000     0     0  56.9292        C    2
    ## 311        1      1 female 24.00000     0     0  83.1583        C    2
    ## 312        1      1 female 18.00000     2     2 262.3750        C    1
    ## 313        0      2 female 26.00000     1     1  26.0000        S    2
    ## 314        0      3   male 28.00000     0     0   7.8958        S    2
    ## 315        0      2   male 43.00000     1     1  26.2500        S    4
    ## 316        1      3 female 26.00000     0     0   7.8542        S    2
    ## 317        1      2 female 24.00000     1     0  26.0000        S    2
    ## 318        0      2   male 54.00000     0     0  14.0000        S    5
    ## 319        1      1 female 31.00000     0     2 164.8667        S    3
    ## 320        1      1 female 40.00000     1     1 134.5000        C    3
    ## 321        0      3   male 22.00000     0     0   7.2500        S    2
    ## 322        0      3   male 27.00000     0     0   7.8958        S    2
    ## 323        1      2 female 30.00000     0     0  12.3500        Q    2
    ## 324        1      2 female 22.00000     1     1  29.0000        S    2
    ## 325        0      3   male 29.69912     8     2  69.5500        S    2
    ## 326        1      1 female 36.00000     0     0 135.6333        C    3
    ## 327        0      3   male 61.00000     0     0   6.2375        S    6
    ## 328        1      2 female 36.00000     0     0  13.0000        S    3
    ## 329        1      3 female 31.00000     1     1  20.5250        S    3
    ## 330        1      1 female 16.00000     0     1  57.9792        C    1
    ## 331        1      3 female 29.69912     2     0  23.2500        Q    2
    ## 332        0      1   male 45.50000     0     0  28.5000        S    4
    ## 333        0      1   male 38.00000     0     1 153.4625        S    3
    ## 334        0      3   male 16.00000     2     0  18.0000        S    1
    ## 335        1      1 female 29.69912     1     0 133.6500        S    2
    ## 336        0      3   male 29.69912     0     0   7.8958        S    2
    ## 337        0      1   male 29.00000     1     0  66.6000        S    2
    ## 338        1      1 female 41.00000     0     0 134.5000        C    4
    ## 339        1      3   male 45.00000     0     0   8.0500        S    4
    ## 340        0      1   male 45.00000     0     0  35.5000        S    4
    ## 341        1      2   male  2.00000     1     1  26.0000        S    0
    ## 342        1      1 female 24.00000     3     2 263.0000        S    2
    ## 343        0      2   male 28.00000     0     0  13.0000        S    2
    ## 344        0      2   male 25.00000     0     0  13.0000        S    2
    ## 345        0      2   male 36.00000     0     0  13.0000        S    3
    ## 346        1      2 female 24.00000     0     0  13.0000        S    2
    ## 347        1      2 female 40.00000     0     0  13.0000        S    3
    ## 348        1      3 female 29.69912     1     0  16.1000        S    2
    ## 349        1      3   male  3.00000     1     1  15.9000        S    0
    ## 350        0      3   male 42.00000     0     0   8.6625        S    4
    ## 351        0      3   male 23.00000     0     0   9.2250        S    2
    ## 352        0      1   male 29.69912     0     0  35.0000        S    2
    ## 353        0      3   male 15.00000     1     1   7.2292        C    1
    ## 354        0      3   male 25.00000     1     0  17.8000        S    2
    ## 355        0      3   male 29.69912     0     0   7.2250        C    2
    ## 356        0      3   male 28.00000     0     0   9.5000        S    2
    ## 357        1      1 female 22.00000     0     1  55.0000        S    2
    ## 358        0      2 female 38.00000     0     0  13.0000        S    3
    ## 359        1      3 female 29.69912     0     0   7.8792        Q    2
    ## 360        1      3 female 29.69912     0     0   7.8792        Q    2
    ## 361        0      3   male 40.00000     1     4  27.9000        S    3
    ## 362        0      2   male 29.00000     1     0  27.7208        C    2
    ## 363        0      3 female 45.00000     0     1  14.4542        C    4
    ## 364        0      3   male 35.00000     0     0   7.0500        S    3
    ## 365        0      3   male 29.69912     1     0  15.5000        Q    2
    ## 366        0      3   male 30.00000     0     0   7.2500        S    2
    ## 367        1      1 female 60.00000     1     0  75.2500        C    5
    ## 368        1      3 female 29.69912     0     0   7.2292        C    2
    ## 369        1      3 female 29.69912     0     0   7.7500        Q    2
    ## 370        1      1 female 24.00000     0     0  69.3000        C    2
    ## 371        1      1   male 25.00000     1     0  55.4417        C    2
    ## 372        0      3   male 18.00000     1     0   6.4958        S    1
    ## 373        0      3   male 19.00000     0     0   8.0500        S    1
    ## 374        0      1   male 22.00000     0     0 135.6333        C    2
    ## 375        0      3 female  3.00000     3     1  21.0750        S    0
    ## 376        1      1 female 29.69912     1     0  82.1708        C    2
    ## 377        1      3 female 22.00000     0     0   7.2500        S    2
    ## 378        0      1   male 27.00000     0     2 211.5000        C    2
    ## 379        0      3   male 20.00000     0     0   4.0125        C    1
    ## 380        0      3   male 19.00000     0     0   7.7750        S    1
    ## 381        1      1 female 42.00000     0     0 227.5250        C    4
    ## 382        1      3 female  1.00000     0     2  15.7417        C    0
    ## 383        0      3   male 32.00000     0     0   7.9250        S    3
    ## 384        1      1 female 35.00000     1     0  52.0000        S    3
    ## 385        0      3   male 29.69912     0     0   7.8958        S    2
    ## 386        0      2   male 18.00000     0     0  73.5000        S    1
    ## 387        0      3   male  1.00000     5     2  46.9000        S    0
    ## 388        1      2 female 36.00000     0     0  13.0000        S    3
    ## 389        0      3   male 29.69912     0     0   7.7292        Q    2
    ## 390        1      2 female 17.00000     0     0  12.0000        C    1
    ## 391        1      1   male 36.00000     1     2 120.0000        S    3
    ## 392        1      3   male 21.00000     0     0   7.7958        S    2
    ## 393        0      3   male 28.00000     2     0   7.9250        S    2
    ## 394        1      1 female 23.00000     1     0 113.2750        C    2
    ## 395        1      3 female 24.00000     0     2  16.7000        S    2
    ## 396        0      3   male 22.00000     0     0   7.7958        S    2
    ## 397        0      3 female 31.00000     0     0   7.8542        S    3
    ## 398        0      2   male 46.00000     0     0  26.0000        S    4
    ## 399        0      2   male 23.00000     0     0  10.5000        S    2
    ## 400        1      2 female 28.00000     0     0  12.6500        S    2
    ## 401        1      3   male 39.00000     0     0   7.9250        S    3
    ## 402        0      3   male 26.00000     0     0   8.0500        S    2
    ## 403        0      3 female 21.00000     1     0   9.8250        S    2
    ## 404        0      3   male 28.00000     1     0  15.8500        S    2
    ## 405        0      3 female 20.00000     0     0   8.6625        S    1
    ## 406        0      2   male 34.00000     1     0  21.0000        S    3
    ## 407        0      3   male 51.00000     0     0   7.7500        S    5
    ## 408        1      2   male  3.00000     1     1  18.7500        S    0
    ## 409        0      3   male 21.00000     0     0   7.7750        S    2
    ## 410        0      3 female 29.69912     3     1  25.4667        S    2
    ## 411        0      3   male 29.69912     0     0   7.8958        S    2
    ## 412        0      3   male 29.69912     0     0   6.8583        Q    2
    ## 413        1      1 female 33.00000     1     0  90.0000        Q    3
    ## 414        0      2   male 29.69912     0     0   0.0000        S    2
    ## 415        1      3   male 44.00000     0     0   7.9250        S    4
    ## 416        0      3 female 29.69912     0     0   8.0500        S    2
    ## 417        1      2 female 34.00000     1     1  32.5000        S    3
    ## 418        1      2 female 18.00000     0     2  13.0000        S    1
    ## 419        0      2   male 30.00000     0     0  13.0000        S    2
    ## 420        0      3 female 10.00000     0     2  24.1500        S    0
    ## 421        0      3   male 29.69912     0     0   7.8958        C    2
    ## 422        0      3   male 21.00000     0     0   7.7333        Q    2
    ## 423        0      3   male 29.00000     0     0   7.8750        S    2
    ## 424        0      3 female 28.00000     1     1  14.4000        S    2
    ## 425        0      3   male 18.00000     1     1  20.2125        S    1
    ## 426        0      3   male 29.69912     0     0   7.2500        S    2
    ## 427        1      2 female 28.00000     1     0  26.0000        S    2
    ## 428        1      2 female 19.00000     0     0  26.0000        S    1
    ## 429        0      3   male 29.69912     0     0   7.7500        Q    2
    ## 430        1      3   male 32.00000     0     0   8.0500        S    3
    ## 431        1      1   male 28.00000     0     0  26.5500        S    2
    ## 432        1      3 female 29.69912     1     0  16.1000        S    2
    ## 433        1      2 female 42.00000     1     0  26.0000        S    4
    ## 434        0      3   male 17.00000     0     0   7.1250        S    1
    ## 435        0      1   male 50.00000     1     0  55.9000        S    4
    ## 436        1      1 female 14.00000     1     2 120.0000        S    1
    ## 437        0      3 female 21.00000     2     2  34.3750        S    2
    ## 438        1      2 female 24.00000     2     3  18.7500        S    2
    ## 439        0      1   male 64.00000     1     4 263.0000        S    6
    ## 440        0      2   male 31.00000     0     0  10.5000        S    3
    ## 441        1      2 female 45.00000     1     1  26.2500        S    4
    ## 442        0      3   male 20.00000     0     0   9.5000        S    1
    ## 443        0      3   male 25.00000     1     0   7.7750        S    2
    ## 444        1      2 female 28.00000     0     0  13.0000        S    2
    ## 445        1      3   male 29.69912     0     0   8.1125        S    2
    ## 446        1      1   male  4.00000     0     2  81.8583        S    0
    ## 447        1      2 female 13.00000     0     1  19.5000        S    1
    ## 448        1      1   male 34.00000     0     0  26.5500        S    3
    ## 449        1      3 female  5.00000     2     1  19.2583        C    0
    ## 450        1      1   male 52.00000     0     0  30.5000        S    5
    ## 451        0      2   male 36.00000     1     2  27.7500        S    3
    ## 452        0      3   male 29.69912     1     0  19.9667        S    2
    ## 453        0      1   male 30.00000     0     0  27.7500        C    2
    ## 454        1      1   male 49.00000     1     0  89.1042        C    4
    ## 455        0      3   male 29.69912     0     0   8.0500        S    2
    ## 456        1      3   male 29.00000     0     0   7.8958        C    2
    ## 457        0      1   male 65.00000     0     0  26.5500        S    6
    ## 458        1      1 female 29.69912     1     0  51.8625        S    2
    ## 459        1      2 female 50.00000     0     0  10.5000        S    4
    ## 460        0      3   male 29.69912     0     0   7.7500        Q    2
    ## 461        1      1   male 48.00000     0     0  26.5500        S    4
    ## 462        0      3   male 34.00000     0     0   8.0500        S    3
    ## 463        0      1   male 47.00000     0     0  38.5000        S    4
    ## 464        0      2   male 48.00000     0     0  13.0000        S    4
    ## 465        0      3   male 29.69912     0     0   8.0500        S    2
    ## 466        0      3   male 38.00000     0     0   7.0500        S    3
    ## 467        0      2   male 29.69912     0     0   0.0000        S    2
    ## 468        0      1   male 56.00000     0     0  26.5500        S    5
    ## 469        0      3   male 29.69912     0     0   7.7250        Q    2
    ## 470        1      3 female  0.75000     2     1  19.2583        C    0
    ## 471        0      3   male 29.69912     0     0   7.2500        S    2
    ## 472        0      3   male 38.00000     0     0   8.6625        S    3
    ## 473        1      2 female 33.00000     1     2  27.7500        S    3
    ## 474        1      2 female 23.00000     0     0  13.7917        C    2
    ## 475        0      3 female 22.00000     0     0   9.8375        S    2
    ## 476        0      1   male 29.69912     0     0  52.0000        S    2
    ## 477        0      2   male 34.00000     1     0  21.0000        S    3
    ## 478        0      3   male 29.00000     1     0   7.0458        S    2
    ## 479        0      3   male 22.00000     0     0   7.5208        S    2
    ## 480        1      3 female  2.00000     0     1  12.2875        S    0
    ## 481        0      3   male  9.00000     5     2  46.9000        S    0
    ## 482        0      2   male 29.69912     0     0   0.0000        S    2
    ## 483        0      3   male 50.00000     0     0   8.0500        S    4
    ## 484        1      3 female 63.00000     0     0   9.5875        S    6
    ## 485        1      1   male 25.00000     1     0  91.0792        C    2
    ## 486        0      3 female 29.69912     3     1  25.4667        S    2
    ## 487        1      1 female 35.00000     1     0  90.0000        S    3
    ## 488        0      1   male 58.00000     0     0  29.7000        C    5
    ## 489        0      3   male 30.00000     0     0   8.0500        S    2
    ## 490        1      3   male  9.00000     1     1  15.9000        S    0
    ## 491        0      3   male 29.69912     1     0  19.9667        S    2
    ## 492        0      3   male 21.00000     0     0   7.2500        S    2
    ## 493        0      1   male 55.00000     0     0  30.5000        S    5
    ## 494        0      1   male 71.00000     0     0  49.5042        C    7
    ## 495        0      3   male 21.00000     0     0   8.0500        S    2
    ## 496        0      3   male 29.69912     0     0  14.4583        C    2
    ## 497        1      1 female 54.00000     1     0  78.2667        C    5
    ## 498        0      3   male 29.69912     0     0  15.1000        S    2
    ## 499        0      1 female 25.00000     1     2 151.5500        S    2
    ## 500        0      3   male 24.00000     0     0   7.7958        S    2
    ## 501        0      3   male 17.00000     0     0   8.6625        S    1
    ## 502        0      3 female 21.00000     0     0   7.7500        Q    2
    ## 503        0      3 female 29.69912     0     0   7.6292        Q    2
    ## 504        0      3 female 37.00000     0     0   9.5875        S    3
    ## 505        1      1 female 16.00000     0     0  86.5000        S    1
    ## 506        0      1   male 18.00000     1     0 108.9000        C    1
    ## 507        1      2 female 33.00000     0     2  26.0000        S    3
    ## 508        1      1   male 29.69912     0     0  26.5500        S    2
    ## 509        0      3   male 28.00000     0     0  22.5250        S    2
    ## 510        1      3   male 26.00000     0     0  56.4958        S    2
    ## 511        1      3   male 29.00000     0     0   7.7500        Q    2
    ## 512        0      3   male 29.69912     0     0   8.0500        S    2
    ## 513        1      1   male 36.00000     0     0  26.2875        S    3
    ## 514        1      1 female 54.00000     1     0  59.4000        C    5
    ## 515        0      3   male 24.00000     0     0   7.4958        S    2
    ## 516        0      1   male 47.00000     0     0  34.0208        S    4
    ## 517        1      2 female 34.00000     0     0  10.5000        S    3
    ## 518        0      3   male 29.69912     0     0  24.1500        Q    2
    ## 519        1      2 female 36.00000     1     0  26.0000        S    3
    ## 520        0      3   male 32.00000     0     0   7.8958        S    3
    ## 521        1      1 female 30.00000     0     0  93.5000        S    2
    ## 522        0      3   male 22.00000     0     0   7.8958        S    2
    ## 523        0      3   male 29.69912     0     0   7.2250        C    2
    ## 524        1      1 female 44.00000     0     1  57.9792        C    4
    ## 525        0      3   male 29.69912     0     0   7.2292        C    2
    ## 526        0      3   male 40.50000     0     0   7.7500        Q    4
    ## 527        1      2 female 50.00000     0     0  10.5000        S    4
    ## 528        0      1   male 29.69912     0     0 221.7792        S    2
    ## 529        0      3   male 39.00000     0     0   7.9250        S    3
    ## 530        0      2   male 23.00000     2     1  11.5000        S    2
    ## 531        1      2 female  2.00000     1     1  26.0000        S    0
    ## 532        0      3   male 29.69912     0     0   7.2292        C    2
    ## 533        0      3   male 17.00000     1     1   7.2292        C    1
    ## 534        1      3 female 29.69912     0     2  22.3583        C    2
    ## 535        0      3 female 30.00000     0     0   8.6625        S    2
    ## 536        1      2 female  7.00000     0     2  26.2500        S    0
    ## 537        0      1   male 45.00000     0     0  26.5500        S    4
    ## 538        1      1 female 30.00000     0     0 106.4250        C    2
    ## 539        0      3   male 29.69912     0     0  14.5000        S    2
    ## 540        1      1 female 22.00000     0     2  49.5000        C    2
    ## 541        1      1 female 36.00000     0     2  71.0000        S    3
    ## 542        0      3 female  9.00000     4     2  31.2750        S    0
    ## 543        0      3 female 11.00000     4     2  31.2750        S    1
    ## 544        1      2   male 32.00000     1     0  26.0000        S    3
    ## 545        0      1   male 50.00000     1     0 106.4250        C    4
    ## 546        0      1   male 64.00000     0     0  26.0000        S    6
    ## 547        1      2 female 19.00000     1     0  26.0000        S    1
    ## 548        1      2   male 29.69912     0     0  13.8625        C    2
    ## 549        0      3   male 33.00000     1     1  20.5250        S    3
    ## 550        1      2   male  8.00000     1     1  36.7500        S    0
    ## 551        1      1   male 17.00000     0     2 110.8833        C    1
    ## 552        0      2   male 27.00000     0     0  26.0000        S    2
    ## 553        0      3   male 29.69912     0     0   7.8292        Q    2
    ## 554        1      3   male 22.00000     0     0   7.2250        C    2
    ## 555        1      3 female 22.00000     0     0   7.7750        S    2
    ## 556        0      1   male 62.00000     0     0  26.5500        S    6
    ## 557        1      1 female 48.00000     1     0  39.6000        C    4
    ## 558        0      1   male 29.69912     0     0 227.5250        C    2
    ## 559        1      1 female 39.00000     1     1  79.6500        S    3
    ## 560        1      3 female 36.00000     1     0  17.4000        S    3
    ## 561        0      3   male 29.69912     0     0   7.7500        Q    2
    ## 562        0      3   male 40.00000     0     0   7.8958        S    3
    ## 563        0      2   male 28.00000     0     0  13.5000        S    2
    ## 564        0      3   male 29.69912     0     0   8.0500        S    2
    ## 565        0      3 female 29.69912     0     0   8.0500        S    2
    ## 566        0      3   male 24.00000     2     0  24.1500        S    2
    ## 567        0      3   male 19.00000     0     0   7.8958        S    1
    ## 568        0      3 female 29.00000     0     4  21.0750        S    2
    ## 569        0      3   male 29.69912     0     0   7.2292        C    2
    ## 570        1      3   male 32.00000     0     0   7.8542        S    3
    ## 571        1      2   male 62.00000     0     0  10.5000        S    6
    ## 572        1      1 female 53.00000     2     0  51.4792        S    5
    ## 573        1      1   male 36.00000     0     0  26.3875        S    3
    ## 574        1      3 female 29.69912     0     0   7.7500        Q    2
    ## 575        0      3   male 16.00000     0     0   8.0500        S    1
    ## 576        0      3   male 19.00000     0     0  14.5000        S    1
    ## 577        1      2 female 34.00000     0     0  13.0000        S    3
    ## 578        1      1 female 39.00000     1     0  55.9000        S    3
    ## 579        0      3 female 29.69912     1     0  14.4583        C    2
    ## 580        1      3   male 32.00000     0     0   7.9250        S    3
    ## 581        1      2 female 25.00000     1     1  30.0000        S    2
    ## 582        1      1 female 39.00000     1     1 110.8833        C    3
    ## 583        0      2   male 54.00000     0     0  26.0000        S    5
    ## 584        0      1   male 36.00000     0     0  40.1250        C    3
    ## 585        0      3   male 29.69912     0     0   8.7125        C    2
    ## 586        1      1 female 18.00000     0     2  79.6500        S    1
    ## 587        0      2   male 47.00000     0     0  15.0000        S    4
    ## 588        1      1   male 60.00000     1     1  79.2000        C    5
    ## 589        0      3   male 22.00000     0     0   8.0500        S    2
    ## 590        0      3   male 29.69912     0     0   8.0500        S    2
    ## 591        0      3   male 35.00000     0     0   7.1250        S    3
    ## 592        1      1 female 52.00000     1     0  78.2667        C    5
    ## 593        0      3   male 47.00000     0     0   7.2500        S    4
    ## 594        0      3 female 29.69912     0     2   7.7500        Q    2
    ## 595        0      2   male 37.00000     1     0  26.0000        S    3
    ## 596        0      3   male 36.00000     1     1  24.1500        S    3
    ## 597        1      2 female 29.69912     0     0  33.0000        S    2
    ## 598        0      3   male 49.00000     0     0   0.0000        S    4
    ## 599        0      3   male 29.69912     0     0   7.2250        C    2
    ## 600        1      1   male 49.00000     1     0  56.9292        C    4
    ## 601        1      2 female 24.00000     2     1  27.0000        S    2
    ## 602        0      3   male 29.69912     0     0   7.8958        S    2
    ## 603        0      1   male 29.69912     0     0  42.4000        S    2
    ## 604        0      3   male 44.00000     0     0   8.0500        S    4
    ## 605        1      1   male 35.00000     0     0  26.5500        C    3
    ## 606        0      3   male 36.00000     1     0  15.5500        S    3
    ## 607        0      3   male 30.00000     0     0   7.8958        S    2
    ## 608        1      1   male 27.00000     0     0  30.5000        S    2
    ## 609        1      2 female 22.00000     1     2  41.5792        C    2
    ## 610        1      1 female 40.00000     0     0 153.4625        S    3
    ## 611        0      3 female 39.00000     1     5  31.2750        S    3
    ## 612        0      3   male 29.69912     0     0   7.0500        S    2
    ## 613        1      3 female 29.69912     1     0  15.5000        Q    2
    ## 614        0      3   male 29.69912     0     0   7.7500        Q    2
    ## 615        0      3   male 35.00000     0     0   8.0500        S    3
    ## 616        1      2 female 24.00000     1     2  65.0000        S    2
    ## 617        0      3   male 34.00000     1     1  14.4000        S    3
    ## 618        0      3 female 26.00000     1     0  16.1000        S    2
    ## 619        1      2 female  4.00000     2     1  39.0000        S    0
    ## 620        0      2   male 26.00000     0     0  10.5000        S    2
    ## 621        0      3   male 27.00000     1     0  14.4542        C    2
    ## 622        1      1   male 42.00000     1     0  52.5542        S    4
    ## 623        1      3   male 20.00000     1     1  15.7417        C    1
    ## 624        0      3   male 21.00000     0     0   7.8542        S    2
    ## 625        0      3   male 21.00000     0     0  16.1000        S    2
    ## 626        0      1   male 61.00000     0     0  32.3208        S    6
    ## 627        0      2   male 57.00000     0     0  12.3500        Q    5
    ## 628        1      1 female 21.00000     0     0  77.9583        S    2
    ## 629        0      3   male 26.00000     0     0   7.8958        S    2
    ## 630        0      3   male 29.69912     0     0   7.7333        Q    2
    ## 631        1      1   male 80.00000     0     0  30.0000        S    7
    ## 632        0      3   male 51.00000     0     0   7.0542        S    5
    ## 633        1      1   male 32.00000     0     0  30.5000        C    3
    ## 634        0      1   male 29.69912     0     0   0.0000        S    2
    ## 635        0      3 female  9.00000     3     2  27.9000        S    0
    ## 636        1      2 female 28.00000     0     0  13.0000        S    2
    ## 637        0      3   male 32.00000     0     0   7.9250        S    3
    ## 638        0      2   male 31.00000     1     1  26.2500        S    3
    ## 639        0      3 female 41.00000     0     5  39.6875        S    4
    ## 640        0      3   male 29.69912     1     0  16.1000        S    2
    ## 641        0      3   male 20.00000     0     0   7.8542        S    1
    ## 642        1      1 female 24.00000     0     0  69.3000        C    2
    ## 643        0      3 female  2.00000     3     2  27.9000        S    0
    ## 644        1      3   male 29.69912     0     0  56.4958        S    2
    ## 645        1      3 female  0.75000     2     1  19.2583        C    0
    ## 646        1      1   male 48.00000     1     0  76.7292        C    4
    ## 647        0      3   male 19.00000     0     0   7.8958        S    1
    ## 648        1      1   male 56.00000     0     0  35.5000        C    5
    ## 649        0      3   male 29.69912     0     0   7.5500        S    2
    ## 650        1      3 female 23.00000     0     0   7.5500        S    2
    ## 651        0      3   male 29.69912     0     0   7.8958        S    2
    ## 652        1      2 female 18.00000     0     1  23.0000        S    1
    ## 653        0      3   male 21.00000     0     0   8.4333        S    2
    ## 654        1      3 female 29.69912     0     0   7.8292        Q    2
    ## 655        0      3 female 18.00000     0     0   6.7500        Q    1
    ## 656        0      2   male 24.00000     2     0  73.5000        S    2
    ## 657        0      3   male 29.69912     0     0   7.8958        S    2
    ## 658        0      3 female 32.00000     1     1  15.5000        Q    3
    ## 659        0      2   male 23.00000     0     0  13.0000        S    2
    ## 660        0      1   male 58.00000     0     2 113.2750        C    5
    ## 661        1      1   male 50.00000     2     0 133.6500        S    4
    ## 662        0      3   male 40.00000     0     0   7.2250        C    3
    ## 663        0      1   male 47.00000     0     0  25.5875        S    4
    ## 664        0      3   male 36.00000     0     0   7.4958        S    3
    ## 665        1      3   male 20.00000     1     0   7.9250        S    1
    ## 666        0      2   male 32.00000     2     0  73.5000        S    3
    ## 667        0      2   male 25.00000     0     0  13.0000        S    2
    ## 668        0      3   male 29.69912     0     0   7.7750        S    2
    ## 669        0      3   male 43.00000     0     0   8.0500        S    4
    ## 670        1      1 female 29.69912     1     0  52.0000        S    2
    ## 671        1      2 female 40.00000     1     1  39.0000        S    3
    ## 672        0      1   male 31.00000     1     0  52.0000        S    3
    ## 673        0      2   male 70.00000     0     0  10.5000        S    6
    ## 674        1      2   male 31.00000     0     0  13.0000        S    3
    ## 675        0      2   male 29.69912     0     0   0.0000        S    2
    ## 676        0      3   male 18.00000     0     0   7.7750        S    1
    ## 677        0      3   male 24.50000     0     0   8.0500        S    2
    ## 678        1      3 female 18.00000     0     0   9.8417        S    1
    ## 679        0      3 female 43.00000     1     6  46.9000        S    4
    ## 680        1      1   male 36.00000     0     1 512.3292        C    3
    ## 681        0      3 female 29.69912     0     0   8.1375        Q    2
    ## 682        1      1   male 27.00000     0     0  76.7292        C    2
    ## 683        0      3   male 20.00000     0     0   9.2250        S    1
    ## 684        0      3   male 14.00000     5     2  46.9000        S    1
    ## 685        0      2   male 60.00000     1     1  39.0000        S    5
    ## 686        0      2   male 25.00000     1     2  41.5792        C    2
    ## 687        0      3   male 14.00000     4     1  39.6875        S    1
    ## 688        0      3   male 19.00000     0     0  10.1708        S    1
    ## 689        0      3   male 18.00000     0     0   7.7958        S    1
    ## 690        1      1 female 15.00000     0     1 211.3375        S    1
    ## 691        1      1   male 31.00000     1     0  57.0000        S    3
    ## 692        1      3 female  4.00000     0     1  13.4167        C    0
    ## 693        1      3   male 29.69912     0     0  56.4958        S    2
    ## 694        0      3   male 25.00000     0     0   7.2250        C    2
    ## 695        0      1   male 60.00000     0     0  26.5500        S    5
    ## 696        0      2   male 52.00000     0     0  13.5000        S    5
    ## 697        0      3   male 44.00000     0     0   8.0500        S    4
    ## 698        1      3 female 29.69912     0     0   7.7333        Q    2
    ## 699        0      1   male 49.00000     1     1 110.8833        C    4
    ## 700        0      3   male 42.00000     0     0   7.6500        S    4
    ## 701        1      1 female 18.00000     1     0 227.5250        C    1
    ## 702        1      1   male 35.00000     0     0  26.2875        S    3
    ## 703        0      3 female 18.00000     0     1  14.4542        C    1
    ## 704        0      3   male 25.00000     0     0   7.7417        Q    2
    ## 705        0      3   male 26.00000     1     0   7.8542        S    2
    ## 706        0      2   male 39.00000     0     0  26.0000        S    3
    ## 707        1      2 female 45.00000     0     0  13.5000        S    4
    ## 708        1      1   male 42.00000     0     0  26.2875        S    4
    ## 709        1      1 female 22.00000     0     0 151.5500        S    2
    ## 710        1      3   male 29.69912     1     1  15.2458        C    2
    ## 711        1      1 female 24.00000     0     0  49.5042        C    2
    ## 712        0      1   male 29.69912     0     0  26.5500        S    2
    ## 713        1      1   male 48.00000     1     0  52.0000        S    4
    ## 714        0      3   male 29.00000     0     0   9.4833        S    2
    ## 715        0      2   male 52.00000     0     0  13.0000        S    5
    ## 716        0      3   male 19.00000     0     0   7.6500        S    1
    ## 717        1      1 female 38.00000     0     0 227.5250        C    3
    ## 718        1      2 female 27.00000     0     0  10.5000        S    2
    ## 719        0      3   male 29.69912     0     0  15.5000        Q    2
    ## 720        0      3   male 33.00000     0     0   7.7750        S    3
    ## 721        1      2 female  6.00000     0     1  33.0000        S    0
    ## 722        0      3   male 17.00000     1     0   7.0542        S    1
    ## 723        0      2   male 34.00000     0     0  13.0000        S    3
    ## 724        0      2   male 50.00000     0     0  13.0000        S    4
    ## 725        1      1   male 27.00000     1     0  53.1000        S    2
    ## 726        0      3   male 20.00000     0     0   8.6625        S    1
    ## 727        1      2 female 30.00000     3     0  21.0000        S    2
    ## 728        1      3 female 29.69912     0     0   7.7375        Q    2
    ## 729        0      2   male 25.00000     1     0  26.0000        S    2
    ## 730        0      3 female 25.00000     1     0   7.9250        S    2
    ## 731        1      1 female 29.00000     0     0 211.3375        S    2
    ## 732        0      3   male 11.00000     0     0  18.7875        C    1
    ## 733        0      2   male 29.69912     0     0   0.0000        S    2
    ## 734        0      2   male 23.00000     0     0  13.0000        S    2
    ## 735        0      2   male 23.00000     0     0  13.0000        S    2
    ## 736        0      3   male 28.50000     0     0  16.1000        S    2
    ## 737        0      3 female 48.00000     1     3  34.3750        S    4
    ## 738        1      1   male 35.00000     0     0 512.3292        C    3
    ## 739        0      3   male 29.69912     0     0   7.8958        S    2
    ## 740        0      3   male 29.69912     0     0   7.8958        S    2
    ## 741        1      1   male 29.69912     0     0  30.0000        S    2
    ## 742        0      1   male 36.00000     1     0  78.8500        S    3
    ## 743        1      1 female 21.00000     2     2 262.3750        C    2
    ## 744        0      3   male 24.00000     1     0  16.1000        S    2
    ## 745        1      3   male 31.00000     0     0   7.9250        S    3
    ## 746        0      1   male 70.00000     1     1  71.0000        S    6
    ## 747        0      3   male 16.00000     1     1  20.2500        S    1
    ## 748        1      2 female 30.00000     0     0  13.0000        S    2
    ## 749        0      1   male 19.00000     1     0  53.1000        S    1
    ## 750        0      3   male 31.00000     0     0   7.7500        Q    3
    ## 751        1      2 female  4.00000     1     1  23.0000        S    0
    ## 752        1      3   male  6.00000     0     1  12.4750        S    0
    ## 753        0      3   male 33.00000     0     0   9.5000        S    3
    ## 754        0      3   male 23.00000     0     0   7.8958        S    2
    ## 755        1      2 female 48.00000     1     2  65.0000        S    4
    ## 756        1      2   male  0.67000     1     1  14.5000        S    0
    ## 757        0      3   male 28.00000     0     0   7.7958        S    2
    ## 758        0      2   male 18.00000     0     0  11.5000        S    1
    ## 759        0      3   male 34.00000     0     0   8.0500        S    3
    ## 760        1      1 female 33.00000     0     0  86.5000        S    3
    ## 761        0      3   male 29.69912     0     0  14.5000        S    2
    ## 762        0      3   male 41.00000     0     0   7.1250        S    4
    ## 763        1      3   male 20.00000     0     0   7.2292        C    1
    ## 764        1      1 female 36.00000     1     2 120.0000        S    3
    ## 765        0      3   male 16.00000     0     0   7.7750        S    1
    ## 766        1      1 female 51.00000     1     0  77.9583        S    5
    ## 767        0      1   male 29.69912     0     0  39.6000        C    2
    ## 768        0      3 female 30.50000     0     0   7.7500        Q    3
    ## 769        0      3   male 29.69912     1     0  24.1500        Q    2
    ## 770        0      3   male 32.00000     0     0   8.3625        S    3
    ## 771        0      3   male 24.00000     0     0   9.5000        S    2
    ## 772        0      3   male 48.00000     0     0   7.8542        S    4
    ## 773        0      2 female 57.00000     0     0  10.5000        S    5
    ## 774        0      3   male 29.69912     0     0   7.2250        C    2
    ## 775        1      2 female 54.00000     1     3  23.0000        S    5
    ## 776        0      3   male 18.00000     0     0   7.7500        S    1
    ## 777        0      3   male 29.69912     0     0   7.7500        Q    2
    ## 778        1      3 female  5.00000     0     0  12.4750        S    0
    ## 779        0      3   male 29.69912     0     0   7.7375        Q    2
    ## 780        1      1 female 43.00000     0     1 211.3375        S    4
    ## 781        1      3 female 13.00000     0     0   7.2292        C    1
    ## 782        1      1 female 17.00000     1     0  57.0000        S    1
    ## 783        0      1   male 29.00000     0     0  30.0000        S    2
    ## 784        0      3   male 29.69912     1     2  23.4500        S    2
    ## 785        0      3   male 25.00000     0     0   7.0500        S    2
    ## 786        0      3   male 25.00000     0     0   7.2500        S    2
    ## 787        1      3 female 18.00000     0     0   7.4958        S    1
    ## 788        0      3   male  8.00000     4     1  29.1250        Q    0
    ## 789        1      3   male  1.00000     1     2  20.5750        S    0
    ## 790        0      1   male 46.00000     0     0  79.2000        C    4
    ## 791        0      3   male 29.69912     0     0   7.7500        Q    2
    ## 792        0      2   male 16.00000     0     0  26.0000        S    1
    ## 793        0      3 female 29.69912     8     2  69.5500        S    2
    ## 794        0      1   male 29.69912     0     0  30.6958        C    2
    ## 795        0      3   male 25.00000     0     0   7.8958        S    2
    ## 796        0      2   male 39.00000     0     0  13.0000        S    3
    ## 797        1      1 female 49.00000     0     0  25.9292        S    4
    ## 798        1      3 female 31.00000     0     0   8.6833        S    3
    ## 799        0      3   male 30.00000     0     0   7.2292        C    2
    ## 800        0      3 female 30.00000     1     1  24.1500        S    2
    ## 801        0      2   male 34.00000     0     0  13.0000        S    3
    ## 802        1      2 female 31.00000     1     1  26.2500        S    3
    ## 803        1      1   male 11.00000     1     2 120.0000        S    1
    ## 804        1      3   male  0.42000     0     1   8.5167        C    0
    ## 805        1      3   male 27.00000     0     0   6.9750        S    2
    ## 806        0      3   male 31.00000     0     0   7.7750        S    3
    ## 807        0      1   male 39.00000     0     0   0.0000        S    3
    ## 808        0      3 female 18.00000     0     0   7.7750        S    1
    ## 809        0      2   male 39.00000     0     0  13.0000        S    3
    ## 810        1      1 female 33.00000     1     0  53.1000        S    3
    ## 811        0      3   male 26.00000     0     0   7.8875        S    2
    ## 812        0      3   male 39.00000     0     0  24.1500        S    3
    ## 813        0      2   male 35.00000     0     0  10.5000        S    3
    ## 814        0      3 female  6.00000     4     2  31.2750        S    0
    ## 815        0      3   male 30.50000     0     0   8.0500        S    3
    ## 816        0      1   male 29.69912     0     0   0.0000        S    2
    ## 817        0      3 female 23.00000     0     0   7.9250        S    2
    ## 818        0      2   male 31.00000     1     1  37.0042        C    3
    ## 819        0      3   male 43.00000     0     0   6.4500        S    4
    ## 820        0      3   male 10.00000     3     2  27.9000        S    0
    ## 821        1      1 female 52.00000     1     1  93.5000        S    5
    ## 822        1      3   male 27.00000     0     0   8.6625        S    2
    ## 823        0      1   male 38.00000     0     0   0.0000        S    3
    ## 824        1      3 female 27.00000     0     1  12.4750        S    2
    ## 825        0      3   male  2.00000     4     1  39.6875        S    0
    ## 826        0      3   male 29.69912     0     0   6.9500        Q    2
    ## 827        0      3   male 29.69912     0     0  56.4958        S    2
    ## 828        1      2   male  1.00000     0     2  37.0042        C    0
    ## 829        1      3   male 29.69912     0     0   7.7500        Q    2
    ## 830        1      1 female 62.00000     0     0  80.0000             6
    ## 831        1      3 female 15.00000     1     0  14.4542        C    1
    ## 832        1      2   male  0.83000     1     1  18.7500        S    0
    ## 833        0      3   male 29.69912     0     0   7.2292        C    2
    ## 834        0      3   male 23.00000     0     0   7.8542        S    2
    ## 835        0      3   male 18.00000     0     0   8.3000        S    1
    ## 836        1      1 female 39.00000     1     1  83.1583        C    3
    ## 837        0      3   male 21.00000     0     0   8.6625        S    2
    ## 838        0      3   male 29.69912     0     0   8.0500        S    2
    ## 839        1      3   male 32.00000     0     0  56.4958        S    3
    ## 840        1      1   male 29.69912     0     0  29.7000        C    2
    ## 841        0      3   male 20.00000     0     0   7.9250        S    1
    ## 842        0      2   male 16.00000     0     0  10.5000        S    1
    ## 843        1      1 female 30.00000     0     0  31.0000        C    2
    ## 844        0      3   male 34.50000     0     0   6.4375        C    3
    ## 845        0      3   male 17.00000     0     0   8.6625        S    1
    ## 846        0      3   male 42.00000     0     0   7.5500        S    4
    ## 847        0      3   male 29.69912     8     2  69.5500        S    2
    ## 848        0      3   male 35.00000     0     0   7.8958        C    3
    ## 849        0      2   male 28.00000     0     1  33.0000        S    2
    ## 850        1      1 female 29.69912     1     0  89.1042        C    2
    ## 851        0      3   male  4.00000     4     2  31.2750        S    0
    ## 852        0      3   male 74.00000     0     0   7.7750        S    7
    ## 853        0      3 female  9.00000     1     1  15.2458        C    0
    ## 854        1      1 female 16.00000     0     1  39.4000        S    1
    ## 855        0      2 female 44.00000     1     0  26.0000        S    4
    ## 856        1      3 female 18.00000     0     1   9.3500        S    1
    ## 857        1      1 female 45.00000     1     1 164.8667        S    4
    ## 858        1      1   male 51.00000     0     0  26.5500        S    5
    ## 859        1      3 female 24.00000     0     3  19.2583        C    2
    ## 860        0      3   male 29.69912     0     0   7.2292        C    2
    ## 861        0      3   male 41.00000     2     0  14.1083        S    4
    ## 862        0      2   male 21.00000     1     0  11.5000        S    2
    ## 863        1      1 female 48.00000     0     0  25.9292        S    4
    ## 864        0      3 female 29.69912     8     2  69.5500        S    2
    ## 865        0      2   male 24.00000     0     0  13.0000        S    2
    ## 866        1      2 female 42.00000     0     0  13.0000        S    4
    ## 867        1      2 female 27.00000     1     0  13.8583        C    2
    ## 868        0      1   male 31.00000     0     0  50.4958        S    3
    ## 869        0      3   male 29.69912     0     0   9.5000        S    2
    ## 870        1      3   male  4.00000     1     1  11.1333        S    0
    ## 871        0      3   male 26.00000     0     0   7.8958        S    2
    ## 872        1      1 female 47.00000     1     1  52.5542        S    4
    ## 873        0      1   male 33.00000     0     0   5.0000        S    3
    ## 874        0      3   male 47.00000     0     0   9.0000        S    4
    ## 875        1      2 female 28.00000     1     0  24.0000        C    2
    ## 876        1      3 female 15.00000     0     0   7.2250        C    1
    ## 877        0      3   male 20.00000     0     0   9.8458        S    1
    ## 878        0      3   male 19.00000     0     0   7.8958        S    1
    ## 879        0      3   male 29.69912     0     0   7.8958        S    2
    ## 880        1      1 female 56.00000     0     1  83.1583        C    5
    ## 881        1      2 female 25.00000     0     1  26.0000        S    2
    ## 882        0      3   male 33.00000     0     0   7.8958        S    3
    ## 883        0      3 female 22.00000     0     0  10.5167        S    2
    ## 884        0      2   male 28.00000     0     0  10.5000        S    2
    ## 885        0      3   male 25.00000     0     0   7.0500        S    2
    ## 886        0      3 female 39.00000     0     5  29.1250        Q    3
    ## 887        0      2   male 27.00000     0     0  13.0000        S    2
    ## 888        1      1 female 19.00000     0     0  30.0000        S    1
    ## 889        0      3 female 29.69912     1     2  23.4500        S    2
    ## 890        1      1   male 26.00000     0     0  30.0000        C    2
    ## 891        0      3   male 32.00000     0     0   7.7500        Q    3

Question 23
-----------

``` r
plot(titanic$Embarked)
```

![](hw-1_files/figure-markdown_github/unnamed-chunk-26-1.png)

``` r
levels(titanic$Embarked)[1] <- "S"
```
