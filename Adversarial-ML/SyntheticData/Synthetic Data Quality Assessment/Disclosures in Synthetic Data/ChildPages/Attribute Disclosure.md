Another type of disclosure is attribute disclosure, when we learn something new about a group of individuals in the dataset without actually assigning an identity to a record. Consider the data in Table, which is a health dataset showing ages, genders, and diagnoses.

Let’s assume that the adversary knows that Hiroshi is in the data, is male, and was born in 1959. By looking at this dataset the adversary would conclude that Hiroshi is one of the first three records, but it is not possible to know which record specifically belongs to Hiroshi. **The adversary can also conclude that Hiroshi has prostate cancer with 100% certainty.** In this case, Hiroshi is a member of a group of males born between 1950 and 1959, and all of the members of this group have prostate cancer. Even though the adversary was not able to assign a record to Hiroshi, by virtue of the fact that Hiroshi is a member of that group the adversary could draw conclusions about him and learn something new.

|Decade of Birth| Gender | Diagnosis|
|---|---|---| 
|1950-59|Male|Prostate cancer|
|1950-59|Male|Prostate cancer|
|1950-59|Male|Prostate cancer|
|1970-79|Male|Lung cancer|
|1980-89|Female|Breast cancer|



What the adversary effectively did here is build a model that relates age and gender to diagnosis. It just happens that based on this dataset the model has no uncertainty (i.e., all males born between 1950 and 1959 have a prostate cancer diagnosis).

Let’s go one step further and say that an analysis was performed, and the decision tree in the figure below was built using a machine learning algorithm run on the data and was published in a journal. If we then go through the tree and match Hiroshi’s specifics, we see that he is very likely to have prostate cancer according to that model. In this case, we are drawing inferences from the model based on Hiroshi’s characteristics.

![[Pasted image 20230515110114.png]]
A decision tree that was built from an oncology dataset

The model the adversary built was simple, but one can imagine that in other types of datasets these models can be more complex, with additional variables and interactions among the variables. The complexity of the model does not matter for making the main point, though. The adversary engaged in statistics or data analysis. The essence of data analysis is to build models that draw conclusions about groups of individuals with certain characteristics.

The other thing to note here is that the adversary can draw conclusions about indi‐ viduals who are not in the data. If the dataset is representative of the population, then a conclusion can be drawn about all men born between 1950 and 1959 in the popula‐ tion. For example, if Satoshi is a male born in 1955 and is a member of the population that data comes from, then one can reasonably conclude that Satoshi also has prostate cancer. Here, the adversary is learning something new about individuals who are not even in the data, and with high certainty. Again, this is the essence of statistics.

The adversary did not identify the record that belongs to Satoshi because it does not exist in the data. The existence of Satoshi’s record in the data, or not, is not relevant here—there is a model that can be used to make inferences without identity disclosure.

We do not want to constrain statistics—that would defeat the whole purpose of AI and data analysis. Therefore, a blanket ban on attribute disclosure would be a bit of an overreach.