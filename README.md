# Summary
The French UD was converted in 2015 from the content head version of the universal
dependency treebank v2.0 (https://github.com/ryanmcd/uni-dep-tb).
It is updated since 2015 independently from the previous source.

# Introduction
The French UD is converted from the content head version of the universal
dependency treebank v2.0 (https://github.com/ryanmcd/uni-dep-tb).
The README for the original project is available in the file `README_Google_dataset.txt`.

The French data consists of 402,404 words (16,448 sentences).
No sentence id were available in the original resource, so new `sent_id` were automatically introduced in the converted corpus with prefixes `fr-ud-train`, `fr-ud-dev` and `fr-ud-test` on the correponding original files, followed by a 5 digit number following the order of sentences.

:warning: to meet the size requirements of test data of 10K words, a part of the dev original file was moved to the test file!
Since version 2.0, the splitting of data is:

 * file `fr-ud-train.conll`: 14,554 sentences; 356,613 words
 	* `fr-ud-train_00001` to `fr-ud-train_14554`
 * file `fr-ud-dev.conll`: 1,478 sentences; 35,771 words
 	* `fr-ud-dev_00001` to `fr-ud-dev_01478`
 * file `fr-ud-test.conll`: 416 sentences; 10,020 words	* `fr_ud-test_00001` to `fr_ud-test_00298`
 	* `fr-ud-dev_01479` to `fr-ud-dev_01596`

Sentences are shuffled and there is no way to know what is the genre of a given sentence.

Probably due to some bug in a conversion program, version 1.2 contained many truncated sentences (date missing for instance). Almost every truncated sentence was sentence from Wikidepia, so it is possible to recover the original text. Most of the truncated sentences were completedin version 1.3. Some sentences are completed later or even still truncated.

# Acknowledgments

The last version of the corpus was produced by Marie-Catherine de Marneffe, Bruno Guillaume and Matias Grioni.
Automatic modifications and consistency checking were partly done using the Grew software (see http://grew.loria.fr).

See file `README_Google_dataset.txt` for references and acknowledgments concerning the original corpus.

# Changelog

* 2017-11-15 v2.1
  * Only être, avoir or faire with the POS tag `AUX`
  * modifications taking into account new decisions taken for harmonisation of several French Treebanks (causative, copules, auxiliaries, change of `nmod:poss` in `det`)
* 2017-03-01 v2.0
  * Conversion of data to follow new guidelines (automatic conversions with manual verifications and manual annotation of `nmod` VS `obl` in ambiguous cases
* 2016-11-15 v.1.4
  * POS annotations were made more consistent
  * Several dependency paths were also made more consistent across similar expressions
  * Only “avoir” and “être” are considered copula
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
Contributors: de Marneffe, Marie-Catherine; Guillaume, Bruno; McDonald, Ryan; Suhr, Alane; Nivre, Joakim; Grioni, Matias
Contributing: here
Contact: demarneffe.1@osu.edu, bruno.guillaume@inria.fr
===============================================================================
