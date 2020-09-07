# Auto-complete tool

Progetto per il corso di _Big Data in Public and Social Services_ 

Il progetto consiste nel realizzare un sistema di auto completamento di parole che rappresentano delle skills tecniche definite nella tassonomia [E.S.C.O.](https://ec.europa.eu/esco/portal/skill)

Il sistema è in grado di fornire suggerimeti in due possibili modi: 
* Identifica le skills da suggerire considerando sia l'input inserito dall'utente che le skills già inserite.
* Suggerisce le skills maggiormente correlate solamente alle skills già inserite in precedenza

### Calcolo delle similarità
Si utilizzano dei vettori di word embeddings ottenuti tramite FastText per calcolare la similarità del coseno tra le skills e l'input utente. Sia _i_ il nuovo input dell'utente, _C_ l'insieme delle skills già inserite detto _Context_. Per ognuno dei due casi espressi sopra sono calcolate in modo separato le similarità:
- Per ogni skill _s_, si calcola la similarità del coseno tra _s_ e l'input dell'utente ottenende l'insieme _A = {(s, sim(i, s)}_
- Per ogni skill _s_, si calcola la media delle similarità del coseno tra _s_ e le skills del _Context_ _C_ ottenendo l'insieme _B = {(s, avg_sim(s, C)}_
- Infine si calcola la misura di similarità aggregata come compinazione lineare pesata
_α * sim(i, s) + (1 - α) * sim(s, C)_ per ogni skill. Questo valore identifica la similarità di ogni skill sia con l'input inserito dal'utente e sia con le skills già inserite.

### Architettura del sistema
Nel _Notebook Jupyter_ son presenti le classi che implementano il sistema di auto-completamento. Una classe _Python_ gestisce l'interfaccia utente mostrando l'area di testo nella quale inserire le skills e i suggerimenti individuato come descritto precedentemente; una seconda classe _Python_ implementa la logica del sistema elaborano l'input dell'utente, calcolando le similarità e individuando i migliori suggerimenti.

### Struttura della repository
Nella cartella data si trovano la lista delle skills usate come suggerimanti e un foglio exel con i dati dello User test sottoposto agli utenti per valutare la loro interazione con il sistema.
Nella cartella report sono presenti, in formato pdf, il report dettagliato dello sviluppo del sistema e una presentazione riassuntiva del lavoro fatto; è presente anche un video demo dell'utilizzo del sistema.
il file _auto-complete tool project_ contiene tutto il codice del sistema.

### References
* Giabelli, A., Malandri, L., Mercorio, F., & Mezzanzanica, M. (2020). GraphLMI: A data driven system for exploring labor market information through graph databases. Multimedia Tools and Applications, 1-30.
* Giabelli, A., Malandri, L., Mercorio, F., Mezzanzanica, M., & Seveso, A. (2020). NEO: A Tool for Taxonomy Enrichment with New Emerging Occupations.
* CEDEFOP: Real-time labour market information on skill requirements: Setting up the eu system for online vacancy analysis. https://goo.gl/5FZS3E (2016).
* Handbook, E. S. C. O. European Skills, Competences, Qualifications and Occupations (2017). EC Directorate E.


