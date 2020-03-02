# DSCI 524 - Collaborative Software Development

# Milestone2: Writing function code and tests 

## Submission guidelines
rubric={mechanics:2}

In this course, each team will be creating two public repositories in the [UBC-MDS organization](https://github.com/UBC-MDS/) on Github.com, one for Python package and one for R package. Before submitting, create a release on your project repository named v1.0.0, and each team member **must** submit a URL for that release in their `milestone2` repo's `README.md` file. 


## Overall project goal

During this course you will work collaboratively [in assigned teams of three or four](https://github.ubc.ca/MDS-2019-20/DSCI_524_collab-sw-dev_students/issues/1) to develop a Python and an R software packages. The Python and R packages should do essentially the same thing (you are making one in each language so that you have the opportunity to learn how to do both).
Your package could contain functions that 
- are entirely new to the R or Python ecosystem or 
- improve upon pre-existing functions in either language or
- re-implement existing code/functions that you wish to deepen your understanding of (e.g., last year one student decided to write a linear regression package from scratch).

At the end of this project, these packages should:
- contain at least 3 or 4 useful functions (depending upon your team size) that handle errors gracefully
- be well documented
- have unit and integration tests
- use GitHub actions for continuous integration (with a passing build stamp in the README)
- have a Software Licence that describes how you will permit others to use your work
- have a code of conduct document that describes behavioural expectations of team interactions
- have a contributions document that outlines how the team will work together (expected workflow practices)
- have a Git history that demonstrates the proposed workflow in the CONTRIBUTING.md file was followed and that all group members contributed equally

**IMPORTANT NOTE - after each submission you will receive timely feedback from the TAs for each milestone as issues or inline code comments on your https://github.com/ repos. This feedback MUST be addressed in the next submission. Failure to do this will be reflected in the grading.**


## Milestone 2 details (new!)
rubric={reasoning:12,accuracy:36,quality:12}

In the last milestone, you created your package structure and empty functions with documentation. In this milestone, you will focus on two things: writing function code for both packages and writing unit tests for your functions. **Recall that each team member should write at least one function in R and one function in Python and unit tests for both functions.** 

Before starting your work we encourage you to go through the bullet points below so that you can plan the milestone and assign tasks to individual team members. Note that your GitHub issues is one of the primary sources for us to see your work devision and contribution.  

In this milestone, each team member is expected to do the following: 

### Expectations for each team member 
Below we are listing specific expectations for each team member for this milestone. 

#### Writing code and test cases iteratively
- Before writing your code, think about what function inputs you expect from the user and what your function is supposed to do (e.g., return). 

- Write code for your functions in R and in Python.

- We expect each function to have a unit test function, which is named after the function being tested (e.g., if the function is named `foo` then the unit test function is named `test_foo`). The unit test function should test 2 to 3 edge cases to ensure that the function returns what is expected to the user. When writing your tests, build them around your function specifications and requirements.

- Write function code and tests in close temporal proximity with each other. The process of writing function code and test cases will be iterative; there will be several rounds of writing tests $\rightarrow$ function improvement $\rightarrow$ writing more tests $\rightarrow$ function improvement $\rightarrow$ writing more tests $\rightarrow$ function improvement, etc. 

- Make sure that the tests cover all branches (e.g., if your function has an if statement, you should have tests where the if statement is true, and where the if statement is false.

- As you develop your code and test cases, update your code documentation so that it makes sense with any of the changes you have made. Do not forget to also document your test functions.  

- Check whether the code passes the unit tests you have written. For your Python unit tests use the [`pytest` package](https://docs.pytest.org/en/latest/getting-started.html) and for your R unit tests use the [`testthat` package](https://cran.r-project.org/web/packages/testthat/index.html). 

#### Exception handling 
- The function should be written defensively. That is, it should handle incorrect input and errors detected during execution via throwing exceptions with useful error messages, and there should be tests to confirm that the exceptions result in the expected behaviour of the function. 

#### Planning and organizing your work
- Any ideas/notes that you generate that are related to your assigned function should be recorded in the corresponding issue you created in milestone1. The issue should be closed by the end of milestone2.

- If you think of new ideas or test cases and you do not have time to implement them in this milestone, create an issue for them which you can complete during the next milestone. 

- Similar to milestone1, we expect you to follow [GitHub Flow workflow](https://guides.github.com/introduction/flow/). **Additionally, each team member must do at least one code review and each member must have some part of their code reviewed by other team members. So please make sure that one of the Python or R functions (and its corresponding unit test) you are responsible for is ready to be reviewed by Wednesday, March 4th, end of the day.**

### Expectations for the team project submission

In your team project submission, we will be looking for: 

- The overall quality of your code, tests, exception handling, and documentation 

- Whether your functions do what is expected of them and pass your test cases

- Whether you are following [GitHub Flow workflow](https://guides.github.com/introduction/flow/) or not when you work collaboratively. For instance, for each task, we would like you to follow the following workflow:   
    - create a branch
    - work on your task in this branch
    - add commits 
    - open a pull request (**aim to be at this step by Wednesday (March 4th) end of the day**)
    - wait for the code review and feedback from other team member 
    - review code of other team member via their pull request
    - deploy your changes 
    - merge if your branch is not causing any problems    

- Whether you have adequately documented your Python and R package `README.md` files including:
  - usage and installation instructions
  - functions
  - tests
  
- Whether you are using GitHub issues, milestones, and project boards effectively or not. In particular, we expect you to set-up milestone 2 on GitHub and add relevant issues to it. You should also continue using the GitHub project board that was set up.
   
## Resources to help you on your way:

- A very short [video](https://www.youtube.com/watch?time_continue=4&v=HW0RPaJqm4g) on GitHub code review process
- [GitHub workflow](https://guides.github.com/introduction/flow/)
- [GitHub milestones](https://help.github.com/articles/about-milestones/)

