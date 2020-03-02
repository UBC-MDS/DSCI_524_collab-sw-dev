## DSCI 524 - Collaborative Software Development

### Lecture 3: Code reviews, testing and advice for testing complex things

#### 2020-03-02

## Lecture 3 learning objectives:
By the end of this lecture, students should be able to:

- [Perform a code review that uses inline comments and suggested code fixes.](#Code-reviews-using-in-line-comments-and-suggested-code-fixes)
- [Define the following 3 types of testing](#Some-common-and-useful-types-of-testing):
    - unit testing
    - integration testing
    - regression testing
- [Employ a workflow that optimizes accurate code.](#Employing-a-workflow-that-optimizes-accurate-code)
- [Write unit tests for complex objects (e.g., data frames, models, plots).](#Write-unit-tests-for-complex-objects)
- [Use `pytest` and `testhat` to run a project's entire test suite](#How-testthat-works:)
- [Explain how `pytest` and `testhat` find the test functions when they are asked to run a project's entire test suite](#How-testthat-works:)


## Code reviews using in-line comments and suggested code fixes

- In the project, you are expected to read and review eachother's code BEFORE accepting a pull request. 

- Do not expect all (or even most) pull requests to be perfect in their first submission. 

- We very often need to have a conversation to get pull requests into good shape before merging into master, and GitHub has a very nice tool we can utilize to do this: **GitHub code reviews**


<img src ="https://help.github.com/assets/images/help/commits/hover-comment-icon.gif" width=700>

*Source: <https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/reviewing-proposed-changes-in-a-pull-request>*

### Exercise: do a code review:

We are going to each do our own code review of a pull request. I have set-up a template GitHub repository for you so that you can easily generate a pull request for you to review.

#### Steps:

**When you are done step #5 indicate so on the [sli.do](https://www.sli.do) poll (`#524-L03`).**

1. **Import** [this repository](https://github.com/ttimbers/review-my-pull-request) to obtain a copy of it for yourself (do not fork it).

2. Create a remote branch named `pr` (this will use GitHub Actions to create a pull request for you to review in this repository).

3. Click on the Pull Requests tab of your copy of the repository, click on the pull request titled "Report most accomplished pilots", and then click on "Files Changed". Next click on the `star-wars.Rmd` file. Review the file and observe the following problems with the R Markdown report that was submitted via the pull request:
  - Reasoning of the sentence on line 15
  - Incompatibility with the sentence on line 15 with the code in the code chunk named `table-of-most-accomplished-pilots`
  - Incorrect code in code chunk named `table-of-most-accomplished-pilots` (unested `film` instead of `starships`) leads to naming the wrong pilot as the most accomplished pilot on line 27
  - Incorrect code in code chunk named `table-of-most-accomplished-pilots` (unested `film` instead of `starships`) leads to the use of the wrong character's picture in the image that is sourced in the code chunk named `top-pilot` (it should be a picture of Han Solo, you could use this URL for example: <https://i1.wp.com/twinfinite.net/wp-content/uploads/2015/11/harrison-ford-Mill_3222044i.jpg>).

4. Add comments and suggested changes using the `+` sign beside the line numbers (the first time you do this will trigger the start of your code review. Need help? See [GitHub's how to on reviewing proposed changes in a pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/reviewing-proposed-changes-in-a-pull-request).

5. After you have made all the comments and suggested changes, then add a general comment for the code review, select "Request Changes" and submit your code review.



**When you are done step #5 indicate so on the [sli.do](https://www.sli.do) poll (`#524-L03`).**


### Exercise: Accept suggested changes from a code review:

#### Steps:

1. Practice accepting code changes that you provided as suggestions by revisiting the Pull Requests tab of your copy of the repository and clicking on the pull request titled "Report most accomplished pilots". Scroll through the pull request comments and find the code suggestions. Then click on the "Commit suggestion button" for each suggestion. 

2. Click on the "Show all reviewers" link beside the red "Changes requested"" text. Then click on the `...` beside the reviewer and click "Approve changes".

3. Finally click on the green buttons ("Merge Pull Request" & "Confirm merge") to merge the pull request.

**When you are done step #3 indicate so on the [sli.do](https://www.sli.do) poll (`#524-L03`).**

### Discussion: 

Was there anything we should have done differently with that code review?

*Hint: if I didn't tell you that the top pilot was Han Solo, how would you have known that?*

### How do you not accept a pull request?

In some cases, it might not make sense to merge a pull request. To close a pull request that should not be merged, scroll to the bottom of the pull request page, and look for a gray "Closes pull request" button. This will end move the pull request to the closed pull requests section (similar to closed issues) and does not merge the changes. 

<img src="img/close-pr.png" width=500>

## Some common and useful types of testing

- unit testing
- integration testing
- regression testing

### Unit testing

- Tests whether an individual component of a piece of software works as expected 

#### Think-pair-share:

With your neighbour, come up with a description of an example of a unit test. 

### Integration testing

- Tests whether separate components of a piece of software, which depend upon eachother, work together as expected.
- **An example**: tests that checks whether `Pipeline` from `sklearn` works as expected.

#### Think-pair-share:

With your neighbour, discuss whether it always makes sense for software packages to have integration tests? Do you think your project needs integration tests?

### Regression testing

- Tests that check that recent changes to the code base do not break already implemented features.
- This is done by running all (or a large) subset of tests that already exist after making changes to the code base to ensure they still all pass

This is especially challenging in projects with a large code base when tests are split across many files and functions/code chunks. How can we do this? 

We can take advantage of using tools designed to automate this (e.g., `pytest` & `testthat`) and following their function/method, file & directory naming conventions & organization (more on this later in the lecture). 

## Testing methods:

### Exercise: what are black box & white box testing

Thinking back to the videos you watched before class, answer the following polls on on [sli.do](https://www.sli.do) using the code: `#524-L03`.


## Employing the following practices in your code development workflow helps you write accurate code:

1. Black box testing

2. White box testing

3. Writing your functions and tests close together in time, and improving them both iteratively

4. Automation of tests

## Write unit tests for complex objects 
(e.g., data frames, models, plots)

Writing unit tests for a single value, vector or list is fairly straight forward from what we have learned in 511, but what about more complex object? How do we write tests when our functions return:

- data frames?
- plot objects?
- model objects?

### General guidelings for testing data frames

- Where possible, use functions designed specifically for this (e.g., `dplyr::all_equal` and `pandas.DataFrame.equals`).

- If not possible, test for equality of important values (e.g., specific columns) and attributes (e.g., shape, column names, column type, etc) using the `expect_*` functions inside of `test_that` in R, or via assertions in Python.

### General guidelings for testing plot objects

- Initial tests should be designed to test that plots have expected attributes (e.g., expected mark, correct mapping to axes, etc)

- Once a desired plot is generated, visual regression tests can be used to ensure that further code refactoring does not change the plot function. Tools for this exist for R in the [`vdiffr`](https://github.com/r-lib/vdiffr) package. AFAIK the Python tools in this space have only been developed/used for GUI & web apps, perhpas they could be used for plots as well? I have not yet tried (nor found any examples of anyone who has).

Consider this function, what tests might we write for it?


```R
library(testthat)

#' scatter2d 
#'
#' A short-cut function for creating 2 dimensional scatterplots via ggplot2.
#'
#' @param data data.frame or tibble
#' @param x unquoted column name to plot on the x-axis from data data.frame or tibble
#' @param y unquoted column name to plot on the y-axis from data data.frame or tibble
#'
#' @return
#' @export
#'
#' @examples
#' scatter2d(mtcars, hp, mpg)
scatter2d <- function(data, x, y) {
    ggplot2::ggplot(data, ggplot2::aes(x = {{x}}, y = {{y}})) +
        ggplot2::geom_point()
}
```

Let's see how we can get `ggplot2` object attributes by first creating an object with our function, and then poking around at the object:


```R
plot2d <- scatter2d(mtcars, hp, mpg)
plot2d
```


![png](03_lecture-code-review-and-testing_files/03_lecture-code-review-and-testing_29_0.png)


Can we find the an attribute that tells us it has a `geom_point` attribute?


```R
#plot2d$layers
#plot2d$layers[[1]]$geom
class(plot2d$layers[[1]]$geom)
```


<ol class=list-inline>
	<li>'GeomPoint'</li>
	<li>'Geom'</li>
	<li>'ggproto'</li>
	<li>'gg'</li>
</ol>



Can we find the an attribute that tells us that the variables have been correctly mapped to the axes?


```R
# x-axes
#plot$mapping$x
rlang::get_expr(plot$mapping$x)
```


    hp



```R
# y-axes
#plot$mapping$y
rlang::get_expr(plot$mapping$y)
```


    mpg


Great, now we know enough that can write some basic tests for our function. This function will need a plot to test on, so we need to create that first within our `test_that` chunk.


```R
test_that('Plot should use geom_point and map x to x-axis, and y to y-axis.', {
    p <- scatter2d(mtcars, hp, mpg)
    expect_true("GeomPoint" %in% c(class(p$layers[[1]]$geom)))
    expect_true("hp"  == rlang::get_expr(p$mapping$x))
    expect_true("mpg" == rlang::get_expr(p$mapping$y))
})
```

### Other attributes you might want to test?

- Labels via `"Some label" == p$labels$x` for the x-axis, for example
- That a variable is mapped to colour via `a_variable == rlang::get_expr(p$colour)`, for example
- That the plot is facetted via `"FacetGrid" %in% class(rlang::get_expr(side_by_side_world$facet))`

### General guidelings for testing model objects

- Initial tests should be designed to test that models have expected attributes and results
- Only secondarily, may you want to compare to existing methods (rationale for this being second: what if their tests are wrong? Or worse, what if they don't have any!)

### But I have another type of object? How do I test it?

If you don't know where to start writing tests for the object you plan to use or return in your function, try the following:

- make such an object and interactively explore it

- look at other packages that have functions and return the same kind of object, what do they test for?

## How testthat works:

To run all tests in an R package that uses `testthat`, run the following from the R console with the working directory being set as the package's root directory:

```
devtools::test()
```

This command is a shortcut for `testthat::test_dir()`, and it runs all the files that live in `tests/testthat/` that start with `test`.

*Source: [R Packages, Chapter 10](https://r-pkgs.org/tests.html)*

### Organizing tests for your R package:

Let's explore the `reader` package!

- https://github.com/tidyverse/readr

### Organizing tests for your R package:

Tests are organised hierarchically: **expectations** are grouped into **tests** which are organised in **files**:

- An **expectation** is the atom of testing. It describes the expected result of a computation: Does it have the right value and right class? Does it produce error messages when it should? An expectation automates visual checking of results in the console. Expectations are functions that start with `expect_`.

- A **test** groups together multiple expectations to test the output from a simple function, a range of possibilities for a single parameter from a more complicated function, or tightly related functionality from across multiple functions. This is why they are sometimes called **unit** as they test one unit of functionality. A test is created with `test_that()`.

- A **file** groups together multiple related tests. Files are given a human readable name with `context()`.

*Source: [R Packages, Chapter 10](https://r-pkgs.org/tests.html)*

**Demonstration** of `pytest` (time permitted)

## How pytest works:

Let's explore the `pandas` package!

- https://github.com/pandas-dev/pandas

## How pytest works:

To run all tests in an Python package that uses `pytest`, run the following from the command line with the working directory being set as the package's root directory:

```
poetry run pytest
```

> Note: because we are using Poetry to build our packages, we need to prefix the pytest command with `poetry run` so that the tests are run in our package's virtual environment.

This command runs a recursive search (downward from the directory where this command is run) for files that are prefixed with `test_*.py` or `*_test.py` files which are imported by their test package name. From these files, it will run the functions whose names are pre-fixed with `test`.

**Demonstration** of `pytest` (time permitted)

### General guidelines for test data and helper functions:

- Keep your tests fast by creating toy data or using built-in data (e.g, `mtcars`) that you can feed to your unit tests. If you create toy data, do this within the unit test code block/function that uses that data. 
- If your tests need to be DRY'ed out in **R**, then:
    - put your helper functions in a file in the `tests/testthat` directory that and pre-fix the filename with `helper` so that they will be run before the tests.
    - store your data as a file in the `tests` directory.
- If your tests need to be DRY'ed out in **Python**, then:
    - **easier**: put your helper functions in the tests files where they are called. Do not use `test` in the name for these functions. 
    - **more flexible, but requires more effort**: either store your data as a file in the `tests` directory or use [pytest fixtures](https://www.tutorialspoint.com/pytest/pytest_fixtures.htm) to generate data in a function before the tests are run. Fixtures can also be used for keeping helper functions in a separate file.

## Summary

What were the biggest take homes and/or most important new things you learned today?

Enter your answers on the [sli.do](https://www.sli.do) poll (`#DSCI-L03`) and I will summarize and post the results here after class.

## Where are we headed next?

- What is code coverage, why is it important and how do we measure it?
- Upping our debugging skills
