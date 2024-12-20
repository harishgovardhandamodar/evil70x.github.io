Now let’s consider the dataset in Table 6-4. Here, the adversary has the same back‐ ground information about Hiroshi as in the previous example (he is in the data, male, and born in 1959). The adversary can conclude that Hiroshi has prostate cancer with only 50% certainty. Similarly for Satoshi, the adversary can conclude that he has pros‐ tate cancer with 50% certainty, even though Satoshi is not in the data.

|Decade of Birth| Gender | Diagnosis|
|---|---|---| 
|1950-59|Male|Prostate cancer|
|1950-59|Male|Prostate cancer|
|1950-59|Male|Lung cancer|
|1950-59|Male|Lung cancer|
|1970-79|Male|Lung cancer|
|1980-89|Female|Breast cancer|


| Decade of Birth | Gender | Diagnosis       | count |
| --------------- | ------ | --------------- | ----- |
| 1950-59         | Male   | Prostate cancer | 2     |
| 1950-59         | Male   | Lung cancer     | 2     |
| 1970-79         | Male   | Lung cancer     | 1     |
| 1950-59         | Female | Breast cancer   | 2     |
| 1980-89         | Female | Breast cancer   | 1     |
^table

```chart 
type: bar 
id: table 
layout: columns 
width: 80% 
beginAtZero: true
```

The basic point about this being the essence of statistics/data analysis still holds. The difference between this case and the one in Table 2 is the level of certainty. In one case a more accurate model has been built. But the record belonging to Hiroshi still cannot be identified, and the only reason we can learn something new about him is because he is a member of a group that has been modeled.