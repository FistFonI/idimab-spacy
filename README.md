# My custom spaCy models
This repository contains [releases](https://github.com/fistfoni/idimab-spacy/releases) of models based on the [spaCy](https://github.com/explosion/spaCy) NLP library. For more info on how to download, install and use the models, see the models documentation.

## Quickstart
Before you can begin working with this model, you will need to install the Spacy library. Please install Spacy in your environment to ensure seamless integration and optimal performance of this model

```bash
pip install spacy
```

## Download

| Model | Size | SpaCy version |
| --- | --- | --- |
| [ru_cv_parse_model-1.0.0.tar.gz](https://github.com/FistFonI/idimab-spacy/releases/download/ru_cv_parse_model-1.0.0/ru_cv_parse_model-1.0.0.tar.gz) | 109 MB | 3.7.4 |

```bash
# pip install .tar.gz archive from path or URL
pip install /Users/you/ru_cv_parse_model-1.0.0.tar.gz
pip install https://github.com/FistFonI/idimab-spacy/releases/download/ru_cv_parse_model-1.0.0/ru_cv_parse_model-1.0.0.tar.gz
```

## Usage

```python
import spacy
from ipymarkup import show_span_ascii_markup

nlp = spacy.load('ru_cv_parse_model')
text = 'Першин Владимир, главный бухгалтер, 260 тыс. рублей, 11.09.1983 г., г. Санкт-Петербург, Приморский район, готов к командировкам, +7 (9хх) ххх-хх-хх, vppershin@ххх.ru, ключевые знания и навыки: ведение бухгалтерского и налогового учета, знание законодательной базы, руководство коллективом, успешный опыт прохождения налоговых проверок, ответственность, активность, умение быстро принимать решения; опыт работы: главный бухгалтер в ООО «Макс» (07.2009–07.2015), бухгалтер в ООО «БСК-консалт» (06.2005–06.2009); достижения: разработка учетной политики и оптимизация налогообложения; образование: Институт экономики и права (2014), Учебный центр «Базис» (2010), Санкт-Петербургский государственный торгово-экономический университет (2005); дополнительная информация: английский язык – B1, уверенный пользователь MS Office, 1С: «Бухгалтерия», «Предприятие», «Склад», Консультант+, «Банк – клиент».'
doc = nlp(text)

spans = [
    (_.start_char, _.end_char, _.label_)
    for _ in doc.ents
]
show_span_ascii_markup(doc.text, spans)

"""
Першин Владимир, главный бухгалтер, 260 тыс. рублей, 11.09.1983 г., г.
fio────────────  title────────────
 Санкт-Петербург, Приморский район, готов к командировкам, +7 (9хх)   
ххх-хх-хх, vppershin@ххх.ru, ключевые знания и навыки: ведение        
бухгалтерского и налогового учета, знание законодательной базы,       
руководство коллективом, успешный опыт прохождения налоговых проверок,
 ответственность, активность, умение быстро принимать решения; опыт   
работы: главный бухгалтер в ООО «Макс» (07.2009–07.2015), бухгалтер в 
        title────────────   org───────  work_date──────
ООО «БСК-консалт» (06.2005–06.2009); достижения: разработка учетной   
org──────────────  work_date──────                                    
политики и оптимизация налогообложения; образование: Институт
экономики и права (2014), Учебный центр «Базис» (2010), Санкт-
                                                        educat
Петербургский государственный торгово-экономический университет
───────────────────────────────────────────────────────────────
(2005); дополнительная информация: английский язык – B1, уверенный
пользователь MS Office, 1С: «Бухгалтерия», «Предприятие», «Склад»,
Консультант+, «Банк – клиент».
"""
```
