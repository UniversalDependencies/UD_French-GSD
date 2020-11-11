# Summary
The **UD_French-GSD** was converted in 2015 from the content head version of the universal
dependency treebank v2.0 (https://github.com/ryanmcd/uni-dep-tb).
It is updated since 2015 independently from the previous source.

# Introduction
The **UD_French-GSD** is converted from the content head version of the universal
dependency treebank v2.0 (https://github.com/ryanmcd/uni-dep-tb).
The README for the original project is available below.

The version 2.7 of **UD_French-GSD** data consists of 400,399 words (16,341 sentences).
No sentence id were available in the original resource, so new `sent_id` were automatically introduced in the converted corpus with prefixes `fr-ud-train`, `fr-ud-dev` and `fr-ud-test` on the corresponding original files, followed by a 5 digit number following the order of sentences in the original files.

:warning: to meet the size requirements of test data of 10K words, a part of the dev original file was moved to the test file!
Since version 2.0, the splitting of data is:

 * file `fr-ud-train.conll`: 14,449 sentences; 354,662 words
  * `fr-ud-train_00001` to `fr-ud-train_14554`
 * file `fr-ud-dev.conll`: 1,476 sentences; 35,718 words
  * `fr-ud-dev_00001` to `fr-ud-dev_01478`
 * file `fr-ud-test.conll`: 416 sentences; 10,019 words
  * `fr_ud-test_00001` to `fr_ud-test_00298`
  * `fr-ud-dev_01479` to `fr-ud-dev_01596`

Sentences are shuffled and there is no way to know what is the source or the genre of a given sentence.

Probably due to some bug in a conversion program, version 1.2 contains many truncated sentences (date missing for instance).
Almost every truncated sentence are from Wikipedia, so it was possible to recover the original text.
Most of the truncated sentences were completed in version 1.3. Some sentences were completed later.
There are probably still some truncated sentences.

# Acknowledgments

The latest version of the corpus was produced by Marie-Catherine de Marneffe, Bruno Guillaume, Matias Grioni, Carly Dickerson and Guy Perrier.
Automatic modifications and consistency checking were partly done using the [Grew software](http://grew.fr).

See below for references and acknowledgments concerning the original corpus.

# Reference

[In French] Bruno Guillaume, Marie-Catherine de Marneffe, Guy Perrier. *Conversion et améliorations de corpus
du français annotés en Universal Dependencies.* Traitement Automatique des Langues, ATALA, 2019,
60 (2), pp.71-95. [hal-02267418](https://hal.inria.fr/hal-02267418)

# Changelog

* 2020-11-15 v2.7
  New conversion from [SUD data](https://github.com/surfacesyntacticud/SUD_French-GSD/tree/r2.7).

* 2020-05-15 v2.6
  * **UD_French-GSD** is now maintained in the [SUD format](https://surfacesyntacticud.github.io/) and converter to UD with the [Grew](http://grew.fr)-based conversion system [SUD_to_UD](https://github.com/surfacesyntacticud/tools/tree/master/converter).

* 2019-11-15 v2.5
  * Google gave permission to drop the "NC" restriction from the license.
    This applies to the UD annotations (not the underlying content, of which Google claims no ownership or copyright).
  * Many corrections:
     * expletive annotation with relations `expl:subj`, `expl:comp` and `expl:pass`
     * `aux` -> `aux:tense`
     * `MWEPOS` -> `EXTPOS`
     * systematic review of non-projective trees
     * improved ellipsis annotations
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


```
===================================
Universal Dependency Treebanks v2.0
(legacy information)
===================================

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
   made available under a CC BY-SA 4.0. GOOGLE MAKES
   THEM AVAILABLE TO YOU 'AS IS', WITHOUT ANY WARRANTY OF ANY KIND, WHETHER
   EXPRESS OR IMPLIED. See attached LICENSE file for the text of CC BY-NC-SA.

Portions of the German data were sampled from the CoNLL 2006 Tiger Treebank
data. Hans Uszkoreit graciously gave permission to use the underlying
sentences in this data as part of this release.

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
See https://github.com/ryanmcd/uni-dep-tb for more details
```


=== Machine-readable metadata (DO NOT REMOVE!) ================================
Data available since: UD v1.0
License: CC BY-SA 4.0
Includes text: yes
Genre: blog news reviews wiki
Lemmas: automatic with corrections
UPOS: converted with corrections
XPOS: not available
Features: automatic with corrections
Relations: converted with corrections
Contributors: de Marneffe, Marie-Catherine; Guillaume, Bruno; McDonald, Ryan; Suhr, Alane; Nivre, Joakim; Grioni, Matias; Dickerson, Carly; Perrier, Guy
Contributing: elsewhere
Contact: demarneffe.1@osu.edu, bruno.guillaume@inria.fr
===============================================================================
