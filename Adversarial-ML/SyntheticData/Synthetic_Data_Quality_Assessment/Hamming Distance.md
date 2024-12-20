The Hamming distance is a **metric** used in **information theory** to measure how much **two messages with the same length differ**.

For message, we mean a **string**: whenever you see a number, you should remember that the digits are no more than **letters of an alphabet**, and you can't perform mathematical operations on them!

The Hamming distance indicates the **number of different digits/letters in a pair of messages**. Take the words "**Hamming**" and "**humming**": what is the Hamming distance?

Let's see. "H**a**mming" and "h**u**mming" — there is **one letter of difference**, so the **Hamming distance is 1**.

Increase the Hamming distance to two: **farming**, **humping**, **camping**. As you can see, there are a few examples. If we increase the Hamming distance to three, there is even more: **fasting**, **hosting**, **hammock** or **Hamburg**.

As you can see, the higher the Hamming distance, the more difficult it is to "see" the original word: that's because we **accumulated errors**.

In [information theory](https://en.wikipedia.org/wiki/Information_theory "Information theory"), the **Hamming distance** between two [strings](https://en.wikipedia.org/wiki/String_(computer_science) "String (computer science)") of equal length is the number of positions at which the corresponding [symbols](https://en.wikipedia.org/wiki/Symbol "Symbol") are different. In other words, it measures the minimum number of _substitutions_ required to change one string into the other, or the minimum number of _errors_ that could have transformed one string into the other. In a more general context, the Hamming distance is one of several [string metrics](https://en.wikipedia.org/wiki/String_metric "String metric") for measuring the [edit distance](https://en.wikipedia.org/wiki/Edit_distance "Edit distance") between two sequences. It is named after the American mathematician [Richard Hamming](https://en.wikipedia.org/wiki/Richard_Hamming "Richard Hamming").

A major application is in [coding theory](https://en.wikipedia.org/wiki/Coding_theory "Coding theory"), more specifically to [block codes](https://en.wikipedia.org/wiki/Block_code "Block code"), in which the equal-length strings are [vectors](https://en.wikipedia.org/wiki/Vector_space "Vector space") over a [finite field](https://en.wikipedia.org/wiki/Finite_field "Finite field").

## Definition##

#### The Hamming distance between two equal-length strings of symbols is the number of positions at which the corresponding symbols are different

![[Pasted image 20230523084626.png]]


