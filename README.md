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

# Applying an operation to every element in vector
v <- 1:3
v * 3
v > 2

v <- c("a", "b", "c")
v != "b"
```

### Factors
```R
f <- factor(c("l", "m", "h", "h", "m", "m"), 
  levels = c("l", "m", "h"),
  labels = c("Low", "Medium", "High"))
```

### Data frames
```R
df <- data.frame(var1 = c(1, 2, 3),
  var2 = c("a", "b", "c"),
  var3 = factor(c("a", "b", "a")))

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

# xslx
library(readxl)
df <- read_excel("ds.xlsx")

# csv
df <- read.csv("ds.csv", sep = ",", dec = ".")

# csv from url
df <- read.csv("https://...", sep = ",", dec = ".")
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
  v4 = c("1", "E", "2")

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

# Descriptive stats
summary(df$v4_num)
```

