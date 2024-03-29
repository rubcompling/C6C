# C6C Importers

1. [CoNLLUPlusImporter](#conlluplusimporter)
2. [CoNLLUImporter](#conlluimporter)
3. [CoNLL2000Importer](#conll2000importer)
4. [TCFDTAImporter](#tcfdtaimporter)
5. [XMLDTAImporter](#xmldtaimporter)
6. [DTATSVImporter](#dtatsvimporter)
7. [TigerImporter](#tigerimporter)
8. [TigerXMLImporter](#tigerxmlimporter)
9. [TuebaDzImporter](#tuebadzimporter)
10. [TUEBADSConllImporter](#tuebadsconllimporter)
11. [TuebaDZPTBImporter](#tuebadzptbimporter)
12. [ANNISGridSentenceImporter](#annisgridsentenceimporter)
13. [WebAnnoTopFImporter](#webannotopfimporter)
14. [WebAnnoTSVImporter](#webannotsvimporter)
15. [CoraXMLReMImporter](#coraxmlremimporter)
16. [CoraXMLAnselmImporter](#coraxmlanselmimporter)
17. [CoraXMLReFBoImporter](#coraxmlrefboimporter)
18. [TextImporter](#textimporter)
19. [XMLKaJuKImporter](#xmlkajukimporter)
20. [MercuriusTigerXMLImporter](#mercuriustigerxmlimporter)
21. [ReFUPImporter](#refupimporter)
22. [XMLFnhdCImporter](#xmlfnhdcimporter)
23. [GerManCCoNLLImporter](#germancconllimporter)
24. [DDBTigerNegraImporter](#ddbtigernegraimporter)
25. [FuerstinnenEXBImporter](#fuerstinnenexbimporter)
26. [SDeWaCIteratorImporter](#sdewaciteratorimporter)
27. [GraphVarEXBImporter](#graphvarexbimporter)

### CoNLLUPlusImporter

- Name for usage in command line: `conlluplus`

#### Input Format

- [CoNLL-U Plus Format](https://universaldependencies.org/ext-format.html)
- Lines containing the annotations of a word (seperated by tabs), blank lines marking sentence boundaries.
- Comment lines starting with hash (#).
- First line is a comment line listing the column names.
- Field contains an underscore if info is not available for the current word.

#### Meta-Info

- No meta-info available in this format.

#### Annotations

- Can contain any subset of the following annotations plus additional annotations.

column name | annotation
------ | ------
ID | word index
FORM | word form
LEMMA | Lemma
UPOS | Universal POS-Tag
XPOS | STTS-Tag
FEATS | morphological features
HEAD | head
DEPREL | dependency relation to the head
DEPS | dependency graph
MISC | other annotation  

### CoNLLUImporter

- Name for usage in command line: `conllu`

#### Input Format

- [CoNLL-U Format](https://universaldependencies.org/format.html)
- Lines containing the annotations of a word (seperated by tabs), blank lines marking sentence boundaries
- 10 columns containing the following annotations for each word:  
	ID (word index), FORM (word form), LEMMA (Lemma), UPOS (universal POS-tag), XPOS (language specific POS-tag),
	FEATS (Morphological features), HEAD (head), DEPREL (dependency relation to the head), DEPS (dependency graph),
	MISC (other annotation)
- Field contains an underscore if info is not available for the current word

#### Input Data

- e.g. RIDGES Corpus ([RIDGES Herbology Version 8.0](https://www.laudatio-repository.org/browse/corpus/EyR8CnMB7CArCQ9CsY6Y/corpora))

#### Meta-Info

- No meta-info available in this format.

#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form
LEMMA | Lemma
UPOS | Universal POS-Tag
XPOS | STTS-Tag
FEATS | morphological features
HEAD | head
DEPREL | dependency relation to the head
DEPS | dependency graph
MISC | other annotation  

#### Additional Info

- Only for RIDGES Corpus: annotations in three columns of the CoNLL-U format (normally corresponding to UPOS, DEPS, MISC) weren't extracted because they contained the same information as the columns XPOS, HEAD, DEPREL

### CoNLL2000Importer

- Name for usage in command line: `conll2000`

#### Input Format

- [CoNLL-2000](https://www.clips.uantwerpen.be/conll2000/chunking/)
- Lines containing the annotations of a word (seperated by whitespaces), blank lines marking sentence boundaries.
- 3 columns containing the following annotations for each word:  
	FORM (word form), XPOS (language specific POS-tag), CHUNK (syntactically correlated parts of words)
- Field contains an underscore if info is not available for the current word.

#### Input Data

- e.g. Data for the [CoNLL-2000 shared task](https://www.clips.uantwerpen.be/conll2000/chunking/)

#### Meta-Info

- No meta-info available in this format.

#### Annotations

column name | annotation
------ | ------
FORM | word form
XPOS | language specific POS-tag
CHUNK | syntactically correlated parts of words  

### TCFDTAImporter

- Name for usage in command line: `tcfdta`

#### Input Format

- [Text Corpus Format](https://weblicht.sfs.uni-tuebingen.de/weblichtwiki/index.php/The_TCF_Format)
- XML-File consisting of a `<MetaData>` and a `<TextCorpus>` node.
- The `<TextCorpus>` node contains the tokens and further annotation layers.

#### Input Data

- [Deutsches Textarchiv](https://www.deutschestextarchiv.de/download#tcf)

#### Meta-Info

- Not available.

#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form
LEMMA | Lemma
XPOS | STTS-Tag
NORM | normalised word form
NORM_OP | operation for normalising the word form
NORM_REASON | reason for normalising the word form  

### XMLDTAImporter

- Name for usage in command line: `xmldta`

#### Input Format

- XML-Format
- File consisting of a `<teiHeader>` node which contains meta-information and a `<text>` node which contains further annotation layers.

#### Input Data

- [Deutsches Textarchiv](https://www.deutschestextarchiv.de)

#### Meta-Info

- Following meta-infos are extracted into a seperate file:
	filename, DTA filename, author, title, subtitle, year, place, number of tokens, number of types, number of characters,
	URL, text class (DTA main), text class (DTA sub), language code, language
- Following meta-infos are extracted into the output file:
	sent_ID (DTA), paragraph_id, text_section, div_type

#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form
LEMMA | Lemma
XPOS | STTS-Tag
DTA:NORM | normalised word form
DTA:ORIG | original word form
DTA:REG | regularised word form  

### DTATSVImporter

- Importer for WebAnno TSV export of custom annotations from [project C6](https://github.com/rubcompling/C6Samples) (SFB 1102).

### TigerImporter

- Name for usage in command line: `tiger`

#### Input Format

- [CoNLL-2009](https://ufal.mff.cuni.cz/conll2009-st/task-description.html)
- Lines containing the annotations of a word (seperated by tabs), blank lines marking sentence boundaries
- 15 columns containing the following annotations for each word:  
	ID (word index), FORM (word form), LEMMA (Lemma), PLEMMA (automatically predicted Lemma), POS (language specific POS-tag),
	PPOS (automatically predicted POS-tag), FEAT (Morphological features), PFEAT (automatically predicted features), HEAD (head),
	PHEAD (automatically predicted head), DEPREL (dependency relation to the head), PDEPREL (automatically predicted dependency relation),
	FILLPRED (contains `Y` if PRED should be filled), PRED (predicate), APREDs (additional predicates)
- Field contains an underscore if info is not available for the current word

#### Input Data

- [Tiger Corpus Release 2.2](https://www.ims.uni-stuttgart.de/forschung/ressourcen/korpora/tiger/)
- All Documents are stored in the file `tiger_release_aug07.corrected.16012013.conll09`

#### Meta-Info

- TSV-Files containing the meta-info for all documents are stored in the directory `TIGER2.2.doc.zip\TIGER2.2.doc`
- Following meta-infos are extracted into a seperate file:  
  filename, author, gender (of the author), folder (train/dev/test), category of note (collection/other), note (type/heading of collection doc/description)
- Following meta-infos are extracted into the output file:  
  sentence ID in Tiger, sentence type

#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form
LEMMA | Lemma
UPOS | Universal POS-Tag
XPOS | STTS-Tag
FEATS | morphological features
HEAD | head
DEPREL | dependency relation to the head
DEPS | dependency graph
MISC | other annotation  

### TigerXMLImporter

- Name for usage in command line: `tigerxml`

#### Input Format

- [TIGER-XML Format](https://www.ims.uni-stuttgart.de/documents/ressourcen/werkzeuge/tigersearch/doc/html/TigerXML.html)
- The `<head>` node contains meta-information and information about the annotations.
- The `<body>` node contains the individual sentences with their syntax-graphs.
- Each graph consists of `<terminals>`, which contain the words and the corresponding annotations, and `<nonterminals>`,
	which contain the structure of the syntax-tree including the corresponding edge and node labels.

#### Input Data

- [TIGER Corpus](https://www.ims.uni-stuttgart.de/forschung/ressourcen/korpora/tiger/)

#### Meta-Info

- Not available in this format.

#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form
LEMMA | Lemma
XPOS | STTS-Tag
FEATS | morphological features
TigerID | word index in the Tiger-files  

### TuebaDzImporter

- Name for usage in command line: `tuebadz`

#### Input Format

- [CoNLL-U Format](https://universaldependencies.org/format.html)
- Lines containing the annotations of a word (seperated by tabs), blank lines marking sentence boundaries
- 10 columns containing the following annotations for each word:  
	ID (word index), FORM (word form), LEMMA (Lemma), UPOS (universal POS-tag), XPOS (language specific POS-tag),
	FEATS (Morphological features), HEAD (head), DEPREL (dependency relation to the head), DEPS (dependency graph),
	MISC (other annotation)
- Field contains an underscore if info is not available for the current word

#### Input Data

- [TüBa-D/Z Release 11.0](https://uni-tuebingen.de/fakultaeten/philosophische-fakultaet/fachbereiche/neuphilologie/seminar-fuer-sprachwissenschaft/arbeitsbereiche/allg-sprachwissenschaft-computerlinguistik/ressourcen/corpora/tueba-dz/)
- All Documents are stored in the file `tuebadz-11.0-conll-u-v2.txt`

#### Meta-Info

- Following meta-infos are extracted into the output file:  
  document ID in TüBa, sentence ID in TüBa
  
#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form
LEMMA | Lemma
UPOS | Universal POS-Tag
XPOS | STTS-Tag
FEATS | morphological features from the universal feature inventory
HEAD | head
DEPREL | dependency relation to the head
DEPS | dependency graph
MISC | SpaceAfter
Morph | morphological features from the source TüBa-D/Z data
NE | named entity type
TopoField | topological field
Typo | typo correction
WSD | GermaNet ID of the word sense  

#### Additional Info

- We divided the documents up into a training, development and test set (80-10-10) via random choice.

### TUEBADSConllImporter

- Name for usage in command line: `tuebadsconll`

#### Input Format

- CoNLL Format
- Lines containing the annotations of a word (seperated by tabs), blank lines marking sentence boundaries
- 5 columns containing the following annotations for each word:  
	ID (word index), FORM (word form), XPOS (language specific POS-tag), POS:HD (head), SYNTAX (syntactical information)
- Field contains an underscore if info is not available for the current word

#### Input Data

- Tübingen Treebank of Spoken German (TüBa-D/S)

#### Meta-Info

- Not available in this format.
  
#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form
XPOS | STTS-Tag
POS:HD | head
SYNTAX | syntactical information  

#### Additional Info

- The Processor `TUEBADSTopFExtractor` can be used to extract the topological field information out of the SYNTAX column.

### TuebaDZPTBImporter

- Name for usage in command line: `tuebatrees`

#### Input Format

- Penn Treebank Format
- Each line contains one sentence in a syntactic bracketing style

#### Input Data

- [TüBa-D/Z Release 11.0](https://uni-tuebingen.de/fakultaeten/philosophische-fakultaet/fachbereiche/neuphilologie/seminar-fuer-sprachwissenschaft/arbeitsbereiche/allg-sprachwissenschaft-computerlinguistik/ressourcen/corpora/tueba-dz/)

#### Meta-Info

- Following meta-info is extracted into the output file:
	syntax-tree string
  
#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form
XPOS | STTS-Tag
PTBLabel | Penn Treebank Label  

### ANNISGridSentenceImporter

- Name for usage in command line: `annisgrid`

#### Input Format

- Grid-Format from the [GridExporter](http://korpling.github.io/ANNIS/3.6/user-guide/aql-export.html) of ANNIS
- Each entry contains one sentence, blank lines mark sentence boundaries
- Each line consists of an annotation layer and the corresponding annotations, in which
	the span of tokens covered by each annotation is given in square brackets
- Lines containing metadata are marked with `meta::`

#### Input Data

- e.g. HIPKON ([Historisches Predigtenkorpus zum Nachfeld, Version 1.0](https://www.laudatio-repository.org/browse/corpus/yiTKCnMB7CArCQ9CxLhJ/corpora))

#### Meta-Info

- Following meta-infos are extracted into a seperate file:  
  filename, selection, edition, Überlieferungsträger (transmitter of the tradition), language stage, corpus part
- Following meta-infos are extracted into the output file:  
  sentence ID in Grid
  
#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form
XPOS | STTS-Tag
CAT | category of a phrase (nominal, verbal etc.)
CLEAN | normalized word form
EDITION | page and line number of the corresponding edition
FOKUS | focus type
GF | grammatical function
IS | information status
Kommentar | remark
POS | POS-Tag
Rekonstruktion | reconstructed word
SATZKLAMMER | left or right sentence bracket
SATZSTATUS | sentence status
Sprache | remark about the language
UEBERLIEFERUNGSTRAEGER | information about the transmission
VERLINKUNG | linking
WIEDERAUFNAHME | coreference   

#### Additional Info

- The Processors `HIPKONtoSTTSMapper` and `addmissingSTTStoHIPKON` can be used to match the POS-tags of HIPKON to the corresponding STTS-tags.

### WebAnnoTopFImporter

- Name for usage in command line: `webannotopf`

#### Input Format

- [WebAnno TSV 3.2](https://webanno.github.io/webanno/releases/3.4.5/docs/user-guide.html#sect_webannotsv)
- Lines containing the annotations of a word (seperated by tabs), blank lines marking sentence boundaries.
- Comment lines starting with hash (#).
- Field contains an underscore if info is not available for the current word.

#### Meta-Info

- Following meta-info is extracted into the output file:
	sent_id(TSV)
  
#### Annotations

- Can contain a subset of the following annotations:

column name | annotation
------ | ------
TSVID | sentence and word index
CharOffset | character offset
FORM | word form
LEMMA | Lemma
POS | POS-tag
XPOS | STTS-Tag
CHUNK | syntactically correlated parts of words
TopF | Topological Field
HEAD | head
DEPREL | dependency relation to the head
DepFlavor | dependency annotation
animacy | morphological feature
aspect | morphological feature
case | morphological feature
definiteness | morphological feature
degree | morphological feature
gender | morphological feature
mood | morphological feature
negative | morphological feature
numType | morphological feature
number | morphological feature
person | morphological feature
possessive | morphological feature
pronType | morphological feature
reflex | morphological feature
tense | morphological feature
transitivity | morphological feature
FEATS | morphological features
verbForm | morphological feature
voice | morphological feature  

### WebAnnoTSVImporter

- Name for usage in command line: `webannotsv`

#### Input Format

- [WebAnno TSV 3.2](https://webanno.github.io/webanno/releases/3.4.5/docs/user-guide.html#sect_webannotsv)
- Lines containing the annotations of a word (seperated by tabs), blank lines marking sentence boundaries.
- Comment lines starting with hash (#).
- Field contains an underscore if info is not available for the current word.

#### Meta-Info

- Following meta-info is extracted into the output file:
	sent_id(TSV)
  
#### Annotations

- Can contain the following annotations plus additional ones.

column name | annotation
------ | ------
TSVID | sentence and word index
CharOffset | character offset
FORM | word form
LEMMA | Lemma
XPOS | STTS-Tag  

### CoraXMLReMImporter

- Name for usage in command line: `coraxmlrem`

#### Input Format

- [CorA-XML Format](https://cora.readthedocs.io/en/latest/coraxml/)
- Each document may contain the following elements:  
	`<cora-header>`, `<header>`, `<layoutinfo>`, `<shifttags>` and an ordered list of `<token>` and `<comment>` elements
- Each `<token>` element may contain diplomatic (`<tok_dipl>`) and modernized (`<tok_anno>`) tokens which could contain further annotations
- Sentence boundaries are realized different: In this corpus there is a sentence bound if the punc-annotation is one of "DE", "IE", "EE", "QE" and
	if the punc-annotation is "$E", the current token also belongs to the sentence before

#### Input Data

- [Referenzkorpus Mittelhochdeutsch](https://www.linguistics.rub.de/rem/access/index.html#)

#### Meta-Info

- Meta Information is included in the `<header>` element of each XML-file.
- Following of these meta-infos are extracted into a seperate file:  
	filename, text, abbr_ddd (abbreviation of the text in ReM), abbr_mwb (abbreviation of the text in the dictionary of Middle High German),
	topic, text-type, genre (P = Prose, U = Urkunde (certificate), V = Verse), reference, reference-secondary, library, library-shelfmark,
	online (link to online database), medium, extent, extract, language, language-type, language-region, language-area, place, time, notes-manuscript,
	date, text-place, text-author, text-language (language of the author), text-source, edition, notes-transcription, notes-annotation

#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form (utf-form of tok_anno)
LEMMA | Lemma
XPOS | STTS-Tag
ANNO_ASCII | ascii-form of tok_anno
ANNO_ID | word index of tok_anno
ANNO_TRANS | trans-form of tok_anno
DIPL | utf-form of tok_dipl
DIPL_ID | word index of tok_dipl
DIPL_TRANS | trans-form of tok_dipl
INFL | morphological information
INFLCLASS | specific inflection class
INFLCLASS_GEN | general inflection class
LEMMA_GEN | general Lemma
LEMMA_IDMWB | Lemma index in the dictionary of Middle High German
LOC | location
NORM | normalized word form
POS | word-specific HiTS-Tag
POS_GEN | lemma-specific HiTS-Tag
PUNC | Tag marking a sentence or segment boundary
SHIFTTAG | Tag marking that a range of token has certain attributes (e.g. "quote")
TOKEN | trans-form of token-element
TOKEN_TYPE | Tag marking the type of difference (if there is one) between the diplomatic and modern token
TOK_ID | word index of token-element  

#### Additional Info

- The Processor `HiTStoSTTSMapper` can be used to match the HiTS-tags of ReM to the corresponding STTS-tags.


### CoraXMLAnselmImporter

- Name for usage in command line: `coraxmlanselm`

#### Input Format

- [CorA-XML Format](https://cora.readthedocs.io/en/latest/coraxml/)
- Each document may contain the following elements:  
	`<cora-header>`, `<header>`, `<layoutinfo>`, `<shifttags>` and an ordered list of `<token>` and `<comment>` elements
- Each `<token>` element may contain diplomatic (`<tok_dipl>`) and modernized (`<tok_anno>`) tokens which could contain further annotations
- Sentence boundaries are realized different: In this corpus there is always a sentence bound if the pos-annotation is "$."

#### Input Data

- [Anselm-Korpus](https://www.linguistics.rub.de/anselm/access/index.html)

#### Meta-Info

- Meta Information is included in the `<header>` element of each XML-file.
- Following of these meta-infos are extracted into a seperate file:  
	filename, Sigle (abbreviation), Aufbewahrungsort (place to keep), shelf mark, printed work, handwritten or printed, prose or verse,
	date, language, language type, language area, number of token, label, URL-facsimile

#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form (utf-form of tok_anno)
LEMMA | Lemma
XPOS | STTS-Tag
ANNO_ASCII | ascii-form of tok_anno
ANNO_ID | word index of tok_anno
ANNO_TRANS | trans-form of tok_anno
DIPL | utf-form of tok_dipl
DIPL_ID | word index of tok_dipl
DIPL_TRANS | trans-form of tok_dipl
MORPH | morphological information
NORM | normalized word form
NORM_BROAD | modern equivalent of the word form
NORM_TYPE | type of adjustment between normalized and modern word form
POS | POS-Tag (slightly modified version of the STTS)
SHIFTTAG | Tag marking that a range of token has certain attributes (e.g. "quote")
TOKEN | trans-form of token-element
TOKEN_TYPE | Tag marking the type of difference (if there is one) between the diplomatic and modern token
TOK_ID | word index of token-element  

#### Additional Info

- The Processor `ANSELMtoSTTSMapper` can be used to match the POS-tags of Anselm to the corresponding STTS-tags.

### CoraXMLReFBoImporter

- Name for usage in command line: `coraxmlrefbo`

#### Input Format

- [CorA-XML Format](https://cora.readthedocs.io/en/latest/coraxml/)
- Each document may contain the following elements:  
	`<cora-header>`, `<header>`, `<layoutinfo>`, `<shifttags>` and an ordered list of `<token>` and `<comment>` elements
- Each `<token>` element may contain diplomatic (`<tok_dipl>`) and modernized (`<tok_anno>`) tokens which could contain further annotations
- Sentence boundaries are realized different: In this corpus there is always a sentence bound if there is a boundary- or a punc-annotation which contains "(.)"

#### Input Data

- [Referenzkorpus Frühneuhochdeutsch](https://www.ruhr-uni-bochum.de/wegera/ref/index.htm)

#### Meta-Info

- Meta Information is included in the `<header>` element of each XML-file.
- Following of these meta-infos are extracted into a seperate file:  
	filename, language area, language region, language type, genre, medium, time, reference, corpus-sigle, text, author, text type, assignment quality, hoffmann_wetter_nr,
	library, library-shelfmark, date, place, printer, edition, literature, size, language, notes-transcription, abbr_ddd (text abbreviation), extent, extent-size


#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form (utf-form of tok_anno)
LEMMA | Lemma
XPOS | STTS-Tag
ANNO_ASCII | ascii-form of tok_anno
ANNO_ID | word index of tok_anno
ANNO_TRANS | trans-form of tok_anno
ANNO_TYPE | type of annotation (manually or automatically)
BOUNDARY | type of punctuation
DIPL | utf-form of tok_dipl
DIPL_ID | word index of tok_dipl
DIPL_TRANS | trans-form of tok_dipl
LEMMA_ID | Lemma index in the dictionary of Middle High German
LEMMA_URL | Link to the entry in the dictionary of Middle High German
LEMMA_VERIFIED | annotation is y (yes) or n (no)
MORPH | morphological information
POS | word-specific HiTS-Tag
POS_LEMMA | lemma-specific HiTS-Tag
PUNC | type of punctuation (if not in BOUNDARY-column)
SHIFTTAG | Tag marking that a range of token has certain attributes (e.g. "quote")
TOKEN | trans-form of token-element
TOKEN_TYPE | Tag marking the type of difference (if there is one) between the diplomatic and modern token
TOK_ID | word index of token-element  

#### Additional Info

- The Processor `ReFHiTStoSTTSMapper` can be used to match the POS-tags of ReF.BO to the corresponding STTS-tags.


### TextImporter

- Name for usage in command line: `text`

#### Input Format

- One word per line, blank lines marking sentence boundaries.

#### Meta-Info

- No meta-info available in this format.

#### Annotations

- Except of the word form there are no annotations available in this format.


### XMLKaJuKImporter

- Name for usage in command line: `xmlkajuk`

#### Input Format

- XML-Format
- Sentences consist of one or more `<lb>` nodes which contain annotated parts of the sentence
- One of these parts can have up to three annotation levels which possibly have further attributes
- Second annotations are put into square brackets (for example used at clitics)
- For further information refer to [KaJuK Documentation](https://www.uni-giessen.de/fbz/fb05/germanistik/absprache/sprachtheorie/kajuk)

#### Input Data

- [Kasseler Junktionskorpus, Version 1.1](https://www.laudatio-repository.org/browse/corpus/nCQsCnMB7CArCQ9CDmun/corpora)
- XML-Files are stored in the directory `KaJuK.zip/kasseler-junktionskorpus/XML`

#### Meta-Info

- XML-Files containing the meta-info for each document are stored in `KaJuK.zip/kasseler-junktionskorpus/TEI-HEADERS/document`
- Following of these meta-infos are extracted into a seperate file:  
	filename, file_id, style, author, editor, title, number of tokens, publisher, place, year, series, language code, language

#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form
ADDIR | additional content relation
ADDtype | additional type
Ebene1 | tag at hierarchical level 1 (if there is another `<lb>` node under the current `lb` node the tag here is `lb_1` or `lb_2`, according to the current `lb` level)
Ebene2 | tag at hierarchical level 2
Ebene3 | tag at hierarchical level 3
Ebene4 | tag at hierarchical level 4 (can only exist if the first level has tag `lb`)
IR | content relation (causal, temporal etc.)
Ident | identity of a verb (finite, infinite etc.)
change | change of an ellipsis
dir | direction of an ellipsis
lb_ADDIR | additional content relation of the current `<lb>` node
lb_EB | level of the current `<lb>` node
lb_IR | content relation of the current `<lb>` node
lb_n | number of the current `<lb>` node (for expressing the relations between different `<lb>` nodes)
lb_type | type of the current `<lb>` node
line | line number
norm | normalised spelling
page | page number
real | realisation of a word/phrase
type | type of a word/phrase

#### Additional Info

- Manual changes of the input files (because of mistakes in the xml-format) are documented in the file `Korrektur.txt`
- In the text of the output file, parts of the sentence that are annotated as ellipsis are put into square brackets

### MercuriusTigerXMLImporter

- Name for usage in command line: `mercuriustigerxml`

#### Input Format

- XML-Tiger/Negra-Format
- The `<head>` node contains meta-information and information about the annotations.
- The `<body>` node contains the individual sentences with their syntax-graphs.
- Each graph consists of `<terminals>`, which contain the words and the corresponding annotations, and `<nonterminals>`,
		which contain the structure of the syntax-tree including the corresponding edge and node labels.

#### Input Data

- [Mercurius-Baumbank, Version 1.1](https://www.laudatio-repository.org/browse/corpus/VyQiCnMB7CArCQ9CjF3O/corpora)

#### Meta-Info

- Not available.

#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form
XPOS | STTS-Tag
FEATS | morphological features
POS | POS-Tag from Mercurius
TigerID | word index in the Tiger/Negra-files  

#### Additional Info

- The Processor `MercuriusToSTTSMapper` can be used to match the POS-tags of Mercurius to the corresponding STTS-tags.

### ReFUPImporter

- Name for usage in command line: `refup`

#### Input Format

- XML-Tiger/Negra-Format
	  - The `<head>` node contains meta-information and information about the annotations.
	  - The `<body>` node contains the individual sentences with their syntax-graphs.
	  - Each graph consists of `<terminals>`, which contain the words and the corresponding annotations, and `<nonterminals>`,
		which contain the structure of the syntax-tree including the corresponding edge and node labels.

#### Input Data

- [Referenzkorpus Frühneuhochdeutsch](https://www.ruhr-uni-bochum.de/wegera/ref/index.htm)

#### Meta-Info

- Not available.

#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form
XPOS | STTS-Tag
FEATS | morphological features
POS | POS-Tag from ReFUP
TigerID | word index in the Tiger/Negra-files  

#### Additional Info

- The Processor `ReFUPToSTTSMapper` can be used to match the POS-tags of ReFUP to the corresponding STTS-tags.
- The Processor `ReFUPCoding` can be used to have the correct coding of 'ß' in the output file.

### XMLFnhdCImporter

- Name for usage in command line: `xmlfnhdc`

#### Input Format

- XML-Format
- The `<bibliographie>` node contains meta-information
- The nodes `<seite>` and `<zeile>` contain the wordforms and their annotations
- For further information refer to the XML-schemata files (e.g. `Fnhd.rnc`) or the [Online-Documentation](https://korpora.zim.uni-duisburg-essen.de/FnhdC/Dokumentation.html)

#### Input Data

- [Bonner Frühneuhochdeutschkorpus](https://korpora.zim.uni-duisburg-essen.de/FnhdC/Download) (XML-Version 2017)

#### Meta-Info

- Following meta-infos are extracted into a seperate file:  
  filename, textname, textnumber, specification number, author, text, title, editor, place of publication,
  year of publication, number of pages, included pages, language area, place, year, text type, URL
  
#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form given under the annotation `gelesen` (if not available, word form under the annotation `gefunden` is taken)
lemma | Lemma
Anmerkungen | annotation is `Name` if the word belongs to a name
Layout | layout information (title, quotation etc.)
Seite_col | page column
Seite_lage | page location
Seite_lf_nr | page number 
Seite_nr | original page number
Seite_position | page position (recto/verso)
Seite_teil | text part on this page
Seite_typ | page type (sheet/chapter/page)
Zeile_lf_nr | continuous line number
Zeile_nr | original line number
adj_links | word form on the left side of an adjective
adj_rechts | word form on the right side of an adjective
adj_rolle | adjective role
adverbial | marking if an adjective is used adverbial
anno_nr | annotation number
fern_teile | number of seperated parts
flexiv | flexes of an adjective
fremdwort | marking if the word form is a foreign word
gefunden | word form where the morphemes are connected via `#`
genus | gender
kasus | case of a noun or adjective
klasse | inflection class of a verb
komparation | comparison morpheme
komparationsstufe | degree of comparison (superlative etc.)
leer | marking if a word form has no morphological annotations
lemma | Lemma
link_lemma | Lemma for searching in the "Wörterbuchnetz" (a digital dictionary network)
modus | mood of a verb
morph | single morphemes of a word form, seperated by whitspaces (only if the morphemes in the original text are not written in one word)
numerus | number (singular/plural)
person | person
praefixe | prefix blocks (`![a,b]` means that there is an isolated prefix block that contains the prefixes a and b; `~[c,d]` means there is an non-isolated prefix block that contains the prefixes c and d)
suffix | suffix of the word form
tempus | tense
typ | word form type (noun, verb etc.)
verb_form | form of a verb (infinitive, participle etc.)
vokal | stresed vowel
wf_nr | word form number  

### GerManCCoNLLImporter

- Name for usage in command line: `germanc`

#### Input Format

- [CoNLL-U Format](https://universaldependencies.org/format.html)
- Lines containing the annotations of a word (seperated by tabs), blank lines marking sentence boundaries
- 10 columns containing the following annotations for each word (the columns here differ slightly from the original CoNLL-U format):  
	ID (word index), FORM (word form), NORM (normalized word form), POS (POS-tag), LEMMA (Lemma), FEATS (Morphological features),
	HEAD (head), DEPREL (dependency relation to the head), DEPS (dependency graph), MISC (other annotation)
- Field contains an underscore if info is not available for the current word
- For further information refer to the [GerManC documentation](https://www1.ids-mannheim.de/fileadmin/lexik/uwv/dateien/GerManC_Documentation.pdf)

#### Input Data

- [GerManC, Version 1.0](https://www.laudatio-repository.org/browse/corpus/9SX7DnMB7CArCQ9CBB_J/corpora)

#### Meta-Info

- XML-Files containing the meta-info for each document are stored in `germanc.zip/germanc-v1.0TEI-HEADERS/document`
- Following of these meta-infos are extracted into a seperate file:  
	filename, style, author, title, number of words, place and year of publication, scope of bibliographic reference,
	source, reference, language, language code, language type

#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form
LEMMA | Lemma
UPOS | Universal POS-Tag
XPOS | STTS-Tag
FEATS | morphological features
HEAD | head
DEPREL | dependency relation to the head
DEPS | dependency graph
MISC | other annotation
NORM | normalized word form
POS | POS-Tag from GerManC  

#### Additional Info

- Several documents contain only 8 columns (ID, FORM, NORM, POS, LEMMA, FEATS, DEPREL, HEAD) instead of 10.
- In some documents the columns HEAD/DEPREL/FORM or NORM/LEMMA are swapped.
- Sometimes there is a single line containing a bracket `)` as word form, without any other annotations.
	In this cases the bracket will be attached to the preceding sentence.

### DDBTigerNegraImporter

- Name for usage in command line: `ddbtigernegra`

#### Input Format

Two different formats:

- XML-Tiger/Negra-Format
	  - The `<head>` node contains meta-information and information about the annotations.
	  - The `<body>` node contains the individual sentences with their syntax-graphs.
	  - Each graph consists of `<terminals>`, which contain the words and the corresponding annotations, and `<nonterminals>`,
		which contain the structure of the syntax-tree including the corresponding edge and node labels.

- EXMARaLDA-Format
	  - The `<head>` node contains meta-information about the file.
	  - The `<basic-body>` consists of a `<common-timeline>` and the `<tier>` nodes, where each node contains the words or one annotation category.
	  - Each word and each annotation belong to one or more timeline-IDs, so one can match the words to their corresponding annotations with this IDs. 

#### Input Data

- [Deutsche Diachrone Baumbank, Version 1.0](https://www.laudatio-repository.org/browse/corpus/bSQeC3MB7CArCQ9Cw8yZ/corpora)

#### Meta-Info

- XML-Files containing the meta-info for each document are stored in `deutsche-diachrone-baumbank.zip/deutsche-diachrone-baumbank-v1.0TEI-HEADERS/document`
- Following of these meta-infos are extracted into a seperate file:  
	filename, style, title, author, number of tokens, publisher, place and year of publication, scope of bibliographic reference,
	original year/place/title, source, reference, language, language code, language type, language area
- Following meta-infos are extracted into the output file (only for files in Tiger/Negra-Format):  
  sentence ID in the Tiger/Negra-files, syntax-tree string

#### Annotations

Annotations of files in XML-Tiger/Negra-Format:

column name | annotation
------ | ------
ID | word index
FORM | word form
XPOS | STTS-Tag
FEATS | morphological features
POS | POS-Tag from DDB
TigerID | word index in the Tiger/Negra-files  

Annotations of files in the other XML-Format:

column name | annotation
------ | ------
ID | word index
FORM | word form
XPOS | STTS-Tag
FEATS | morphological features
ASPECT | aspect
CAT | corresponding syntactical sentence part
CONTEXT | context
POS | POS-Tag from DDB
TENSE | tense
TimelineID | corresponding index in the timeline
VOICE | voice  

#### Additional Info

- Not all files of the corpus are avilable in the XML-Tiger/Negra-Format; only the files in the folder with Old High German texts have this format,
	while the other texts (Middle High German and Early New High German) have a different format (as discribed under "Input Format").
- Since the POS-tags from DDB partly are uncomplete or do not contain the right STTS-tag (especially for punctuation marks),
	the tags are corrected in the Importer and the right STTS-tags are saved in the XPOS-column.

### FuerstinnenEXBImporter

- Name for usage in command line: `fuerstinnenexb`

#### Input Format

- EXMARaLDA-Format
- The `<head>` node contains meta-information about the file.
- The `<basic-body>` consists of a `<common-timeline>` and the `<tier>` nodes, where each node contains the words or one annotation category.
- Each word and each annotation belong to one or more timeline-IDs, so one can match the words to their corresponding annotations with this IDs. 

#### Input Data

- [Fuerstinnenkorrespondenz, Version 1.1](https://www.laudatio-repository.org/browse/corpus/ZCSVC3MB7CArCQ9CVedt/corpora)
- For further information refer to the [Documentation](http://dwee.eu/Rosemarie_Luehr/?Projekte___DFG-Projekte___Fruehneuzeitliche_Fuerstinnenkorrespondenz_im_mitteldeutschen_Raum)

#### Meta-Info

- XML-Files containing the meta-info for each document are stored in `fuerstinnenkorrespondenz.zip/fuerstinnenkorrespondenz-v1.1TEI-HEADERS/document`
- Following of these meta-infos are extracted into a seperate file:  
	filename, style, title, author, addressee, number of tokens, place, date, scope of bibliographic reference,
	manuscript name, language, language code, language type, language area, comment

#### Annotations

column name | annotation
------ | ------
ID | word index
FORM | word form
LEMMA | Lemma
XPOS | STTS-Tag
FEATS | morphological features
CLAUSE-ST | clause-status
COMMENT | explanation of the features that are tagged under LEX_GR
COMPLEX | sentence complexity
FORMAL | formal features
GRAPH | graphematic features
GRFUNCT | grammatical function
LEX_GR | lexical or grammatical features
MANU | marking if text is from foreign hand
MEAN | meaning of certain lemmata
MOD_POLITE | tagging signals of modesty and politeness
NORM | normalized word form
ORIG | original writing
PHON | phonological features
PHRAS | phrasing categories of the letter
POS | POS-tags from the Fuerstinnnen-Corpus
QUOT | biblical quotations or proverbial expressions
S_GRFUNCT | grammatical function of subclauses
TimelineID | corresponding index in the timeline  

#### Additional Info

- The Processor `FuerstinnentoSTTSMapper` can be used to match the POS-tags of the 'Fuerstinnenkorrespondez' to the corresponding STTS-tags.

### SDeWaCIteratorImporter

- Name for usage in command line: `sdewac`

#### Input Format

- Lines containing the annotations of a word (seperated by tabs), blank lines marking sentence boundaries
- Field contains an underscore if info is not available for the current word

#### Input Data

- [SdeWaC](ims.uni-stuttgart.de/forschung/ressourcen/korpora/sdewac/)

#### Meta-Info

- Following meta-info is extracted into the output file:  
  sentence ID in SDeWaC

#### Annotations

column name | annotation
------ | ------
ID | word index
Joined_ID | sentence and word index
FORM | word form
LEMMA | Lemma
UPOS | Universal POS-Tag
XPOS | STTS-Tag
FEATS | morphological features
HEAD | head
DEPREL | dependency relation to the head
UNK1 | unknown
UNK2 | unknown
UNK3 | unknown
UNK4 | unknown
UNK5 | unknown
UNK6 | unknown  

### GraphVarEXBImporter

- Name for usage in command line: `graphvar`

#### Input Format

- EXMARaLDA-Format
- The `<head>` node contains meta-information about the file.
- The `<basic-body>` consists of a `<common-timeline>` and the `<tier>` layers with `<event>` nodes, where each node contains the words or one annotation category.
- Each word and each annotation belong to one or more timeline-IDs, so one can match the words to their corresponding annotations with this IDs. 

#### Input Data

- [GraphVar: Das Klausurenkorpus, Version 1.4](https://graphvar.uni-bonn.de/)
- For further information refer to the [Documentation](https://graphvar.uni-bonn.de/dokumentation.html)

#### Meta-Info

- Following meta-info is extracted into a separate file:  
  	    Dokument (text ID), Jahr (year), Fach (subject), Punkte (credit points), Geschlecht (sex), Topologie (whether syntax annotation has been validated)

#### Annotations

column name | annotation
------ | ------
ID     | word index within a sentence
FORM   | corrected word form (new orthography; called NORMAL in the original corpus)
LEMMA  | lemma (NORMALlemma)
XPOS   | STTS tag (NORMALpos)
TimelineID  | start attribute of events
IST         | original writing
IST_ZIEL    | corrected writing (old or new orthography) (separated by comma, if more than one according to rules of 1991 vs. 1996)
IST_INDEX   | IST word index
IST_NORMAL_DIFF  | difference between orig and corrected writing
ZEILENTRENNUNG | line break in original writing
FEHLER      | error (binary: "XXX" or "\_") (separated by comma, if more than one according to rules of 1991 vs. 1996)
FEHLERKATEGORIE | type of error (separated by comma, if more than one)
SENT         | sentence spans (NORMALS)
SYNTAX	     | path of syntactic nodes (topological fields and phrases), starting with top node (nodes separated by \|, e.g. I-SIMPX\|I-SIMPX\|B-VVINF\|B-VXINF\|B-VC)
UEBERSCHRIFT | header spans
ZITAT        | citation
UNEINDEUTIG  | unclear
KOMMENTAR    | comments
WEBANNO      | annotation validated (using WebAnno)
...          | (further annotation layers are possible)


#### Additional Info

- FORM consists of corrected forms. If the original writing contains additional words (e.g. a superfluous comma), there is no corresponding corrected form. Instead, an artificial empty token `<EMPTY>` is introduced.

- Span annotations use prefixes `B-` (begin of span), `I-` (internal), and `E-` (end of span). Singletons are not marked as such.

- Such prefixes may occur even at free-text layers such as FORM, LEMMA or IST. In theses cases, the prefixes are `<B->`, `<I->`, and `<E->`, to avoid confusion with real characters. Example: If students incorrectly spelled one word as two words (e.g. "weiter vererben" instead of "weitervererben"), the corrected form FORM is represented as `<B->weitervererben` + `<E->weitervererben` (and, similarly, the LEMMA).

- Vice versa, if students incorrectly spelled two words as one word (e.g. "Desweiteren"), this word is split in two at the layer FORM: `Des` + `weiteren`, and the IST form becomes a span annotation: `<B->Desweiteren` + `<E->Desweiteren`.

#### Examples


>\# global.columns = ID FORM LEMMA UPOS XPOS ... FEHLER FEHLERKATEGORIE IST    ...  
\# sent_id = 68  
\# text = Auch der weitere Verlauf der Romans \<EMPTY\> lässt das Geschehen realistisch wirken.  
...  
6	Romans	Roman	_	NN	...	_	0	Romans  ...  
7	\<EMPTY\>	_	_	_	...	1	PKT	,  	...  
...  
	
>\# global.columns = ID FORM LEMMA UPOS XPOS ... FEHLER FEHLERKATEGORIE IST ...  
\# sent_id = 143  
\# text = Sein Stoffwechselsystem würde gefährdet werden und er kann seine Erbinformationen nicht an die Nachfolgegeneration \<B-\>weitervererben \<E-\>weitervererben.  
...  
15	\<B-\>weitervererben	\<B-\>weitervererben	_	B-VVINF	...	B-1	B-GZS	weiter	...  
16	\<E-\>weitervererben	\<E-\>weitervererben	_	E-VVINF	...	E-1	E-GZS	vererben	...  
...  

>\# global.columns = ID FORM LEMMA UPOS XPOS ... FEHLER FEHLERKATEGORIE IST   ...  
\# sent_id = 13  
\# text = Des Weiteren bewahre die Poesie das, was ...  
1	Des	die	_	ART  ...  B-1	  B-GZS	\<B-\>Desweiteren	...  
2	Weiteren	Weiter	_	NN ...	E-1	E-GZS	\<E-\>Desweiteren	...  
...  
	
