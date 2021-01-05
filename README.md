[![Check Allowed Files](https://github.com/statprog-s1-2020/hw02_tut01_team01/workflows/Check%20Allowed%20Files/badge.svg)](https://github.com/statprog-s1-2020/hw02_tut01_team01/actions?query=workflow:%22Check%20Allowed%20Files%22) [![Check RMarkdown Renders](https://github.com/statprog-s1-2020/hw02_tut01_team01/workflows/Check%20RMarkdown%20Renders/badge.svg)](https://github.com/statprog-s1-2020/hw02_tut01_team01/actions?query=workflow:%22Check%20RMarkdown%20Renders%22) [![Check Rmd Structure](https://github.com/statprog-s1-2020/hw02_tut01_team01/workflows/Check%20Rmd%20Structure/badge.svg)](https://github.com/statprog-s1-2020/hw02_tut01_team01/actions?query=workflow:%22Check%20Rmd%20Structure%22)


Statistical Programming
------------
Authors:
* Callum Abbott 
* Georgia Zhao 
* Panagiotis Maouris 
* Li Xihang 
<br/>

## Lego Sales Data

### Data

For we worked with a synthetic data set of sales records for Lego construction sets. We assumed that the original data was stored in a JSON format but a colleague has managed to import it into R as a list of lists (of lists). The code below will load a copy of the object, called `sales`, into your environment.

```r
sales = readRDS("data/lego_sales.rds")
```

The data is structured such that each entry in the top list represents a different purchaser. These list entries contain basic information about the purchaser (name, age, phone number, etc.) as well as their purchase history. Everyone in the data set has purchased at least one lego set but many have purchased more than one. The purchase histories are stored in the `purchases` element which is also a list of lists. Each entry within the `purchases` list reflects a different Lego set which the customer purchased. Note that the customer may have purchased more than one copy of any particular set, this number is stored as `Quantity` within the purchase record.

<br/>


### Questions

We sought to answer a number of questions about that data that will involve the lego sales dataset such as:

<br/>

1. What are the three most common first names of purchasers?

1. Which Lego theme has made the most money for Lego?

1. Do men or women buy more Lego sets (per person) on average?

1. What are the five most popular hobbies of Lego purchasers?

1. Which area code has spent the most money on Legos? (In the US the area code is the first 3 digits of a phone number)


## GitHub and dplyr

### Data

This is similarly structured data to the lego sales dataset. However, in this case we are provided with details on all of the commits made to the dplyr package on GitHub since the beginning of the year. These data were obtained from the GitHub API and were originally formatted as JSON. Once again, we have pre-processed these data into a list of lists of lists (etc.) and the resulting object can be read into R using the following code:

```r
commits = readRDS("data/dplyr_commits.rds")
```

These data are somewhat more complicated than the lego data, however much of the data values provided are redundant and/or irrelevant for the assigned tasks. Our goal initially is to tidy up a subset of these data to construct a useful data frame which can then be used to answer several questions about the development and contributions to dplyr this year.

Some relevant details about git / GitHub that will be useful for understanding / working with these data:

* git commits are uniquely identified by a hexidecimal hash called the `sha`

* git makes a distinction between who wrote the code and who committed it, the vast majority of the time these are the same and we will not worry about the cases where this is not true. For this task, you should assume that data stored under `author` should be used when determining who is responsible for a commit.

* Remember that a commit can involve a single file or multiple files, the reported `stats` are for all the files collectively, individual file's stats are available within the `files` element.

* git / GitHub tracks the changes made to files in terms of additions and deletions - these changes might be as little as deleting a single character to as complicated as adding hundreds of lines of new functions. These statistics are stored for the commit as a whole in `stats` and on a per file basis within `files`.

* The data contains information on the commit history of the repository, including which commit is descended from which, while interesting none of this will be necessary for completing the rest of the task. Examples of this type of data can be found the in the `parents` entry. 

### Questions

1. Who are the top five contributors (in terms of the most commits) to dplyr in 2020?

2. Who is the top contributor who is not a current employee of RStudio? Current employees can be found [here](https://rstudio.com/about/). Briefly describe one or more of their commits to the project.

3. Which four files have been modified most often? (i.e. show up in the most number of commits)

4. Describe the general pattern for development of dplyr. Specifically, show a tabulation or visualization for the number of commits made for each hour of the day and day of the week and then describe the general patterns that you see.

5. dplyr has had 5 releases to [CRAN](https://cran.r-project.org/web/packages/dplyr/index.html) in 2020, create a visualization exploring an interesting relationship between these releases and the commit history.


<br/>
