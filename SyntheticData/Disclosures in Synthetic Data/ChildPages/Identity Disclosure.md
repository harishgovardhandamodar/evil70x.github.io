**Identity Disclosure**

Consider the simple dataset in Table We have three records with a person’s origin and a person’s income. For now we assume that this is a real dataset that has not been perturbed.

Let’s say that an adversary or hacker is trying to find the record that belongs to some‐ one named Hiroshi. The adversary knows that Hiroshi is in that dataset, and that Hiroshi is Japanese. By using that background knowledge, the adversary would be able to conclude that the first record in the dataset belongs to Hiroshi. In this case, the adversary assigned an identity to the first record. This is called identity disclosure.

```
| Origin       | Income |
| -----------  | ----------- |
| Japanese     | $120K       |
| North African| $100K$      |
| Eurpoean     | $110K$      |
```
After matching the first record with Hiroshi, the adversary learns something new about Hiroshi that they did not know beforehand: Hiroshi’s income is $120K. This is a material point.

We care only about correct assignments of an identity to a record. This is one of the fundamental criteria for considering whether records in synthetic data (or any kind of depersonalized data) have been compromised. For example, if an adversary is unable to find a record that matches Hiroshi’s criteria, then disclosure has not occur‐ red. If the adversary assigns the second record to Hiroshi, that would be incorrect, and therefore disclosure has not occurred. Being able to incorrectly assign identities to records is not a problem that we can solve, and therefore the focus is only on correct identity disclosure.