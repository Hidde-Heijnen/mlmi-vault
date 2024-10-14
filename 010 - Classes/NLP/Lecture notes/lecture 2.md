## Morphology

**Morphemes** smallest meaningful units of language. Words are composed of morphemes

**Affix**: Morpheme which only occurs together with other morphemes (3 types) 
	Can't use them independently 
- suffix (unit-s)
- prefix (in-complete)
- infix (salat: write; s-um-ulat: wrote)
- circumfix: occur on both sides (berg; ge-berg-te)

**Root**: nucleus of the word that affixes attach to

### Types of morphology
**Inflection**: creates new forms of the same word: 
- bring, brought, bringing
- applies to most words in the language except some irregular forms 
- (fully productive): you can decompose it into smaller meanings, handy for algorithms
- only affect syntactic function 
	- (like in ASL all the bringing forms are one sign)

**Derivation**: creates new words
- logic, logical, logician
- semi-productive. Applies to some words
- irregular: the same type of change might change the meaning of different words differently, and can't be applied to many other words (escapee, cricketee)
- affect meaning of the word
	- Would be a different sign in ASL

Sometimes there can be ambiguity
- Unlockable
	- un-lock  -able: capable of being unlocked
	- un-  lock-able: not capable of being locked
- beautiful dancer
	- beautiful dance   -er: says something about the dance
	- beautiful    dance-er: says something about the dancer

### Stem Lexeme and Lemma
**Stem:** word without its inflectional affixes = roots + all derivational affixes
- book.shopp.ed: 
	- stem: book.shopp, 
	- root: book and shopp
	- affix: ed

**Lexeme:** set of all forms related by inflection (but not derivation) 
- (so connected by the same lemma)
- bookshops, bookshopped, bookshopping

**Lemma**: cleaned up version of the stem. Bookshopp -> bookshop

### Phonaestheme
**Etymology**: origin of words, some similar words can be historically related

**phonaestheme:**
- a pattern of sounds systemically paired with a certain meaning in a language
- Even smaller than morphemes
	- cl-: related to a closing motion
		- clam, clasp, clip, clutch
	- gl-: related to light
		- glance, glare, glimmer, gloom, gloss, glow
- slide and slip have similar meanings, but sl- is not a morpheme

**Compounds**: contain more than one root
	- post-truth, railway, sunset

## Multiword expressions
--- 
combinations of two or more words that exhibit:
- **Syntactic idiosyncrasy**: The way the words are combined may not follow typical grammatical rules
- **Semantic idiosyncrasy:** meaning of the phrase as a whole being different from the sum of its parts
Fe: Computer Science, Climate change
### Types of multiword expressions

**Fixed vs Flexible:**
- **Fixed:** order is fixed (by and large)
- **Flexible:** order is flexible: "put on": put on the clothes, put the clothes on

**Compositionality**: How much of the multiword expression can be understood from the meaning of it's individual roots
- **Compositional**: meaning of expression comes directly from it's parts
	- strong tea => tea that is strong in flavour
- **Semi-compositional**: partly derived from the roots, but may require some interpretation
	- Spill the beans => spilling is revealing, but beans doesn't refer to secret
- **Non-compositional**: cannot be deduced from it's roots. 
	- Kick the bucket => to die. A learner needs to see this combination of words as a complete new thing

Code mixed languages
- A speaker alternates between two or more languages in the context of a single conversation
	- 我唔sure => english word mixed in sentence

## Text normalisation
- **Not using any punctuation at all**  
	- _Eh speak english mi malay not tt good_ (Eh, speak English! My Ma-lay is not that good.)
- **Using spelling/punctuation for emphasis**  
	- _goooooood Sunday morning !!!!!!_ (Good Sunday morning!)
- **Using phonetic spelling**  
	- _dat iz enuf_ (That is enough)
- **Dropping vowel**  
	- _i hv cm to c my luv._ (I have come to see my love.)
- **Introducing local flavour**  
	- _yar lor where u go juz now_ (Yes, where did you go just now?)
- **Dropping verb**  
	- _I hv 2 go. Dinner w parents._ (I have to go. Have dinner with parents.)

## Relevant NLP tasks
---
We want to be able to go from natural language expressions to representations $\mathcal{R}$
- morphological structure
- syntactic structure
- semantic structure
- discourse structure
- application-related structured

Going from natural language to those is called **comprehension** 
Going from those to natural language is called **production**
### Computational tasks
- Lemmatisation
	- Word: saw
	- $\mathcal{R}$: lexeme: {see, saw}
- Tagging
	- contextualised word: saw @ J saw M
	- $\mathcal{R}$: contextualised tag <see, VERB.PAST>
- Segmentation
	- word: meaningful
	- $\mathcal{R}$: morphemes: mean+ing+ful
		- Word segmentation: Some languages don't have spaces, so it is useful to be able to split a string up into it's component words
- Generation
	- $\mathcal{R}$: abstract word: <see, VERB.PAST>
	- word: saw

### Finite State techniques
The order of things matter a lot in language
- $\text{talk-ed} \neq \text{ed-talk}$

A finite state machine is:
- A symbolic system that can recognise or transform forms.
	- An automaton remembers only a finite amount of information.
	- Information is represented by its states.
	- State changes in response to inputs and may trigger outputs.
	- Transition rules define how the state changes in response to inputs.
	- Given a sequence of input symbols, a recognition process starts in the start state and follow the transitions in turn. Input is accepted if this process ends up in an accepting state.
	- Partial grammars for text preprocessing, tokenisation, named entity recognition etc.
![[CleanShot 2024-10-13 at 19.58.54.png]]
- Circles are **states** of the automaton.
- Arrows are called **transitions**.
- The automaton changes states by following transitions.
- The double circle indicates that this state is an **accepting state**. The automaton accepts the string if it ends in an accepting state.
### Byte-Pair Encoding
BPE was initially developed as an algorithm to compress texts, and then used by OpenAI for tokenisation when pre-training the GPT model.
- Start from a small base vocabulary, e.g. 256 ASCII code.
- Add new tokens to the vocabulary until the desired vocabulary size is reached by learning merges, which are rules to merge two elements of the existing vocabulary together into a new one.
- At each step, the BPE algorithm search for the most frequent pair, namely two consecutive tokens, of existing tokens.
