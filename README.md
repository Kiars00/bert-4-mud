# Fine-tuning di BERT per NER (NERMUD 2023)

Progetto di **Named Entity Recognition (NER)** su documenti in lingua italiana realizzato per l'a.a. 2024-2025.
**Autrici:** Chiara Mancuso e Virginia Ranciaro.

## Obiettivo del Progetto
Il progetto si propone di effettuare il fine-tuning di un modello Transformer per identificare e classificare entità nominate (nomi propri di persone, luoghi e organizzazioni) da documenti di varia tipologia testuale. 

Nello specifico, è stato replicato il task di **classificazione dominio-indipendente** presentato nella campagna EVALITA 2023 (NERMUD), operando su testi giornalistici, narrativa e discorsi politici con un modello unico.

## Architettura e Dataset
* **Modello:** `BertForTokenClassification` basato su `bert-base-italian-cased`.
* **Dataset:** Subset del *Kessler Italian Named-entities Dataset* (KIND), contenente annotazioni per le classi PER (Persone), LOC (Luoghi) e ORG (Organizzazioni)
* **Ottimizzatore:** AdamW con learning rate di $2 \times 10^{-5}$ e batch size 16.

## Struttura del Repository
Il codice è organizzato in modo modulare per gestire la pipeline in maniera pulita:
*`train.py`: Gestisce l'intero flusso di addestramento, caricamento dati e salvataggio modelli.
* `funzioni.py`: Contiene le funzioni di supporto per la lettura dati (CoNLL/TSV), la tokenizzazione e l'allineamento delle label.
* `classe.py`: Definisce la classe `NERDataset` compatibile con PyTorch DataLoader.

## Risultati (Test Set)
Le performance medie ottenute su 3 run indipendenti evidenziano la stabilità e l'efficacia del modello:

| Categoria | Precision (P) | Recall (R) | F1-Score |
| :--- | :---: | :---: | :---: |
| **Persone (PER)** | 92.26% | 93.18% | **92.71%** |
| **Luoghi (LOC)** | 84.26% | 87.30% | **85.75%** |
| **Organizzazioni (ORG)** | 81.34% | 80.41% | **80.87%** |
| **Macro Average** | 85.95% | 86.96% | **86.44%** |


## Istruzioni per l'uso

1. Clonare la repository da GitHub:

```
git clone https://github.com/vranc00/bert-4-mud.git
```

2. Installare le dipendenze:

```
pip install -r requirements.txt
```

3. Eseguire lo script train.py con i parametri desiderati:

```
python train.py
```

---
### Documentazione Completa
Per un'analisi approfondita della metodologia, della scelta degli iperparametri (come il learning rate a $2 \times 10^{-5}$) e del confronto dettagliato con i risultati della campagna EVALITA 2023, consulta il documento integrale:

[**Consulta il Report di Progetto (PDF)**](./report.pdf)


