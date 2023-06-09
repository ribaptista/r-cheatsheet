# R cheat sheet

### Packages
```R
# Installing the package
install.packages("tidyverse")

# Loading the package
library(tidyverse)
```

### Special values
```R
NaN
NA
Inf
-Inf
NULL

# NAs and NaNs
is.na(v)
# NaNs only
is.nan(v)
```

### Environment
```R
v <- 1
rm(v)
```

### Conversion
```R
v <- 1:3
as.character(v)
as.numeric(v)
as.logical(v)
```

### Data structures
| Dimensions | Homegeneous | Heterogeneous |
| --- | --- | --- |
| 1 | Vector | List |
| 2 | Matrix | Data frame |
| n | Array | |

### Inspect
```R
# also works with other object types (data frames etc)
v <- 1:3
class(v)
typeof(v)
str(v)
mode(v)
attributes(v)
attr(v, "names")
attr(v, "names") <- c()
print(v)
View(v)
head(v, n = 1)
```

### Vectors
```R
# Numeric
v <- c(1, 2, 3)
v <- 1:3

# Character
v <- c("a", "b", "c")

# Logical
v <- c(T, F)

# Combining
v <- c(1:3, "a", c(T, F))

# Coercion to numeric
v <- c(T, F, 0)

# Coercion to character
v <- c(T, F, 0, 1, "a")

length(v)
range(v)
max(v)
min(x)
sum(v)
prod(v)
pmax(v, ...)
pmin(v, ...)

# Applying an operation to every element in vector
v <- 1:3
v * 3
v > 2

v <- c("a", "b", "c")
v != "b"

# Concatenation
paste(c("X","Y"), 1:10)

# Truncate/extend length
length(v) <- 3

# matrix of products of every x*y combination
outer(x, y, "*")
```

### Vector indexing
```R
v <- c(1, 2, 3, NA, NA)
s <- !is.na(v)
v[s]
v[c(T, T, T, F, F)]
v[1:3]
v[-(1:3)]
names(v) = c("a", "b", "c", "d", "e")
v[c("b", "c")]

# assignment
x <- 1:10
x[x>5] <- 1:5
```

### Factors
```R
f <- factor(c("l", "m", "h", "h", "m", "m"), 
  levels = c("l", "m", "h"),
  labels = c("Low", "Medium", "High"))

levels(f) <- c("l", "m", "h")

# sum by factor
n <- 1:10
f <- factor(rep(c("a", "b"), each=5))
tapply(n, f, sum)

# 2-way table
f <- factor(rep(c("a", "b", "c"), 15))
g <- factor(rep(c("d", "f", "g"), 15))
table(f, g)
```

### Matrices
```R
# From vector
x <- 1:100
attr(x, "dim") <- c(10,10)
# or 
m <- matrix(x, ncol=10)

# transpose
t(m)

# matrix product
m %*% t(m)

# diagonal as vector
diag(m)

# diagonal matrix
diag(1:3)

# joining vectors horizontally
cbind(1:3, 1:6)

# joining matrices
m1 <- matrix(1:20, ncol=2)
cbind(m1, m1)

# joining matrices vertically
rbind(m1, m1)

# vectors to row and column matrices
rbind(1:3)
cbind(1:3)

# to vector
as.vector(m)
```

### Arrays
```R
# 2-d zeroed array
x <- array(0, dim=c(4,5))

# 3-dimensional array from vector
x <- 1:27
dim(x) <- c(3,3,3)
x[1,2,3]
x[2,,]
x[,,2]
x[5:8]

# outer product
# all possible products of elements from a and b
# dim(ab) is dim(a) and dim(b) concatenated
ab <- a %o% b
```

### Lists
```R
l <- list(a = 1, b = 2, 3, 4, 5)

# first component
l[[1]]

# sublist
l[1]
l[1:3]

# named component
l$a
l[["a"]]

# concatenating
c(l, l)

# extending
l[6] = 1
```

### Data frames
```R
df <- data.frame(var1 = c(1, 2, 3),
  var2 = c("a", "b", "c"),
  var3 = factor(c("a", "b", "a")))

# From lists
df <- data.frame(x = 1:3, list(y = 4:6, z = 7:9))

# Using variables
var1 <- c(1, 2, 3)
var2 <- c("a", "b", "c")
var3 <- factor(c("a", "b", "a"))
df <- data.frame(var1, var2, var3)
df2 <- data.frame(v1 = var1, v2 = var2, v3 = var3)
```

### Loading datasets
```R
# R format
ds_name = load("ds.RData", verbose = T)

# Table
df <- read.table("houses.data")

# xslx
library(readxl)
df <- read_excel("ds.xlsx")

# csv
df <- read.csv("ds.csv", sep = ",", dec = ".")

# csv from url
df <- read.csv("https://...", sep = ",", dec = ".")

# scan?
scan(...)
```

### Saving datasets
```R
# R Format
df <- data.frame(v1 = 1:3)
save(df, file = "df.RData")

# xslx
install.packages("writexl")
library("writexl")
write_xlsx(df, "df.xlsx")

# csv
write.csv(df, file = "df.csv", row.names = F)
```

### Manipulating datasets
```R
df <- data.frame(v1 = 1:3,
  v2 = c("a", "b", "c"),
  v3 = c(T, T, F),
  v4 = c("1", "E", "2"))

# Variable names
names(df)

# Dimensions
nrow(df)
ncol(df)
dim(df)

# Selecting a single value
df[2, 2]

# Selecting a row
df[2,]

# Selecting a column
df$v2
df[, 2]

# Rows 1 and 3
df[c(1, 3),]

# Columns 1 and 3
df[, c(1, 3)]
df[, c("v1", "v3")]

# Reordering rows
df[c(2, 3, 1),]

# Reordering columns
df[, c(2, 3, 1)]

# Removing columns
df[, -c(1)]

# Removing rows
df[-c(1),]

# Filtering rows
df[df$v1 > 2,]
df[df$v1 > 2 | df$v2 == "b",]

# Renaming variables
names(df) <- c("var1", "var2", "var3", "var4")

# Converting to numeric
df$v4_num <- as.numeric(df$var4)
# Warning message:
# NAs introduced by coercion 

# Converting to factor
df$var2 <- factor(df$var2, 
  levels = c("a", "b", "c"))
  
# Descriptive stats
summary(df$v4_num)
```

### Functions
```R
fn <- function(arg1, arg2) {
  return(arg1 + arg2)
}

fn(1, 2)

# Vectorization
fn(1:3, 4:6)
```

### Conditionals
```R
v <- 1
if (v < 10) {} 
else if (v < 20) {}
else {}
```

### Loops
```R
# For
v <- 1:10
for (i in v) print(i)

# While
i <- 1
while (i < 10) i <- i + 1
```

### Statistics
```R
v <- 1:10

# Ignore NAs
mean(v, na.rm = T)

# Sample variance
var(v)
```

### Manipulating vectors
```R
# Append elements to vector
v <- 1:3
v[4] <- 4
v <- c(v, 5, 6)

# Classify by range
cut(1:100, breaks = seq(0, 100, by=10))
```

### Manipulating lists
```R
# Append elements to list
l <- list(1,2,3)
l[[4]] <- 4
```

### Sequences
```R
seq(-5, 5, by=.2)
seq(length=51, from=-5, by=.2)
rep(x, times=5)
rep(x, each=5)
```

### Workspace
```R
df <- data.frame(x = 1:3)
attach(df)
search()
ls(2)
x
detach(df)
```

### Datasets
```R
data()
```  
