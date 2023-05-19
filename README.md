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
