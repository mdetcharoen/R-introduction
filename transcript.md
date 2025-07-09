# A Hands-On Introduction to R

## Course objectives

By the end of this class, you should be able to:

* Navigate and use the RStudio Integrated Development Environment (IDE).
* Understand and use basic R syntax, including creating and manipulating objects.
* Recognize and work with the primary data types and structures in R.
* Select appropriate types of data visualization for different scenarios.
* Create plots using both Base R and the `ggplot2` package.
* Install and load external R packages to extend your analytical toolkit.

---

## Part 1: Foundational concepts

### R and the RStudio

* **R** is the core programming language for statistical analysis and data manipulation.
* **RStudio** is an Integrated Development Environment (IDE) that makes working with R easier by providing an organized interface for coding, data viewing, plotting, and package management.

**RStudio's four-pane layout:**

* **Script editor (top-left):** Where you write and edit reusable scripts.
* **Console (bottom-left):** Where code is executed and output is displayed; also allows for quick, one-off commands.
* **Environment/history (top-right):** View active variables, datasets, and the command history.
* **Files/plots/packages/help (bottom-right):** Manage files, view plots, manage installed packages, and access R documentation.

### Basic operations in R

R supports standard arithmetic:

```r
5 + 3          # Addition
4 * 7          # Multiplication
100 / 4        # Division
2^3            # Exponentiation
(5 + 5) * 2    # Parentheses for order of operations
```

### Object assignment

To work effectively, you must store data in *objects*. Use the `<-` operator to assign values:

```r
a <- 10            # Assign value 10 to 'a'
result <- a * 5    # Assign the product to 'result'
result             # Display result in console
```

Objects you create appear in the Environment pane, making it easy to track your session.

### Using functions

Functions automate common operations. Call a function by its name, followed by parentheses containing *arguments*:

```r
sqrt(144)                  # Compute the square root
round(3.14159, digits=2)   # Round to 2 decimal places
```

To access help for a function, prefix its name with a question mark:

```r
?round
```


---

## Part 2: Data types and structures

### Fundamental data types

R works with several fundamental data types:

* **numeric:** real numbers, e.g., `3.14`, `-100`
* **integer:** whole numbers, specified with an `L`, e.g., `5L`
* **character:** text, in quotes, e.g., `"sample"`
* **logical:** boolean values, `TRUE` or `FALSE`
* **factor:** categorical data, stored as levels, crucial for modeling and plotting

### Core data structures

* **Vectors:** ordered collections of elements of the same type

  ```r
  numeric_vector <- c(10.5, 20.0, 30.5)
  character_vector <- c("alpha", "beta", "gamma")
  ```
* **Data frames:** The fundamental way to organize tabular data; each column can have a different data type, but all columns must be the same length.

**Working with data frames:**

R comes with built-in datasets such as `mtcars`:

```r
head(mtcars)      # First 6 rows
str(mtcars)       # Structure: columns, types, preview
summary(mtcars)   # Statistical summary
```

**Always inspect your data before analysis to check for errors or unexpected values.**

---

## Part 3: Data visualization

### Principles of visualization selection

Choose your plot based on the type and relationship of your variables:

* **One variable:**

  * *Continuous*: Use a **histogram**
  * *Categorical*: Use a **bar chart**
* **Two variables:**

  * *Continuous vs. continuous*: Use a **scatter plot**
  * *Categorical vs. continuous*: Use a **box plot**

### Plotting with base R

Access columns of data frames with the `$` operator:

```r
hist(mtcars$mpg, main="Distribution of Miles Per Gallon", xlab="Miles Per Gallon (MPG)")
plot(mtcars$wt, mtcars$mpg, main="Vehicle Weight vs. MPG", xlab="Weight (1000 lbs)", ylab="MPG")
```

### Extending R: Packages and `ggplot2`

Packages add new functionality to R. To use a package:

```r
install.packages("ggplot2")   # Install once
library(ggplot2)              # Load each session
```

#### The grammar of graphics and `ggplot2`

`ggplot2` builds plots by layering components:

* `ggplot()`: Initializes the plot and data
* `aes()`: Maps variables to visual properties (axes, color)
* `geom_*()`: Specifies how data are represented (points, bars, boxes, etc.)

**Examples:**

* **Histogram:**

  ```r
  ggplot(mtcars, aes(x = mpg)) +
    geom_histogram(binwidth = 5, fill = "blue", color = "black") +
    labs(title = "Distribution of Miles Per Gallon", x = "MPG", y = "Frequency")
  ```
* **Scatter Plot:**

  ```r
  ggplot(mtcars, aes(x = wt, y = mpg)) +
    geom_point(color = "darkred") +
    labs(title = "Weight vs. MPG", x = "Weight (1000 lbs)", y = "MPG")
  ```
* **Box Plot:** (Convert `cyl` to a factor for categories)

  ```r
  mtcars$cyl_factor <- as.factor(mtcars$cyl)
  ggplot(mtcars, aes(x = cyl_factor, y = mpg)) +
    geom_boxplot(fill = "lightblue") +
    labs(title = "MPG by Cylinder Count", x = "Number of Cylinders", y = "MPG")
  ```


---

## Further Resources

* **R for Data Science** by Hadley Wickham and Garrett Grolemund ([https://r4ds.had.co.nz/](https://r4ds.had.co.nz/))
* **RStudio Cheatsheets** ([https://posit.co/resources/cheatsheets/](https://posit.co/resources/cheatsheets/))
* **Stack Overflow** ([https://stackoverflow.com/](https://stackoverflow.com/)) For troubleshooting and advice from the global programming community.
* **R Documentation**: Use `?function_name` in R or visit [https://cran.r-project.org/manuals.html](https://cran.r-project.org/manuals.html).

