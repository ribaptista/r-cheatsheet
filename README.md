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
