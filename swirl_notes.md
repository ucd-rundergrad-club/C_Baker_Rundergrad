---
title: "Swirl Notes"
author: "Cassandra"
date: "July 10, 2019"
output: 
  html_document: 
    keep_md: yes
---



Use `bye()` to exit swirl and save progress.   
Use `info()` to display options for swirl.

## R Programming

### 1. Basic Building Blocks

Values can be assigned into variables and stored for later use. 

```r
x <- 5 + 7
x
```

```
## [1] 12
```

Vectors of numbers can also be stored in R.

```r
z <- c(1.1, 9, 3.14)
z
```

```
## [1] 1.10 9.00 3.14
```

Vectors can then be combined into new vectors or used for calculations.

```r
c(z, 555, z)
```

```
## [1]   1.10   9.00   3.14 555.00   1.10   9.00   3.14
```

```r
z*2 + 100
```

```
## [1] 102.20 118.00 106.28
```

Common operators  

* `+` = addition  
* `-` = subtraction  
* `*` = multiplication  
* `/` = division  
* `^` = exponents  
* `sqrt()` = square root  
* `abs()` = absolute value   

**Note:** When working with vectors, R will perform operations element by element. If two vectors are different lengths though, R will recycle the shorter vector. 

```r
long <- c(1, 2, 3, 4)
short <- c(0, 10)

long + short
```

```
## [1]  1 12  3 14
```

### 3. Sequences of Numbers

Creating a basic sequence of numbers: 

```r
1:20 
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
```

```r
seq(1, 20)
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
```

`seq` can also specify increments other than the default of 1.

```r
seq(0, 10, by = 0.5)
```

```
##  [1]  0.0  0.5  1.0  1.5  2.0  2.5  3.0  3.5  4.0  4.5  5.0  5.5  6.0  6.5
## [15]  7.0  7.5  8.0  8.5  9.0  9.5 10.0
```

Make a sequence of a certain length:

```r
my_seq <- seq(5, 10, length = 30)
length(my_seq)
```

```
## [1] 30
```

Make a sequence the length of another vector:

```r
1:length(my_seq)
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23
## [24] 24 25 26 27 28 29 30
```

```r
seq(along.with = my_seq)
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23
## [24] 24 25 26 27 28 29 30
```

```r
seq_along(my_seq)
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23
## [24] 24 25 26 27 28 29 30
```

create vectors using `rep()`: 

```r
# repeat something in order a specific number of times
rep(0, times = 40)
```

```
##  [1] 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
## [36] 0 0 0 0 0
```

```r
rep(c(0, 1, 2), times = 10)
```

```
##  [1] 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2
```

```r
# repeat each thing a specific number of times
rep(c(0, 1, 2), each = 10)
```

```
##  [1] 0 0 0 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1 1 1 2 2 2 2 2 2 2 2 2 2
```

### 4. Vectors

Atomic vectors contain one data type while lists may contain multiple data types.

```r
num_vect <- c(0.5, 55, -10, 6)
(tf <- num_vect < 1)
```

```
## [1]  TRUE FALSE  TRUE FALSE
```

Logical operators

* `<` = less than
* `>` = greater than
* `<=` = less than or equal to
* `>=` = greater than or equal to
* `==` = equal to 
* `!=` = not equal to 
* `|` = or
* `&` = and
* `!` = not 

Use `"` to notate characters.

```r
my_char <- c("My", "name", "is")
```

Vectors can also be collapsed or manipulated later.

```r
# combine multiple vector elements into one element
paste(my_char, collapse = " ")
```

```
## [1] "My name is"
```

```r
# add a new element to the original vector
my_name <- c(my_char, "calbaker")
# and combine again 
paste(my_name, collapse = " ")
```

```
## [1] "My name is calbaker"
```

Use `paste` to join multiple vectors together. Recycling will occur here as well.

```r
paste(1:3, c("X", "Y", "Z"), sep = "")
```

```
## [1] "1X" "2Y" "3Z"
```

```r
paste(LETTERS, 1:4, sep = "-")
```

```
##  [1] "A-1" "B-2" "C-3" "D-4" "E-1" "F-2" "G-3" "H-4" "I-1" "J-2" "K-3"
## [12] "L-4" "M-1" "N-2" "O-3" "P-4" "Q-1" "R-2" "S-3" "T-4" "U-1" "V-2"
## [23] "W-3" "X-4" "Y-1" "Z-2"
```

### 5. Missing Values 

`NA` represents missing or unavailable values. Operations involving `NA` will typically return `NA`. 

```r
x <- c(44, NA, 5, NA)
x*3
```

```
## [1] 132  NA  15  NA
```

Additional practice with `NA`:

```r
# draw 1000 numbers from normal distribution
y <- rnorm(1000)
# make vector containing 1000 NAs
z <- rep(NA, 1000)
# randomly select 100 elements from the two vectors above
my_data <- sample(c(y, z), 100)

# where are the NA values?
(my_na <- is.na(my_data))
```

```
##   [1] FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE  TRUE
##  [12] FALSE  TRUE FALSE  TRUE  TRUE FALSE FALSE  TRUE  TRUE FALSE  TRUE
##  [23]  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE
##  [34] FALSE  TRUE FALSE  TRUE FALSE FALSE  TRUE  TRUE FALSE FALSE  TRUE
##  [45] FALSE FALSE  TRUE  TRUE  TRUE FALSE  TRUE FALSE FALSE FALSE  TRUE
##  [56]  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE FALSE  TRUE  TRUE FALSE
##  [67] FALSE FALSE  TRUE  TRUE FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE
##  [78] FALSE  TRUE FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE FALSE  TRUE
##  [89] FALSE FALSE  TRUE  TRUE  TRUE FALSE FALSE FALSE  TRUE FALSE  TRUE
## [100] FALSE
```

```r
# how many NA values?
sum(my_na)
```

```
## [1] 48
```

`NaN` is another notation in R that stands for 'not a number'. 

```r
0/0
```

```
## [1] NaN
```

### 6. Subsetting Vectors

Useful for only looking at specific elements of a vector. 

```r
x <- sample(c(y, z), 20)

# look at first ten elements of x
x[1:10]
```

```
##  [1] -0.12069832  1.29920753 -0.12048357          NA  0.53791822
##  [6]  0.45963995          NA  0.69192443          NA -0.03200945
```

```r
# only select elements that aren't NA
y <- x[!is.na(x)]
y
```

```
##  [1] -0.12069832  1.29920753 -0.12048357  0.53791822  0.45963995
##  [6]  0.69192443 -0.03200945  1.36897130  1.06210818 -0.46648324
```

Subsetting can be performed to fit multiple criteria at once. 

```r
# subset for values that are positive and not NA
x[!is.na(x) & x > 0]
```

```
## [1] 1.2992075 0.5379182 0.4596399 0.6919244 1.3689713 1.0621082
```

```r
# pull out specific elements from a vector
x[c(3, 5, 7)]
```

```
## [1] -0.1204836  0.5379182         NA
```

```r
# exclude specific elements from a vector
x[c(-2, -10)]
```

```
##  [1] -0.1206983 -0.1204836         NA  0.5379182  0.4596399         NA
##  [7]  0.6919244         NA         NA         NA         NA         NA
## [13]  1.3689713         NA         NA         NA  1.0621082 -0.4664832
```

```r
x[-c(2, 10)]
```

```
##  [1] -0.1206983 -0.1204836         NA  0.5379182  0.4596399         NA
##  [7]  0.6919244         NA         NA         NA         NA         NA
## [13]  1.3689713         NA         NA         NA  1.0621082 -0.4664832
```

Elements within vectors can be named.

```r
# create vector with names
vect <- c(foo = 11, bar = 2, norf = NA)
vect
```

```
##  foo  bar norf 
##   11    2   NA
```

```r
# see the names of a vector
names(vect)
```

```
## [1] "foo"  "bar"  "norf"
```

```r
# or you can add names later
# first create vector without names
vect2 <- c(11, 2, NA)
# then add names
names(vect2) <- c("foo", "bar", "norf")

# same vector? 
identical(vect, vect2)
```

```
## [1] TRUE
```

```r
# subset using names
vect[c("foo", "bar")]
```

```
## foo bar 
##  11   2
```

### 7. Matrices and Data Frames

Matrices can only have one data class while data frames can have many different data classes. 

Matrices can be created from vectors.

```r
# create initial vector
my_vector <- 1:20
dim(my_vector)
```

```
## NULL
```

```r
# change dimensions of vector 
dim(my_vector) <- c(4, 5)
# check new dimensions
dim(my_vector)
```

```
## [1] 4 5
```

```r
attributes(my_vector)
```

```
## $dim
## [1] 4 5
```

```r
# this is now a matrix
class(my_vector)
```

```
## [1] "matrix"
```

```r
my_matrix <- my_vector
```

`matrix()` can also be used to create matrices.

```r
my_matrix2 <- matrix(1:20, 4, 5)
identical(my_matrix, my_matrix2)
```

```
## [1] TRUE
```

Additional information can be added to matrices later.

```r
# create name vector
patients <- c("Bill", "Gina", "Kelly", "Sean")

# combine name vector with information in matrix
cbind(patients, my_matrix)
```

```
##      patients                       
## [1,] "Bill"   "1" "5" "9"  "13" "17"
## [2,] "Gina"   "2" "6" "10" "14" "18"
## [3,] "Kelly"  "3" "7" "11" "15" "19"
## [4,] "Sean"   "4" "8" "12" "16" "20"
```
**Note:** Since matrices can only have one class of data, R coerced the numbers into characters when the character vector was combined with the matrix.

Data frames must be used when there are multiple data classes involved.

```r
# combine name vector and matrix information into data frame
# make the data frame
my_data <- data.frame(patients, my_matrix)
my_data
```

```
##   patients X1 X2 X3 X4 X5
## 1     Bill  1  5  9 13 17
## 2     Gina  2  6 10 14 18
## 3    Kelly  3  7 11 15 19
## 4     Sean  4  8 12 16 20
```

```r
# check that this is a data frame
class(my_data)
```

```
## [1] "data.frame"
```

Additional information can also be added to data frames later.

```r
# create a vector of column names
cnames <- c("patient", "age", "weight", "bp", "rating", "test")

# assign the column names to the data frame
colnames(my_data) <- cnames
my_data
```

```
##   patient age weight bp rating test
## 1    Bill   1      5  9     13   17
## 2    Gina   2      6 10     14   18
## 3   Kelly   3      7 11     15   19
## 4    Sean   4      8 12     16   20
```

### 8. Logic 

Logical expressions evaluate to `TRUE` or `FALSE`.   
Remember the logical operators from section 4 above. 

```r
TRUE == TRUE 
```

```
## [1] TRUE
```

```r
6 < 7
```

```
## [1] TRUE
```

```r
10 <= 10
```

```
## [1] TRUE
```

```r
5 != 7
```

```
## [1] TRUE
```

These expressions can also be nested together to get an overall answer.

```r
(FALSE == TRUE) == FALSE
```

```
## [1] TRUE
```

Using `!` means 'not' and will reverse the answer. 

```r
!(5 == 7)
```

```
## [1] TRUE
```

For 'and' statements, use `&` to evaluate across an entire vector and `&&` to only evaluate the first element of a vector.

```r
TRUE & c(TRUE, FALSE, FALSE) 
```

```
## [1]  TRUE FALSE FALSE
```

```r
TRUE && c(TRUE, FALSE, FALSE)
```

```
## [1] TRUE
```

Similarly, `|` evaluates 'or' across an entire vector and `||` evalutes 'or' for only the first element of a vector.

```r
FALSE | c(TRUE, FALSE, FALSE)
```

```
## [1]  TRUE FALSE FALSE
```

```r
FALSE || c(TRUE, FALSE, FALSE)
```

```
## [1] TRUE
```

### 12. Looking at Data

R has many functions to help you get a sense of your data.

```r
# look at dimensions (rows then columns)
dim(mpg)
```

```
## [1] 234  11
```

```r
# number of rows
nrow(mpg)
```

```
## [1] 234
```

```r
# number of columns
ncol(mpg)
```

```
## [1] 11
```

```r
# look at variable names
names(mpg)
```

```
##  [1] "manufacturer" "model"        "displ"        "year"        
##  [5] "cyl"          "trans"        "drv"          "cty"         
##  [9] "hwy"          "fl"           "class"
```

```r
# preview the first few rows of data (6 by default)
head(mpg)
```

```
## # A tibble: 6 x 11
##   manufacturer model displ  year   cyl trans  drv     cty   hwy fl    class
##   <chr>        <chr> <dbl> <int> <int> <chr>  <chr> <int> <int> <chr> <chr>
## 1 audi         a4      1.8  1999     4 auto(~ f        18    29 p     comp~
## 2 audi         a4      1.8  1999     4 manua~ f        21    29 p     comp~
## 3 audi         a4      2    2008     4 manua~ f        20    31 p     comp~
## 4 audi         a4      2    2008     4 auto(~ f        21    30 p     comp~
## 5 audi         a4      2.8  1999     6 auto(~ f        16    26 p     comp~
## 6 audi         a4      2.8  1999     6 manua~ f        18    26 p     comp~
```

```r
# look at the last ten rows of data
tail(mpg, 10)
```

```
## # A tibble: 10 x 11
##    manufacturer model displ  year   cyl trans drv     cty   hwy fl    class
##    <chr>        <chr> <dbl> <int> <int> <chr> <chr> <int> <int> <chr> <chr>
##  1 volkswagen   new ~   2    1999     4 auto~ f        19    26 r     subc~
##  2 volkswagen   new ~   2.5  2008     5 manu~ f        20    28 r     subc~
##  3 volkswagen   new ~   2.5  2008     5 auto~ f        20    29 r     subc~
##  4 volkswagen   pass~   1.8  1999     4 manu~ f        21    29 p     mids~
##  5 volkswagen   pass~   1.8  1999     4 auto~ f        18    29 p     mids~
##  6 volkswagen   pass~   2    2008     4 auto~ f        19    28 p     mids~
##  7 volkswagen   pass~   2    2008     4 manu~ f        21    29 p     mids~
##  8 volkswagen   pass~   2.8  1999     6 auto~ f        16    26 p     mids~
##  9 volkswagen   pass~   2.8  1999     6 manu~ f        18    26 p     mids~
## 10 volkswagen   pass~   3.6  2008     6 auto~ f        17    26 p     mids~
```

`summary` is good for getting an overview of the data.

```r
summary(mpg)
```

```
##  manufacturer          model               displ            year     
##  Length:234         Length:234         Min.   :1.600   Min.   :1999  
##  Class :character   Class :character   1st Qu.:2.400   1st Qu.:1999  
##  Mode  :character   Mode  :character   Median :3.300   Median :2004  
##                                        Mean   :3.472   Mean   :2004  
##                                        3rd Qu.:4.600   3rd Qu.:2008  
##                                        Max.   :7.000   Max.   :2008  
##       cyl           trans               drv                 cty       
##  Min.   :4.000   Length:234         Length:234         Min.   : 9.00  
##  1st Qu.:4.000   Class :character   Class :character   1st Qu.:14.00  
##  Median :6.000   Mode  :character   Mode  :character   Median :17.00  
##  Mean   :5.889                                         Mean   :16.86  
##  3rd Qu.:8.000                                         3rd Qu.:19.00  
##  Max.   :8.000                                         Max.   :35.00  
##       hwy             fl               class          
##  Min.   :12.00   Length:234         Length:234        
##  1st Qu.:18.00   Class :character   Class :character  
##  Median :24.00   Mode  :character   Mode  :character  
##  Mean   :23.44                                        
##  3rd Qu.:27.00                                        
##  Max.   :44.00
```

```r
# to look at categorical variables that were cut off 
table(mpg$class)
```

```
## 
##    2seater    compact    midsize    minivan     pickup subcompact 
##          5         47         41         11         33         35 
##        suv 
##         62
```

`str` also provides a concise view of the data structure.

```r
str(mpg)
```

```
## Classes 'tbl_df', 'tbl' and 'data.frame':	234 obs. of  11 variables:
##  $ manufacturer: chr  "audi" "audi" "audi" "audi" ...
##  $ model       : chr  "a4" "a4" "a4" "a4" ...
##  $ displ       : num  1.8 1.8 2 2 2.8 2.8 3.1 1.8 1.8 2 ...
##  $ year        : int  1999 1999 2008 2008 1999 1999 2008 1999 1999 2008 ...
##  $ cyl         : int  4 4 4 4 6 6 6 4 4 4 ...
##  $ trans       : chr  "auto(l5)" "manual(m5)" "manual(m6)" "auto(av)" ...
##  $ drv         : chr  "f" "f" "f" "f" ...
##  $ cty         : int  18 21 20 21 16 18 18 18 16 20 ...
##  $ hwy         : int  29 29 31 30 26 26 27 26 25 28 ...
##  $ fl          : chr  "p" "p" "p" "p" ...
##  $ class       : chr  "compact" "compact" "compact" "compact" ...
```

