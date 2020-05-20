# BDPSS-lab

Il progetto consiste nel realizzare un sistema di auto completamento di parole che rappresentano delle skill tecniche.

Il sistema suggerisce all'utente la skill con la relazione maggiore rispetto a quelle già inserite, è anche in grado di suggerire il completamento di una skill, mentre l'utente la sta inserendo, basandosi sullo stesso principio.


### Articoli e altre risorse

* Urra, F. (2019). Measuring Enrichment Of Word Embeddings With Subword And Dictionary Information.

Confronto tra modelli: FastText, word2vec e un terzo modello proposto. Per la parte di FastText: calcolo della similarità con il coseno, pesatura delle sottoparole

* Toshevska, M., Stojanovska, F., & Kalajdjieski, J. (2020). Comparative Analysis of Word Embeddings for Capturing Word Similarities. arXiv preprint arXiv:2005.03812.

Confronto tra modelli: FastText, word2vec, GloVe. Calcolo delle somiglianze con il coseno, valutazione tra le similarità trovate e una base di conoscenza tramite: Spearman correlation coefficient, Pearson correlation coefficient e Kendall’s tau correlation coefficient. GloVe e FastText migliori. Nel nostro caso non si ha una base di conoscenza

* Faruqui, M., Tsvetkov, Y., Rastogi, P., & Dyer, C. (2016). Problems with evaluation of word embeddings using word similarity tasks. arXiv preprint arXiv:1605.02276.

Analisi di problemi e situazioni da tener presente nel calcolo della similarità usando, in particolare, il coseno

* Li, D., & Summers-Stay, D. (2017). Dual embeddings and metrics for relational similarity. In IWCS 2017—12th International Conference on Computational Semantics—Short papers.

Descrive un approccio per il calcolo di similarità tra coppie di parole rappresentate mediante i vettori delle parole che formano tali coppie 

* https://medium.com/@adriensieg/text-similarities-da019229c894

Carrellata di funzioni di similarità analizate in vari contesti anche con modelli pre-trained come FastText o GloVe

