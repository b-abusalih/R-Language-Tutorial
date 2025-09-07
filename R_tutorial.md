# R Programming: A Comprehensive Tutorial

## 1. Introduction to R and RStudio

R is a powerful, open-source programming language and environment specifically designed for statistical computing and graphics. It is widely used by statisticians, data scientists, and researchers for data analysis, visualization, and machine learning. Its strength lies in its extensive collection of packages, which are user-contributed libraries that extend R's capabilities to a vast array of statistical and graphical techniques.

While R provides the computational engine, RStudio serves as an integrated development environment (IDE) that significantly enhances the R programming experience. RStudio offers a user-friendly interface that simplifies code writing, debugging, and project management. It integrates various tools, including a console, script editor, environment pane, and plot viewer, into a single, cohesive workspace.

### Installation Guide

To begin your R programming journey, you'll need to install both R and RStudio. The process is straightforward:

1.  **Install R:**
    *   Navigate to the official CRAN (Comprehensive R Archive Network) website: [https://cran.r-project.org/](https://cran.r-project.org/) [1].
    *   Select the download link appropriate for your operating system (Windows, macOS, or Linux).
    *   Follow the instructions provided by the installer, generally accepting the default settings.

2.  **Install RStudio Desktop:**
    *   Visit the official Posit (formerly RStudio) download page for RStudio Desktop: [https://posit.co/download/rstudio-desktop/](https://posit.co/download/rstudio-desktop/) [2].
    *   Download the free version of RStudio Desktop for your operating system.
    *   Run the installer and accept the default installation options.

Once both R and RStudio are installed, opening RStudio will present you with its intuitive interface, typically divided into several panes:

*   **Console:** This is where R commands are executed directly, and output is displayed.
*   **Script Editor:** This pane allows you to write, save, and run R scripts. It's where you'll compose most of your R code.
*   **Environment:** This pane displays all the objects (variables, datasets, functions) currently loaded into your R session.
*   **Plots/Files/Packages/Help:** These tabs provide various functionalities, including viewing plots, navigating files, managing installed packages, and accessing R's help documentation.

### References

[1] CRAN - The R Project for Statistical Computing. Available at: [https://cran.r-project.org/](https://cran.r-project.org/)
[2] Download RStudio Desktop - Posit. Available at: [https://posit.co/download/rstudio-desktop/](https://posit.co/download/rstudio-desktop/)

## 2. R Basics: Data Types and Structures

Understanding the fundamental data types and structures in R is crucial for effective programming. R handles various types of data, and organizing this data into appropriate structures allows for efficient manipulation and analysis.

### Variables

In R, variables are used to store data. The primary assignment operator in R is `<-`, though `=` can also be used. It's good practice to use `<-` for assignment as it is more idiomatic to R and avoids confusion with the equality operator.

```R
x <- 5         # Assigns the numeric value 5 to variable x
y = 10         # Assigns the numeric value 10 to variable y (using =)
z <- x + y     # Performs addition and assigns the result to z
print(z)       # Outputs the value of z, which is 15
```

### Data Types

R supports several basic data types:

*   **Numeric:** Represents numbers, including integers and decimals (e.g., `5`, `3.14`). This is the default numeric type.
*   **Integer:** Whole numbers, explicitly defined by appending `L` (e.g., `5L`).
*   **Character:** Represents text or strings (e.g., `"hello"`, `"R Programming"`).
*   **Logical:** Represents boolean values, `TRUE` or `FALSE`.
*   **Factor:** Used to store categorical data. Factors are essentially integer vectors with a `levels` attribute.

```R
# Numeric
num_var <- 10.5
print(class(num_var)) # "numeric"

# Integer
int_var <- 10L
print(class(int_var)) # "integer"

# Character
char_var <- "R is fun"
print(class(char_var)) # "character"

# Logical
log_var <- TRUE
print(class(log_var)) # "logical"

# Factor
gen_var <- factor(c("Male", "Female", "Male", "Female"))
print(gen_var)
print(class(gen_var)) # "factor"
```

### Data Structures

R provides several built-in data structures to organize data:

#### Vectors

Vectors are the most basic R data structure. They are one-dimensional arrays that can hold elements of the *same* data type. The `c()` function (combine) is used to create vectors.

```R
# Numeric vector
nums <- c(1, 2, 3, 4, 5)
print(nums)
print(class(nums)) # "numeric"

# Character vector
fruits <- c("apple", "banana", "cherry")
print(fruits)
print(class(fruits)) # "character"

# Accessing elements (1-based indexing)
print(nums[3])    # Outputs 3
print(fruits[1])  # Outputs "apple"

# Vector operations
sum_nums <- sum(nums)
mean_nums <- mean(nums)
print(sum_nums)   # Outputs 15
print(mean_nums)  # Outputs 3
```

#### Matrices

Matrices are two-dimensional, rectangular collections of elements of the *same* data type. They are essentially vectors with dimension attributes (number of rows and columns).

```R
# Create a matrix from a vector
matrix_data <- c(1, 2, 3, 4, 5, 6)
my_matrix <- matrix(matrix_data, nrow = 2, ncol = 3, byrow = TRUE) # TRUE: Tells R to fill the matrix row-wise (left to right, then top to bottom). If set to FALSE, it fills column-wise (top to bottom, then left to right).
print(my_matrix)
# Output:
#      [,1] [,2] [,3]
# [1,]    1    2    3
# [2,]    4    5    6

# Accessing elements [row, column]
print(my_matrix[1, 2]) # Outputs 2
print(my_matrix[, 1])  # Outputs first column: 1 4
print(my_matrix[2, ])  # Outputs second row: 4 5 6
```

#### Lists

Lists are highly flexible data structures that can contain elements of *different* data types. They can even contain other lists, making them suitable for complex data organisations.

```R
# Create a list
my_list <- list(
  name = "Alice",
  age = 30,
  scores = c(95, 88, 92),
  is_student = TRUE
)
print(my_list)

# Accessing elements
print(my_list$name)    # Outputs "Alice"
print(my_list[[2]])     # Outputs 30 (by index)
print(my_list[["scores"]][1]) # Outputs 95 (accessing element within a list element)
```

#### Data Frames

Data frames are the most commonly used data structure in R for tabular data. They are essentially lists of vectors of equal length, where each vector represents a column and each element of the vector represents a row. This structure is analogous to a spreadsheet or a database table, making them ideal for statistical analysis.

```R
# Create a data frame
students <- data.frame(
  name = c("Ali", "Sara", "Tom"),
  age = c(20, 22, 19),
  grade = c("A", "B", "A")
)
print(students)
# Output:
#    name age grade
# 1   Ali  20     A
# 2  Sara  22     B
# 3   Tom  19     A

# Accessing columns
print(students$name)  # Outputs "Ali" "Sara" "Tom"
print(students["age"]) # Outputs a data frame with the 'age' column

# Accessing rows
print(students[1, ])   # Outputs the first row

# Accessing specific elements
print(students[2, "grade"]) # Outputs "B"
```

## 3. Data Import and Export

A crucial step in any data analysis workflow is importing data into your R environment and exporting your results. R provides a rich set of functions for reading data from various file formats and writing data to files.

### Importing Data

#### From CSV Files

Comma-Separated Values (CSV) files are a common format for storing tabular data. R's `read.csv()` function is designed to read data from CSV files into a data frame.

```R
# Assuming you have a file named 'students.csv' in your working directory

students_data <- read.csv("students.csv")
print(students_data)
```

#### From Excel Files

To read data from Excel files (`.xls` or `.xlsx`), you'll need to install and load a package like `readxl`.

```R
# Install the readxl package (only needs to be done once)
install.packages("readxl")

# Load the package
library(readxl)

# Read an Excel file
excel_data <- read_excel("my_data.xlsx", sheet = 1) # Reads the first sheet
print(excel_data)
```

### Exporting Data

Once you've processed your data, you may want to save it to a file. The `write.csv()` function is used to export a data frame to a CSV file.

```R
# Create a sample data frame
output_data <- data.frame(
  ID = 1:5,
  Value = rnorm(5) # Generate 5 random numbers
)

# Write the data frame to a CSV file
write.csv(output_data, "output.csv", row.names = FALSE) # row.names = FALSE prevents writing row numbers
```

### Working with Built-in Datasets

R comes with a variety of built-in datasets that are useful for practice and learning. The `data()` function can be used to load these datasets into your environment.

```R
# Load the 'iris' dataset
data(iris)

# Display the first few rows of the dataset
head(iris)

# Get information about the dataset
?iris

# Load the 'mtcars' dataset
data(mtcars)

# Display the first few rows of the dataset
head(mtcars)
```

## 4. Data Wrangling with Tidyverse (dplyr and tidyr)

Data wrangling, or data manipulation, is a critical part of data analysis. The `tidyverse` is a collection of R packages designed for data science that share an underlying design philosophy, grammar, and data structures. The two most important packages for data wrangling are `dplyr` for data manipulation and `tidyr` for tidying data.

First, you need to install and load the `tidyverse` package.

```R
# Install the tidyverse package (only needs to be done once)
install.packages("tidyverse")

# Load the package
library(tidyverse)
```

### `dplyr`: A Grammar of Data Manipulation

`dplyr` provides a set of verbs that help you solve the most common data manipulation challenges.

*   `select()`: Pick columns by name.
*   `filter()`: Pick rows by condition.
*   `mutate()`: Create new columns.
*   `arrange()`: Reorder rows.
*   `summarise()` and `group_by()`: Collapse many values down to a single summary.
*   `join()`: Combine multiple data frames.

Let's use the `iris` dataset to demonstrate these functions.

```R
# Select specific columns
iris_selected <- iris %>% select(Sepal.Length, Sepal.Width, Species)
head(iris_selected)

# Filter for a specific species
iris_setosa <- iris %>% filter(Species == "setosa")
head(iris_setosa)

# Create a new column
iris_mutated <- iris %>% mutate(Sepal.Area = Sepal.Length * Sepal.Width)
head(iris_mutated)

# Arrange by a column
iris_arranged <- iris %>% arrange(desc(Petal.Length))
head(iris_arranged)

# Summarize data by group
iris_summary <- iris %>%
  group_by(Species) %>%
  summarise(avg_sepal_length = mean(Sepal.Length))
print(iris_summary)
```

## 5. Data Visualization with ggplot2

`ggplot2` is an elegant and versatile data visualization package in R, based on the "Grammar of Graphics" concept. This grammar allows you to build plots layer by layer, providing immense flexibility and control over your visualizations. It's part of the `tidyverse`.

```R
# Load the ggplot2 package (it's part of tidyverse, but good to explicitly load if not using tidyverse)
library(ggplot2)

# We'll continue to use the built-in iris dataset for examples
data(iris)
```

### Basic Plot Types

Every `ggplot2` plot starts with `ggplot()` which specifies the data frame and the aesthetic mappings (how variables in your data are mapped to visual properties of the plot, like x-axis, y-axis, color, size, etc.). Then, you add `geom_` functions to define the geometric objects (points, lines, bars, etc.) that represent your data.

#### Scatter Plots

Scatter plots are used to visualize the relationship between two continuous variables.

```R
# Scatter Plot: Sepal Length vs. Sepal Width, colored by Species
ggplot(iris, aes(x = Sepal.Length, y = Sepal.Width, color = Species)) +
  geom_point(size = 3, alpha = 0.8) +
  labs(title = "Sepal Length vs. Sepal Width",
       x = "Sepal Length (cm)",
       y = "Sepal Width (cm)") +
  theme_minimal()
```

#### Histograms

Histograms display the distribution of a single continuous variable.

```R
# Histogram: Distribution of Petal Length, filled by Species
ggplot(iris, aes(x = Petal.Length, fill = Species)) +
  geom_histogram(binwidth = 0.2, alpha = 0.7, position = "identity") +
  labs(title = "Distribution of Petal Length",
       x = "Petal Length (cm)",
       y = "Frequency") +
  theme_minimal()
```

#### Box Plots

Box plots are excellent for visualizing the distribution of a continuous variable across different categories, showing median, quartiles, and outliers.

```R
# Box Plot: Petal Length by Species
ggplot(iris, aes(x = Species, y = Petal.Length, fill = Species)) +
  geom_boxplot() +
  labs(title = "Petal Length by Species",
       x = "Species",
       y = "Petal Length (cm)") +
  theme_minimal()
```

#### Bar Charts

Bar charts are used to display the counts or proportions of categorical variables.

```R
# Bar Chart: Count of each Species
ggplot(iris, aes(x = Species, fill = Species)) +
  geom_bar() +
  labs(title = "Count of Iris Species",
       x = "Species",
       y = "Count") +
  theme_minimal()
```

#### Line Plots

Line plots are typically used to show trends over time or ordered categories. For this example, we'll create a dummy time series.

```R
# Create a dummy dataset for line plot
time_data <- data.frame(
  Year = 2000:2010,
  Value = c(10, 12, 15, 13, 18, 20, 22, 19, 25, 28, 30)
)

# Line Plot: Value over Year
ggplot(time_data, aes(x = Year, y = Value)) +
  geom_line(color = "steelblue", size = 1) +
  geom_point(color = "steelblue", size = 3) +
  labs(title = "Trend of Value Over Time",
       x = "Year",
       y = "Value") +
  theme_minimal()
```

### Customization

`ggplot2` offers extensive options for customizing your plots:

*   `labs()`: Add titles, subtitles, captions, and change axis labels.
*   `theme_` functions: Apply predefined themes (e.g., `theme_minimal()`, `theme_classic()`) or customize individual theme elements (e.g., `theme(plot.title = element_text(hjust = 0.5))`).
*   `scale_` functions: Control the appearance of scales (e.g., `scale_color_manual()`, `scale_fill_brewer()`).
*   `facet_wrap()` or `facet_grid()`: Create small multiples of plots based on categorical variables.

```R
# Example of customization: Scatter plot with custom colors and facets
ggplot(iris, aes(x = Sepal.Length, y = Sepal.Width, color = Species)) +
  geom_point(size = 3, alpha = 0.8) +
  labs(title = "Sepal Length vs. Sepal Width by Species",
       subtitle = "A deeper look into Iris dataset",
       x = "Sepal Length (cm)",
       y = "Sepal Width (cm)",
       caption = "Data source: Fisher's Iris dataset") +
  scale_color_manual(values = c("setosa" = "red", "versicolor" = "green", "virginica" = "blue")) +
  facet_wrap(~ Species) +
  theme_bw() +
  theme(plot.title = element_text(hjust = 0.5, face = "bold"),
        plot.subtitle = element_text(hjust = 0.5))
```

### Saving Plots

You can save your `ggplot2` plots to various file formats using `ggsave()`.

```R
# Save the last plot to a PNG file
ggsave("iris_scatter_plot.png", width = 8, height = 6, dpi = 300)

# You can also specify the plot object to save
my_plot <- ggplot(iris, aes(x = Petal.Length, fill = Species)) +
  geom_histogram(binwidth = 0.2, alpha = 0.7, position = "identity")
ggsave("iris_histogram.pdf", plot = my_plot, width = 8, height = 6)
```

## 6. Basic Statistical Analysis

R is fundamentally a statistical programming language, and it provides a vast array of tools for performing various statistical analyses. This section covers some fundamental statistical concepts and how to implement them in R.

### Descriptive Statistics

Descriptive statistics summarize and describe the main features of a dataset. Common descriptive statistics include measures of central tendency (mean, median, mode) and measures of variability (range, variance, standard deviation).

Let's use the `iris` dataset again to demonstrate.

```R
data(iris)

# Mean of Sepal Length
mean_sepal_length <- mean(iris$Sepal.Length)
print(paste("Mean Sepal Length:", mean_sepal_length))

# Median of Sepal Width
median_sepal_width <- median(iris$Sepal.Width)
print(paste("Median Sepal Width:", median_sepal_width))

# Standard Deviation of Petal Length
sd_petal_length <- sd(iris$Petal.Length)
print(paste("Standard Deviation of Petal Length:", sd_petal_length))

# Summary statistics for a single variable
summary(iris$Sepal.Length)

# Summary statistics for the entire data frame
summary(iris)
```


