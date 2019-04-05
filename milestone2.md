# Introduction

The study we will conduct will try to prove the following claim: are musical tastes statistically different across multiple fields of study ? To answer this question, we will propose an online questionnaire that students (of EPFL, UNIL or another university) could take, and then statistical methods can be applied in order to prove our problematic. The questionnaire is planned to be held on a Google Form due to its efficiency and simplicity. The questions are specified below, but we want to address first some potential problems that we had to think about when designing the survey.

# Potential problems addressed

The terms “musical taste” here is meant as a frequency of listening to some genres. The subjects could, for example, fill the survey with genre names. Since the results of survey answers will be merged together, we need some standards for the definition of genres. The initial thought was to propose a list of genres for the participants to choose from, but we were scared that doing it this way will bias the data, as we may provide a list that is too generic. The subjects know better about their favorite genres, so we can rely on their description of the genre they listen to. A mix of both versions was then proposed: We wanted to ask that a subject submits a genre that they like, and have them categorize inside a list that we propose. This way we could pick either the very specific genres of the more general, without the fear of discrimination. An important point would also be to add a “Not in this list” option in our list in case the genre they propose is still not represented. Adding this button means we will have to treat this kind of data by hand if we want to make sense from it.
After some research, we found a similar study [1] where the genres were not directly asked. Instead, the subjects had to give titles and artists names. Thinking about it, it is certainly easier for people to point out to a song they enjoy rather than to give a specific genre. The genre can be then later retrieved by using Spotify’s API [2], the only catch being that a song’s genre can only be retrieved by checking the genre attached to its corresponding album. This new alternative would be realised by having fields that can be filled in, one for each of the following information: title, artist, genre. The genre could be left blank, in which case the song will be queried to the Spotify API. The genres could then be generalised into 9 major categories:
- Classical
- Rock
- Pop
- R&B and Soul
- Electronic 
- Folk
- Jazz
- Blues
- Hip hop

This list will surely be adapted regarding the answers we will get, some might need to be splitted, so might need to be merged. All of the major categories can be found on Wikipedia [3] with subgenres attached to them, and this is what will be used in order to stay as unbiased as possible when generalizing genres.
We looked for genre classification literature but we only found about people using machine learning to extract the genre of songs, which is not what we want here.

The number of results will be a key component of the quality of our analysis to answer the main question. As the number of exclusive fields of study might get bigger than 10, drawing conclusions will be too hard, because there won’t be enough example in each fields. Furthemore, we might encounter the problem of convenience sampling because we will ask to people we know, thus having unbalanced data, with subjects that are ours. The original idea was to compare every subjects together, but this will definitely be undoable due to the reasons just listed. Categorizing the subjects could be done here, by having more global categories of fields:
- Basic sciences
- Architecture and civil engineering
- Computer science
- Social sciences
- Economics

There will then be less categories to compare to one another, but we might still encounter fields that are not well represented. After discussion with the TA’s, the final idea is to have those categories (in order to have groups that have enough samples), but having several binary tests (one field versus everyone else) instead of one big test (every field at the same time). To be more clear on the binary test, we could for example test the hypothesis “The people in computer science listen to different music than the other people”. This way we can tackle the problem with more ease and flexibility. In the questionnaire, the field of study will still be specific, and the grouping will be done automatically by us afterwards.
We will have the fields of EPFL and UNIL as possibilities inside the questionnaire. If someone is from another university, there will be high chances that this person’s field will fall into one of the options. If not, we will have to account for this case and add the possibility to write a new field (that will be once again hand processed after the data collection).
The sample size is expected to be around 60 people.

# Description of questionnaire

The questionnaire will consist of the following questions as basic information:
* What is your age ?
  * Blank field expecting a number.
* What is your gender ?
  * Dropdown list containing options, namely “Male”, “Female”, “Neither of those”.
* What is your field of study ?
  * Dropdown list containing options, namely every sections of EPFL and UNIL, along with “None of those”.
  * If “None of those” has been selected, blank field asking for the field.

Then we will come to the music preference section that will be represented this way:
* Give a song or artist that you listen to. Try to choose a song that represents this artist well enough. If you can, please specify the genre you would classify this song.
  * 3 blank fields expecting song, artist, genre
* Add a new song.
  * Option to add a new genre following the previous format.

We will typically ask for at least two songs, and the maximum number of inputs will be 10. Subjects will probably not put as much as 10, but restricting them to a lower number might cut the most motivated ones.

# Tests

For each field of study, we will a get a list of genres that we can mash together, and extract the frequency of each genre across each field. The frequency of each genre is what will be compared.
As said before, the kind of tests that will be verified are revolving around a hypothesis in the style of “Field X listens to different music than the other fields”. In order to verify or to disprove our claim, we will use correlation tests. 
Once we get the results we can aggregate the data and construct structures from it. Typically, the results can be described as vectors in a n-dimensional space, n being the number of genres (the list of general genres). There will be 1 vector for each field of study, and we can easily merge two or more vectors. Once two vectors are available (one for field X, one for the other fields), a correlation value is easily extracted. A hypothesis can then be verified by using this correlation value, as is specified in [5]
If the sample size is too small in both group (normally less than 30 samples), we need to use t-test to find out is there significant differences between the groups represented by the samples.

# Gathering data

Data gathering will be essential. Each team member will ask their friends to answer the survey, but it will still be sent out to an EPFL mailing list [7] in order to get more diverse results. We will have to ask for a permission to send something to this mailing list because it is restricted and moderated. In case we do not get the permission, we will try to spread the survey even more by ourselves.

# Sample resize

Before we start to gather samples, we will try to have as many samples as possible, because Generally, the larger the sample size, the more statistically significant it is—meaning there’s less of a chance that your results happened by coincidence.
But after gathering all the samples, due to different classification to different groups (e.g. divide all the samples in CS group  and no-CS group), the confidence level might be different with same margin of error. For example, with same margin of error (15) and confidence level (80), the ideal sample numbers of CS (with 187 student in MA-2) VS. no-CS (1235 students in MA-2) should be 17 and 18 respectively [8]. But in real situation, the confidence level of no-CS group will have a higher confidence level than CS with 18 samples.
So, in order to make sure different groups have same confidence level, we need to change the number of samples in one group to make sure all the groups have same confidence level.

# What's next

The questionnaire will be set in place for next milestone, and we intend to have some dummy data generated on our own that will resemble the data we will get from the questionnaire, to get familiar with the tests. Once we get the feedback on the next milestone, we will release the questionnaire to the world and collect data for two weeks. Two weeks is already a big enough time window, and we do not expect to get new results after only a couple of days anyway. If we get feedback soon enough, the questionnaire might coincide with the Easter break, which could potentially help us get more answers (as people might not have the time during a normal week), but this is speculation, and maybe it will be too few time between the milestone and the beginning of the break.

# References

[1] Choix musicaux, modes de découverte et contextes d’écoute. Une typologie des univers musicaux des 15-25 ans, M. Azam,  M. Grossetti, L. Laffont et B. Tudoux, Sociologie, 2018, N° 4, Volume 9, PP 343 - 360
https://www.cairn.info/revue-sociologie-2018-4-page-343.htm?contenu=resume

[2] Spotify API https://developer.spotify.com/documentation/web-api/

[3] Music genres classification https://en.wikipedia.org/wiki/List_of_music_styles

[4] Spotify genre list http://everynoise.com/

[5] Computing significance from correlation
https://www.texasgateway.org/resource/124-testing-significance-correlation-coefficient-optional

[6] Class Position and Musical Tastes: A Sing‐Off between the Cultural Omnivorism and Bourdieusian Homology Frameworks, G. Veenstra, DOI https://doi.org/10.1111/cars.12068

[7] Mailing list specification 
https://help-mail.epfl.ch/en/mailing-lists/#faq-1f37dccdbcb7efae9d6871d745e4c155
https://cadiwww.epfl.ch/listes?categorie=etudiants
https://cadiwww.epfl.ch/listes/viewlist?unite=epfl&categorie=etudiants/etudiants

[8] Calculate the ideal sample size with the support from:
https://www.surveymonkey.com/mp/sample-size-calculator/

Traduction for [1]: Musical tastes, discovering modes and listening contexts. A topology of the musical universes of 15-25 year olds
For references [1] and [6], the articles are in French, but the abstracts are available in English as well, so you can get the idea behind the study.
