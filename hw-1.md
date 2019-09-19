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
S1 = sum(x)
S2 = sum(x^2)
S3 = sum(x^x)
y <- c(1,-1)
S4 = sum((x^x)*y)
```

    ## Warning in (x^x) * y: longer object length is not a multiple of shorter
    ## object length

``` r
S5 = sum(x^-2)
S6 = sum(x^-1)
S7 = sum(x^-3)
S8 = sum((x^-1)*y)
```

    ## Warning in (x^-1) * y: longer object length is not a multiple of shorter
    ## object length

Question 2
----------

``` r
x <- rnorm(1000,mean=10,sd=1)
mean(x)
```

    ## [1] 10.03738

``` r
sd(x)
```

    ## [1] 0.9525169

``` r
sum(x>10)
```

    ## [1] 524

``` r
#hist(x)
x <- rnorm(1000,mean=2,sd=1)
sum(x>1)/1000
```

    ## [1] 0.831

Question 3
----------

``` r
x <- sample(c(1:6),1000,replace = TRUE)
mean(x)
```

    ## [1] 3.506

``` r
sd(x)
```

    ## [1] 1.738098

``` r
sum(x==6)
```

    ## [1] 171

``` r
table(x)
```

    ## x
    ##   1   2   3   4   5   6 
    ## 180 159 150 168 172 171

``` r
#prop.table(table(x))
#hist(x)
```

Question 4a
-----------

``` r
x1 = sample(c(1:6), 1000, replace=TRUE)
x2 = sample(c(1:6), 1000, replace=TRUE)
x3 = sample(c(1:6), 1000, replace=TRUE)
sum(x1 > x2 +x3)/1000
```

    ## [1] 0.082

Question 4b
-----------

``` r
sum(x1^2 > x2^2 +x3^2)/ 1000
```

    ## [1] 0.216

Question 5
----------

``` r
m <- matrix(sample(c(0,1),3000, replace = TRUE), ncol = 3)
sum(rowSums(m)==3)/3000
```

    ## [1] 0.04433333

Question 6
----------

``` r
#m <- matrix(sample(c(0,1),10000, replace = TRUE), ncol = 10)
#for (n in 1000){
#for (i in 8){
# if(sum(m[n,i:(i+2)])==0){
#  t = t + 1
#  i = i + 1 #trying to make sure it's exactly three in a row
# }}}
#t/1000
```

Question 7
----------

``` r
m <- matrix(rep(runif(1000, min = 0, max = 1),100), nrow = 100)
x <- rowMeans(m,na.rm = FALSE, dims = 1)
h <- hist(x)
```

![](hw-1_files/figure-markdown_github/unnamed-chunk-9-1.png)

``` r
n <- matrix(rep(rpois(1000,lambda = 12),100),nrow = 100)
y <-  rowMeans(n,na.rm = FALSE, dims = 1)
i <- hist(y)
```

![](hw-1_files/figure-markdown_github/unnamed-chunk-9-2.png)

``` r
o <- matrix(rep(rbinom(1000,1000,.5),100),nrow = 100)
z <-  rowMeans(o,na.rm = FALSE, dims = 1)
s <- hist(z)
```

![](hw-1_files/figure-markdown_github/unnamed-chunk-9-3.png) \#\# Question 7

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
sum(is.na(titanic))
```

    ## [1] 177

``` r
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
titanic <- cbind(titanic, sfare)
```

Question 21
-----------

``` r
cfare <- ifelse(titanic$Fare < mean(titanic$Fare), c("cheap"), c("expensive"))
titanic <- cbind(titanic, cfare)
```

Question 22
-----------

``` r
attach(titanic)
```

    ## The following objects are masked _by_ .GlobalEnv:
    ## 
    ##     cfare, sfare

``` r
titanic$cage[titanic$Age <= 10] <- 0
titanic$cage[titanic$Age > 10 & titanic$Age <= 20] <- 1
titanic$cage[titanic$Age > 20 & titanic$Age <= 30] <- 2
titanic$cage[titanic$Age > 30 & titanic$Age <= 40] <- 3
titanic$cage[titanic$Age > 40 & titanic$Age <= 50] <- 4
titanic$cage[titanic$Age > 50 & titanic$Age <= 60] <- 5
titanic$cage[titanic$Age > 60 & titanic$Age <= 70] <- 6
titanic$cage[titanic$Age > 70 & titanic$Age <= 80] <- 7
detach(titanic)
```

Question 23
-----------

``` r
plot(titanic$Embarked)
```

![](hw-1_files/figure-markdown_github/unnamed-chunk-26-1.png)

``` r
levels(titanic$Embarked)[1] <- "S"
```
