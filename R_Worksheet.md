# R Programming Worksheet

This worksheet is designed to test your understanding of fundamental R programming concepts, data manipulation with `tidyverse`, and data visualization with `ggplot2`. Work through each section, answering the questions and completing the coding exercises.

## Section 1: R Basics - Data Types and Structures

1.  **Variables and Basic Operations:**
    a. Create a numeric variable `a` with the value 15 and a character variable `b` with the value "Hello R". Print their classes.
    b. Perform an addition operation between `a` and `5`. Store the result in a new variable `c` and print `c`.

2.  **Vectors:**
    a. Create a numeric vector `my_numbers` containing the values 10, 20, 30, 40, 50.
    b. Create a character vector `my_fruits` containing "apple", "banana", "orange", "grape".
    c. Access and print the third element of `my_numbers`.
    d. Access and print the first and last elements of `my_fruits`.
    e. Calculate the sum and mean of `my_numbers`.

3.  **Matrices:**
    a. Create a 3x3 matrix named `my_matrix` with values from 1 to 9, filled by row.
    b. Access and print the element in the second row, third column.
    c. Access and print the entire first row.
    d. Access and print the entire second column.

4.  **Lists:**
    a. Create a list named `student_info` containing:
        *   Name: "John Doe" (character)
        *   Age: 21 (numeric)
        *   Courses: c("Math", "Physics", "Chemistry") (character vector)
        *   Enrolled: TRUE (logical)
    b. Access and print the student's name using the `$` operator.
    c. Access and print the second course using double square brackets `[[]]`.

5.  **Data Frames:**
    a. Create a data frame named `employees` with the following columns:
        *   `Name`: "Alice", "Bob", "Charlie"
        *   `Department`: "HR", "IT", "Finance"
        *   `Salary`: 60000, 75000, 80000
    b. Print the entire data frame.
    c. Access and print the `Department` column.
    d. Access and print the first row.
    e. Access and print Bob's salary.

## Section 2: Data Import and Export

1.  **CSV Import:**
    a. Imagine you have a CSV file named `sales_data.csv` with columns `Region`, `Product`, `Sales`. Describe the R function you would use to import this data into a data frame.
    b. Write the R code to import `sales_data.csv` into a data frame called `sales`.

2.  **Excel Import (Conceptual):**
    a. What R package would you typically use to import data from an Excel file (`.xlsx`)?
    b. Describe the general steps to install and load this package, and then read the first sheet of an Excel file named `inventory.xlsx`.

3.  **CSV Export:**
    a. Create a small data frame `results` with two columns: `ID` (1, 2, 3) and `Score` (85, 92, 78).
    b. Write the R code to export this `results` data frame to a CSV file named `my_results.csv`, ensuring that row names are not written to the file.

## Section 3: Data Wrangling with Tidyverse (dplyr and tidyr)

For this section, we will use the built-in `mtcars` dataset. Load it using `data(mtcars)`.

1.  **`dplyr` - `select()` and `filter()`:**
    a. Select only the `mpg`, `cyl`, and `hp` columns from `mtcars` and store them in a new data frame `mtcars_subset`.
    b. Filter `mtcars` to include only cars with `cyl` equal to 6 and `gear` equal to 4. Store the result in `mtcars_filtered`.

2.  **`dplyr` - `mutate()` and `arrange()`:**
    a. Add a new column `hp_per_cyl` to `mtcars` that calculates horsepower per cylinder (`hp / cyl`). Store the result in `mtcars_mutated`.
    b. Arrange `mtcars` in descending order of `mpg`. Store the result in `mtcars_arranged`.

3.  **`dplyr` - `group_by()` and `summarise()`:**
    a. Group `mtcars` by `cyl` and calculate the average `mpg` for each cylinder group. Store the result in `mtcars_summary`.

4.  **`tidyr` - `pivot_longer()` and `pivot_wider()`:**
    a. Create a small data frame `student_grades` with columns `Name`, `Math`, `Science`. Populate it with some sample data.
    b. Use `pivot_longer()` to transform `student_grades` into a long format, with new columns `Subject` and `Grade`.
    c. Use `pivot_wider()` to transform the long format data back into the original wide format.

## Section 4: Data Visualization with ggplot2

For this section, we will use the built-in `iris` dataset. Load it using `data(iris)`.

1.  **Scatter Plot:**
    a. Create a scatter plot of `Sepal.Length` (x-axis) vs. `Petal.Length` (y-axis) from the `iris` dataset.
    b. Color the points by `Species`.
    c. Add appropriate x and y-axis labels and a title "Sepal Length vs. Petal Length by Species".

2.  **Histogram:**
    a. Create a histogram of `Sepal.Width` from the `iris` dataset.
    b. Fill the bars by `Species`.
    c. Add a title "Distribution of Sepal Width by Species" and appropriate axis labels.

3.  **Box Plot:**
    a. Create a box plot showing the distribution of `Petal.Width` for each `Species`.
    b. Add a title "Petal Width Distribution by Species" and appropriate axis labels.

4.  **Bar Chart:**
    a. Create a bar chart showing the count of each `Species` in the `iris` dataset.
    b. Add a title "Count of Iris Species" and appropriate axis labels.

5.  **Customization and Saving:**
    a. Take any of the plots you created above and add at least two additional customizations (e.g., change theme, add subtitle, change colors manually).
    b. Save your customized plot as a PNG file named `my_custom_plot.png` with a width of 10 inches, height of 7 inches, and a resolution of 300 dpi.

--- 

**Author:** Manus AI
**Date:** September 07, 2025

