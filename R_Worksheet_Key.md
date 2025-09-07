# R Programming Worksheet - Answer Key

This document provides the solutions and R code snippets for the R Programming Worksheet.

## Section 1: R Basics - Data Types and Structures

1.  **Variables and Basic Operations:**

a. Create a numeric variable `a` with the value 15 and a character variable `b` with the value "Hello R". Print their classes.
```R
a <- 15
b <- "Hello R"
print(class(a))
print(class(b))

```

b. Perform an addition operation between `a` and `5`. Store the result in a new variable `c` and print `c`.

```R
c <- a + 5
print(c)
```

2.  **Vectors:**
a. Create a numeric vector `my_numbers` containing the values 10, 20, 30, 40, 50.

```R
my_numbers <- c(10, 20, 30, 40, 50)
```
b. Create a character vector `my_fruits` containing "apple", "banana", "orange", "grape".

```R
my_fruits <- c("apple", "banana", "orange", "grape")
```
c. Access and print the third element of `my_numbers`.

```R
print(my_numbers[3])
```
d. Access and print the first and last elements of `my_fruits`.

```R
print(my_fruits[c(1, length(my_fruits))])
```
e. Calculate the sum and mean of `my_numbers`.

```R
sum_my_numbers <- sum(my_numbers)
mean_my_numbers <- mean(my_numbers)
print(sum_my_numbers)
print(mean_my_numbers)
```

3.  **Matrices:**
a. Create a 3x3 matrix named `my_matrix` with values from 1 to 9, filled by row.
```R
my_matrix <- matrix(1:9, nrow = 3, ncol = 3, byrow = TRUE)
print(my_matrix)
```
b. Access and print the element in the second row, third column.
```R
print(my_matrix[2, 3])
```
c. Access and print the entire first row.
```R
print(my_matrix[1, ])
```
d. Access and print the entire second column.
```R
print(my_matrix[, 2])
```

4.  **Lists:**
a. Create a list named `student_info` containing:
*   Name: "John Doe" (character)
*   Age: 21 (numeric)
*   Courses: c("Math", "Physics", "Chemistry") (character vector)
*   Enrolled: TRUE (logical)
```R
student_info <- list(
  Name = "John Doe",
  Age = 21,
  Courses = c("Math", "Physics", "Chemistry"),
  Enrolled = TRUE
)
print(student_info)
```
b. Access and print the student's name using the `$` operator.
```R
print(student_info$Name)
```
c. Access and print the second course using double square brackets `[[]]`.
```R
print(student_info[["Courses"]][2])
```

5.  **Data Frames:**
a. Create a data frame named `employees` with the following columns:
*   `Name`: "Alice", "Bob", "Charlie"
*   `Department`: "HR", "IT", "Finance"
*   `Salary`: 60000, 75000, 80000
```R
employees <- data.frame(
  Name = c("Alice", "Bob", "Charlie"),
  Department = c("HR", "IT", "Finance"),
  Salary = c(60000, 75000, 80000)
)
```
b. Print the entire data frame.
```R
print(employees)
```
c. Access and print the `Department` column.
```R
print(employees$Department)
```
d. Access and print the first row.
```R
print(employees[1, ])
```
e. Access and print Bob's salary.
```R
print(employees[employees$Name == "Bob", "Salary"])
```

## Section 2: Data Import and Export

1.  **CSV Import:**
a. Imagine you have a CSV file named `sales_data.csv` with columns `Region`, `Product`, `Sales`. Describe the R function you would use to import this data into a data frame.
*   The `read.csv()` function is used to import data from a CSV file into an R data frame.
b. Write the R code to import `sales_data.csv` into a data frame called `sales`.
```R
sales <- read.csv("sales_data.csv")
print(sales)
```

2.  **Excel Import (Conceptual):**
a. What R package would you typically use to import data from an Excel file (`.xlsx`)?
*   The `readxl` package is typically used to import data from Excel files.
b. Describe the general steps to install and load this package, and then read the first sheet of an Excel file named `inventory.xlsx`.
*   **Install the package:** `install.packages("readxl")`
*   **Load the package:** `library(readxl)`
*   **Read the Excel file:** `inventory_data <- read_excel("inventory.xlsx", sheet = 1)`

3.  **CSV Export:**
a. Create a small data frame `results` with two columns: `ID` (1, 2, 3) and `Score` (85, 92, 78).
```R
results <- data.frame(
  ID = c(1, 2, 3),
  Score = c(85, 92, 78)
)
```
b. Write the R code to export this `results` data frame to a CSV file named `my_results.csv`, ensuring that row names are not written to the file.
```R
write.csv(results, "my_results.csv", row.names = FALSE)
```

## Section 3: Data Wrangling with Tidyverse (dplyr and tidyr)

For this section, we will use the built-in `mtcars` dataset. Load it using `data(mtcars)`.

```R
data(mtcars)
library(tidyverse) # Ensure tidyverse is loaded for dplyr and tidyr functions
```

1.  **`dplyr` - `select()` and `filter()`:**
a. Select only the `mpg`, `cyl`, and `hp` columns from `mtcars` and store them in a new data frame `mtcars_subset`.
```R
mtcars_subset <- mtcars %>%
  select(mpg, cyl, hp)
print(head(mtcars_subset))
```
b. Filter `mtcars` to include only cars with `cyl` equal to 6 and `gear` equal to 4. Store the result in `mtcars_filtered`.
```R
mtcars_filtered <- mtcars %>%
  filter(cyl == 6, gear == 4)
print(head(mtcars_filtered))
```

2.  **`dplyr` - `mutate()` and `arrange()`:**
a. Add a new column `hp_per_cyl` to `mtcars` that calculates horsepower per cylinder (`hp / cyl`). Store the result in `mtcars_mutated`.
```R
mtcars_mutated <- mtcars %>%
  mutate(hp_per_cyl = hp / cyl)
print(head(mtcars_mutated))
```
b. Arrange `mtcars` in descending order of `mpg`. Store the result in `mtcars_arranged`.
```R
mtcars_arranged <- mtcars %>%
  arrange(desc(mpg))
print(head(mtcars_arranged))
```

3.  **`dplyr` - `group_by()` and `summarise()`:**
a. Group `mtcars` by `cyl` and calculate the average `mpg` for each cylinder group. Store the result in `mtcars_summary`.
```R
mtcars_summary <- mtcars %>%
  group_by(cyl) %>%
  summarise(average_mpg = mean(mpg))
print(mtcars_summary)
```

4.  **`tidyr` - `pivot_longer()` and `pivot_wider()`:**
a. Create a small data frame `student_grades` with columns `Name`, `Math`, `Science`. Populate it with some sample data.
```R
student_grades <- data.frame(
  Name = c("Alice", "Bob"),
  Math = c(90, 85),
  Science = c(92, 88)
)
print(student_grades)
```
b. Use `pivot_longer()` to transform `student_grades` into a long format, with new columns `Subject` and `Grade`.
```R
long_grades <- student_grades %>%
  pivot_longer(cols = c(Math, Science), names_to = "Subject", values_to = "Grade")
print(long_grades)
```
c. Use `pivot_wider()` to transform the long format data back into the original wide format.
```R
wide_grades <- long_grades %>%
  pivot_wider(names_from = "Subject", values_from = "Grade")
print(wide_grades)
```

## Section 4: Data Visualization with ggplot2

For this section, we will use the built-in `iris` dataset. Load it using `data(iris)`.

```R
data(iris)
library(ggplot2) # Ensure ggplot2 is loaded
```

1.  **Scatter Plot:**
a. Create a scatter plot of `Sepal.Length` (x-axis) vs. `Petal.Length` (y-axis) from the `iris` dataset.
b. Color the points by `Species`.
c. Add appropriate x and y-axis labels and a title "Sepal Length vs. Petal Length by Species".
```R
ggplot(iris, aes(x = Sepal.Length, y = Petal.Length, color = Species)) +
  geom_point() +
  labs(title = "Sepal Length vs. Petal Length by Species",
   x = "Sepal Length (cm)",
   y = "Petal Length (cm)")
```

2.  **Histogram:**
a. Create a histogram of `Sepal.Width` from the `iris` dataset.
b. Fill the bars by `Species`.
c. Add a title "Distribution of Sepal Width by Species" and appropriate axis labels.
```R
ggplot(iris, aes(x = Sepal.Width, fill = Species)) +
  geom_histogram(binwidth = 0.2, alpha = 0.7, position = "identity") +
  labs(title = "Distribution of Sepal Width by Species",
   x = "Sepal Width (cm)",
   y = "Frequency")
```

3.  **Box Plot:**
a. Create a box plot showing the distribution of `Petal.Width` for each `Species`.
b. Add a title "Petal Width Distribution by Species" and appropriate axis labels.
```R
ggplot(iris, aes(x = Species, y = Petal.Width, fill = Species)) +
  geom_boxplot() +
  labs(title = "Petal Width Distribution by Species",
   x = "Species",
   y = "Petal Width (cm)")
```

4.  **Bar Chart:**
a. Create a bar chart showing the count of each `Species` in the `iris` dataset.
b. Add a title "Count of Iris Species" and appropriate axis labels.
```R
ggplot(iris, aes(x = Species, fill = Species)) +
  geom_bar() +
  labs(title = "Count of Iris Species",
   x = "Species",
   y = "Count")
```

5.  **Customization and Saving:**
a. Take any of the plots you created above and add at least two additional customizations (e.g., change theme, add subtitle, change colors manually).
```R
# Example customization of the scatter plot
custom_scatter_plot <- ggplot(iris, aes(x = Sepal.Length, y = Petal.Length, color = Species)) +
  geom_point(size = 3, alpha = 0.8) +
  labs(title = "Sepal Length vs. Petal Length by Species (Customized)",
   subtitle = "Exploring Iris Data with Enhanced Visuals",
   x = "Sepal Length (cm)",
   y = "Petal Length (cm)") +
  theme_minimal() +
  scale_color_manual(values = c("setosa" = "#FF9999", "versicolor" = "#99FF99", "virginica" = "#9999FF"))

print(custom_scatter_plot)
```
b. Save your customized plot as a PNG file named `my_custom_plot.png` with a width of 10 inches, height of 7 inches, and a resolution of 300 dpi.
```R
ggsave("my_custom_plot.png", plot = custom_scatter_plot, width = 10, height = 7, dpi = 300)
```

--- 


