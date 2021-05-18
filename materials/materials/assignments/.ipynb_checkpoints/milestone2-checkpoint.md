# Milestone2

In this milestone, you will write the unit tests and function internals for your Python package, as well as setup the R package structure and function specifications.

## Python package checklist

In the last milestone, you created your Python package structure and empty functions with documentation. In this milestone, you will focus on two things for your Python package: writing unit tests for your function specifications and writing the internal code for your functions. **Recall that each team member should write at least one function in R and one function in Python and unit tests for both functions.** 

Before starting your work we encourage you to go through the bullet points below so that you can plan the milestone and assign tasks to individual team members. Note that your GitHub issues is one of the primary sources for us to see your work devision and contribution.  

**By the end of this milestone, we should be able to install and use your Python package functions from GitHub** (you do not need to publish your package on PyPI yet).

### 1. Write test cases and code iteratively
rubric={accuracy:20,quality:10,mechanics:10}

- Before writing any code, revisit your function specifications from last week and revise them if needed. As you do this, think critically about what function inputs you expect from the user and what your function is supposed to do (*e.g.,* return). 

- Write a unit test function for each specified function, which is named after the function being tested (e.g., if the function is named `foo` then the unit test function is named `test_foo`). The unit test function should test 3 to 5 edge cases to ensure that the function returns what is expected to the user. When writing your tests, build them around your function specifications and requirements.

- After writing your unit tests, write the internal code for your Python functions.

- Write function code and tests in close temporal proximity with each other. The process of writing function code and test cases will be iterative; there will be several rounds of writing tests $\rightarrow$ function improvement $\rightarrow$ writing more tests $\rightarrow$ function improvement $\rightarrow$ writing more tests $\rightarrow$ function improvement, etc. 

- Make sure that the tests cover all branches (e.g., if your function has an if statement, you should have tests where the if statement is true, and where the if statement is false.

- As you develop your code and test cases, update your code documentation so that it makes sense with any of the changes you have made. Do not forget to also document your test functions.  

- Check whether the code passes the unit tests you have written using the [`pytest` package](https://docs.pytest.org/en/latest/getting-started.html).

#### Exception handling 
rubric={quality:10}
- The function should be written defensively. That is, it should handle incorrect input and errors detected during execution via throwing exceptions with useful error messages, and there should be tests to confirm that the exceptions result in the expected behaviour of the function. 

#### Planning and organizing your work
- Any ideas/notes that you generate that are related to your assigned function should be recorded in the corresponding issue you created in milestone 1. The issue should be closed by the end of milestone 2.

- If you think of new ideas or test cases and you do not have time to implement them in this milestone, create an issue for them which you can complete during the next milestone. 

## R package checklist

### 1. Create project structure for the R project
rubric={mechanics:20}

1. Create [project structure for the R package](https://r-pkgs.org/whole-game.html) and push it as a public repository in the [UBC-MDS organization](https://github.com/UBC-MDS/) on Github.com. 

1. The name of the repository should be relevant to the package/project topics.

1. For now choose the MIT license. You may change it later when you learn more about licenses.  

1. Use [`usethis::use_code_of_conduct`](https://usethis.r-lib.org/reference/use_code_of_conduct.html) to add a code of conduct. You may want to customize it further to suit your group.

1. Add the team members as authors to the `DESCRIPTION` file.
 
1. Use [`usethis::use_tidy_contributing()`](https://usethis.r-lib.org/reference/tidyverse.html) to add a `CONTRIBUTING.md` file to your package. This file will live in `.github` and it will create that folder if it does not already exist. Edit the boiler plate document this gives to to reflect your contribution strategy that your team has agreed upon. 

1. Outline the package you would like to build in the `README.Rmd` file. (This can be identical for both projects at this point in the project). In particular, your `README.md` should contain:  
    - a summary paragraph that describes the project at a high level
    - a bulleted list of the functions (and datasets if applicable) that will be included in the package (this should be a 1-2 sentence description for each function/dataset)
    - a paragraph describing where your packages fit into the R ecosystem (are there any other R packages that have the same/similar functionality? Provide links to any that do. If none exist, then clearly state this as well).  

### 2. R package function specifications
rubric={quality:10}

For this milestone you will write R function documentation that will serve as specifications, but you will **NOT** write any code for your package functions. Specifically, set-up empty functions (with appropriate function names) containing no code in the files where you will eventually write code. Write function documentation (e.g., complete roxygen2 comments). These are the functions you wrote about in your proposal.


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
    - Create GitHub milestones to group related issues.  In particular, make a milestone for this milestone called `milestone2` and put all the relevant issues linked to it.
4. Use proper grammar and full sentences throughout the project, especially in your `README`. 

## Submission instructions
rubric={mechanics:10}

In the textbox provided on Canvas for the Milestone 2 assignment you must include:
1. The URL for each of your your public projects' repositories
2. The URL to a release for each of your projects repositories

## Resources to help you on your way:

### Python  
- [Python Packages book](https://py-pkgs.org/)
- [`convertempPy` Python package example](https://github.com/ttimbers/convertempPy)

### R  
- [R Packages book](https://r-pkgs.org/)
- [`convertempr` R package example](https://github.com/ttimbers/convertempr)
