1. Taub et al., Differential Correct Attribution Probability for Synthetic Data: An Exploration, In: Proceedings of the 8th PSD, 2018. 2. M. Hittmeir, A. Ekelhart, R. Mayer, A Baseline for Attribute Disclosure Risk in Synthetic Data, In: Proceedings of the 20th CODASPY, 2020.

  ![[[ReadingInProgress]Synthetic Data- An Exploration of Data Utility and Disclosure Risk.pdf]]

Targeted Correct Attribution Probability (TCAP)

**Measuring Disclosure Risk using TCAP**

The TCAP method in full is based on an intruder scenario in which two data owners produce a linked dataset (using a trusted third party), which is then synthesised and the synthetic data published. The adversary is one of the data owners who attempts to use the synthetic data to make inferences about the others’ dataset. This is obviously a fairly strong attack.

More modestly, at the individual record level the adversary is somebody who has partial knowledge about a particular population unit (including the values for some of the variables in the dataset - the key - and knowledge that the population unit is in the original dataset) and wishes to infer the value of sensitive variable (the target) for that population unit for the original data.

The adversary views the synthetic dataset surmises that key equivalence class with low l-diversity on the target are most at risk. Here we assume that the adversary will focus on records which are in equivalence class which has l-diversity of 1 on the target and attempts to match them to their data. The TCAP metric is then the probability that those matched records yield a correct value for the target variable (ie that the adversary makes a correct attribution inference).

TCAP is calculated as follows: We define do as the original data and Ko and To as vectors for the key and target information

do ={Ko,To}

Likewise, ds is the synthetic dataset.

ds ={Ks,Ts}

We then calculate the Within Equivalence Class Attribution Probability (WEAP) score for the synthetic dataset. The WEAP score for the record indexed j is the empirical probability of its target variables given its key variables,

Pni=1[Ts,i = Ts,j,Ks,i = Ks,j]  
WEAPs,j = Pr(Ts,j|Ks,j) = Pni=1[Ks,i = Ks,j]

where the square brackets are Iverson brackets, n is the number of records, and and K and T as vectors for the key and target information. Then using the WEAP score the synthetic dataset will be reduced to records with a WEAP score that is 15. The TCAP for record j based on a corresponding original dataset do is the same empirical, conditional probability but derived from do,

Pni=1[To,i = Ts,j,Ko,i = Ks,j]  
TCAPo,j = Pr(Ts,j|Ks,j)o = Pni=1[Ko,i = Ks,j]

For any record in the synthetic dataset for which there is no corresponding record in the original dataset with the same key variable values, the denominator in Equation 4 will be zero and the TCAP is therefore undefined. If the TCAP score is 0 then the synthetic dataset carries little risk of disclosure; if the dataset has an TCAP score close to 1, then for most of the riskier records disclosure is possible. We will be using four different size keys of three to six variables (Shown in Appendix D).


[[Disclosures in Synthetic Data]]