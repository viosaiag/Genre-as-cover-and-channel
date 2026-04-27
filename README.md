# Genre as Cover and Channel: Computational Evidence from Belle Époque Lesbian Writing

This repository contains the code accompanying the paper:

> Saiag, V., Baumard, N., Cafiero, F., & Puren, M. (2026). Genre as Cover and Channel:
> Computational Evidence from Belle Époque Lesbian Writing.
> *Journal of Cultural Analytics.*

---

## Overview

Our pipeline implements a BERTopic-based approach to compare the thematic salience
of sapphic, romantic, and erotic vocabularies across poetry and prose in four corpora
of Belle Époque francophone literature (lesbian women, heterosexual women, homosexual
men, heterosexual men).

The analysis addresses two research questions:

- **Q1** — Are themes of love, desire, and sapphism more prominent in poetry or in prose?
- **Q2** — Are these themes treated differently across genres within the lesbian corpus?

---

## Repository structure

    .
    ├── comparison_poetry_prose.ipynb    Main notebook (all cells)
    ├── lexicon_master.xlsx              Lexical fields used for scoring
    └── README.md

The corpora are not included in this repository for copyright reasons.

---

## Requirements

Python 3.10 or higher is recommended.

Key dependencies include bertopic, sentence-transformers, umap-learn, hdbscan,
spacy, transformers, functionwordsets, and openpyxl.

To install the French spaCy model:

    python -m spacy download fr_core_news_md

---

## Data

The corpora used in this study consist of 499 digitised francophone literary works
(poetry and prose) by authors who were wrote between 1880 and 1914. These texts were
either collected from open-access repositories (Wikisource, Gallica), or from library
holdings and then digitised using OCR (Tesseract).

The corpora are not redistributed here, as some texts have not yet entered the public domain and are therefore still subject to copyrigh. To replicate the analysis, texts should be organised as follows:

    corpi_these/
    ├── corpus_poesie_lesb/          Lesbian women — poetry
    ├── corpus_lesbiennes/           Lesbian women — prose
    ├── corpus_poesie_hetero/        Heterosexual women — poetry
    ├── corpus_hetero/               Heterosexual women — prose
    ├── corpus_poesie_homosexuels/   Homosexual men — poetry
    ├── corpus_homosexuels/          Homosexual men — prose
    ├── corpus_poesie_homhet/        Heterosexual men — poetry
    └── corpus_homhet/               Heterosexual men — prose

Each subfolder should contain plain text files (.txt), one per work.

---

## Usage

1. Place your corpora in the directory structure described above.
2. Update the corpus paths in Cell 2 of the notebook if necessary.
3. Run the notebook cells sequentially (Cells 1 through 11).
4. Results are saved to ./final_results/

---

## Output structure

    final_results/
    ├── {corpus}/
    │   ├── bertopic_topic_info.csv
    │   ├── bertopic_topic_words_with_lemma.csv
    │   ├── ablation_summary_long.csv
    │   ├── mode_lemma_only/
    │   │   └── run_B_topn_40/
    │   │       ├── chunk_level_scores.csv
    │   │       ├── work_level_scores.csv
    │   │       ├── genre_tests_topic_affinity.csv
    │   │       └── genre_tests_direct.csv
    │   └── analyse_differentielle/        Q2 results (lesbian corpus only)
    │       └── {lexicon}/
    │           ├── axe1_global_stats_{lexicon}.csv
    │           ├── axe1_topic_distribution_{lexicon}.csv
    │           ├── axe2_tfidf_differential_{lexicon}.csv
    │           ├── axe3_cooc_tfidf_{lexicon}.csv
    │           ├── axe3_cooc_chi2_global_{lexicon}.csv
    │           ├── axe3_cooc_chi2_words_{lexicon}.csv
    │           └── axe4_sentiment_stats_{lexicon}.csv
    └── _synthese_comparative/
        ├── synthese_Q1_{lexicon}.xlsx
        └── synthese_Q1_tous_lexiques.xlsx

---

## Citation

If you use this code, please cite:

    @article{saiag2026genre,
      title   = {Genre as Cover and Channel: Computational Evidence
                 from Belle {\'E}poque Lesbian Writing},
      author  = {Saiag, Violette and Baumard, Nicolas and Cafiero, Florian and
                 Puren, Marie},
      journal = {Journal of Cultural Analytics},
      year    = {2026}
    }

---

## License

The code in this repository is released under the MIT License.
The lexicon (lexicon_master.xlsx) is released under CC BY 4.0.