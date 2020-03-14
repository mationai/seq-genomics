# Genome Sequencing with Seq

Solutions (spoilers!) for [Coursera Bioinformatics](https://www.coursera.org/specializations/bioinformatics) / Stepik Genome Sequencing course with [Seq](https://seq-lang.org/)


## Motivation

I've always wanted to learn Bioinformatics / Genome Sequencing. Seq-lang's [debut](https://news.ycombinator.com/item?id=22107510) last week is the prefect catalyst for starting. 

Seq seems like the perfect tool since it was created specifically for the job. The downside is that it is too young, so many features and "batteries" you expect from python, the language it is based on, are missing. In addition, the following some of the things I felt missing working on the problem set: 

- functools
- better parse errors
- splat / unpack
- defaultdict

That being said, its speed, statical typing, pipeline operator `|>`, and similarities with python have made me overlook its early drawbacks easily.


## Setup and Running

1. Follow [instructions](https://seq-lang.org/intro.html#install) to Install

2. Setup your editor to associate .seq as python.

3. Run via `seqc FILE.seq ARG`, eg.:
  ```
  seqc stepik/1-1.seq 1  # run exercise 1 in stepik/1-1.seq
  seqc stepik/1-1.seq    # run all exercises in stepik/1-1.seq
  ```


## Seq Language Notes

### Iteration
Not sure if 
```python
for kmr in dna.kmers[Kmer[4]](1):
```
is faster than
```python
for kmr in dna.split(k, 1):
```
or not, but since `Kmer[n]` requires `n` to be a compile time constant, it' not too useful here.

### Hamming Distance
```python
abs(k1 - k2) # vs. len([1 for i in range(len(k1)) if k1[i] != k2[i]])
```
