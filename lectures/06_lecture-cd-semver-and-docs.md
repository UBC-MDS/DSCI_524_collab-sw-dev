## DSCI 524 - Collaborative Software Development

### Lecture 6: Introductions to Continuous Development (CD), package documentation & publishing

#### 2020-03-11

### Note before we get started:

For your Python packages - see the Cookiecutter Quickstart for a coles notes on everything you need to do for your package this week: https://github.com/UBC-MDS/cookiecutter-ubc-mds/blob/master/README.md#quickstart

## Lecture 6 learning objectives:
By the end of this lecture, students should be able to:
- [Define continuous deployment](#Continous-Deployment-(CD))
- [Explain why continuous deployment is superior to manually deploying software](#Why-use-CD?)
- [Use GitHub Actions to set-up automated deployment of Python packages upon push to the master branch](#Using-GitHub-Actions-to-perform-CD-for-your-Python-package)
- [Explain semantic versioning, and define what constitutes patch, minor, major and breaking changes](#Semantic-versioning)
- [Write conventional commit messages that are useful for semantic release](#Conventional-commit-messages)
- [Generate well formatted function and package-level documentation for Python packages using Sphinx & Read the Docs](#Package-level-documentation-for-Python)
- [Generate well formatted function and package-level documentation for R using Roxygen and `pkgdown`](#Package-level-documentation-for-R)
- [Publish Python packages to test PyPI](#Publishing-your-Python-package-for-this-milestone:)
- [Publish R packages to GitHub, document how to install them via `devtools::install_github`](#Publishing-your-R-package-for-this-milestone:)

## Continous Deployment (CD)

Defined as the practice of automating the deployment of software that has successfully run through your test-suite.

For example, upon merging a pull request to master, an automation process builds the Python package and publishes to PyPI without further human intervention. 

### Why use CD?

- little to no effort in deploying new version of the software allows new features to be rolled out quickly and frequently
- also allows for quick implementation and release of bug fixes
- deployment can be done by many contributors, not just one or two people with a high level of Software Engineering expertise

### Why use CD?

Perhaps this story is more convincing:

*The company, let’s call them ABC Corp, had 16 instances of the same software, each as a different white label hosted on separate Linux machines in their data center. What I ended up watching (for 3 hours) was how the client remotely connected to each machine individually and did a “capistrano deploy”. For those unfamiliar, Capistrano is essentially a scripting tool which allows for remote execution of various tasks. The deployment process involved running multiple commands on each machine and then doing manual testing to make sure it worked.*

*The best part was that this developer and one other were the only two in the whole company who knew how to run the deployment, meaning they were forbidden from going on vacation at the same time. And if one of them was sick, the other had the responsibility all for themselves. This deployment process was done once every two weeks.*

[*Source*](https://levelup.gitconnected.com/heres-why-continuous-integration-and-deployment-is-so-important-to-the-software-development-c0caeead5881)*: Tylor Borgeson*


Infrequent & manual deployment makes me feel like this when it comes time to do it:

![](https://media.giphy.com/media/bEVKYB487Lqxy/giphy.gif)

*and so it can become a viscious cycle of delaying deployment because its hard, and then making it harder to do deployment because a lot of changes have been made since the last deployment...*

So to avoid this, we are going to do continuous deployment when we can! And where we can't, we will automate as much as we can up until the point where we need to manually step in.

## Using GitHub Actions to perform CD for your Python package

We will be building off what we learned last class about continuous integration with GitHub actions for Python. What we need to change to make a continuous deployment work for our package?

- change the event trigger

- change the runner to one machine - ubuntu

- bump the version

- create a release on GitHub that corresponds to that version

- build our package

- publish to (test) PyPI




```python
import IPython
poll = "https://app.sli.do/event/njqzylol"
IPython.display.IFrame(poll, 500, 700)
```





<iframe
    width="500"
    height="700"
    src="https://app.sli.do/event/njqzylol"
    frameborder="0"
    allowfullscreen
></iframe>




### Exercise: read [`release.yml`](https://github.com/UBC-MDS/cookiecutter-ubc-mds/blob/master/%7B%7Bcookiecutter.project_slug%7D%7D/.github/workflows/release.yml)

To make sure we understand what is happening in our workflow that performs CD, let's convert each **step** to a human-readable explanation:

1. checkout our repository files from GitHub and put them on the runner

2. Sets up Python on the runner

3. Installs our package and the package dependencies

4. Check Style of package code and test suite

5. Run test suite

6. Upload coverage report to codecov.io

7. 

8. 

9. 

10. 

11. 

12. 

> Note: I filled in the steps we went over last class, so you can just fill in the new stuff

### How can we automate version bumping?

Let's look at the step that accomplishes this:

```
- name: Bump version and tagging and publish
      run: |
        git config --local user.email "action@github.com"
        git config --local user.name "GitHub Action"
        git pull origin master
        poetry run semantic-release version
        poetry version $(grep "version" */__init__.py | cut -d "'" -f 2 | cut -d '"' -f 2)
        git commit -m "Add changes" -a
```

Our key command in this step is `poetry run semantic-release version`. 

[Python semantic-release](https://python-semantic-release.readthedocs.io/en/latest/) is a Python tool which parses commit messages looking for keywords to indicate how to bump the version. It bumps the version in the `__init__.py` file of your package, and then we use `poetry version` and some regex to grab that version from `__init__.py` and also update the `pyproject.toml` file.

To understand how it works so that we can use it, we need to understand **semantic versioning** and how to write **conventional commit** messages.

Let's unpack eack of these on its own.

## Semantic versioning

- When we make changes and publish new versions of our packages, we should tag these with a version number so that we and others can view and use older versions of the package if needed. 


- These version numbers should also communicate something about how the underlying code has changed from one version to the next. 

- Semantic versioning is an agreed upon "code" by developers that gives meaning to version number changes, so developers and users can make meaningful predictions about how code changes between versions from looking solely at the version numbers.

- Semantic versioning assumes version 1.0.0 defines the API, and the changes going forward use that as a starting reference.

## Semantic versioning

Given a version number `MAJOR.MINOR.PATCH` (e.g., `2.3.1`), increment the:

- MAJOR version when you make incompatible API changes (often called breaking changes 💥) 

- MINOR version when you add functionality in a backwards compatible manner ✨↩️

- PATCH version when you make backwards compatible bug fixes 🐞

*Source: https://semver.org/*

### Semantic versioning case study

**Case 1:** In June 2009, Python bumped versions from 3.0.1, some changes in the new release included:
- Addition of an ordered dictionary type
- A pure Python reference implementation of the import statement
- New syntax for nested with statements

**Case 2:** In Dec 2017, Python bumped versions from 3.6.3, some changes in the new release included:

- Fixed several issues in printing tracebacks (`PyTraceBack_Print()`).
- Fix the interactive interpreter looping endlessly when no memory.
- Fixed an assertion failure in Python parser in case of a bad `unicodedata.normalize()`

**Case 3:** In Feb 2008, Python bumped versions from 2.7.17, some changes in the new release included:
- `print` became a function
- integer division resulted in creation of a float, instead of an integer
- Some well-known APIs no longer returned lists (e.g., `dict.keys`, `dict.values`, `map`)

### Exercise: name that semantic version release

Reading the three cases posted above, think about whether each should be a major, minor or patch version bump. Answer the poll below when prompted.


```python
poll = "https://app.sli.do/event/njqzylol"
IPython.display.IFrame(poll, 500, 700)
```





<iframe
    width="500"
    height="700"
    src="https://app.sli.do/event/njqzylol"
    frameborder="0"
    allowfullscreen
></iframe>




## Conventional commit messages

Python semantic-release by default uses a parser that works on the conventional (or Angular) commit message style, which is:

```
<type>(optional scope): succinct description of the change

(optional body: the motivation for the change and contrast this with previous behavior)

(optional footer: note BREAKING CHANGES here, as well as any issues to be closed)
```


How to affect semantic versioning with conventional commit messages:
- a commit with the type `fix` leads to a patch version bump
- a commit with the type `feat` leads to a minor version bump
- a commit with a body or footer that starts with `BREAKING CHANGE:` - these can be of any type

> Note - commit types other than `fix` and `feat` are allowed. Recommeneded ones include `docs`, `style`, `refactor`, `test`, `ci` and [others](https://github.com/angular/angular/blob/master/CONTRIBUTING.md#type).

### An example of a conventional commit message

```
git commit -m "feat(function_x): added the ability to initialize a project even if a pyproject.toml file exists 
```

What kind of version bump would this result in?


```python
poll = "https://app.sli.do/event/njqzylol"
IPython.display.IFrame(poll, 500, 700)
```





<iframe
    width="500"
    height="700"
    src="https://app.sli.do/event/njqzylol"
    frameborder="0"
    allowfullscreen
></iframe>




### Another example of a conventional commit message

```
git commit -m "feat: change to use of `%>%` to add new layers to ggplot objects

BREAKING CHANGE: `+` operator will no longer work for adding new layers to ggplot objects after this release
```

What kind of version bump would this result in?


```python
poll = "https://app.sli.do/event/njqzylol"
IPython.display.IFrame(poll, 500, 700)
```





<iframe
    width="500"
    height="700"
    src="https://app.sli.do/event/njqzylol"
    frameborder="0"
    allowfullscreen
></iframe>




### Some practical notes for usage in your packages:

0. You must add `python-semantic-release` as a dev dependency via poetry

1. You must add the following to the tool section of your `pyproject.toml` file for this to work (filling in `<package_name>` with the appropriate value):
    ```
    [tool.semantic_release]
    version_variable = "<package_name>/__init__.py:__version__"
    version_source = "commit"
    upload_to_pypi = "false"
    patch_without_tag = "true"
    ```
2. If `feat` or `BREAKING CHANGES:` are not included in the commits when a pull request is merged to master, by default Python's `semantic-release` bumps the patch version.

### Some practical notes for usage in your packages:

3. Given that you are working with master branch protection, you will need to add two addtional steps to `release.yml`. The reason for this, is that this workflow to bump versions and deploy the package is triggered to run **after** the pull request is merged to master. Therefore, when we bump the versions in the `pyproject.toml` file and the `package/__init__.py` file (the two places in our package where the version must be stored) we need to push these changes to the master branch - however this is problematic given that we have set-up master branch protection!

    What are we to do? The most straightforward thing appears to be to use a bot to briefly turn off master brancg protection just before we push the files where we bumped the version, and then use the bot to turn it back on again after pushing. To do this, we will use the [`benjefferies/branch-protection-bot` action](https://github.com/benjefferies/branch-protection-bot).
    
    Looking at [`release.yml`](https://github.com/UBC-MDS/cookiecutter-ubc-mds/blob/master/%7B%7Bcookiecutter.project_slug%7D%7D/.github/workflows/release.yml), we will add the `branch-protection-bot` action to **turn off** master branch protection after the step named "checkout" but before the step named "Bump package versions". We will also add the `branch-protection-bot` action to **turn on** master branch protection after the step named "Push package version changes" but before the step named "Get release tag version from package version".
    
    Below is the section of our [`release.yml`](https://github.com/UBC-MDS/cookiecutter-ubc-mds/blob/master/%7B%7Bcookiecutter.project_slug%7D%7D/.github/workflows/release.yml) **before** we add the `branch-protection-bot`:
    
    ```
    - name: checkout
      uses: actions/checkout@master
      with:
        ref: master
        fetch-depth: '0'
    - name: Bump package versions
      run: |
        git config --local user.email "action@github.com"
        git config --local user.name "GitHub Action"
        poetry run semantic-release version
        poetry version $(grep "version" */__init__.py | cut -d "'" -f 2 | cut -d '"' -f 2)
        git commit -m "Bump versions" -a
    - name: Push package version changes
      uses: ad-m/github-push-action@master
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
    - name: Get release tag version from package version
      run: |
        echo ::set-output name=release_tag::$(grep "version" */__init__.py | cut -d "'" -f 2 | cut -d '"' -f 2)
      id: release
    ```
    
    Below is the section of our [`release.yml`](https://github.com/UBC-MDS/cookiecutter-ubc-mds/blob/master/%7B%7Bcookiecutter.project_slug%7D%7D/.github/workflows/release.yml) **after** we add the `branch-protection-bot`:
    
    ```
    - name: checkout
      uses: actions/checkout@master
      with:
        ref: master
        fetch-depth: '0'
    - name: Temporarily disable "include administrators" branch protection
      uses: benjefferies/branch-protection-bot@master
      if: always()
      with:
          access-token: ${{ secrets.ACCESS_TOKEN }}
    - name: Bump package versions
      run: |
        git config --local user.email "action@github.com"
        git config --local user.name "GitHub Action"
        poetry run semantic-release version
        poetry version $(grep "version" */__init__.py | cut -d "'" -f 2 | cut -d '"' -f 2)
        git commit -m "Bump versions" -a
    - name: Push package version changes
      uses: ad-m/github-push-action@master
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
    - name: Enable "include administrators" branch protection
      uses: benjefferies/branch-protection-bot@master
      if: always()  # Force to always run this step to ensure "include administrators" is always turned back on
      with:
        access-token: ${{ secrets.ACCESS_TOKEN }}
        owner: <github_username_or_org>
        repo: <github_repo_name>
    - name: Get release tag version from package version
      run: |
        echo ::set-output name=release_tag::$(grep "version" */__init__.py | cut -d "'" -f 2 | cut -d '"' -f 2)
      id: release
    ```
    
    Finally, to make this work you will need to add one of your team members personal GitHub access tokens as a GitHub secret named `ACCESS_TOKEN` (see [here](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line) for how to get your personal GitHub access token).

### Demo of Continous Deployment!

- <https://github.com/ttimbers/convertempPy>

### What about CD with R packages

- This is not a common practice (yet!). One reason for this could be that CRAN has a policy where they only want to see updates every 1-2 months.

- Semantic versioning is used in Tidyverse R packages, but creating versions is done manually

## Package-level documentation for Python

There are several levels of documentation possible for Python packages:
- code-level documentation (formatted docstrings)
- package-level documentation via [`sphinx`](https://www.sphinx-doc.org/en/master/index.html)
- package websites (via [Read the Docs](https://readthedocs.org/))

### Code & package-level documentation

- We learned the basics of how to write formatted docstrings for our functions in DSCI 511


- These docstrings can not only be accessed via `?function_name`, but can also be used to automatically generate package-level documentation via [`sphinx`](https://www.sphinx-doc.org/en/master/index.html)


- We already did this with our toy `foocat` package by:
    - adding sphinx as a dev dependency via `poetry add --dev sphinx`
    - and then ran `poetry run make html` from the docs directory

### Code & package-level documentation

- To have `sphinx` correctly render the docstring as package-level documentation, we need to either write our docstrings in the correct format for restructured text (RST) or we can use the `sphinx` extension `napolean` that can render Numpy- or Google-style docstrings (which are much easier for you to write and read).

### Example of RST formatted docstrings:

```
:type path: str
:param field_storage: The :class:`FileStorage` instance to wrap
:type field_storage: FileStorage
:param temporary: Whether or not to delete the file when the File
   instance is destructed
:type temporary: bool
:returns: A buffered writable file descriptor
:rtype: BufferedFileStorage
```

### Example of Numpy-style docstrings:

```
Summary line.

    Extended description of function.

    Parameters
    ----------
    arg1 : int
        Description of arg1
    arg2 : str
        Description of arg2

    Returns
    -------
    bool
        Description of return value
```

### Code & package-level documentation

When using Numpy-style docstrings, we need to do the following:

- add `sphinxcontrib-napoleon` as a dev dependency via `poetry add --dev`

- add `extensions = ['sphinx.ext.napoleon']` to the docs configuration file (`docs/conf.py`) - we have already done this for you in the Cookiecutter template.

### Editing & Rendering package-level documentation

- As we did in the toy `foocat` package, we render the docs via running `poetry run make html` from the docs directory

- *Note: it is not essential that you locally render the docs, as we will see next that Read the Docs does this for your on their remote machines, however it is a best practice to do so because it is a lot faster than Read the Docs and therefore editing and proof-reading is more efficient when done locally.*

### Editing & Rendering package-level documentation

- The Python community has been heavily invested in ReStructuredText (rst) as a mark-up language for a long time, and thus `sphinx` works best when used with that as opposed to markdown (although it is possible, see [here](https://www.sphinx-doc.org/en/master/usage/markdown.html) for details).

- [ReStructuredText cheat sheet](https://thomas-cokelaer.info/tutorials/sphinx/rest_syntax.html)

### Package websites (via [Read the Docs](https://readthedocs.org/))

The standard practice for hosting and sharing docs in the Python community is to use [Read the Docs](https://readthedocs.org/)

- Similar to codecov.io, to use Read the Docs with our package, we need to link it to our GitHub repository

- Read the Docs then checks out the files from the GitHub repo and uses their remote machines to render and serve your documentation

- To do this, Read the Docs needs access to the packages `pyproject.toml` file. This is done via the creation of a `.readthedocs.yml` file in the root of your project that looks like this:

```
build:
  image: latest
python:
  version: 3.7
  pip_install: true
  extra_requirements:
    - docs
```

*note - the version of Python specified here has to be a version that your package can be installed with!*

## Package documentation for R

There are several levels of documentation possible for R packages:
- code-level documentation (Roxygen-style comments)
- vignettes
- package websites (via `pkgdown`)

### Code-level documentation (Roxygen-style comments)

- We learned the basics of how to write Roxygen-style comments in DSCI 511
- In the package context, there are Namespace tags you should know about:
    - `@export` - this should be added to all package functions you want your user to know about
    - `@NoRd` - this should be added to helper/internal helper functions that you don't want your user to know about

### Vignettes
- Think of your vignette as a demonstration of how someone would use your function to solve a problem. 

- It should demonstrate how the individual functions in your package work, as well as how they can be integrated together.

- To create a template for your vignette, run:
    ```
    usethis::use_vignette("package_name-vignette")
    ```
    
- Add content to that file and knit it when done.

As an example, here's the `dplyr` vignette: <https://cran.r-project.org/web/packages/dplyr/vignettes/dplyr.html>

### Package websites (via [`pkgdown](https://pkgdown.r-lib.org/)`)

- Vignettes are very helpful, however they are not that discoverable by others, websites are a much easier way to share your package with others

- The `pkgdown` R package let's you build a beautiful website for your R package in 4 steps!

    1. Install `pkgdown`: `install.packages("pkgdown")

    2. Run `pkgdown::build_site()` from the root of your project, and commit and push the changes made by this.

    3. Turn on GitHub pages in your package repository, setting `master branch / docs folder` as the source.
    
    4. Oh wait, there's no step 4! 🎉

In addition to the beautiful website, `pkgdown` automatically links to your vignette under the articles section of the website!!! 🎉🎉🎉

## Publishing your Python package for this milestone:

For this course, we will only publish your package on test PyPI. You will use continuous deployment via the `release.yml` workflow file to do this.

To get your packages README and important links to show-up on the test PyPI page for your package, add the  following information to the [tool.poetry] table in pyproject.toml

```
readme = "README.md"
homepage = "https://github.com/<github_username>/<github_repo>"
repository = "https://github.com/<github_username>/<github_repo>"
documentation = 'https://<package_name>.readthedocs.io'
```

## Publishing your R package for this milestone:

For this course, we will only publish your package on GitHub, not CRAN. For this to work, you need to push your package code to GitHub and provide users these instructions to download, build and install your package:

```
# install.packages("devtools")
devtools::install_github("ttimbers/convertempr")
```

Next week we will talk about publishing on CRAN.

## Summary

 What did we learn today? Biggest take homes?
 
 - semantic versioning and automated versioning
 
 - how to use GitHub Actions
 
 - Difference between CI & CD
 

## Where to next:

- Tha package indices, PyPI and CRAN
- Peer review of data science software packages
- Working with other teams (specifications, opening issues, how to ask for help, etc) 
- Licenses

### Semantic versioning case study - answers

In 2008, Python bumped versions from 2.7.17 to 3.0.0. Some changes in the 3.0.0 release included:
- `print` became a function
- integer division resulted in creation of a float, instead of an integer
- Some well-known APIs no longer returned lists (e.g., `dict.keys`, `dict.values`, `map`)
- and many more (see [here](https://docs.python.org/3.0/whatsnew/3.0.html) if interested)

[*Source*](https://docs.python.org/3.0/whatsnew/3.0.html)

In 2009, Python bumped versions from 3.0.1 to 3.1.0. Some changes in the 3.1.0 release included:
- Addition of an ordered dictionary type
- A pure Python reference implementation of the import statement
- New syntax for nested with statements

[*Source*](https://www.python.org/download/releases/3.1/)

In 2017, Python bumped versions from 3.6.3 to 3.6.4. Some changes in the 3.6.4 release included:

- Fixed several issues in printing tracebacks (`PyTraceBack_Print()`).
- Fix the interactive interpreter looping endlessly when no memory.
- Fixed an assertion failure in Python parser in case of a bad `unicodedata.normalize()`

[*Source*](https://docs.python.org/3.6/whatsnew/changelog.html#python-3-6-4-final)
