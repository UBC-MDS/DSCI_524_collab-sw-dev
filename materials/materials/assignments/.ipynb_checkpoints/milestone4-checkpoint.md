# Milestone 4

In this milestone, you will setup continuous integration of your R package and polish its documentation, as well as discuss and review your projects' license choice (and change it if you deem it is warranted). Next week others in the course will be installing and test driving your packages as part of our peer review. So this week is your chance to polish them as well before that happens! Finally, you will open an issue for each of your software packages in the UBC MDS software-review-2021 repository following the ROpenSci and PyOpenSci review submission templates to prepare your packages for peer review next week.

## R package checklist

### 1. GitHub actions workflow for continuous integration
rubric={mechanics:35}

Your task here is to add continuous integration workflows using GitHub Actions for running R CMD check and your tests and sending the results to <https://codecov.io/>. In particular, you want to use the `usethis` package functions to add the following two workflows to your project:

- <https://github.com/r-lib/actions/blob/master/.github/workflows/check-standard.yaml>
- <https://github.com/r-lib/actions/blob/master/.github/workflows/test-coverage.yaml>

At time of submission, we expect that your project successfully runs these workflows.

### 2. Documentation
rubric={reasoning:25}

Your package documentation should be very clear by the end of this milestone. To do this, you should use [vignette](https://r-pkgs.org/vignettes.html#vignettes) package-wide documentation in R, as well as the [pkgdown](https://pkgdown.r-lib.org/) R package to set up a website for your package. In doing this make sure you:
  - include a full usage demonstration of all your package functions (this means a runnable example - give them data!) in your vignette
  - include installation instructions in the `README.Rmd` file
  - examine Roxygen2 documentation of your functions to make sure it is clear

#### Planning and organizing your work
Keep using issues to plan and organize your work! 

## License checklist
rubric={reasoning:10}

Examine the license for your project and consider whether this is the choice you want to make, or whether you want to change the license. Discuss and reason the license choice by opening issues in both Python and R repositories. As it is likely to be a very similar discussion for both projects, one of these issues can just link to the other issue where it is thoroughly dicussed.

### 3. Initiate a package review request
rubric={mechanics:10}

- Each team must initiate a review request by opening an issue per package in the [UBC-MDS/software-review-2021](https://github.com/UBC-MDS/software-review-2021) repository. 
    - For initiating a reviewing request in R, use [this template](https://github.com/ropensci/software-review/blob/master/.github/ISSUE_TEMPLATE/A-submit-software-for-review.md). 
    - For initiating a reviewing request in Python, use the template under Submit Software for Review at [this link](https://github.com/pyOpenSci/software-review/issues/new/choose).

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

In the textbox provided on Canvas for the Milestone 4 assignment you must include:
1. The URL for each of your your public projects' repositories
2. The URL to a release for each of your projects' repositories
3. The URL to the issue that thoroughly dicusses and reasons the license choice

## Resources to help you on your way:

### Python  
- [Python Packages book](https://py-pkgs.org/)
- [`convertempPy` Python package example](https://github.com/ttimbers/convertempPy)

### R  
- [R Packages book](https://r-pkgs.org/)
- [`convertempr` R package example](https://github.com/ttimbers/convertempr)
