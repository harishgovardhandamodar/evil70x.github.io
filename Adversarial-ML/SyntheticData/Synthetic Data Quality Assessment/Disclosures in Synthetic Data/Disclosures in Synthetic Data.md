The analysis of privacy risks with synthetic data remains an important topic. In the context of a privacy analysis, we are concerned here with data that pertains to individuals. If the data does not pertain to individuals, then there will be no privacy concerns. For example, if the data pertains to prescriptions or cars, then we would not worry as much about privacy. However, data synthesis is being used extensively to generate data about individuals, and therefore we need to understand the privacy implications.

There is a general belief that synthetic data has negligible privacy risk because there is no unique mapping between the records in the synthetic data and the records in the original data. 

Reiter noted that “identification of units and their sensitive data from synthetic samples is nearly impossible,”

and Taub et al. said that “it is widely understood that thinking of risk within synthetic data in terms of re-identification, which is how many other SDC (statistical disclosure control) methods approach disclosure risk, is not meaningful.”

![[Pasted image 20230515153759.png]]
The decision tree in Figure illustrates the types of risks that data synthesis would protect against: meaningful identity disclosure. The risks from other types of disclosure shown here would be managed through ethics reviews and other governance mechanisms, but not through data synthesis.

-   **[[Identity Disclosure]]**, which occurs if the intruder associates a known individual with a released data record. For example, the intruder links a released data record with external information, or identifies a respondent with extreme data values. In this case, an intruder can exploit a small subset of variables to make the linkage, and once the linkage is successful, the intruder has access to all other information in the released data related to the specific respondent.
-   **[[Attribute Disclosure]]**, which occurs if the intruder is able to determine some new characteristics of an individual based on the information available in the released data. Attribute disclosure occurs if a respondent is correctly re-identified and the dataset contains variables containing information that was previously unknown to the intruder. Attribute disclosure can also occur without identity disclosure. For example, if a hospital publishes data showing that all female patients aged 56 to 60 have cancer, an intruder then knows the medical condition of any female patient aged 56 to 60 in the dataset without having to identify the specific individual.
-   **[[Inferential Disclosure]]**, which occurs if the intruder is able to determine the value of some characteristic of an individual more accurately with the released data than would otherwise have been possible. For example, with a highly predictive regression model, an intruder may be able to infer a respondent’s sensitive income information using attributes recorded in the data, leading to inferential disclosure.



**[[Learning Something New]]**

**[[Meaningful Identity Disclosure]]**

**[[Defining Information Gain]]**

**[[Unique Matches]]**








------------------------------------------------------------------------
References
1. Practical Synthetic Data Generation - Balancing Privacy and the Broad Availability of Data by 
Khaled El Emam, Lucy Mosquera, and Richard Hoptroff
2. https://sdcpractice.readthedocs.io/en/latest/intro.html
3. ![[Final Report on the Disclosure Risk Associated with the Synthetic Data Produced by the SYLLS Team - Mark Elliot.pdf]]
4. 