# Milestone 3

In this milestone, you will write the unit tests and function internals for your R package, as well as setup continuous integration and deployment of your Python package, as well as polish its documentation.

## R package checklist

In the last milestone, you created your R package structure and empty functions with documentation. In this milestone, you will focus on two things for your R package: writing unit tests for your function specifications and writing the internal code for your functions. **Recall that each team member should write at least one function in R and one function in Python and unit tests for both functions.** 

Before starting your work we encourage you to go through the bullet points below so that you can plan the milestone and assign tasks to individual team members. Note that your GitHub issues is one of the primary sources for us to see your work devision and contribution.  

**By the end of this milestone, we should be able to install and use your R package functions from GitHub** (you are not expected to publish your package on CRAN during this course, just GitHub).

### 1. Write test cases and code iteratively
rubric={accuracy:20,quality:10,mechanics:10}

- Before writing any code, revisit your function specifications from last week and revise them if needed. As you do this, think critically about what function inputs you expect from the user and what your function is supposed to do (*e.g.,* return). 

- Write a unit tests for each specified function using `testthat`. `test_that` code blocks do not need to be wrapped in a function. Each function should have 3 to 5 edge cases tested to ensure that the function returns what is expected to the user. Group these test cases in a sensible way so that what is being tested matches the string associated with the `test_that` code blocks. This might mean that you may end up with 2-3 `test_that` code blocks per function. Remember, when writing your tests, build them around your function specifications and requirements.

- After writing your unit tests, write the internal code for your R functions.

- Write function code and tests in close temporal proximity with each other. The process of writing function code and test cases will be iterative; there will be several rounds of writing tests $\rightarrow$ function improvement $\rightarrow$ writing more tests $\rightarrow$ function improvement $\rightarrow$ writing more tests $\rightarrow$ function improvement, etc. 

- Make sure that the tests cover all branches (e.g., if your function has an if statement, you should have tests where the if statement is true, and where the if statement is false.

- As you develop your code and test cases, update your code documentation so that it makes sense with any of the changes you have made. Do not forget to also document your test functions.  

- Check whether the code passes all the unit tests you have written using the `devtools::test()` function.

#### Exception handling 
rubric={quality:10}
- The function should be written defensively. That is, it should handle incorrect input and errors detected during execution via throwing exceptions with useful error messages, and there should be tests to confirm that the exceptions result in the expected behaviour of the function. 

#### Planning and organizing your work
- Any ideas/notes that you generate that are related to your assigned function should be recorded in the corresponding issue you created in milestone 2. The issue should be closed by the end of milestone 3.

- If you think of new ideas or test cases and you do not have time to implement them in this milestone, create an issue for them which you can complete during the next milestone. 

## Python package checklist

In the last milestone, you wrote your tests and function internals for your Python package. In this milestone you will setup continuous integration and deployment of your Python package, as well as polish its documentation.


### 1. GitHub actions workflow for continuous integration
rubric={mechanics:10}

Your task here is to make sure the workflow in [`.github/workflows/build.yml`](https://github.com/UBC-MDS/cookiecutter-ubc-mds/blob/main/%7B%7Bcookiecutter.project_slug%7D%7D/.github/workflows/build.yml) is correctly configured so that at a minimum, it runs the test suite and style checkers on pushes and pull requests to your project's repository's deployment branch (typically the `main` branch). At time of submission, we expect that your project successfully runs this workflow.

A couple things you might need to change in your `.github/workflows/build.yml` file:

1. Ensure the deployment branch (typically the `main` branch) is correctly specified on lines 7 & 10

2. Ensure that the correct Python version is listed on lines 21 and 24 (it should match the version in your `pyproject.toml` file)

### 2. GitHub actions workflow for continuous deployment
rubric={mechanics:10}

Your task here is to make sure the workflow in [`.github/workflows/deploy.yml`](https://github.com/UBC-MDS/cookiecutter-ubc-mds/blob/main/%7B%7Bcookiecutter.project_slug%7D%7D/.github/workflows/deploy.yml) is correctly configured so it runs the test suite, style checkers and deplys to package to test PyPI on pushes to your project's repository's deployment branch (typically the `main` branch). At time of submission, we expect that your project successfully runs this workflow. This should be evidenced by a green release button on your package repository's README.

A couple things you might need to change in your `.github/workflows/deploy.yml` file:

1. Ensure the deployment branch (typically the `main` branch) is correctly specified on lines 7

2. Ensure that the correct Python version is listed on line 14 (it should match the version in your `pyproject.toml` file)

3. **New note:** Remove the testing of package versions from the test file (this was added to the cookiecutter template by mistake and interferes with the automated version bumping)

### 3. Documentation
rubric={reasoning:10}

Your package documentation should be very clear by the end of this milestone and deployed by ReadTheDocs. All docstrings for all functions should be rendered using the `napolean` Sphinx extnesion and readable on ReadTheDocs. Your documentation should also include a demonstration of how to use each function in the package, so that any user with minimal Python expertise would be able to run your package functions and play around with them.



## Specific expectations for this milestone are:
rubric={mechanics:10}

1. You should be committing to git every time you work on this project. The git commit messages should be meaningful. These will be marked. It is OK if one or two are less meaningful, but most should be.
2. In this project, we ask you to follow [the GitHub Flow workflow](https://guides.github.com/introduction/flow/). In particular, once the repositories are set up, each team member will 
    - create a branch
    - work on the function you are responsible for in this branch
    - add commits 
    - open a pull request
    - wait for the code review and feedback from another team member, and once you have addressed the feedback from the other team member(s), one of them will merge your pull request 
3. Use GitHub for project-related communication. 
    - Use GitHub issues to communicate with team mates (as opposed to email or Slack).
    - Create project boards using GitHub and link tasks to issues.
    - Create GitHub milestones to group related issues.  In particular, make a milestone for this milestone called `milestone3` and put all the relevant issues linked to it.
4. Use proper grammar and full sentences throughout the project, especially in your `README`. 

## Submission instructions
rubric={mechanics:10}

In the textbox provided on Canvas for the Milestone 3 assignment you must include:
1. The URL for each of your your public projects' repositories
2. The URL to a release for each of your projects' repositories

## Resources to help you on your way:

### Python  
- [Python Packages book](https://py-pkgs.org/)
- [`convertempPy` Python package example](https://github.com/ttimbers/convertempPy)

### R  
- [R Packages book](https://r-pkgs.org/)
- [`convertempr` R package example](https://github.com/ttimbers/convertempr)
