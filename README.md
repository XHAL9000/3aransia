# 3aransia

Languages and Dialects transliteration

[![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.svg?v=102)](https://github.com/ellerbrock/open-source-badge/)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![made-with-python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/)
![GitHub last commit](https://img.shields.io/github/last-commit/google/skia.svg)

## Prerequisites

- [`Python 3`](https://www.python.org/downloads/)
  
## Installation

```pip install aaransia```

## Usage

### Get all alphabets codes

```python
from aaransia import get_alphabets_codes

print(get_alphabets_codes())
```

```
>>> ['ma', 'ar', 'la', 'ab', 'gr']
```

### Get all alphabets

```python
from aaransia import get_alphabets

print(get_alphabets())
```

```
>>> {   
>>>     'ab': 'Abjadi Alphabet',
>>>     'ar': 'Arabian Alphabet',
>>>     'gr': 'Greek Alphabet',
>>>     'la': 'Latin Alphabet',
>>>     'ma': 'Moroccan Alphabet'
>>> }
```

### Transliterate from a language or dialect to another
```python
s_ar = "كتب بلعربيا هنايا شحال ما بغيتي"

print(transliterate(s_ar, source_language='ar', target_language='ma'))
```

```
>>> ktb bl3rbya hnaya ch7al ma bghiti
```

### Transliterate from all languages to all languages

```python
from aaransia import transliterate, SourceLanguageException

s_ma = "ktb bl3rbya hnaya ch7al ma bghiti"
s_ar = "كتب بلعربيا هنايا شحال ما بغيتي"
s_la = "ktb bl'rbya hnaya chhal ma bghiti"
s_ab = "ktb bl'rbya hnaya chḥal ma bghiti"
s_gr = "κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι"

strings = [s_ma, s_ar, s_la, s_ab, s_gr]

for s in strings:
    for source_language in get_alphabets_codes():
        for target_language in get_alphabets_codes():
            try:
                print(f'{s}\n{source_language} ==> {target_language}\n{transliterate(s, source_language, target_language)}\n')
             except SourceLanguageException as sle:
                 print(p, sle)
```

```
>>> ktb bl3rbya hnaya ch7al ma bghiti
>>> ma ==> ma
>>> ktb bl3rbya hnaya ch7al ma bghiti
>>> 
>>> ktb bl3rbya hnaya ch7al ma bghiti
>>> ma ==> ar
>>> كتب بلعربيا هنايا شحال ما بغيتي
>>> 
>>> ktb bl3rbya hnaya ch7al ma bghiti
>>> ma ==> la
>>> ktb bl'rbya hnaya chhal ma bghiti
>>> 
>>> ktb bl3rbya hnaya ch7al ma bghiti
>>> ma ==> ab
>>> ktb bl'rbya hnaya chḥal ma bghiti
>>> 
>>> ktb bl3rbya hnaya ch7al ma bghiti
>>> ma ==> gr
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι
>>> 
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: ar
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: ar
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: ar
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: ar
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: ar
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: la
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: la
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: la
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: la
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: la
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: ab
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: ab
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: ab
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: ab
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: ab
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: gr
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: gr
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: gr
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: gr
>>> ktb bl3rbya hnaya ch7al ma bghiti Source language doesn't match the input text: gr
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: ma
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: ma
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: ma
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: ma
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: ma
>>> كتب بلعربيا هنايا شحال ما بغيتي
>>> ar ==> ma
>>> ktb bl3rbya hnaya ch7al ma bghyty
>>> 
>>> كتب بلعربيا هنايا شحال ما بغيتي
>>> ar ==> ar
>>> كتب بلعربيا هنايا شحال ما بغيتي
>>> 
>>> كتب بلعربيا هنايا شحال ما بغيتي
>>> ar ==> la
>>> ktb bl'rbya hnaya chhal ma bghyty
>>> 
>>> كتب بلعربيا هنايا شحال ما بغيتي
>>> ar ==> ab
>>> ktb bl'rbya hnaya shḥal ma bghyty
>>> 
>>> كتب بلعربيا هنايا شحال ما بغيتي
>>> ar ==> gr
>>> κτμπ μπλ'ρμπυα χναυα σχαλ μα μπγυτυ
>>> 
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: la
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: la
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: la
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: la
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: la
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: ab
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: ab
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: ab
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: ab
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: ab
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: gr
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: gr
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: gr
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: gr
>>> كتب بلعربيا هنايا شحال ما بغيتي Source language doesn't match the input text: gr
>>> ktb bl'rbya hnaya chhal ma bghiti Source language doesn't match the input text: ma
>>> ktb bl'rbya hnaya chhal ma bghiti Source language doesn't match the input text: ma
>>> ktb bl'rbya hnaya chhal ma bghiti Source language doesn't match the input text: ma
>>> ktb bl'rbya hnaya chhal ma bghiti Source language doesn't match the input text: ma
>>> ktb bl'rbya hnaya chhal ma bghiti Source language doesn't match the input text: ma
>>> ktb bl'rbya hnaya chhal ma bghiti Source language doesn't match the input text: ar
>>> ktb bl'rbya hnaya chhal ma bghiti Source language doesn't match the input text: ar
>>> ktb bl'rbya hnaya chhal ma bghiti Source language doesn't match the input text: ar
>>> ktb bl'rbya hnaya chhal ma bghiti Source language doesn't match the input text: ar
>>> ktb bl'rbya hnaya chhal ma bghiti Source language doesn't match the input text: ar
>>> ktb bl'rbya hnaya chhal ma bghiti
>>> la ==> ma
>>> ktb bl3rbya hnaya chhal ma bghiti
>>> 
>>> ktb bl'rbya hnaya chhal ma bghiti
>>> la ==> ar
>>> كتب بلعربيا هنايا كههال ما بڭهيتي
>>> 
>>> ktb bl'rbya hnaya chhal ma bghiti
>>> la ==> la
>>> ktb bl'rbya hnaya chhal ma bghiti
>>> 
>>> ktb bl'rbya hnaya chhal ma bghiti
>>> la ==> ab
>>> ktb bl'rbya hnaya chhal ma bghiti
>>> 
>>> ktb bl'rbya hnaya chhal ma bghiti
>>> la ==> gr
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι
>>> 
>>> ktb bl'rbya hnaya chhal ma bghiti
>>> ab ==> ma
>>> ktb bl3rbya hnaya chhal ma bghiti
>>> 
>>> ktb bl'rbya hnaya chhal ma bghiti
>>> ab ==> ar
>>> كتب بلعربيا هنايا كههال ما بڭهيتي
>>> 
>>> ktb bl'rbya hnaya chhal ma bghiti
>>> ab ==> la
>>> ktb bl'rbya hnaya chhal ma bghiti
>>> 
>>> ktb bl'rbya hnaya chhal ma bghiti
>>> ab ==> ab
>>> ktb bl'rbya hnaya chhal ma bghiti
>>> 
>>> ktb bl'rbya hnaya chhal ma bghiti
>>> ab ==> gr
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι
>>> 
>>> ktb bl'rbya hnaya chhal ma bghiti Source language doesn't match the input text: gr
>>> ktb bl'rbya hnaya chhal ma bghiti Source language doesn't match the input text: gr
>>> ktb bl'rbya hnaya chhal ma bghiti Source language doesn't match the input text: gr
>>> ktb bl'rbya hnaya chhal ma bghiti Source language doesn't match the input text: gr
>>> ktb bl'rbya hnaya chhal ma bghiti Source language doesn't match the input text: gr
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: ma
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: ma
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: ma
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: ma
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: ma
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: ar
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: ar
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: ar
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: ar
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: ar
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: la
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: la
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: la
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: la
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: la
>>> ktb bl'rbya hnaya chḥal ma bghiti
>>> ab ==> ma
>>> ktb bl3rbya hnaya ch7al ma bghiti
>>> 
>>> ktb bl'rbya hnaya chḥal ma bghiti
>>> ab ==> ar
>>> كتب بلعربيا هنايا كهحال ما بڭهيتي
>>> 
>>> ktb bl'rbya hnaya chḥal ma bghiti
>>> ab ==> la
>>> ktb bl'rbya hnaya chhal ma bghiti
>>> 
>>> ktb bl'rbya hnaya chḥal ma bghiti
>>> ab ==> ab
>>> ktb bl'rbya hnaya chḥal ma bghiti
>>> 
>>> ktb bl'rbya hnaya chḥal ma bghiti
>>> ab ==> gr
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι
>>> 
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: gr
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: gr
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: gr
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: gr
>>> ktb bl'rbya hnaya chḥal ma bghiti Source language doesn't match the input text: gr
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: ma
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: ma
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: ma
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: ma
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: ma
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: ar
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: ar
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: ar
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: ar
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: ar
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: la
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: la
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: la
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: la
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: la
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: ab
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: ab
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: ab
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: ab
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι Source language doesn't match the input text: ab
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι
>>> gr ==> ma
>>> ktmp mpl3rmpya hnaya chhhal ma mpghiti
>>> 
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι
>>> gr ==> ar
>>> كتمپ مپلعرمپيا هنايا شههال ما مپڭهيتي
>>> 
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι
>>> gr ==> la
>>> ktmp mpl'rmpya hnaya chhhal ma mpghiti
>>> 
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι
>>> gr ==> ab
>>> ktmp mpl'rmpya hnaya shhhal ma mpghiti
>>> 
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι
>>> gr ==> gr
>>> κτμπ μπλ'ρμπυα χναυα σχχαλ μα μπγχιτι
```

## Other related projects

- [3aransia.api](https://3aransia.github.io/3aransia.api) The api of 3aransia
- [3aransia.web](http://3aransia.com) The web application of 3aransia
