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


### Primo workflow del sistema
Ad ogni input dell'utente, il sistema considera la sotto-parola inserita e seleziona le skill che contengono quella sotto-parola. Si suggerisce quindi la parola con similarità maggiore tra le parole considerate precedentemente e le skill già inserite.
Sia il contesto $C = [c_1, ... , c_n]$ le skill già inserite e $s$ la sotto-parola inserita dall'utente, il primo passo è quello di individuare le skill di cui $s$ è sotto-parola: $W = [w_1, ... , w_m]$. Si suggerisce quindi all'utente la skill con la maggior similarità con il contesto $C$ calcolata usando la similarità del coseno:

$$
max(sim(w_i, C)) \qquad \forall \> w_i \in W
$$

![equation](https://latex.codecogs.com/png.latex?\max(sim(w_i,%20C))&space;\qquad\forall\%3Ew_i\in%20W)

dove $sim(w_i, C)$ esprime la similarità tra la i-esima parola di cui $s$ è sotto-parola e le skill già inserite, si possono combinare le similarità calcolate per ogni skill nel contesto utilizzando, ad esempio, la media
$$
\frac{\sum_{j=1}^n sim(w_i, c_j)}{n} \qquad \forall \>  w_i \in W , \> c_j \in C
$$

### Considerazioni
* Capire come distinguere le skill composte da più parole dalla separazione delle skill.
*  Nel selezionare le parole di $W$ non si tiene in considerazione il loro embedding.
*  Usare un altro approccio per aggregare le similarità tra la skill candidata e il contesto $C$ oltre la media.
*  Usare un altro modo per il calcolo della similarità oltre al coseno.
