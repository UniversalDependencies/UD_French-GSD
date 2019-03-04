# UD_French-GSD
We have decided in 2018 to enrich the annotation of MWE with a mechanism to encode a partially fixed expressions: an expression for which we can give a regular internal syntactic structure but which is not externally regular (see example above).

Since February 2019, these annotations are not considered as valid. As they are richer than the `fixed` annotation expected in UD, we keep the richer annotation in the `not-to-release` subfolder, together with a automatic convertion to standard and valid UD.

## Transformation
The Grew software is used for the transforamtion (see [Grew installation procedure](http://grew.fr/install), note that a recent installation is needed with at least `libcaml-grew` version `1.1.3` released in March 2019).
The conversion is done with the 3 commands:

```
grew transform -grs grs/regularize_synt_into_fixed.grs -i fr_gsd-ud-dev.conllu -o ../fr_gsd-ud-dev.conllu
grew transform -grs grs/regularize_synt_into_fixed.grs -i fr_gsd-ud-test.conllu -o ../fr_gsd-ud-test.conllu
grew transform -grs grs/regularize_synt_into_fixed.grs -i fr_gsd-ud-train.conllu -o ../fr_gsd-ud-train.conllu
```

## Validation
After transformation, it is sensible to apply the UD validator on the converted files. It supposes that you have a local copy (or a link to) the [UD tools repository](https://github.com/UniversalDependencies/tools).

```
tools/validate.py --lang fr ../fr_gsd-ud-dev.conllu
tools/validate.py --lang fr ../fr_gsd-ud-test.conllu
tools/validate.py --lang fr ../fr_gsd-ud-train.conllu
```



## Example
For the sentence `fr-ud-dev_00372`: _En effet, il croyait connaître les classiques ;_, the enriched annotation is:

```
# sent_id = fr-ud-dev_00372
# text = En effet, il croyait connaître les classiques ;
1	En	en	ADP	_	_	2	case	_	INMWE=Yes
2	effet	effet	NOUN	_	Gender=Masc|Number=Sing	5	advmod	_	MWEPOS=ADV|SpaceAfter=No
3	,	,	PUNCT	_	_	2	punct	_	_
4	il	il	PRON	_	Gender=Masc|Number=Sing|Person=3|PronType=Prs	5	nsubj	_	_
5	croyait	croire	VERB	_	Mood=Ind|Number=Sing|Person=3|Tense=Imp|VerbForm=Fin	0	root	_	_
6	connaître	connaître	VERB	_	VerbForm=Inf	5	xcomp	_	_
7	les	le	DET	_	Definite=Def|Gender=Masc|Number=Plur|PronType=Art	8	det	_	_
8	classiques	classique	NOUN	_	Gender=Masc|Number=Plur	6	obj	_	_
9	;	;	PUNCT	_	_	5	punct	_	_
```

![Alt Text](images/1_fr-ud-dev_00372.svg)

This annotation is not valid because the word _effet_ is a `NOUN` and it is the dependent of the `advmod` relation.

This is projeted on:

```
# sent_id = fr-ud-dev_00372
# text = En effet, il croyait connaître les classiques ;
1	En	en	ADP	_	_	5	advmod	_	MWEPOS=ADV
2	effet	effet	NOUN	_	Gender=Masc|Number=Sing	1	fixed	_	SpaceAfter=No
3	,	,	PUNCT	_	_	1	punct	_	_
4	il	il	PRON	_	Gender=Masc|Number=Sing|Person=3|PronType=Prs	5	nsubj	_	_
5	croyait	croire	VERB	_	Mood=Ind|Number=Sing|Person=3|Tense=Imp|VerbForm=Fin	0	root	_	_
6	connaître	connaître	VERB	_	VerbForm=Inf	5	xcomp	_	_
7	les	le	DET	_	Definite=Def|Gender=Masc|Number=Plur|PronType=Art	8	det	_	_
8	classiques	classique	NOUN	_	Gender=Masc|Number=Plur	6	obj	_	_
9	;	;	PUNCT	_	_	5	punct	_	_
```
![Alt Text](images/2_fr-ud-dev_00372.svg)
