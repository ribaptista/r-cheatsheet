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
v <- 1:3
class(v)
typeof(v)
str(v)
print(v)
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
