# DSCI 524 - Collaborative Software Development

# Milestone3: Integration testing and continuous integration (CI)

## Submission guidelines
rubric={mechanics:2}

In this course, each team will be creating two public repositories in the [UBC-MDS organization](https://github.com/UBC-MDS/) on Github.com, one for Python package and one for R package. Before submitting, create a release on your project repository that is named with a version of 1.1.0 (or higher), and each team member **must** submit a URL for that release in their `milestone3` repo's `README.md` file. 


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


## Milestone 3 details (new!)
rubric={reasoning:16,writing:10,quality:6,mechanics:16}

- By the end of this milestone, your both packages should be fully documented, and another user should be able to download and install them and play around with them. 
- Your Python package should be published on test PyPI with installation instructions in the appropriate `README.md`. 
- Your R package should be published just via GitHub and your installation instructions in the appropriate `README.md` should recommend that the package be installed via `devtools`. 
  - `devtools::install_github("PACKAGE_NAME")`


## Specific expectations for this milestone are:

### Continuous Integration (CI)
- Set up GitHub Actions for Continuous Integration (CI) and Continuous Deployment (CD) with Python. 
- Set up GitHub Actions workflows for CI with R. 
     
### Integration tests 

- Add adequate integration tests in each package, if applicable. 
- At submission time for this milestone, all GitHub Action workflows in your packages repos should build without error. To facilitate this, before submitting or accepting a pull request, make it a practice check the build status and read GitHub Actions logs. 

### Additional tests

- Revisit your test cases and add additional test cases, if required, in your Python and R packages. At the end of this milestone, we want you to have 90% branch coverage (or higher!). The coverage should be communicated by a [codecov.io](https://codecov.io/) button on your package GitHub repository README's.
- You may ask other team members to examine your test cases and add new ones, if appropriate. 
- At each step, check the build status and read GitHub Actions logs. 

### Documentation

- Remember that next week other groups are going to download your package and carry out peer review. So make sure that your both packages are fully documented. In particular,  

  - use [Read the Docs](https://ubc-mds.github.io/py-pkgs/whole-game.html#pkg-docs) for documentation in Python.   
  - use [vignette](https://r-pkgs.org/vignettes.html#vignettes) package-wide documentation in R, as well as the [pkgdown](https://pkgdown.r-lib.org/) R package to set up a website for your package.
  - include usage (this means a runnable example - give them toy data!) and installation instructions in `README.md` files
  - examine docstrings of your functions
  - examine whether one-line descriptions of your unit test functions make sense
  
### Other miscellaneous notes
- You should continue using [the GitHub Flow workflow](https://guides.github.com/introduction/flow/), 
 GitHub issues, milestones, and project boards effectively. 
 - Review the ROpenSci and PyOpenSci package reviewer guides and checklists to make sure your package meets the criteria on which it will be reviewed on next week in our peer review:
   - ROpenSci reviewer [guide](https://devguide.ropensci.org/reviewerguide.html) and [checklist](https://devguide.ropensci.org/reviewtemplate.html)
   - PyOpenSci reviewer [guide](https://www.pyopensci.org/dev_guide/peer_review/reviewer_guide.html) and [checklist](https://www.pyopensci.org/dev_guide/appendices/templates#review-template)

- Before submission, all GitHub Actions workflows should run without error and be advertised as such using badges in the `README.md` of your R and Python repositories. 
