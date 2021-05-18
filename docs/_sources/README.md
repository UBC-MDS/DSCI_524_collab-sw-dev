# DSCI 524: Collaborative Software Development

How to exploit practices from collaborative software development techniques in data scientific workflows. Appropriate use of the software life cycle, unit testing / continuous integration, and packaging for use by others.

## Learning Outcomes

By the end of the course, students are expected to be able to:
- complete a project that demonstrates appropriate use of collaborative software development processes and tools, including:
    - packaging code for use by others, including the specification of dependencies/requirements
    - using advanced distributed version control workflows and features (e.g., GitHub flow, master branch protection, code reviews, project boards and issue tracking) to effectively manage a multi-person project
    - writing comprehensive test suites
    - carrying out continuous integration via GitHub Actions
    - deploying packaged software using semantic versioning
    - writing clear and helpful documentation
    - selecting software licenses that best suit the project
    - critically evaluating work of others and providing constructive feedback

See [here](lecture_learning_objectives.md) for lecture-by-lecture learning objectives

## Teaching Team

| Position | Name  | Slack Handle |
| :------: | :---: | :----------: |
| Lecture Instructor | Tiffany Timbers  | `@tiff` |
| Lab Instructor | Tiffany Timbers| `@tiff`  |
| Teaching Assistant | TBD | TBD |
| Teaching Assistant | TBD | TBD |
| Teaching Assistant | TBD | TBD |
| Teaching Assistant | TBD | TBD |

## Deliverables
This is a project-based course where you will work collaboratively in groups to develop a Python and a R software package. In lecture and lab, we'll work on the skills and concepts that you need to learn to complete the project. You will work in randomly assigned groups of three (or four, if needed) for the project milestones. There are also some individual weekly assignments that act as stepping stones to the project milestones. Finally, because collaboration is so important in data science, 1/5 of your final grade will be devoted to how good of a team member you were. A combination of peer evaluation and GitHub history will be used to evaluate this.

| Assessment | weight | Deadline |
|------------|----------|----------|
| Project Proposal and Milestone 1: Coming up with a topic, and setting up Python package structure & function specifications | 15% | 2020-02-27 11:59 PT |
| Create your own toy Python package (graded for completion) | 2.5 % | 2020-02-27 11:59 PT |
| Milestone 2: writing the code and tests for the Python package, setting up R package structure & function specifications | 20% |  2020-03-06 11:59 PT |
| Create your own toy R package (graded for completion) | 2.5 % | 2020-03-06 11:59 PT |
| Milestone 3: writing the code and tests for the R package, Setting up continuous integration and all the other bells and whistles for the Python package  | 20% | 2020-03-13 11:59 PT |
| Milestone 4: Setting up continuous integration and all the other bells and whistles for the R package | 15% | 2020-03-20 11:59 PT |
| Individual Peer review | 5% | 2020-03-25 11:59 PT |
| Team work reflection | 20% |  2020-03-25 11:59 PT  |

## Lecture Schedule

> Course notes can be found in the course Jupyter book: [https://ubc-mds.github.io/DSCI_524_collab-sw-dev/](https://ubc-mds.github.io/DSCI_524_collab-sw-dev/)

| Lecture  | Topic | Required pre-work | Readings and Resources| Video |
|----------|-------|-------------------|-----------------------|-------|
| 1 |  Introduction to R & Python packages  | <ul><li>[Setting up your system for R packages](https://r-pkgs.org/setup.html)</li><li>[Setting up your system for creating Python packages](https://py-pkgs.org/02-setup#)</li></ul> |  <ul><li>[Package structure and state (R)](https://r-pkgs.org/package-structure-state.html)</li><li>[Package structure and state (Python)](https://py-pkgs.org/04-package-structure#)</li><li>[R Markdown Driven Development](https://emilyriederer.netlify.app/post/rmarkdown-driven-development/)</li></ul> |  
| 2  | Introduction to collaborative software development |  | <ul><li>[GitHub project boards](https://help.github.com/en/github/managing-your-work-on-github/about-project-boards)</li><li>[How To Use Git Branches](https://www.digitalocean.com/community/tutorials/how-to-use-git-branches)</li><li>[GitHub flow](https://githubflow.github.io/)</li><li>[About protected branches](https://docs.github.com/en/github/administering-a-repository/about-protected-branches) |
| 3 | Code reviews, testing and advice for testing complex things | 20 min of videos (by Reid Holmes) to watch: <ul><li>[Why Test?](http://www.youtube.com/watch?v=Uamo4Ej0tWk)</li><li>[Terminology](http://www.youtube.com/watch?v=WKrvx7qCUDI)</li><li>[Properties of Tests](http://www.youtube.com/watch?v=ll1k3Pks3ZA)</li><li>[Introduction to Coverage](http://www.youtube.com/watch?v=iujQEm9oono)</li></ul> | <ul><li>[Testing in R](https://r-pkgs.org/tests.html)</li><li>[Testing in Python](https://py-pkgs.org/05-testing)</li><li>[pytest docs](https://docs.pytest.org/en/latest/)</li></ul> |
| 4 | Testing coverage |  |  |
| 5 | Continous integration (CI) via GitHub Actions |  | <ul><li>[GitHub Actions docs](https://help.github.com/en/actions)</li><li>[Github actions with R](https://ropenscilabs.github.io/actions_sandbox/packageci.html)</li><li>[Continuous integration (Python)](https://py-pkgs.org/08-ci-cd#ci-cd-tools)</li></ul> |
| 6 | Continuous deployment, versioning & package documentation |  | <ul><li>[Semantic versioning](https://semver.org/)</ul><li>[R: Object Documentation](https://r-pkgs.org/man.html)</li><li>[R: Vignettes](https://r-pkgs.org/vignettes.html)</li><li>[`pkgdown`](https://pkgdown.r-lib.org/)<li>[Documentation (Python)](https://py-pkgs.org/06-documentation)</li></ul> |
| 7 | Publishing your package on the package indices (CRAN & PyPI), and peer review of data science R & Python packages |  | <ul><li>[rOpenSci Packages: Development, Maintenance, and Peer Review](https://devguide.ropensci.org/)</li><li>[The pyOpenSci Developer Guide](https://www.pyopensci.org/dev_guide/intro)</li></ul> |  |
| 8 | Copyright & Licenses |  | [Who owns the code?](https://asp-software.org/www/misv_resources/business-articles/who-owns-the-code/) | |

## Textbooks:
- [R packages](https://r-pkgs.org/) by Hadley Wickham and Jenny Bryan
- [Python packages](https://py-pkgs.org/) by Tomas Beuzen and Tiffany Timbers

## Class Schedule & office hours

See [calendar](https://ubc-mds.github.io/calendar/).

## Policies

Please see the general [MDS policies](https://ubc-mds.github.io/policies/).

## Dealing With COVID-19

The [COVID-19 pandemic](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/events-as-they-happen) has affected us all in different ways: it's okay to not be okay, and we all need to support each other during this time. With that said:

- My (virtual) door is always open, please feel free to talk to me about how you're doing and if/how I can help you (and if I can't help you, I can point you in the direction of someone who can);
- You don't ever need to explain yourself; if you need support, need to miss a class, or need extra time for an assignment, just ask;
- UBC has [great student support resources](https://students.ubc.ca/covid19) related to COVID-19 (and otherwise).

Further, teaching/learning an intense graduate course like MDS online is a very new concept to all of us. If you have feedback on how I can improve the teaching experience, don't hesitate to reach out - I'm sure things won't be perfect from the get-go.

Finally, here is an official statement from UBC regarding the online learning experience:

>*During this pandemic, the shift to online learning has greatly altered teaching and studying at UBC, including changes to health and safety considerations. Keep in mind that some UBC courses might cover topics that are censored or considered illegal by non-Canadian governments. This may include, but is not limited to, human rights, representative government, defamation, obscenity, gender or sexuality, and historical or current geopolitical controversies. If you are a student living abroad, you will be subject to the laws of your local jurisdiction, and your local authorities might limit your access to course material or take punitive action against you. UBC is strongly committed to academic freedom, but has no control over foreign authorities (please visit http://www.calendar.ubc.ca/vancouver/index.cfm?tree=3,33,86,0 for an articulation of the values of the University conveyed in the Senate Statement on Academic Freedom). Thus, we recognize that students will have legitimate reason to exercise caution in studying certain subjects. If you have concerns regarding your personal situation, consider postponing taking a course with manifest risks, until you are back on campus or reach out to your academic advisor to find substitute courses. For further information and support, please visit: http://academic.ubc.ca/support-resources/freedom-expression.*
