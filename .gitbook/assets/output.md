
##Токенизация по предложениям

Токенизация (иногда – сегментация) по предложениям – это процесс разделения письменного языка на предложения-компоненты. Идея выглядит довольно простой. В английском и некоторых других языках мы можем вычленять предложение каждый раз, когда находим определенный знак пунктуации – точку.

Но даже в английском эта задача нетривиальна, так как точка используется и в сокращениях. Таблица сокращений может сильно помочь во время обработки текста, чтобы избежать неверной расстановки границ предложений. В большинстве случаев для этого используются библиотеки, так что можете особо не переживать о деталях реализации.



---





**Возьмем два небольших текста на русском и на англиском (При желании можете изменить на свой)**


```
textEN = "The Great Wall of China, one of the greatest wonders of the world, was first built between 220–206 BC. In fact, it began as independent walls for different states when it was first built, and did not become the “Great” wall until the Qin Dynasty. Emperor Qin Shihuang succeeded in his effort to have the walls joined together to serve as fortification to protect the northern borders of the Chinese Empire from invasion. Afterwards it was rebuilt and maintained over the years, between the 5th century BC and the 16th century."
textRUS = "Великая китайская стена – одно из величайших чудес мира – была впервые построена между 220 и 206 годами до нашей эры. В действительности, она начиналась как независимые стены для разных государств, когда была впервые построена, и не стала «великой» стеной до династии Цинь. Император Цинь Шихуанди преуспел в своих усилиях по объединению этих стен, чтобы они служили как укрепления для защиты северных границ Китайской империи от вторжения. Впоследствии, она была перестроена и поддерживалась долгие годы между 5-м веком до нашей эры и 16-м веком."
```

Чтобы сделать токенизацию предложений с помощью NLTK, можно воспользоваться методом nltk.sent_tokenize


```
import nltk
```


```
nltk.download('punkt')
```

    [nltk_data] Downloading package punkt to /root/nltk_data...
    [nltk_data]   Package punkt is already up-to-date!





    True




```
sentencesEN = nltk.sent_tokenize(textEN)
for sentenceEN in sentencesEN:
    print(sentenceEN)
    print()
```

    The Great Wall of China, one of the greatest wonders of the world, was first built between 220–206 BC.
    
    In fact, it began as independent walls for different states when it was first built, and did not become the “Great” wall until the Qin Dynasty.
    
    Emperor Qin Shihuang succeeded in his effort to have the walls joined together to serve as fortification to protect the northern borders of the Chinese Empire from invasion.
    
    Afterwards it was rebuilt and maintained over the years, between the 5th century BC and the 16th century.
    



```
sentencesRUS = nltk.sent_tokenize(textRUS)
for sentenceRUS in sentencesRUS:
    print(sentenceRUS)
    print()
```

    Великая китайская стена – одно из величайших чудес мира – была впервые построена между 220 и 206 годами до нашей эры.
    
    В действительности, она начиналась как независимые стены для разных государств, когда была впервые построена, и не стала «великой» стеной до династии Цинь.
    
    Император Цинь Шихуанди преуспел в своих усилиях по объединению этих стен, чтобы они служили как укрепления для защиты северных границ Китайской империи от вторжения.
    
    Впоследствии, она была перестроена и поддерживалась долгие годы между 5-м веком до нашей эры и 16-м веком.
    


##Токенизация по словам

Токенизация (иногда – сегментация) по словам – это процесс разделения предложений на слова-компоненты. В английском и многих других языках, использующих ту или иную версию латинского алфавита, пробел – это неплохой разделитель слов.

Тем не менее, могут возникнуть проблемы, если мы будем использовать только пробел – в английском составные существительные пишутся по-разному и иногда через пробел. И тут вновь нам помогают библиотеки.



---




```
for sentenceEN in sentencesEN:
    wordsEN = nltk.word_tokenize(sentenceEN)
    print(wordsEN)
```

    ['The', 'Great', 'Wall', 'of', 'China', ',', 'one', 'of', 'the', 'greatest', 'wonders', 'of', 'the', 'world', ',', 'was', 'first', 'built', 'between', '220–206', 'BC', '.']
    ['In', 'fact', ',', 'it', 'began', 'as', 'independent', 'walls', 'for', 'different', 'states', 'when', 'it', 'was', 'first', 'built', ',', 'and', 'did', 'not', 'become', 'the', '“', 'Great', '”', 'wall', 'until', 'the', 'Qin', 'Dynasty', '.']
    ['Emperor', 'Qin', 'Shihuang', 'succeeded', 'in', 'his', 'effort', 'to', 'have', 'the', 'walls', 'joined', 'together', 'to', 'serve', 'as', 'fortification', 'to', 'protect', 'the', 'northern', 'borders', 'of', 'the', 'Chinese', 'Empire', 'from', 'invasion', '.']
    ['Afterwards', 'it', 'was', 'rebuilt', 'and', 'maintained', 'over', 'the', 'years', ',', 'between', 'the', '5th', 'century', 'BC', 'and', 'the', '16th', 'century', '.']



```
for sentenceRUS in sentencesRUS:
    wordsRUS = nltk.word_tokenize(sentenceRUS)
    print(wordsRUS)
```

    ['Великая', 'китайская', 'стена', '–', 'одно', 'из', 'величайших', 'чудес', 'мира', '–', 'была', 'впервые', 'построена', 'между', '220', 'и', '206', 'годами', 'до', 'нашей', 'эры', '.']
    ['В', 'действительности', ',', 'она', 'начиналась', 'как', 'независимые', 'стены', 'для', 'разных', 'государств', ',', 'когда', 'была', 'впервые', 'построена', ',', 'и', 'не', 'стала', '«', 'великой', '»', 'стеной', 'до', 'династии', 'Цинь', '.']
    ['Император', 'Цинь', 'Шихуанди', 'преуспел', 'в', 'своих', 'усилиях', 'по', 'объединению', 'этих', 'стен', ',', 'чтобы', 'они', 'служили', 'как', 'укрепления', 'для', 'защиты', 'северных', 'границ', 'Китайской', 'империи', 'от', 'вторжения', '.']
    ['Впоследствии', ',', 'она', 'была', 'перестроена', 'и', 'поддерживалась', 'долгие', 'годы', 'между', '5-м', 'веком', 'до', 'нашей', 'эры', 'и', '16-м', 'веком', '.']


##Стоп-слова

###Для англиского


```
import nltk
from nltk.corpus import stopwords
nltk.download('stopwords')
```

    [nltk_data] Downloading package stopwords to /root/nltk_data...
    [nltk_data]   Package stopwords is already up-to-date!





    True




```
stop_wordsEN = set(stopwords.words("english"))
```


```
tok_sentenceEN = []
sentencesEN = nltk.sent_tokenize(textEN)
for sentenceEN in sentencesEN:
    tok_sentenceEN.append(sentenceEN)
print(tok_sentenceEN)
```

    ['The Great Wall of China, one of the greatest wonders of the world, was first built between 220–206 BC.', 'In fact, it began as independent walls for different states when it was first built, and did not become the “Great” wall until the Qin Dynasty.', 'Emperor Qin Shihuang succeeded in his effort to have the walls joined together to serve as fortification to protect the northern borders of the Chinese Empire from invasion.', 'Afterwards it was rebuilt and maintained over the years, between the 5th century BC and the 16th century.']



```
tok_wordsEN = []
for tok_sentenceEN in tok_sentenceEN:
    wordsEN = nltk.word_tokenize(tok_sentenceEN)
    tok_wordsEN.append(wordsEN)
print(tok_wordsEN)
```

    [['The', 'Great', 'Wall', 'of', 'China', ',', 'one', 'of', 'the', 'greatest', 'wonders', 'of', 'the', 'world', ',', 'was', 'first', 'built', 'between', '220–206', 'BC', '.'], ['In', 'fact', ',', 'it', 'began', 'as', 'independent', 'walls', 'for', 'different', 'states', 'when', 'it', 'was', 'first', 'built', ',', 'and', 'did', 'not', 'become', 'the', '“', 'Great', '”', 'wall', 'until', 'the', 'Qin', 'Dynasty', '.'], ['Emperor', 'Qin', 'Shihuang', 'succeeded', 'in', 'his', 'effort', 'to', 'have', 'the', 'walls', 'joined', 'together', 'to', 'serve', 'as', 'fortification', 'to', 'protect', 'the', 'northern', 'borders', 'of', 'the', 'Chinese', 'Empire', 'from', 'invasion', '.'], ['Afterwards', 'it', 'was', 'rebuilt', 'and', 'maintained', 'over', 'the', 'years', ',', 'between', 'the', '5th', 'century', 'BC', 'and', 'the', '16th', 'century', '.']]



```
without_stop_wordsEN = []

for tok_wordEN in tok_wordsEN:
    local_listEN = []

    for element in tok_wordEN:
        if element not in stop_wordsEN:
            local_listEN.append(element)
    
    without_stop_wordsEN.append(local_listEN)

print(without_stop_wordsEN)
```

    [['The', 'Great', 'Wall', 'China', ',', 'one', 'greatest', 'wonders', 'world', ',', 'first', 'built', '220–206', 'BC', '.'], ['In', 'fact', ',', 'began', 'independent', 'walls', 'different', 'states', 'first', 'built', ',', 'become', '“', 'Great', '”', 'wall', 'Qin', 'Dynasty', '.'], ['Emperor', 'Qin', 'Shihuang', 'succeeded', 'effort', 'walls', 'joined', 'together', 'serve', 'fortification', 'protect', 'northern', 'borders', 'Chinese', 'Empire', 'invasion', '.'], ['Afterwards', 'rebuilt', 'maintained', 'years', ',', '5th', 'century', 'BC', '16th', 'century', '.']]


###Для русского


```
import nltk
from nltk.corpus import stopwords
nltk.download('stopwords')
```

    [nltk_data] Downloading package stopwords to /root/nltk_data...
    [nltk_data]   Package stopwords is already up-to-date!





    True




```
stop_wordsRUS = set(stopwords.words("russian"))
```


```
tok_sentenceRUS = []
sentencesRUS = nltk.sent_tokenize(textRUS)
for sentenceRUS in sentencesRUS:
    tok_sentenceRUS.append(sentenceRUS)
    
print(tok_sentenceRUS)
```

    ['Великая китайская стена – одно из величайших чудес мира – была впервые построена между 220 и 206 годами до нашей эры.', 'В действительности, она начиналась как независимые стены для разных государств, когда была впервые построена, и не стала «великой» стеной до династии Цинь.', 'Император Цинь Шихуанди преуспел в своих усилиях по объединению этих стен, чтобы они служили как укрепления для защиты северных границ Китайской империи от вторжения.', 'Впоследствии, она была перестроена и поддерживалась долгие годы между 5-м веком до нашей эры и 16-м веком.']



```
tok_wordsRUS = []
for tok_sentenceRUS in tok_sentenceRUS:
    wordsRUS = nltk.word_tokenize(tok_sentenceRUS)
    tok_wordsRUS.append(wordsRUS)
    
print(tok_wordsRUS)
```

    [['Великая', 'китайская', 'стена', '–', 'одно', 'из', 'величайших', 'чудес', 'мира', '–', 'была', 'впервые', 'построена', 'между', '220', 'и', '206', 'годами', 'до', 'нашей', 'эры', '.'], ['В', 'действительности', ',', 'она', 'начиналась', 'как', 'независимые', 'стены', 'для', 'разных', 'государств', ',', 'когда', 'была', 'впервые', 'построена', ',', 'и', 'не', 'стала', '«', 'великой', '»', 'стеной', 'до', 'династии', 'Цинь', '.'], ['Император', 'Цинь', 'Шихуанди', 'преуспел', 'в', 'своих', 'усилиях', 'по', 'объединению', 'этих', 'стен', ',', 'чтобы', 'они', 'служили', 'как', 'укрепления', 'для', 'защиты', 'северных', 'границ', 'Китайской', 'империи', 'от', 'вторжения', '.'], ['Впоследствии', ',', 'она', 'была', 'перестроена', 'и', 'поддерживалась', 'долгие', 'годы', 'между', '5-м', 'веком', 'до', 'нашей', 'эры', 'и', '16-м', 'веком', '.']]



```
without_stop_wordsRUS = []

for tok_wordRUS in tok_wordsRUS:
    local_listRUS = []

    for element in tok_wordRUS:
        if element not in stop_wordsRUS:
            local_listRUS.append(element)
    
    without_stop_wordsRUS.append(local_listRUS)

print(without_stop_wordsRUS)
```

    [['Великая', 'китайская', 'стена', '–', 'одно', 'величайших', 'чудес', 'мира', '–', 'впервые', 'построена', '220', '206', 'годами', 'нашей', 'эры', '.'], ['В', 'действительности', ',', 'начиналась', 'независимые', 'стены', 'разных', 'государств', ',', 'впервые', 'построена', ',', 'стала', '«', 'великой', '»', 'стеной', 'династии', 'Цинь', '.'], ['Император', 'Цинь', 'Шихуанди', 'преуспел', 'своих', 'усилиях', 'объединению', 'этих', 'стен', ',', 'служили', 'укрепления', 'защиты', 'северных', 'границ', 'Китайской', 'империи', 'вторжения', '.'], ['Впоследствии', ',', 'перестроена', 'поддерживалась', 'долгие', 'годы', '5-м', 'веком', 'нашей', 'эры', '16-м', 'веком', '.']]


##Лемматизация текста

Обычно тексты содержат разные грамматические формы одного и того же слова, а также могут встречаться однокоренные слова. Лемматизация и стемминг преследуют цель привести все встречающиеся словоформы к одной, нормальной словарной форме.




---



Пример

dog, dogs, dog’s, dogs’ => dog

То же самое, но уже применительно к целому предложению:

the boy’s dogs are different sizes => the boy dog be differ size



---



Лемматизация – это процесс, который использует словарь и морфологический анализ, чтобы в итоге привести слово к его канонической форме – лемме.



---



Примеры:

Слово good – это лемма для слова better. Стеммер не увидит эту связь, так как здесь нужно сверяться со словарем.
Слово play – это базовая форма слова playing. Тут справятся и стемминг, и лемматизация.
Слово meeting может быть как нормальной формой существительного, так и формой глагола to meet, в зависимости от контекста. В отличие от стемминга, лемматизация попробует выбрать правильную лемму, опираясь на контекст.



---



###Для англиского


```
import nltk
from nltk.stem import WordNetLemmatizer
nltk.download('wordnet')
from nltk.corpus import wordnet
```

    [nltk_data] Downloading package wordnet to /root/nltk_data...
    [nltk_data]   Package wordnet is already up-to-date!



```
WordNetLemmatizer().lemmatize("drove", wordnet.VERB)
```




    'drive'





---




```
lema_textEN = []

for without_stop_wordEN in without_stop_wordsEN:
    local_listLEMAen = []

    for elementLemEN in without_stop_wordEN:
        local_listLEMAen.append(WordNetLemmatizer().lemmatize(elementLemEN, wordnet.VERB))
    
    lema_textEN.append(local_listLEMAen)

print(lema_textEN)
```

    [['The', 'Great', 'Wall', 'China', ',', 'one', 'greatest', 'wonder', 'world', ',', 'first', 'build', '220–206', 'BC', '.'], ['In', 'fact', ',', 'begin', 'independent', 'wall', 'different', 'state', 'first', 'build', ',', 'become', '“', 'Great', '”', 'wall', 'Qin', 'Dynasty', '.'], ['Emperor', 'Qin', 'Shihuang', 'succeed', 'effort', 'wall', 'join', 'together', 'serve', 'fortification', 'protect', 'northern', 'border', 'Chinese', 'Empire', 'invasion', '.'], ['Afterwards', 'rebuild', 'maintain', 'years', ',', '5th', 'century', 'BC', '16th', 'century', '.']]


**Для сравнения**


```
print(without_stop_wordsEN)
```

    [['The', 'Great', 'Wall', 'China', ',', 'one', 'greatest', 'wonders', 'world', ',', 'first', 'built', '220–206', 'BC', '.'], ['In', 'fact', ',', 'began', 'independent', 'walls', 'different', 'states', 'first', 'built', ',', 'become', '“', 'Great', '”', 'wall', 'Qin', 'Dynasty', '.'], ['Emperor', 'Qin', 'Shihuang', 'succeeded', 'effort', 'walls', 'joined', 'together', 'serve', 'fortification', 'protect', 'northern', 'borders', 'Chinese', 'Empire', 'invasion', '.'], ['Afterwards', 'rebuilt', 'maintained', 'years', ',', '5th', 'century', 'BC', '16th', 'century', '.']]


###Для русского


```
from IPython.display import clear_output
```


```
!pip install pymorphy2
clear_output()
```


```
import pymorphy2
```


```
morph = pymorphy2.MorphAnalyzer()
```


```
 morph.parse("читавшему")[0].normal_form
```




    'читать'





---




```
lema_textRUS = []

for without_stop_wordRUS in without_stop_wordsRUS:
    local_listLEMArus = []

    for elementLemRUS in without_stop_wordRUS:
        local_listLEMArus.append(morph.parse(elementLemRUS)[0].normal_form)
    
    lema_textRUS.append(local_listLEMArus)

print(lema_textRUS)
```

    [['великий', 'китайский', 'стена', '–', 'один', 'великий', 'чудо', 'мир', '–', 'впервые', 'построить', '220', '206', 'год', 'наш', 'эра', '.'], ['в', 'действительность', ',', 'начинаться', 'независимый', 'стена', 'разный', 'государство', ',', 'впервые', 'построить', ',', 'стать', '«', 'великий', '»', 'стена', 'династия', 'цинь', '.'], ['император', 'цинь', 'шихуанди', 'преуспеть', 'свой', 'усилие', 'объединение', 'этот', 'стена', ',', 'служить', 'укрепление', 'защита', 'северный', 'граница', 'китайский', 'империя', 'вторжение', '.'], ['впоследствии', ',', 'перестроить', 'поддерживаться', 'долгий', 'год', '5-й', 'век', 'наш', 'эра', '16-й', 'век', '.']]


**Для сравнения**


```
print(without_stop_wordsRUS)
```

    [['Великая', 'китайская', 'стена', '–', 'одно', 'величайших', 'чудес', 'мира', '–', 'впервые', 'построена', '220', '206', 'годами', 'нашей', 'эры', '.'], ['В', 'действительности', ',', 'начиналась', 'независимые', 'стены', 'разных', 'государств', ',', 'впервые', 'построена', ',', 'стала', '«', 'великой', '»', 'стеной', 'династии', 'Цинь', '.'], ['Император', 'Цинь', 'Шихуанди', 'преуспел', 'своих', 'усилиях', 'объединению', 'этих', 'стен', ',', 'служили', 'укрепления', 'защиты', 'северных', 'границ', 'Китайской', 'империи', 'вторжения', '.'], ['Впоследствии', ',', 'перестроена', 'поддерживалась', 'долгие', 'годы', '5-м', 'веком', 'нашей', 'эры', '16-м', 'веком', '.']]


##TF-IDF

**TF-IDF** расшифровывается как Term Frequency - Inverse Document Frequency (Обратная периодичность документа) и представляет собой статистическую меру для оценки важности слова в документе, который является частью коллекции или корпуса.
Это достигается путем рассмотрения того, на сколько часто слово встречается в документе.

---
**TF** (term frequency — частота слова) – отношение числа вхождений слова к общему числу слов документа.

---
**DF** (inverse document frequency — обратная частота документа) — инверсия частоты, с которой некоторое слово встречается в документах коллекции.

https://en.wikipedia.org/wiki/Tf%E2%80%93idf




---



##Пример:


```
from google.colab import drive
drive.mount('/content/drive')
import os
os.chdir('/content/drive/My Drive/nltk')
```

    Mounted at /content/drive



```
! jupyter nbconvert data.ipynb --to markdown --output nltk/output.md
```

    [NbConvertApp] Converting notebook data.ipynb to markdown
    [NbConvertApp] Writing 18185 bytes to nltk/output.md
    Traceback (most recent call last):
      File "/usr/local/bin/jupyter-nbconvert", line 8, in <module>
        sys.exit(main())
      File "/usr/local/lib/python2.7/dist-packages/jupyter_core/application.py", line 267, in launch_instance
        return super(JupyterApp, cls).launch_instance(argv=argv, **kwargs)
      File "/usr/local/lib/python2.7/dist-packages/traitlets/config/application.py", line 658, in launch_instance
        app.start()
      File "/usr/local/lib/python2.7/dist-packages/nbconvert/nbconvertapp.py", line 338, in start
        self.convert_notebooks()
      File "/usr/local/lib/python2.7/dist-packages/nbconvert/nbconvertapp.py", line 508, in convert_notebooks
        self.convert_single_notebook(notebook_filename)
      File "/usr/local/lib/python2.7/dist-packages/nbconvert/nbconvertapp.py", line 480, in convert_single_notebook
        write_results = self.write_single_notebook(output, resources)
      File "/usr/local/lib/python2.7/dist-packages/nbconvert/nbconvertapp.py", line 441, in write_single_notebook
        output, resources, notebook_name=notebook_name)
      File "/usr/local/lib/python2.7/dist-packages/nbconvert/writers/files.py", line 126, in write
        with io.open(dest, 'w', encoding='utf-8') as f:
    IOError: [Errno 2] No such file or directory: 'nltk/output.md'

