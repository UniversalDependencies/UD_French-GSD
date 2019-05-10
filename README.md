# Summary
The **UD_French-GSD** was converted in 2015 from the content head version of the universal
dependency treebank v2.0 (https://github.com/ryanmcd/uni-dep-tb).
It is updated since 2015 independently from the previous source.

# Introduction
The **UD_French-GSD** is converted from the content head version of the universal
dependency treebank v2.0 (https://github.com/ryanmcd/uni-dep-tb).
The README for the original project is available below.

The version 2.4 of **UD_French-GSD** data consists of 400,387 words (16,342 sentences).
No sentence id were available in the original resource, so new `sent_id` were automatically introduced in the converted corpus with prefixes `fr-ud-train`, `fr-ud-dev` and `fr-ud-test` on the corresponding original files, followed by a 5 digit number following the order of sentences.

:warning: to meet the size requirements of test data of 10K words, a part of the dev original file was moved to the test file!
Since version 2.0, the splitting of data is:

 * file `fr-ud-train.conll`: 14,450 sentences; 354,655 words
  * `fr-ud-train_00001` to `fr-ud-train_14554`
 * file `fr-ud-dev.conll`: 1,478 sentences; 35,714 words
  * `fr-ud-dev_00001` to `fr-ud-dev_01478`
 * file `fr-ud-test.conll`: 416 sentences; 10,018 words
  * `fr_ud-test_00001` to `fr_ud-test_00298`
  * `fr-ud-dev_01479` to `fr-ud-dev_01596`

Sentences are shuffled and there is no way to know what is the source or the genre of a given sentence.

Probably due to some bug in a conversion program, version 1.2 contains many truncated sentences (date missing for instance).
Almost every truncated sentence is from Wikipedia, so it was possible to recover the original text.
Most of the truncated sentences were completed in version 1.3. Some sentences were completed later.
There are probably still some truncated sentences.

# Acknowledgments

The latest version of the corpus was produced by Marie-Catherine de Marneffe, Bruno Guillaume, Matias Grioni, Carly Dickerson and Guy Perrier.
Automatic modifications and consistency checking were partly done using the [Grew software](http://grew.fr).

See below for references and acknowledgments concerning the original corpus.

# Changelog

* 2019-05-15 v2.4
  * Change annotations to make the corpus valid
  * Change MWE annotations (see [here](https://github.com/UniversalDependencies/UD_French-GSD/blob/dev/not-to-release/README.md))
* 2018-11-15 v2.3
  * add subtyping for preposition "à"
  * remove duplicate sentences
  * fix errors found with conversion to SUD
* 2018-04-15 v2.2
  * Partial subtyping of `obl` into the 3 relations `obl:agent`, `obl:mod` and `obl:arg` (This is done form 43,5% of the total number of the `obl` relations; this is completely done from PP introduced by prepositions *de*, *par*, *dans* and *avec*).
  * Many error corrections
* 2017-11-15 v2.1
  * Only "être", "avoir" or "faire" with the POS tag `AUX`
  * modifications taking into account new decisions taken for harmonisation of several French Treebanks (causative, copulas, auxiliaries, change of `nmod:poss` in `det`)
* 2017-03-01 v2.0
  * Conversion of data to follow new guidelines (automatic conversions with manual verifications and manual annotation of `nmod` VS `obl` in ambiguous cases)
* 2016-11-15 v.1.4
  * POS annotations were made more consistent
  * Several dependency paths were also made more consistent across similar expressions
  * Only "avoir" and "être" are considered copula
* 2016-05-15 v1.3
  * Add lemmas and features
  * Complete truncated sentences 	
* 2015-11-15 v1.2
  * Add sent_id and full text in metadata
  * Removed duplicate sentences (overlaps with train) from dev and test data.
* 2015-05-15 v1.1
  * Manual corrections of full text
  * change of `det` in `nmod:poss` for possessive determiners
* 2015-01-15 v1.0
  * Initial release

# README of the original resource
See https://github.com/ryanmcd/uni-dep-tb for more details

```
===================================
Universal Dependency Treebanks v2.0
===================================

This directory contains treebanks for the following languages:
  English, German, French, Spanish, Swedish, Korean, Japanese, Indonesian,
  Brazilian Portuguese, Italian and Finnish.

A description of how the treebanks were generated can be found in:

  Universal Dependency Annotation for Multilingual Parsing
  Ryan McDonald, Joakim Nivre, Yvonne Quirmbach-Brundage, Yoav Goldberg,
  Dipanjan Das, Kuzman Ganchev, Keith Hall, Slav Petrov, Hao Zhang,
  Oscar Tackstrom, Claudia Bedini, Nuria Bertomeu Castello and Jungmee Lee
  Proceedings of ACL 2013

A more detailed description of each relation type in our harmonized scheme is
included in the file universal-guidelines.pdf.

Each treebank has been split into training, development and testing files.

Each file is formatted according to the CoNLL 2006/2007 guidelines:

  http://ilk.uvt.nl/conll/#dataformat

The treebank annotations use basic Stanford Style dependencies, modified
minimally to be sufficient for each language and be maximally consistent across
languages. The original English Stanford guidelines can be found here:

  http://nlp.stanford.edu/software/dependencies_manual.pdf


==============================================================================
Version 2.0 - What is new
==============================================================================

1. Added more data for German, Spanish and French.
2. Added Portuguese Brazilian, Indonesian, Japanese, Italian and Finnish.
3. New content-head versions for 5 languages (see below).
4. A number of bug fixes in the harmonization process.

=====================
Standard dependencies
=====================

In release 2.0 we include two sets of dependencies. The first is standard
Stanford dependencies, which correspond roughly to the output of the
Stanford converter for English with the copula as head set to true. In
general, these are content-head dependency representations with two major
exceptions: 1) adpositions are the head in adpositional phrases, and 2) copular
verbs are the head in copluar constructions.

This data is in the std/ directory and contains all languages but Finnish.

Version 1.0 of the data is only standard.

==========================
Content head dependencies
==========================

In order to converge to a more uniform multilingual standard, in particular
for morphologically rich languages, this release also includes a beta version
of content-head dependencies for five languages: German, Spanish, Finnish,
French and Swedish. Here the content word is always the head of a phrase.

=============================================================================
Language Specific Information
=============================================================================

====================
English dependencies
====================

Note that the English dependencies are based on the original Penn Treebank data
automatically converted with the Stanford Dependency Converter. Instructions for
how to do this with corresponding scripts are included in the English directory.

====================
Finnish dependencies
====================

Finnish data is in the ch/fi directory and was produced by researchers at
the University of Turku. In that directory there are specific README and
LICENSE files for that data. Two things to note. First, the Finnish data is
only content-head. This is due to difficulties in automatically converting the
data to standard format from its original annotations. Second, we have included
a test set in the release, but this is not the real test set, just a subset of
the training. The true test set for this data is blind (as per the wishes of
the researchers at Turku). The unannotated test data is included as well as
instructions for obtaining scores on predictions.

=============================================================================
Other Information
=============================================================================

================================
Fine-grained part-of-speech tags
================================

In the CoNLL file format there is a coarse part-of-speech tag field (4) and a
fine-grained part-of-speech tag field (5). In this data release, we use the
coarse field to store the normalized universal part-of-speech tags that are
consistent across languages. The fine-grained field contains potentially richer
part-of-speech information depending on the language, e.g., a richer tag
representation for clitics.

=========================
Licenses and terms-of-use
=========================

For the following languages

  German, Spanish, French, Indonesian, Italian, Japanese, Korean and Brazilian
  Portuguese

we will distinguish between two portions of the data.

1. The underlying text for sentences that were annotated. This data Google
   asserts no ownership over and no copyright over. Some or all of these
   sentences may be copyrighted in some jurisdictions.  Where copyrighted,
   Google collected these sentences under exceptions to copyright or implied
   license rights.  GOOGLE MAKES THEM AVAILABLE TO YOU 'AS IS', WITHOUT ANY
   WARRANTY OF ANY KIND, WHETHER EXPRESS OR IMPLIED.

2. The annotations -- part-of-speech tags and dependency annotations. These are
   made available under a CC BY-NC-SA 3.0 non commercial license. GOOGLE MAKES
   THEM AVAILABLE TO YOU 'AS IS', WITHOUT ANY WARRANTY OF ANY KIND, WHETHER
   EXPRESS OR IMPLIED. See attached LICENSE file for the text of CC BY-NC-SA.

Portions of the German data were sampled from the CoNLL 2006 Tiger Treebank
data. Hans Uszkoreit graciously gave permission to use the underlying
sentences in this data as part of this release.

For English, Italian, Finnish and Swedish, please see licences included in
these directories or the following sources.

Finnish - http://bionlp.utu.fi/fintreebank.html
Swedish - http://stp.lingfil.uu.se/~nivre/swedish_treebank/
Italian - http://medialab.di.unipi.it/wiki/ISDT

We are greatful to researchers at those institutes who provided us data, in
particular:

Maria Simi and company from the University of Pisa.
  Converting Italian Treebanks: Towards an Italian Stanford Dependency Treebank
  Bosco, Cristina and Montemagni, Simonetta and Simi, Maria
  Proceedings of LAW VII \& ID

Filip Ginter and company from the University of Turku.
  Building the essential resources for Finnish: the Turku Dependency Treebank
  Haverinen, Katri and Nyblom, Jenna and Viljanen, Timo and Laippala,
  Veronika and Kohonen, Samuel and Missil{\"a}, Anna and Ojala, Stina and
  Salakoski, Tapio and Ginter, Filip
  Language Resources and Evaluation, 2013

Joakim Nivre and company from Uppsala University.

And Chris Manning and Marie-Catherine de Marneffe from Stanford and Ohio.
  Generating typed dependency parses from phrase structure parses
  MC De Marneffe, B MacCartney, CD Manning,
  Proceedings of LREC, 2006

Any use of the data should reference the above plus:

  Universal Dependency Annotation for Multilingual Parsing
  Ryan McDonald, Joakim Nivre, Yvonne Quirmbach-Brundage, Yoav Goldberg,
  Dipanjan Das, Kuzman Ganchev, Keith Hall, Slav Petrov, Hao Zhang,
  Oscar Tackstrom, Claudia Bedini, Nuria Bertomeu Castello and Jungmee Lee
  Proceedings of ACL 2013

=======
Contact
=======

ryanmcd@google.com
joakim.nivre@lingfil.uu.se
slav@google.com
```


=== Machine-readable metadata (DO NOT REMOVE!) ================================
Data available since: UD v1.0
License: CC BY-NC-SA 3.0 US
Includes text: yes
Genre: blog news reviews wiki
Lemmas: automatic with corrections
UPOS: converted with corrections
XPOS: not available
Features: automatic with corrections
Relations: converted with corrections
Contributors: de Marneffe, Marie-Catherine; Guillaume, Bruno; McDonald, Ryan; Suhr, Alane; Nivre, Joakim; Grioni, Matias; Dickerson, Carly; Perrier, Guy
Contributing: here
Contact: demarneffe.1@osu.edu, bruno.guillaume@inria.fr
===============================================================================
