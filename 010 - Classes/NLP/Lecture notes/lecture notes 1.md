This course will do breadth over depth.

The definition of what is a language is not obvious

For example in the Cambridge dictionary
Word is used to define language, and word is defined using language. 

Formal languages, precise definition:
A string of length $n$ over an

A string of length $n$ over an alphabet $\Sigma$ is an ordered $n$-tuple of elements of $Σ$.
- $\Sigma^*$ denotes the set of all strings over $\Sigma$ of finite length.
- Given an alphabet $\Sigma$ any subset of $\Sigma^*$ is a formal language over alphabet $\Sigma$ 

Is it adequate to characterise a natural language in the same way?

We want to make some model to understand the human language. 

## Goal and scope
Build a computational system that can be used for communication, that mirrors how humans use human language

For example that a machine can understand what we want to do from our language. (so from natural language to machine instructions)

### Aristotle's Syllogism
aka implications. Language goes beyond communication. We can infer things from previous language. 
1. All men are mortal 
2. Socrates is a man 
3. Therefore, Socrates is mortal

## Topics in this course
What does it mean to know a language?
Sentence structure

Morphology: -  the structure of words

#### What does it mean to *know* a language?
- **Example Sentence**: *Some yinkish dripners blorked quastofically into the nindin with the pidibs.*
- Key points derived from the example:
  - A **BLORK** event occurred in the **PAST**.
  - The **AGENT** of **BLORK** is **dripners**.
  - The **dripners** are **YINKISH**.
  - **SOME** but **NOT ALL** dripners **blorked**.
  - **WITH THE PIDIBS** might discuss **NINDIN** or **BLORK**.

#### Structuring a Sentence
- **Lexical Semantics**: Meaning of individual words (e.g., *yinkish* = ADJ, *dripners* = NOUN, *blorked* = VERB).
- **Compositional Semantics**: Meaning derived from sentence structure (combining syntax and word meanings).
- **Syntax**: Sentence structure, e.g., word order (subject, object, verb). The way words are used to form sentences. 
- **Morphology**: Word structure (e.g., *quastofically* is derived from *quastofy* + *-cal* + *-ly*; *pidibs* = *pidib* + *-s*).
- **Vectorisation**: Words, phrases, sentences, and paragraphs are vectorised for processing.

Word combinations can contain crucial information. Some combinations are more important than others. 

Transform words to vectors so we can use them for example in neural models. 

![[CleanShot 2024-10-11 at 10.35.04@2x.png]]

### Form transformation
![[CleanShot 2024-10-11 at 10.41.24@2x.png]]

Map to and from natural language expressions to mathematical models. 

I-NP: inside noun phrase
We go from words to token labels

named entities
Per: person
Org: organisation
Loc: Location
B-Loc:

Syntactic dependencies: assymetrical dependencies on other words modelled using a list of numbers. 

Go from one side to another. 

Technology is changing very fast. For each lecture some recommended chapters: 
After class reading: https://web.stanford.edu/~jurafsky/slp3/

today reading just for motivation:

https://www.bbc.com/future/article/20220804-kusunda-the-language-isolate-with-no-word-for-no

https://plato.stanford.edu/entries/computational-linguistics/

