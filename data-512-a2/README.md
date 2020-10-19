

# DATA 512 A1: Data Curation
### By Mayank Goel

## License
The repostory follows MIT License as mention [here](https://github.com/mickkygoel/data-512/blob/main/data-512-a2/LICENSE).

## Goal
In this notebook, I will walk through potential sources of bias in a corpus of human-annotated data, and describe some implications for those biases.

The corpus I am using is called the Wikipedia Talk corpus, and it consists of three datasets. Each dataset contains thousands of online discussion posts made by Wikipedia editors who were discussing how to write and edit Wikipedia articles. Crowdworkers labelled these posts for three kinds of hostile speech: “toxicity”, “aggression”, and “personal attacks”. Many posts in each dataset were labelled by multiple crowdworkers for each type of hostile speech, to improve accuracy.


### Dataset Sources
The Datasets used in the analysis are available in Figshare:
1. Toxicity - Datasets [here](https://figshare.com/articles/dataset/Wikipedia_Talk_Labels_Toxicity/4563973)
2. Aggression - Datasets [here](https://figshare.com/articles/dataset/Wikipedia_Talk_Labels_Aggression/4267550)
3. Personal Attack - Datasets [here](https://figshare.com/articles/dataset/Wikipedia_Talk_Labels_Personal_Attacks/4054689)

More details about the data files and its schema can be found [here](https://meta.wikimedia.org/wiki/Research:Detox/Data_Release#Toxicity)
These datasets are used for a creating a project called [Conversation AI](https://conversationai.github.io/). These models are freely available for use via the [Perspective API](https://www.perspectiveapi.com/#/home) <br />

## Reproduce
This repository should be straight forward to reproduce. Simply download the python notebook file and run it in your python environment. The code uses standard libraries and generates all outputs without any other manual step.

## Analysis 1: Identifying labeling bias due to demographics

Demographics can play a big role on how thre worker annotate the dataset. Your gender, region, education, age can play a massive role in shaping your mindset, which would evenutally reflect in the labels annotated. Therefore, it is important to check the labelling is not being affected by the demographics of the lablellers. Further, it is also very important to ensure that the distribution of demographics of the labellers is similar to that of the population.
Through this analysis, we will try to gaze if the demographics of the labellers have impacted how they have labelled this corpus dataset. We will assume that the true probablity of a particular comment to be toxic, attack or aggressive is the same for all labellers.

**Dataset for this analysis**
To provide a wholesome picture of the corpus data, I would be doing this analysis on all the three datasets. This would provide a deeper understanding of bias compared to picking only one or two datasets.

**How are we measuring the bias**
* We will first set up a function to measure and plot this bias so that we can reuse this for each dataset.
* The function first groups the joined datasets based on the given demographic.
* The next step is to find the percentage of the comments that were annotated positively for that particular group. This can be easily done by taking the mean of the indicator column, since our labels are 1 and 0
* After manipulating the dataset and calculating the measures, we can then plot the measures.
* Two differnt plots have been shown by taking the transform of the dataframe, so that its easier to see that data fom different perspective.

### Sample output from Analysis 1

![Bias in labelling due to gender](https://github.com/mickkygoel/data-512/blob/main/data-512-a2/output/gender_labelling_bias.png)

## Analysis 2: Identifying bias due to disagreement in labelling

As the comments in this dataset were annotated by multiple workers, we have the opportunity to analyse the diagreement among these workers. Since this is a subjective issue, workers are likely to have different opinions abou the comments. However, this difference of opinion can become a socurce of major bias. When there is not enough clarity about the outcome of the label, or there is not consensus, in that case, is is very hard to obtain high level of accuracy based on that dataset. Hence, it is important to measure disagreement in this dataset.
Through this analysis, we will try to gaze if the disagreement among the labellers and how it may impact any subsequent models. We will assume that in a ideal scenario all the workers annotating a particular comment will either mark it as 0 or 1. I have defined the disagreement as the ratio of number of labellers on the intority side divided by the number of abellers on the majority side.

**Disagreement Ratio = Min(# of True Labellers, # of False Labellers)/Max(# of True Labellers, # of False Labellers)**

**Dataset for this analysis**
To provide a wholesome picture of the corpus data, I would be doing this analysis on all the three datasets. This would provide a deeper understanding of bias compared to picking only one or two datasets.

**How are we measuring the bias**
* We will first set up a function to measure the disagreement ratio.
* We will create another function which measures the disagreement ratio by first filtering out the comments where no labellers has marker it positive. This will allow us to gaze disagreement among the comments where at least one labellers believes that it should be marked positively.
* The function first calculates the number of yes labellers and no labellers.
* Thereafter, the function calculates the min and max of these two groups.
* Once this is done, the function calculates the ratio as defined above.
* After manipulating the dataset and calculating the measures, we can then plot the histogram for this ratio to see overall disagreement in the dataset.
* Two differnt plots have been shown by for each ratio so that we can interpret both scenarios.

## Repository content
- data - contains all input data files used in notebook
- output - contains all graphs and analysis produced by notebook
- Python notebook containing all code and information: *A2-Bias.ipynb*



