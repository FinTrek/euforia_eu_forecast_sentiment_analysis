# EUforia: Sentiment analysis on EU forecasts

Sentiment analysis for journalistic reporting on EU Forecasts per member-state.
Lexicon-based approaches (for now) using the following lexicons:
- McDonald and Loughan financial sentiment lexicon
- Harvard Inquirer 4 general purpose sentiment lexicon
- Lexicoder political sentiment lexicon

## Installation
Requirements:
- Python 3.6+
- Pipenv

Install:
- Python dependencies using pipenv. Run from this directory:
`pipenv install` and then to use the virtualenv run `pipenv shell`
- Lexicoder 3.0 for Lexicoder political text sentiment analysis: download from lexicoder site and follow manual instructions.

## Usage
Lexicoder political sentiment SA:
- Install Lexicoder software from their site.
- Download the Lexicoder political lexicon from site.
- Set dirs in settings. Clean and make the data directory: `python lexicoder.py`
- `cd "/home/gilles/software/Lexicoder 3.0"`
- Preprocess: `./lex pre dat="./dat/"`
- Lexicon count: `./lex dc dat="./dat/" md="/home/gilles/datasets/LexicoderSADaug2015/LSD2015.lc3" > /home/gilles/repos/euforia_eu_forecast_sentiment_analysis/dataset/lexicoder_counts.tsv`
- Annotation HTML file for manual inspection: `./lex tag dat="./dat/" md="/home/gilles/datasets/LexicoderSADaug2015/LSD2015.lc3" > /home/gilles/repos/euforia_eu_forecast_sentiment_analysis/dataset/lexicoder.html`

Package files:
- `./sentiment_analysis/settings.py`: Set in/output paths, analyser settings. Set FROM_SCRATCH to True to run sentiment analysis from scratch.
- `./sentiment_analysis/sentimentanalyser.py`: Run analysis and plotting.
- `./sentiment_analysis/preprocessor.py`: Functions for text preprocessing.
- `./sentiment_analysis/datahandler.py`: Functions for dataset reading, cleaning, and writing.

## Lexicons:

* Loughran and McDonald Financial Sentiment Dictionary: unbalanced classes: should factor this in

| Scale | No. of words | Sample words |
|-------|--------------|--------------|
| Negative | 2,337 | termination, discontinued, penalties, misconduct, serious, noncompliance, deterioration, felony |
| Positive | 353 |	achieve, attain, efficient, improve, profitable |
| Uncertainty | 285 |approximate, contingency, depend, fluctuate, indefinite, uncertain, variability |
| Litigiousness | 731 |	claimant, deposition, interlocutory, testimony, tort |
| Weak Modal Words | 27 | could, depending, might, possibly |
| Strong Modal Words | 19 |	always, highest, must, will |

## TODO:
- ~~Implement Lexicoder political sentiment lexicon scoring~~
- ~~Research more sentiment lexicons (political discourse could be useful)~~
- Add final SA lexicon for general purpose: Wordstat
- Combine results: scale scores, take into account subjectivity score in linear combination + use a voting or linear combination at document.


by Gilles Jacobs and Ioannis Antypas