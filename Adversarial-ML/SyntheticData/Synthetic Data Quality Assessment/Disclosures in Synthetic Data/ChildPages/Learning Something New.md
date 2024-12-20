Another situation is illustrated in Table, Here, the adversary knows that Hiroshi is in the dataset, that his year of birth is 1959, that he is male, and that he earns $120K. Knowing these four things, the adversary can say with certainty that the first record belongs to Hiroshi. However, the adversary used all of the information in the data to determine Hiroshi’s record. In fact, the adversary does not learn anything new by figuring out which record belongs to Hiroshi—the information gain is zero.

Even though the adversary did identify the record that belongs to Hiroshi, when the information gain is zero it is not really a meaningful identity disclosure. In theory, it is not a good thing to be able to assign a record to an individual, but in practice, if the information gain is zero, then there is no point to the identity disclosure. In such cases the risk of harm to the individual is arguably negligible.

| Year of Birth     | Gender | Income |
| -----------  | ----------- | -------|
| 1959 | Male      |$ $120K$|
| 1959 | Male      |$ $100K$|
| 1959 | Female    |$ $110K$|
| 1959 | Male      |$ $110K$|
| 1959 | Male      |$ $120K$|


Therefore, an important criterion to consider when deciding whether a disclosure has occurred is whether there is an information gain from the disclosure.


