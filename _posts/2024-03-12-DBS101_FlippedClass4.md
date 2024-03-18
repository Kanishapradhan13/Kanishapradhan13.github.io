---
Title: DBS101 Flipped class 4
categories: (DBS101,Flipped_class 4)
tags: (DBS101,Advanced Aggregation Functions)
---

### Topic: Advanced Aggregation Functions
----

This flipped class we discussed about the advanced aggregation functions in PSQL and its functions. Advanced Aggregation Functions are the functions used efficient data analysis for sophisticated data,perform calculations,assign a rank to each row,rotate data from row to columns or vice versa, generate subtotal and grand total rows for a specified set of columns, and generate all possible combinations of grouping sets from the specified columns.

As we were divided into four groups, the topic for the first group was Ranking and from their presentation I understood that:

1. Ranking functions in SQL are used to assign a rank to each row based on a specific criteria. These functions can be used for identifying top performers, analyzing trends, or partitioning data.

Below is an example of the using the RANK() function to rank employees by their salaries.

    SELECT 
        employee_id,
        employee_name,
        salary,
        RANK() OVER (ORDER BY salary DESC) AS salary_rank
    FROM 
        employees;

If two employees have the same salary they will be ranked the same and the next rank will be skipped.

OUTPUT

| employee_id | employee_name | salary | salary_rank |
|-------------|---------------|--------|-------------|
| 101         | John          | 60000  | 1           |
| 102         | Alice         | 55000  | 2           |
| 103         | Bob           | 55000  | 2           |
| 104         | Mary          | 52000  | 4           |
| 105         | Sam           | 48000  | 5           |
| ...         | ...           | ...    | ...         |

The next presentation by group 2 was done on the topic Windowing functions and by their presentation I understood that:

2. Window functions in SQL allows us to perform calculations across a set of table rows related to the current row and they do not group rows into a single output row for each group.

Below is an example to calculate the total revenue for each month, but and include a column showing the total revenue across all months as well considering we have a table named sales with columns month, product, and revenue.

    SELECT 
        month,
        product,
        revenue,
        SUM(revenue) OVER (PARTITION BY month) AS total_monthly_revenue,
        SUM(revenue) OVER () AS total_revenue_across_all_months
    FROM 
        sales;


The presentation by group 3 was done on the topic Pivoting functions which was our group so before the presentation the things we discussed were:

3. Pivoting is a process of transforming rows into columns or vice versa in a DB. It involes reshaping data and it makes the data easrier to analyze and summarize by categories and present the data in a more readable way.

Below is an example of if we had a table named Sales with columns Product, Year, and Revenue and to pivot the data to show the revenue for each product over different years we can use the following command:

    SELECT
        Product,
        [2019] AS Revenue_2019,
        [2020] AS Revenue_2020,
        [2021] AS Revenue_2021
    FROM
        (SELECT Product, Year, Revenue FROM Sales) AS SourceTable
    PIVOT
    (
     SUM(Revenue)
     FOR Year IN ([2019], [2020], [2021])
    ) AS PivotTable;

OUTPUT 


    | Product | Revenue_2019 | Revenue_2020 | Revenue_2021 |
    |---------|--------------|--------------|--------------|
    | A       | 10000        | 15000        | 20000        |
    | B       | 12000        | 18000        | 22000        |
    | C       | 8000         | 14000        | 18000        |
    | ...     | ...          | ...          | ...          |


The last group 4 presented about ROLLUP and CUBE functions, they talked about:

4. ROLLUP function allows us to include extra rows that represent the subtotals along with the grand total row. By using the ROLLUP option, we can you can obtain subtotals, intermediate totals, and a grand total for a dataset, all in one go.

Below is an example of how to implement the ROLLUP function if we have a table named Sales with columns Region, Product, and Revenue. You want to generate subtotals for revenue by region and product, as well as a grand total.

    SELECT
        Region,
        Product,
        SUM(Revenue) AS TotalRevenue
    FROM
        Sales
    GROUP BY
        ROLLUP(Region, Product);


5. CUBE function generates all possible combinations of grouping sets from the specified columns. It produces a result set containing subtotals for each combination of values across the specified dimensions, as well as a grand total.

    SELECT
        Region,
        Product,
        SUM(Revenue) AS TotalRevenue
    FROM
        Sales
    GROUP BY
        CUBE(Region, Product);


ROLLUP and CUBE helps us make really detailed reports without writing lots of complicated queries. They let us group our data in different ways all at once. It's like getting a big picture and zooming in to see the details, all in one go. These functions are great for analyzing data from different angles without making things too complicated.

                                            ~ THANK YOU ~
