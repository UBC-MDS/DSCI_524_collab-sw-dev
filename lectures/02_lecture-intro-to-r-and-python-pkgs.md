## DSCI 524 - Collaborative Software Development

### Lecture 2: Introduction to R & Python packages

#### 2020-02-26

## Lecture 2 learning objectives:
By the end of this lecture, students should be able to:
- [Explain the circumstances in which one should consider creating a package for their code](#When-to-start-writing-an-R-or-Python-package)
- [Name the key files and directories in both R & Python pacakges and describe the function of each](#On-going-lecture-exercise)
- [Given a function and a unit test written in Python, use a Cookiecutter template and `poetry` to create a small and simple Python package](#The-Whole-Game-in-Python-(30-min))
- [Given a function and a unit test written in R, use `devtools` and `usethis` to create a small and simple R package](#The-Whole-Game-in-R-(30-min))


## When to start writing an R or Python package

- When your DRY radar goes off:

    > It depends on your level of patience for violating the DRY principle, for me the magic number is about 3. If I repeat writing code within a single script or notebook, on the third try hair starts to stand up on the back of my neck and I am irritated sufficiently to either write a funciton or a loop. The same goes with copying files containing functions that I would like to re-use. The third time that I do this, I am convinced that I will likely want to use this code again on another project and thus I should package it to make my life easier. 

- When you think your code has general usefullness others could benefit from: 

    > Another reason to package your code is that you think that it is a general enough solution that other people would find it useful. Doing this can be viewed as an act of altruism that also provides you professional gain by putting your data science skills on display (and padding your CV!).
    
- When you want to share data:

    > The R package ecosystem has found great use in packaging data in addition to Software. Packaging data is beyond the scope of this course, but you should know that it is widely done in R and that you can do it if you want or need to.

## On-going lecture exercise 

As you work through the tutorials below, fill out the missing data in the table below (which tries to match up the corresponding R and Python package key files and directories:

| Description                                            | Python        | R            |
|--------------------------------------------------------|---------------|--------------|
| Online package repository or index                     |               |              |
| Directory for user-facing package functions            |               |              |
| Directory for tests for user-facing package functions  |               |              |
| Directory for documentation                            |               |              |
| Package metadata                                       |               |              |

> Note: at the end of lecture I will post the answers to this table.

## The Whole Game in Python (30 min)

### Activity
In the first half of this lecture we will start to work through [the Whole Game Chapter](https://ubc-mds.github.io/py-pkgs/whole-game.html) from the Python Packages book. There are two instructors and two TAs present to help you when you get stuck. To get our attention please put a sticky note 🗒️ on the top of your laptop 💻, we will keep an eye out for these. Please also chat/problem solve with your neighbours as well.

### Questions
If you have a general question that you think others might be intersted in knowing the answer to, please post it on <https://www.sli.do/> at `#524-L02`. Questions can be asked anonymously or signed. If you like other's questions you can upvote them. I will answer all questions, but due to time constraints, some may be answered on Slack after class.

### But I already did this?
Use this time to work on your Python package layout for your group project then based on the Whole Game Chapter layout. 

---

## 5 min break - get up and move around!

---

## The Whole Game in R (30 min)

### Activity
In the first half of this lecture we will work through [the Whole Game Chapter](https://r-pkgs.org/whole-game.html) from the R Packages book. There are two instructors and two TAs present to help you when you get stuck. To get our attention please put a sticky note 🗒️ on the top of your laptop 💻, we will keep an eye out for these. Please also chat/problem solve with your neighbours as well.

### Questions
If you have a general question that you think others might be intersted in knowing the answer to, please post it on <https://www.sli.do/> at `#524-L02`. Questions can be asked anonymously or signed. If you like other's questions you can upvote them. I will answer all questions, but due to time constraints, some may be answered on Slack after class.

### But I already did this?
Use this time to work on your R package layout for your group project then based on the Whole Game Chapter layout. 

## On-going lecture exercise solution

> Note: to be added at the end of lecture
