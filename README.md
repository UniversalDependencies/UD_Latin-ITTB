# Summary

Latin data from the _Index Thomisticus_ Treebank. The treebank data are taken from the _Index Thomisticus_ corpus by Roberto Busa SJ, which contains the complete work by Thomas Aquinas (1225–1274; Medieval Latin), and by 61 authors related to Thomas.


# Releases

The UD_Latin-IT-TB dataset results from the conversion of the _Index Thomisticus_ Treebank.
The data were first converted to the Prague dependency style as a part of HamleDT;
then they were automatically converted to Universal Dependencies (HamleDT 3.0, 2015).

The first release of Universal Dependencies that includes this treebank was UD v1.2 in November 2015. The
conversion of dependency relations and morphological features was almost identical to HamleDT
3.0.
On the other hand, part of speech tags were significantly improved. The original IT-TB
categories are based on a “tripartite” classification, which is based purely on the inflectional
behavior of words, and distinguishes nominal inflection (including participles), no inflection and verbal inflection.

In HamleDT 3.0, all nominally inflected words were tagged NOUN. In UD v1.2, they were further
divided according to their lemma. A lexicon was obtained from the latin lemmatizer LEMLAT (https://github.com/CIRCSE/LEMLAT3), and words not covered by the lexicon were manually disambiguated by Berta González Saavedra and Marco
C. Passarotti. Thus the nominally inflected words were retagged as NOUN, ADJ, PRON, DET or NUM.
Furthermore, the uninflected words, previously tagged PART, are now retagged as ADV, ADP, CONJ,
INTJ.


# Acknowledgments

* http://itreebank.marginalia.it/ ... Index Thomisticus Treebank
* http://ufal.mff.cuni.cz/hamledt ... HamleDT
* http://ufal.mff.cuni.cz/treex ... Treex is the software used for conversion
* http://ufal.mff.cuni.cz/interset ... Interset was used to convert POS tags and features

<pre>
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

2017-03-01 v2.0
  * Converted to UD v2 guidelines.
  * Reconsidered PRON vs. DET distinction.
  * Improved advmod vs. obl distinction.
2016-05-15 v1.3
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
Relations: converted from manual
Contributors: Passarotti, Marco; Zeman, Daniel; Gonzáles Saavedra, Berta
Contributing: elsewhere
Contact: zeman@ufal.mff.cuni.cz
===============================================================================
</pre>
