# Summary

Latin data from the _Index Thomisticus_ Treebank. Data are taken from the _Index Thomisticus_ corpus by Roberto Busa SJ, which contains the complete work by Thomas Aquinas (1225–1274; Medieval Latin) and by 61 other authors related to Thomas.


# History of the Releases

The UD_Latin-ITTB dataset results from the automated conversion of the _Index Thomisticus_ Treebank from the Prague dependency treebank (PDT) style into the Universal Dependencies (UD) style.

Its first version was part of HamleDT and as such made use of the PDT style, which was later automatically converted to the UD style as part of HamleDT 3.0 in 2015. That same year in November UD v1.2 was released, including for the first time the IT-TB, with almost identical dependency relations and morphological features as those in HamleDT 3.0, all the while improving its part-of-speech tagging.

The original part-of-speech classification of the _Index Thomisticus_ is tripartite, in that solely the pure inflectional behaviour of words is taken into account, thus distinguishing only between nominal inflection (adjectives, nouns, pronouns, numerals, with a subclass for verbal nominal inflection, such as participles), verbal inflection and absence of inflection (adverbs, prepositions, conjunctions,...). In HamleDT 3.0, all nominally inflecting words had been tagged NOUN. In UD v1.2 a first differentiation was implemented: separated lexicons for adjectives (corresponding to PoS ADJ or NUM), nouns (NOUN) and pronouns (PRON and DET) were obtained by means of the Latin lemmatiser LEMLAT, and unrecognized words were manually disambiguated by Berta González Saavedra and Marco Passarotti. This way, tagging nominally inflecting words became possible, also for later versions, and at the same time invariable words, previously generically treated as PART, were reanalyzed as ADV, ADP, CCONJ, SCONJ or INTJ.

The release of UD v2.3 sees a major update and revision of the conversion scripts for the _Index Thomisticus_ Treebank into the UD style, significantly improving the overall conversion quality, both in terms of _deprel_'s and subtree structures, as of part-of-speech tagging and lemmatisation. Guidelines for a common annotation style of the three current Latin UD treebanks have also been put into effect.

Release UD v2.13 mainly see the realisation in IT-TB of a harmonisation effort between Latin UD treebanks following (Gamba & Zeman 2023a) and (Gamba & Zeman 2023b), bringing all of them closer to being based on the same standard, despite their different origins and conversion processes.

# Acknowledgments

* https://lila-erc.eu/ ... The LiLa project (Linking Latin) also includes the _Index Thomisticus_ and its UD version
* http://itreebank.marginalia.it/ ... Index Thomisticus Treebank
* http://ufal.mff.cuni.cz/hamledt ... HamleDT
* http://ufal.mff.cuni.cz/treex ... Treex is the software used for conversion
* http://ufal.mff.cuni.cz/interset ... Interset is used to convert PoS tags and features

<pre>
@article{morpharmo,
  author    = {Gamba, Federica and Zeman, Daniel},
  title     = {Latin Morphology through the Centuries: Ensuring Consistency for Better Language Processing},
  journal   = {Proceedings of the Ancient Language Processing Workshop associated with the 14th International Conference on Recent Advances in Natural Language Processing RANLP 2023},
  year      = {2023},
  address = {Varna, Bulgaria},
url = {https://ufal.mff.cuni.cz/biblio/attachments/2023-gamba-p3787387064232511302.pdf}
}

@article{harmo,
  author    = {Gamba, Federica and Zeman, Daniel},
  title     = {Universalising Latin Universal Dependencies: a harmonisation of Latin treebanks in UD},
  journal   = {Proceedings of the Sixth Workshop on Universal Dependencies (UDW, GURT/SyntaxFest 2023)}},
  year      = {2023},
  address = {Washington, DC, USA},
  url = {https://aclanthology.org/2023.udw-1.2/}
}

@article{lait-ud,
  author    = {Cecchini, Flavio Massimiliano and Passarotti, Marco and Marongiu, Paola and Zeman, Daniel},
  title     = {Challenges in Converting the \emph{Index Thomisticus} treebank into Universal Dependencies},
  journal   = {Proceedings of the Universal Dependencies Workshop 2018 (UDW 2018)},
  year      = {2018},
  address = {Brussels, Belgium}
}

@article{lait,
  author    = {Passarotti, Marco and Dell’Orletta, Felice},
  title     = {Improvements in parsing the index thomisticus treebank. Revision, combination and a feature model for medieval Latin},
  journal   = {Training},
  volume    = {2},
  pages     = {61--024},
  year      = {2010}
}
</pre>

# Changelog

* 2023-11-15 v2.13
    * Implementation of overall syntactic and morphologic harmonisation following (Gamba & Zeman 2023a) and (Gamba & Zeman 2023b), though excluding multi-word treatment (splitting) of some tokens (e.g. *inquantum*, *respublica*,...)
        * most notable is the general restructuring of copular constructions, now having the `AUX` *sum* regularly depending as a functional element 
    * Enrichment through heuristics with additional [`obl:agent`]() (agent arguments in passive constructions) and [`advcl:abs`]() (so-called ablativus absolutus) subrelations (totally absent in previous releases)
    * Improvement of annotation for foreign terms/names and "proper nouns" in general
    * General further rationalisation and/or correction of some lemmas and morphological features (e.g. *procul+dubius* > *proculdubio*, *semetipse* > *semetipsum*, regular treatment of *inuicem* as a reciprocal `PRON`, missing features for *sum*, etc.) 
    * Stark reduction of the use of the [`fixed`]() relation
        * complete re-annotation of 86 "gapping" (i.e. non/projective) `fixed` constructions, some of which now treated by means of [`reparandum`]()
        * down from 921 to 111 occurrences for all other contiguous `fixed` constructions, including phrases such as *secundum quod*, *usque ad*, *etiam si*, etc. 
    * Orthographic univerbation of the conjunctional clitics *que* (34) and *ue* (1), introducing multi-word tokens   
* 2022-11-15 v2.11
    * Implementations of the [amendment](https://universaldependencies.org/changes.html#multiple-subjects) for clausal non-verbal copular constructions and corrections regarding multiple subjects and introduction of the `:outer` subtype for subjects and copulas
    * Implementation of the [amendment for reported speech](https://universaldependencies.org/changes.html#reported-speech), with the introduction of the `:reported` and `:reporting` subtypes
    * Implementation of the proposal of [`VerbForm`](la-feat/VerbForm) reform as for (Cecchini, 2021; see documentation entry for `VerbForm`)
        * at the same time, introduction of the `TraditionalMood` and `TraditionalTense` features in `MISC` to take into account traditional denominations  
    * Double-pronoun constructions, also called free relatives, have been highlighted semi-automatically by means of the newly introduced `:relcl` subtype
    * Many "small words" (especially particles) and their features have started being standardised among treebanks. For example, *is*/*ea*/*id* is now always a `PRON` with `PronType=Prs`, *nam* always a `PART`, `AdvType` has been added to many "adverbs"...
        * *et*, *nec* etc. now stay `CCONJ` even when acting as focalisers
        * *unus* is uniformed to a determiner (`DET`) with both cardinal numeral type and indefinite pronoun type, and numeric value `1`
        * multiple (comma-separated) `PronType`s have been revised and reduced to one; the interrogative `Int` value has been streamlined as possible 
    * Remotion of the value `Pos` for the feature `Degree` ("positive" degree is still retrievable as the absence of another degree)
    * Various other occasional corrections of the annotation
        * the IT-TB is still waiting for a multiword treatment of clitics (e.g. *-que* 'and') and a standardisation of copular constructions

* 2020-11-1 v2.7
    * Addition of the fourth book of the _Summa contra gentiles_ by Thomas Aquinas to the treebank
        * 97 480 new tokens, for a total of 450 515 annotated tokens in the IT-TB
        * All the new sentences have been added to the `train` dataset, which now amounts to 390 785 tokens
    * The documents are split in the following way:
        * Aquinas's _Summa contra gentiles_ book I (SCG1): the whole `dev` and `test` sets, up to sentence 104 in the `train` set
        * SCG2: from `train` 105 to `train` 5657
        * SCG3: from `train` 5658 to `train` 13 519
        * SCG4: from `train` 16 810 to `train` 22 775
        * Concordances of _forma_ in the IT-TB (various authors): from `train` 13520 to `train` 16 809
    * The issue of this update follows the same pipeline as the previous one and focuses only on the SCG4; already existing tokens have not been modified
        * As in the last update, some minor and limited manual corrections have been necessary for problematic constructions
    * Following improved standards, there are some very limited updates to the annotation style, which will be extended to the rest of the treebank in a future release
    * At the moment, the treatment of some token categories is somewhat inconsistent (e.g. NOUN/PROPN distinction, abbreviations, etc.), and this will be also addressed in a future release 

* 2020-5-18 v2.6
    * Update to meet new validation standards:
        * All non-projective punctuations solved by means of Udapi's FixPunct module
        * Major manual corrections of some problematic structures (ellipses and/or co-ordinations) in some sentences
    * Minor occasional manual corrections of annotation or conversion errors (punctuation having dependencies, wrong parts of speech, etc)
        * Improvement of the morphological layer by automatic addition of new features (Aspect, Number[psor], etc)
    * Added the distinction between sentence reference in the sets (e.g. dev1) and reference in the corpus (e.g. ittb-scg-s1) 

* 2019-5-15 v2.4
    * The new UD validation script has prompted further improvements to the conversion routine:
        * parts of speech PART and DET (for the lemma _plerusque_), that continued to appear in the conversion, have been changed to ADV and ADJ respectively;
        * small improvements to the treatment of nested co-ordinations and relative clauses;
        * correct treatment of justaxposed nominals as either _flat_ or _appos_, especially in the case of ambiguity between NOUN and ADJ;
        * new coherent treatment of abbreviations, symbols and numbers, now receiving a part of speech instead of X;
        * other minor adjustments regarding more esoteric aspects of morphosyntactic annotation and technicalities;    
        * finally, various morphological and syntactical annotation errors in the original annotation of the _Index Thomisticus_ have been detected and corrected.
      * Note: as of now, unfortunately the conllu files do not pass the UD validation script. Future work will be needed to smooth the conversion, but the present version still maintains its validity.

* 2018-11-01 v2.3
      * Book three of _Summa contra gentiles_ now completely annotated with more than 3500 new sentences and 60000 additional tokens
      * Generic major update of the conversion script:
        * ellipsis and ExD _afun_'s are now addressed; where heuristics might fail, warnings are issued;
        * PDT-style apposition subtrees are completely restructured for UD conversion; new relation subtype _appos_ and composite _deprel_ advmod:cc for appositive adverbial modifiers (_scilicet_);
        * tagging of proper nouns with PROPN by means of a hard-coded lexicon;
        * correct treatment of xcomp and ccomp;
        * INTJ PoS removed;
        * introduction of relation subtype advmod for verbal attributes (often corresponding to PDT _afun_ AtvV);
        * many other minor corrections, additions and improvements. 
    * Applied common guidelines for Latin treebanks. The major points:
        * adverbs always get their positive degree as lemma;
        * the part-of-speech DET has been removed and retained only for the proto-article _ly_;
        * pronouns in an attributive function receive _deprel_ det;
        * possessive pronouns in an attributive function receive PoS ADJ and _deprel_ amod;
        * some lemmas were harmonised to a common standard.
    * Manual corrections of annotation errors in the original data (mostly regarding co-ordinations and appositions)
    * New split of dev/test/train data: dev and test contain the first 2101+2101 sentences in the _Summa contra gentiles_, while train all the remaining ones, including the concordances of the word _forma_ in the work of Thomas Aquinas.

* 2017-03-01 v2.0
      * Converted to UD v2 guidelines.
      * Reconsidered PRON vs. DET distinction.
      * Improved advmod vs. obl distinction.

* 2016-05-15 v1.3
      * Fixed adverbs that were attached as nmod; correct: advmod.
      * Improved conversion of AuxY.
      * PROPN are now distinguished from NOUN.
      * Larger data: almost 2000 newly annotated sentences.
      * Manual fixes of annotation errors in the old data.
      * An exceptional one-time change of the train/dev/test data split was
    necessary to overcome past bad design and to reflect the evolution of the
    treebank. Beware: UD 1.2 dev/test data have become UD 1.3 train data and
    vice versa, the data split is thus not backwards compatible!



<pre>
=== Machine-readable metadata =================================================
Data available since: UD v1.2
License: CC BY-NC-SA 3.0
Includes text: yes
Genre: nonfiction
Lemmas: converted from manual
UPOS: converted from manual
XPOS: manual native
Features: converted from manual
Relations: converted with corrections
Contributors: Passarotti, Marco; Testori, Marinella; Zeman, Daniel; González Saavedra, Berta; Cecchini, Flavio Massimiliano
Contributing: elsewhere
Contact: zeman@ufal.mff.cuni.cz
===============================================================================
</pre>
