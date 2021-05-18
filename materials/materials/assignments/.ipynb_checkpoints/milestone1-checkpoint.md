# Milestone1

## Overall project goal

During this course you will work collaboratively in assigned teams of three or four (see groups assigned on Canvas)) to develop a Python and a R software package. The Python and R packages should do essentially the same thing (you are making one in each language so that you have the opportunity to learn how to do both).
Your package could contain functions that: 
- are entirely new to the R or Python ecosystem or 
- improve upon pre-existing functions in either language or
- re-implement existing code/functions that you wish to deepen your understanding of (e.g., in a past year one student decided to write a linear regression package from scratch).

At the end of this project, these packages should:
- contain at least 3 or 4 useful functions (depending upon your team size) that handle errors gracefully
- be well documented
- have unit and integration tests
- use GitHub actions for continuous integration (with a passing build stamp in the `README`)
- have a Software Licence that describes how you will permit others to use your work
- have a code of conduct document that describes behavioural expectations of team interactions
- have a contributions document that outlines how the team will work together (expected workflow practices)
- have a Git history that demonstrates the proposed workflow in the `CONTRIBUTING.md` file was followed and that all group members contributed equally

This lab has two parts: project proposal and milestone1. 

## Milestone 1 checklist

### 1. Team work contract:
rubric={correctness:10}

Similar to what you did in DSCI 522, create a team-work contract. The contract should outline how you are committed to work together so that you are accountable to one another. Again, you may start with your team contract document from 522 and adapt it for your new team. **It is a fairly personal document and please do not push it into your public repositories. Instead, save it somewhere your team can easily share it, and you can share a link to it, or a copy with us in your submission to Canvas to prove you did this.**

### 2. Pick a topic 

Come up with a topic for your project. Discuss the topic with your TA or lab instructor and proceed only after your topic has been approved by one of them. 

### 3. Create project structure for the Python project
rubric={mechanics:40}

1. Create [project structure for python project](https://py-pkgs.org/03-how-to-package-a-python) and push it as a public repository in the [UBC-MDS organization](https://github.com/UBC-MDS/) on Github.com. There is a quickstart guide for setting up the structure for python project, you can find it [here](https://github.com/UBC-MDS/cookiecutter-ubc-mds#quickstart). **This time when you are prompted as whether to include GitHub Actions, say yes! In particular, choose option 3 (build + deploy).**

1. The name of the repositories should be relevant to the package/project topics.

1. During project creation, you will be prompted to pick a license and for now choose the MIT license. You may change it later when you learn more about licenses.  

1. Once the projects have been created, edit `CONTRIBUTORS.md` to add the contributor names (the students on the teams).

1. Edit `CONDUCT.md` to include the code of conduct for  contributing to your project. The intention behind creating this file is fostering a healthy and positive work dynamic. Recall that you already have done  something similar in DSCI 522, and you can start with that document and adapt it for your new team. Note that when you create the project structure with the methods above, a default version of this file will be created. You may choose to use it or adapt it with appropriate attributions. 
 
1. Agree upon a collaboration strategy that describes how you will work together on this project (e.g., [GitHub flow](https://guides.github.com/introduction/flow/) and edit `CONTRIBUTING.md` to reflect your strategy. Again, there will be a default version of this file. You can use it as is or adapt it with appropriate attribution. Here are some example `CONTRIBUTING.md` files for your reference. 

    * [Software Carpentry CONTRIBUTING.md](https://github.com/swcarpentry/r-novice-inflammation/blob/gh-pages/CONTRIBUTING.md)
    * [factory_bot_rails CONTRIBUTING.md](https://github.com/thoughtbot/factory_bot_rails/blob/master/CONTRIBUTING.md)
    * [moby CONTRIBUTING.md](https://github.com/moby/moby/blob/master/CONTRIBUTING.md)


1. Outline the package you would like to build in the `README.md` file. (This can be identical for both projects at this point in the project). In particular, your `README.md` should contain:  
    - a summary paragraph that describes the project at a high level
    - a bulleted list of the functions (and datasets if applicable) that will be included in the package (this should be a 1-2 sentence description for each function/dataset)
    - a paragraph describing where your packages fit into the Python ecosystem (are there any other Python packages that have the same/similar functionality? Provide links to any that do. If none exist, then clearly state this as well).  

### 4. Function specifications
rubric={quality:20}

For this milestone you will write function documentation that will serve as specifications, but you will **NOT** write any code for your package functions. Specifically, set-up empty functions (with appropriate function names) containing no code in the files where you will eventually write code. Write function documentation (e.g., complete docstrings). These are the functions you wrote about in your proposal.

### 5. Manage issues
rubric={mechanics:10}

Manage issues effectively through project boards and milestones, make it clear who is responsible for what and what project milestone each task is associated with. In particular, create an issue for each function in the package. Each of these issues must be assigned to a single person on the team. We want all of you to get coding experience in the project and **each team member should be responsible for a function in R and Python.** So if you are a team of four, you'll be writing four functions for each package and if you are a team of three, you will be writing three functions for each package. 

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
    - Create GitHub milestones to group related issues.  In particular, make a milestone for this milestone called `milestone1` and put all the relevant issues linked to it.
4. Use proper grammar and full sentences throughout the project, especially in your `README`. 

## Submission instructions
rubric={mechanics:10}

In the textbox provided on Canvas for the Milestone 1 assignment you must include:
1. The URL of your public project's repo
2. The URL to a release on your project repo named v0.1.0
3. A link to your team work document that is accessible to the teaching team. Alternatively a copy of your team work document can be pasted there.
    
## Resources to help you on your way:

### Python  
- [Python Packages book](https://py-pkgs.org/)
- [`convertempPy` Python package example](https://github.com/ttimbers/convertempPy)
