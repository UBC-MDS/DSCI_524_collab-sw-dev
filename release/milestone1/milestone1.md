# DSCI 524 - Collaborative Software Development

# Proposal and milestone1

## Submission guidelines
rubric={mechanics:5}
- In this course, each team will be creating two public repositories in the [UBC-MDS organization](https://github.com/UBC-MDS/) on Github.com, one for Python package and one for R package.
Each team member **must** include the URLs of these repositories in the `README.md` file of your `milestone1`'s repository, so that we know where to find your projects.
- Before submitting, create a release on your project repository named v0.1.0 and submit that URL in your `milestone1` repo's `README.md` file. 

## Overall project goal

During this course you will work collaboratively [in assigned teams of three or four](https://github.ubc.ca/MDS-2019-20/DSCI_524_collab-sw-dev_students/issues/1) to develop a Python and a R software package. The Python and R packages should do essentially the same thing (you are making one in each language so that you have the opportunity to learn how to do both).
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

This lab has two parts: project proposal and milestone1. 

## Project proposal

### 1. Pick a topic 
rubric={reasoning:5}

Come up with a topic for your project. Discuss the topic with your TA or lab instructor and proceed only after your topic has been approved by one of them. 

### 2. Create project structure
rubric={mechanics:10,reasoning:5}
1. Create [project structure for python project](https://ubc-mds.github.io/py-pkgs/whole-game.html) and push it as a public repository in the [UBC-MDS organization](https://github.com/UBC-MDS/) on Github.com. 

2. Create [project structure for r project](https://r-pkgs.org/whole-game.html) and push it as a public repository in the [UBC-MDS organization](https://github.com/UBC-MDS/) on Github.com.  

3. The name of the repositories should be relevant to the package/project topics.

4. During project creation, you will be prompted to pick a license and for now choose the MIT license. You may change it later when you learn more about licenses.  

### 3. Edit and/or create team-work documents
rubric={mechanics:2,reasoning:4,writing:4}

1. Once the projects have been created, edit `CONTRIBUTORS.md` to add the contributor names (the students on the teams).

2. Edit `CONDUCT.md` to include the code of conduct for  contributing to your project. The intention behind creating this file is fostering a healthy and positive work dynamic. Recall that you already have done  something similar in DSCI 522, and you can start with that document and adapt it for your new team. Note that when you create the project structure with the methods above, a default version of this file will be created. You may choose to use it or adapt it with appropriate attributions. 
 
3. Similar to what you did in DSCI 522, create a team-work contract and save it as `team_work_contract.md`. The contract should outline how you are committed to work together so that you are accountable to one another. Again, you may start with your team contract document from 522 and adapt it for your new team. **It is a fairly personal document and please do not push it into your public repositories. Instead, push it in your github.ubc.ca's `milestone1` repository.**

4. Agree upon a collaboration strategy that describes how you will work together on this project (e.g., [GitHub flow](https://guides.github.com/introduction/flow/) and edit `CONTRIBUTING.md` to reflect your strategy. Again, there will be a default version of this file. You can use it as is or adapt it with appropriate attribution. Here are some example `CONTRIBUTING.md` files for your reference. 

    * [Software Carpentry CONTRIBUTING.md](https://github.com/swcarpentry/r-novice-inflammation/blob/gh-pages/CONTRIBUTING.md)
    * [factory_bot_rails CONTRIBUTING.md](https://github.com/thoughtbot/factory_bot_rails/blob/master/CONTRIBUTING.md)
    * [moby CONTRIBUTING.md](https://github.com/moby/moby/blob/master/CONTRIBUTING.md)


### 4. Edit `README.md`
rubric={reasoning:10,writing:5}

Outline the package you would like to build in the `README.md` file. (This can be identical for both projects at this point in the project). In particular, your `README.md` should contain: 

1. a summary paragraph that describes the project at a high level

2. a bulleted list of the functions (and datasets if applicable) that will be included in the package (this should be a 1-2 sentence description for each function/dataset)

3. a paragraph describing where your packages fit into the Python and R ecosystems (are there any other Python or R software packages that have the same/similar functionality? Provide links to any that do. If none exist, then clearly state this as well).  

**A reminder to include the URL to your Python and R projects' repositories in your `milestone1` repo's `README.md` file so that we know where to find them.**

**Make sure to finish the above steps before the end of the lab so that TAs can provide you feedback on your topic in writing in the next couple of days.** (Note that the feedback will be given to you by opening issues in your project repositories.)


## Milestone 1: Function specifications, project boards, [GitHub Flow workflow](https://guides.github.com/introduction/flow/)

rubric={reasoning:30,accuracy:6,quality:4}

For this milestone you will write function documentation that will serve as specifications, but you will **NOT** write any code for your package functions. 

#### Specific expectations for this milestone are:

1. Set-up appropriate file/directory structure for your code. 

2. Set-up empty functions (with appropriate function names) containing no code in the files where you will eventually write code. Write function documentation (e.g., complete docstrings). These are the functions you wrote about in your proposal.

3. Using project boards and tasks, make it clear who is responsible for what function. In particular, create an issue for each function in each package. Each of these issues must be assigned to a single person on the team. We want all of you to get coding experience in the project and **each team member should be responsible for a function in R and Python.** So if you are a team of four, you'll be writing four functions for each package and if you are a team of three, you will be writing three functions for each package. 

4. You should be committing to git every time you work on this project. The git commit messages should be meaningful. These will be marked. It is OK if one or two are less meaningful, but most should be.
5. In this project, we ask you to follow [the GitHub Flow workflow](https://guides.github.com/introduction/flow/). In particular, once the repositories are set up, each team member will 
    - create a branch
    - work on the function you are responsible for in this branch
    - add commits 
    - open a pull request
    - wait for the code review and feedback from other team member 
    - review code of other team member via their pull request
    - deploy your changes 
    - merge if your branch is not causing any problems
6. Use GitHub for project-related communication. 
    - Use GitHub issues to communicate with team mates (as opposed to email or Slack).
    - Create project boards using GitHub and link tasks to issues.
    - Create GitHub milestones to group related issues.  In particular, make a milestone for this milestone called `milestone1` and put all the relevant issues linked to it.
    - Set-up master branch protection before you submit this milestone. 

7. For submission, 
    - Include the URL of your public project's repo in the `README.md` file of your `milestone1`'s repo so that we know where to find it.
    - Create a release on your project repo named v0.1.0 and submit that URL in your `milestone1` repo's `README.md` file so we know where to find it.
    - Use proper grammar and full sentences throughout the project, especially in your README. 

## Resources to help you on your way:

### Python  
- [Python package Tutorial](https://ubc-mds.github.io/py-pkgs/whole-game.html)
- [MDS Standard Deviation Python package example](https://github.com/ttimbers/convertempPy)

### R
- [R package Tutorial](https://r-pkgs.org/whole-game.html)
- [MDS Standard Deviation R package example](https://github.com/ttimbers/convertempr)