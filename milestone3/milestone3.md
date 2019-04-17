Following the meeting with the TA's regarding milestone 2, we had to adapt a bit our project.

# Changes and updates
## Agreement

The first minor thing we added is a checkbox in the survey making sure the subjects aggree that we use the data they provided for our study.

## Musical taste representation

Second, we changed how our survey will ask for the subjects' musical taste. We have a list of pre-defined genres, namely:

- Classical
- Rock
- Pop
- R&B and Soul
- Electronic 
- Folk
- Jazz
- Blues
- Hip hop

For each genre, a subject will have to give a number of how much they listen to this genre, on a scale from 0 to 10. This gives a rough idea as to the proportion of each genre. The TA's told us it might be a good idea to be able to have an absolute value, rather than just a proportion. We thus introduced a new question at the end of the survey, asking how people would consider a 10 in terms of weekly hours. The total number of hours can then be extrapolated. 

## Statistical tests

The biggest change is the way we will draw conclusion from the data. 
Just as specified in milestone 2, each subject can be represented as a vector of 9 values, one value for each genre. The vectors can be grouped by splitting the population into two categories: one for a section/school, and the other for every other sections/schools. The goal is to be able to test whether there is a statistical difference between the two categories distributions. The original idea was to compute a correlation term between aggregated vectors for each category. The aggregation is a mean of every vector in the category. The problem was that the correlation term did not have statistical properties in itself, meaning we could not reject a hypothesis with any confidence value. The TA's thus advised to make use of the **2-sample bootstrap** method [1]. This method can resolve the problem just addressed.

The 2-sample bootstrap method works as follows. A null hypothesis $$H_0$$ is defined as being "The two sets of values are taken from the same population". In the case of our study, rejecting the hypothesis means that two categories have expressed different tastes. A distance metric has to be used in order to compare the value of one category to the value of the other category. This distance metric is used to compute a basis value which is the difference between the original categories' values. A random sampling (with replacement) is done one the original values, and then the distance metric is used again. We thus have one "difference value" for each sample. By doing a lot of different samples and collecting the "difference value", a distribution starts to form. Percentiles can be computed on this distribution, and we can compare the original "difference value" to the distribution drawn from the data. We can check whether the original value is - within a confidence interval - close to the mean of the distribution. In the case where the original value is too far away (taking percentiles into account), then the null hypothesis can be rejected.

An implementation of this has been done in the Jupyter notebook called `bootstrap.ipynb`. First, dummy data is created in order to simulate a situation we could get once the all data from the survey has been gathered. Then the statistical tests are applied to this dummy data. In this simulation, computer science people **do** have a difference in their distribution regarding the other sections. 

# Survey

The survey did not change between last time and now, except for what is mentionned above. It is available here https://docs.google.com/forms/d/e/1FAIpQLScCuFyOoHVOOYsLn-WIURYDwlgJ94Tpd-nMv1eORkGaQ_jjVA/viewform.

# Distribution of the survey

We contacted the people in charge of the mailing lists in order to ask permission to send our survey. They told us that student may use mailing lists, but they are restrained to the mailing list of their section. This is not that good for us because we need diversity, but we also need as much data as possible so we will use it anyway. We will ask our entourage in order to reach more diverse sections. 

# Survey release

We released the survey to some people of our entourage on April 17th and got 18 responses, mostly from people from UNIL in several different sections. The data can be exported as a `csv` file and this is how we will link it back to the script to perform the statistical method. We wanted to upload examples of the results but the TA's advised us not to share the data we gathered as it is considered sensitive.

# What is next

The next step is the data collection. The survey will be opened until we see that no more responses are given. We still have to send the survey to the mailing lists. In the mean time, we can start to use the `csv` file to better adapt the bootstrap script (as now it still uses the dummy data that is not following the format used when exporting from a Google form). Then we will be able to start analyzing the results and do the proper study of the results.

# References

[1] _Two-sample bootstrap tests: When to mix?_ Subhash Lele, Ed Carlstein