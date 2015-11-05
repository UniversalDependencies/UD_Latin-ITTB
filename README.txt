Latin data from the Index Thomisticus Treebank. It contains the complete work by Thomas Aquinas
(1225–1274; medieval Latin), and by 61 authors related to Thomas.

The UD_Latin-ITT dataset results from conversion of the Index Thomisticus Treebank.
The data was first converted to the Prague dependency style as a part of HamleDT;
then it was automatically converted to Universal Dependencies (HamleDT 3.0, 2015). The first
release of Universal Dependencies that includes this treebank is UD v1.2 in November 2015. The
conversion of dependency relations and morphological features is almost identical to HamleDT
3.0. On the other hand, part of speech tags have been significantly improved. The original ITT
categories were based on a “tripartity” classification, which is based purely on inflectional
behavior of words, and distinguishes nominal inflection, participles, and verbal inflection.

In HamleDT 3.0, all nominally inflected words were tagged NOUN. In UD 1.2, they are further
divided according to their lemma. A lexicon was obtained from the latin lemmatizer LEMLAT, and
words not covered by the lexicon were manually disambiguated by Berta Gonzales and Marco
Passarotti. Thus the nominally inflected words were retagged as NOUN, ADJ, PRON, DET or NUM.
Furthermore, the uninflected words, previously tagged PART, are now retagged as ADV, ADP, CONJ,
INTJ.

References:

http://itreebank.marginalia.it/ ... Index Thomisticus Treebank
http://ufal.mff.cuni.cz/hamledt ... HamleDT
http://ufal.mff.cuni.cz/treex ... Treex is the software used for conversion
http://ufal.mff.cuni.cz/interset ... Interset was used to convert POS tags and features

@article{lait,
  author    = {Passarotti, Marco and Dell’Orletta, Felice},
  title     = {Improvements in parsing the index thomisticus treebank. Revision, combination and a feature model for medieval Latin},
  journal   = {Training},
  volume    = {2},
  pages     = {61--024},
  year      = {2010}
}



=== Machine-readable metadata =================================================
Documentation status: stub
Data source: automatic
Data available since: UD v1.2
License: CC BY-NC-SA 3.0
Genre: nonfiction
Contributors: Passarotti, Marco; Zeman, Daniel; Gonzales, Berta
===============================================================================
