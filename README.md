# Genome Sequencing with Seq

Solutions (spoilers!) for Coursera Bioinformatics / Stepik Genome Sequencing course with [Seq](https://seq-lang.org/)

## Motivation

I've always wanted to learn Bioinformatics / Genome Sequencing. Seq-lang's [debut](https://news.ycombinator.com/item?id=22107510) last week is the prefect catalyst for starting. 

## Seq Language Notes

Seq seems like the perfect tool since it was created specifically for the job. The downside is that it is too young, so many features and "batteries" you expect from python, the language it is based on, are missing. In addition, the following some of the things I felt missing working on the problem set: 

- functools
- better parse errors
- splat / unpack

That being said, its speed, statical typing, pipeline operator `|>`, and similarities with python have made me overlook its early drawbacks easily.

## Setup and Running

1. Follow [instructions](https://seq-lang.org/intro.html#install) to Install

2. Setup your editor to associate .seq as python.

3. Run via `seqc FILE.seq ARG`, eg.:
  ```
  seqc stepik-01.seq 1  # run exercise 1 in stepik-01.seq
  seqc stepik-01.seq    # run all exercises in stepik-01.seq
  ```
