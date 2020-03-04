## DSCI 524 - Collaborative Software Development

### Lecture 4: Debugging and package documentation

#### 2020-03-04

## Lecture 4 learning objectives:
By the end of this lecture, students should be able to:

- [Define code, test and branch coverage. Explain why high coverage in each of these metrics is desired.](#Coverage)
- [Calculate code coverage in R and Python](#Calculating-coverage-in-Python)
- [Manage package dependencies in R and Python packages.](#Dealing-with-other-package-dependencies-in-your-package)
- [Create a reprex to get help](#Create-a-reprex-to-get-help)
- [Use `traceback`, `options(error = recover)`, and `browser` to debug R code](#Debugging-tools-in-R-&-Python)
- [Use `traceback.print_last`, `pdb.pm` and `breakpoint` to debug Python code](#Debugging-tools-in-R-&-Python)

## Coverage

**Definition:** Proportion of system being executed by the test suite.

- usually reported as a percentage: $$Coverage = \frac{covered}{covered + uncovered} * 100$$



### Coverage metrics:

There are many, but here are the ones our automated tools in this course will calculate for you:

| Metric | Description                           | Dependent upon control flow |
|--------|---------------------------------------|-----------------------------|
| line   | lines of code that tests execute      | No                          |
| branch | number of branches (independent code segments) that tests execute | Yes                         |


### What exactly is a branch?

```
def my_function(x):
    # Branch 1
    if condition_met:
        y = function_a(x)
        z = function_b(y)
    # Branch 2
    else: 
        y = function_b(x)
        z = function_c(y)
    return z
```

*Adapted from: <http://www.ncover.com/blog/code-coverage-metrics-branch-coverage/>*

## How are line and branch coverage different?

Consider the same example we just saw and the unit test below, let's manually calculate the coverage using line and branch coverage metrics:

```
def my_function(x):
    # Branch 1
    if x == "pony":
        y = function_a(x)
        z = function_b(y)
    # Branch 2
    else: 
        y = function_c(x)
        w = function_d(y)
        z = function_e(y)
    return z
```

```
def test_my_function():
    assert my_function("pony") == ("Actually a unicorn")
```

*Note: function definitions are not counted as lines when calculating coverage*

#### Using branch as the coverage metric:

$Coverage = \frac{covered}{covered + uncovered} * 100$

$Coverage = \frac{1}{1 + 1} * 100$

$Coverage = 50\%$

#### Using line as the coverage metric:

$Coverage = \frac{covered}{covered + uncovered} * 100$

$Coverage = \frac{4}{4 + 4} * 100$

$Coverage = 50\%$

### But wait, line coverage can be misleading... 

Let's alter our function and re-calculate line and branch coverage:

```
def my_function(x):
    # Branch 1
    if x == "pony":
        y = function_a(x)
        z = function_b(y)
        print(z)
        print("some important message")
        print("another important message")
        print("a less important message")
        print("just makin' stuff up here...")
        print("out of things to say...")
        print("how creative can I be...")
        print("I guess not very...")
    # Branch 2
    else: 
        y = function_c(x)
        w = function_d(y)
        z = function_e(y)
    return z
```

```
def test_my_function():
    assert my_function("pony") == ("Actually a unicorn")
```

#### Using branch as the coverage metric:

$Coverage = \frac{covered}{covered + uncovered} * 100$

$Coverage = \frac{1}{1 + 1} * 100$

$Coverage = 50\%$

#### Using line as the coverage metric:

$Coverage = \frac{covered}{covered + uncovered} * 100$

$Coverage = \frac{12}{12 + 4} * 100$

$Coverage = 75\%$

🤯

### Take home message:

Use branch coverage when you can, especially if your code uses control flow!

### Calculating coverage in Python

We use the plugin  tool [`pytest-cov`](https://github.com/pytest-dev/pytest-cov) to do this. 

Install as a package dependency via poetry:
```
poetry add --dev pytest-cov
```

### Calculating coverage in Python

To calculate line coverage and print it to the terminal:
```
poetry run pytest --cov=<project_slug> 
```

To calculate line coverage and print it to the terminal:
```
poetry run pytest --cov-branch --cov=<project_slug>
```

Next week we will learn to use GitHub actions to link this to [codecov.io](https://codecov.io/) to get a shiny button ✨ that advertises your code coverage!

### Exercise: Calculate coverage in Python

Let's practice calculating coverage in Python!

#### Steps:

1. Fork & clone this GitHub repository: <https://github.com/ttimbers/big_abs> 

2. Using a command line, navigate to the root of this repository and run `poetry install`

3. Calculate the line coverage and print it to the terminal via `poetry run pytest --cov=big_abs`

4. Calculate the branch coverage and print it to the terminal via `poetry run pytest --cov-branch --cov=big_abs`

**When you are done step #4 indicate so on the [sli.do](https://www.sli.do) poll (`#524-L04`).**


### Exercise: Improve branch coverage

Let's add some additional test cases to improve the branch coverage for the `big_abs` Python package!

#### Steps:
1. Open `big_abs/big_abs.py` and `tests/test_big_abs.py` and identify the branch(es) that the current test case covers

2. Add at least one new test case that will improve branch coverage. Prove this to yourself by calculating the branch coverage and print it to the terminal via `poetry run pytest --cov-branch --cov=big_abs`

**When you are done step #2 indicate so on the [sli.do](https://www.sli.do) poll (`#524-L04`).**

### Calculating coverage in R

We use the [`covr`](https://covr.r-lib.org/) R package to do this. 

Install via R console:
```
install.packages("covr")
```

### Calculating coverage in R

To calculate line coverage and have it show in the viewer pane in RStudio:
```
covr::report()
```

Currently `covr` does not have the functionality to calculate branch coverage. Thus this is up to you in R to calculate this by hand if you really want to know. 

> Why has this not been implemented? It has been in an now unsupported package (see [here](https://github.com/MangoTheCat/testCoverage)), but its implementation was too complicated for others to understand. Automating the calculation of branch coverage is non-trivial, and this is a perfect demonstration of that.

## Dealing with other package dependencies in your package

### Dealing with package dependencies in R

- When we write code in our package that uses functions from other packages we need to import those functions from the namespace of their packages.

- In R, we do this via `use_package`, which adds that package to the “Imports” section of DESCRIPTION

- We also need to refer to that package in our function code, there are two ways to do this:
  1. refer the function by `package::fun_name` (e.g., `dplyer::filter`) whenever you use the function in your code
  2. add the function to your packages namespace so that you can just refer to it as your normally would. To do this add `@importFrom <package_name> <function_or_operator>` to the Roxygen documentation of the function that you would like to use the function from the other package in and then use `document()` to update the DESCRIPTION and NAMESPACE file. 
  
*It is recommended to use method 1 (`pkg::fun_name`) because it is more explicit on what external functions your package code depends on (making it easier to read for collaborators, including future you). The trade off is that it’s a little more work to write.*

### The pipe, `%>%`, a special dependency

- Given the ubiquity of the pipe operator, `%>%`, in R, there is a function that automates exposing to your entire package: `usethis::use_pipe()`

- Note, in general, the tidyverse team does not recommend using the pipe in packages unless they are personal, low use packages, or “pro” packages with a lot of data wrangling because:
  - In most cases it is really an unnecessary dependency 
  - It is not that readable for folks who do not typically use the pipe
  - makes debugging more challenging 
  
So, should you use the pipe in your package? The answer is, it depends on your package's scope, aims and goals. Also, this is probably your first package, so it doesn't have to be perfect. If using the pipe helps you get the job done this time around, go for it. Just know that if you aim to ever build a widely used package, you probably do not want to depend on it.

### Dealing with package dependencies in Python

- Given that we are using Poetry to manage our Python packages, we can take advantage of Poetry to manage our package dependencies. 

- To add a package dependency (one that our package functions depend on), we use `poetry add <package_name>`.

- When we do this Poetry adds this depenedency to the `pyproject.toml` file under the `[tool.poetry.dependencies]` table as well as to the `poetry.lock` file.

- Then we need to import these dependencies in our `.py` files where our functions live. Given that [PEP 08](https://www.python.org/dev/peps/pep-0008/) states that: _"Imports are always put at the top of the file, just after any module comments and docstrings, and before module globals and constants."_ we typically do this at the very top of the file, even when we are writing code that will end up in a package.

  > It is possible to import packages inside a function, and there is sound reasoning in doing so to make your code more readable, however, it goes against convention and so you need to get your whole team to agree to this if you want to do things this way.

### How does Poetry `install` use `pyproject.toml` & `poetry.lock`

- The install command reads the `pyproject.toml` file from the current project, resolves the dependencies, and installs them.

- If there is a `poetry.lock` file in the current directory, it will use the exact versions from there instead of resolving them. This ensures that everyone using the library will get the same versions of the dependencies.

- If there is no `poetry.lock` file, Poetry will create one after dependency resolution.

*Source: [Poetry install documentation](https://python-poetry.org/docs/cli/#install)*


## Debugging tools in R & Python



|Task |    |  R  | Python |
|-----|----|-----|--------|
| <img src="img/traceback.png" width=200> | Look at the death certificate to get some general information about the death | `traceback` | `traceback.print_last` |
| <img src="img/options.png" width=200> | Do a post mortem autopsy find further evidence of why it died  | `options(error = recover)` | `pdb.postmortem` |
| <img src="img/browser.png" width=200> | Revive the dead so it may walk again |  `browser` | `breakpoint` |

*Source (images and R functions): [Jenny Bryan's rstudio::conf 2020 talk](https://resources.rstudio.com/rstudio-conf-2020/object-of-type-closure-is-not-subsettable-jenny-bryan)*

### Using `print_last` in Python


```python
import traceback
```


```python
x = [2, 4, 6]
x[3]
```


```python
traceback.print_last()
```

## Using `pdb.postmortem` to do a postmortem


```python
import pdb
import sys
```


```python
x = [2, 4, 6]
x[3]
```


```python
pdb.pm()
```

### Using `breakpoint` in Python:


```python
x = [2, 4, 6]
breakpoint()
x[3]
```

## Create a reprex to get help

As you work on projects in MDS, and then your work in the real world, you are going to be doing MANY things you haven't done before, and you are going to hit points when you need to ask others for help. 

If you watched Jenny's rstudio::conf 2020 video this week, you learned about the importance of creating a reproducible and minimal working example to optimize your chance of getting help. 

Furthermore, writing a reproducible and minimal working example will not only help you get help more easily, often times the process of doing this will help you find your own bug and fix it!

### Tools to help you create a reprex

- [reprex R package](https://reprex.tidyverse.org/)
- [reprexpy Python package](https://reprexpy.readthedocs.io/en/latest/)

## Summary

What were the biggest take homes and/or most important new things you learned today?

Enter your answers on the [sli.do](https://www.sli.do) poll (`#524-L04`) and I will summarize and post the results here after class.

## Where are we headed next?

- Package bells & whistles! Including
    - Continuous integration
    - Documentation
    - Package versioning
    - Package publishing
