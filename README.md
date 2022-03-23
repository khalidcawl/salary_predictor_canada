
# Salary predictor for tech employees in Canada


### About

The aim of this project is to create a reproducible machine learning model that
can predict the annual salary of a tech employee in Canada given their years of 
experience, skills, education, and job type.

The data set for the project is the [Stack Overflow Annual Developer
Survey](https://insights.stackoverflow.com/survey) (Silge 2021) data.
After carrying EDA (see src/EDA.ipynb file), I came up with some features that
could predict the expected yearly compensation of tech
employees.The reproduce the analysis, you may follow these steps.

The data set used in this project is from the [Stack Overflow Annual
Developer Survey](https://insights.stackoverflow.com/survey), which is
conducted annually. The survey data set has nearly 80,000 responses.
Several useful features could be extracted from this survey such as
education level, location, the language used, job type, all of which are
potentially associated with annual compensation.

### Usage

![The dependency diagram of the Makefile](out.png)

### Dependencies

-   GNU make 4.2.1

There are two suggested ways to run this analysis:

#### 1. Using Docker

*note - the instructions in this section also depends on running this in
a unix shell (e.g., terminal or Git Bash)*

To run this analysis using Docker, clone/download this repository, use
the command line to navigate to the root of this project on your
computer, and then type the following (filling in PATH_ON_YOUR_COMPUTER
with the absolute path to the root of this project on your computer).

    docker run --rm -v PATH_ON_YOUR_COMPUTER:/home/tech_salary_predictor_canada_us ssingh90/tech_salary_predictor_canada_us make -C '/home/tech_salary_predictor_canada_us' all

To reset the repo to a clean state, with no intermediate or results
files, run the following command at the command line/terminal from the
root directory of this project:

    docker run --rm -v PATH_ON_YOUR_COMPUTER:/home/tech_salary_predictor_canada_us ssingh90/tech_salary_predictor_canada_us make -C '/home/tech_salary_predictor_canada_us' clean

#### 2. Without using Docker

The Python dependencies can be found in the tech_salary_pred_env.yaml
file. However, you don’t have to manually install these dependencies.
You need to install conda (v4.10.3) and then follow the installation
instructions described below.
Note: You need tech_salary_pred_env.yaml file to do the following steps
for this option.

To replicate the analysis, clone this GitHub repository, install the
dependencies listed below, and run the following command at the command
line/terminal from the root directory of this project:

The R dependencies are listed below:

-   R version 3.6.1 and R packages:
    -   tidyverse==1.3.1
    -   caret==6.0.90
    -   docopt==0.7.1
    -   testthat=3.0.4

<!-- -->

    # create conda environment
    conda env create -f tech_salary_pred_env.yaml
    conda activate tech_salary_pred_env

    make all

To reset the repo to a clean state, with no intermediate or results
files, run the following command at the command line/terminal from the
root directory of this project:

    make clean

### Report

The final report can be found
[here](https://ubc-mds.github.io/tech_salary_predictor_canada_us/report.html)

### Exploratory data analysis

After carrying out EDA, we realize that the following features might
help us predict the salary of tech workers: years of experience,
education level, programming languages used, and their role (full-stack
developer, front-end developer, etc.)

Based on the data corresponding to the four features in the survey, we
created plots to visualize how the four features impact on the annual
compensation of developers. As we can see from the plots, a large
professional coding years and certain programming language
skills(Bash,C,SQL,HTML,Java) would have positive influence on the
average annual compensation. Then we dig a little deeper by visualizing
the combination of these two features in a heatmap, which shows the
average annual compensation given the number of professional coding
years and combination of programming language skills.

### Modelling

We built a multiple linear regression model to see the relationship
between these features and the annual compensation.

To simplify our analysis, we focused on Canada. We initially thought of
building the model on Canada and USA data. However, we learned from our
EDA that there is pay disparity and currency conversion involved. In the
future, we plan to include USA in the model and handle those
discrepancies.

Additionally, the regression model can also provide other important
information such as the weight of each feature or how much each of those
features we picked contributes to the overall predicted annual
compensation.

To evaluate our model and selected features, we plan to use R squared
score as the score metric and see how well the tuned model can
generalize on the test data. For the purpose of visualizing the
performance of our prediction, we will plot the regression line on the
scattered data points to infer whether the relationship between features
and response is linear or not.

The research question is:

> To predict the expected salary of a tech employee in Canada given
> their number of years of experience, education level, programming
> languages used, and role

This topic is a predictive question, also extending to the following
sub-questions:

1.  Which features have a significant statistical effect on the response
    (inference)?
2.  Whether the model is robust (model estimation, a predictive problem)
3.  The confidence interval of predictions (predictive)

### LICENSE

This database, The Public 2019 Stack Overflow Developer Survey Results,
is made available under the Open Database License (ODbL):
<http://opendatacommons.org/licenses/odbl/1.0/>. Any rights in
individual contents of the database are licensed under the Database
Contents License: <http://opendatacommons.org/licenses/dbcl/1.0/>

# References

<div id="refs" class="references csl-bib-body hanging-indent">

<div id="ref-stack_overflow_survey" class="csl-entry">

Silge, Julia. 2021. “2021 Developer Survey.” 2021.
<https://insights.stackoverflow.com/survey/2021>.

</div>

</div>