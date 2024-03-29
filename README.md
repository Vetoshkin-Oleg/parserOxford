# parserOxford
**парсинг сайтов Oxford и Cambridge с целью получения готовых предложений по заданному списку слов**
  (Описание для приватного репозитория).

Репозиторий представляет собой программу из 5 классов:  
FormingTemplates, ParserSiteOxford, ReadFile, WorkForString, WriteFile.  
  
Классы ReadFile и WriteFile предназначены для чтения и записи соотвественно.
  
Класс WorkForString предназначен для обработки строковых данных:  
- workForString: получает на входе строку, удаляет все символы, кроме английских букв и пробелов.  
Многократные пробелы преобразует к одинарному, удаляет пробелы в начале и конце строки.  
- compareWithDictionary: этот метод проверяет, что все слова в предложении из множества предложений соответствуют заданному словарю.  
Например, из исходного множества можно оставить только те предложения, где каждое слово состоит в первой тысяче самых распространенных английских слов.  
- compareWithDictionaryAnyWord: этот метод проверяет, что хотя бы одно из слов в предложении из множества предложений соответствуют заданному словарю.  
Таким образом, из всей массы предложений можно вычленить только предложения, содержащие слово "cat", либо группу любых слов "dog, cat, man".  
- twoWords: этот метод находит строки из одного или двух слов.  
- oneWords: этот метод находит строки только из одного слова.  
- subString: этот метод находит строки, которые содержат в себе часть других существующих строк  
(например, строка "one two" входит в состав строки "one two three", и нет смысла учить две разные строки - достаточно одну более длинную).  Метод в своей работе не учитывает последнее слово каждой строки.  
- readFileDeckWords: метод предназначен для обработки "кривых" списков слов с сайта "карточек слов".  
В результате получается список только из английских символов, где "склеенные" слова типа "homehome" преобразованы к виду "home".  
- findCodeAndReplace: метод преобразует все символы к строго определенному ограниченному набору символов.  
Например, различные виды знака "тире" (длинное тире без полей, короткое тире без полей, короткое тире с широкими полями) преобразует к трем символам "пробел тире пробел".  

Класс FormingTemplates предназначен для формирования ссылок, которые требуется парсить для получения английских предложений.  
В метод поступает английское слово/словосочетание в любом из трех возможных вариантов:  
- слово как оно есть "mother",
- словосочетание с пробелом "have to",
- словосочетание с дефисом "old-fashioned".

Методы класса возвращают множество ссылок для каждого из заданных словосочетаний.  
На сайте Oxford таких возможных вариантов обнаружено несколько:  
- ...english/word
- ...english/word_1
- ...english/word_2
- ...english/word1_1
- ...english/word1_2
- ...english/word2_1
- ...english/word2_2
- и так далее.  

Класс ParserSiteOxford предназначен непосредственно для парсинга сайта Оксфорда.  
В результирующий набор записываются только завершенные предложения (не словосочетания), и только в том случае, когда длина предложения находится в пределах от 10 до 70 символов включительно.  

В результате выполнения программы после всех описанных выше преобразований сформирован список из 112_365 уникальных предложений в алфавитном порядке.  
Из них 51365 предложений образованы с помощью 5000 самых употребительных английских слов (Oxford 5000).  
Остальные 61000 предложений сформированы с помощью списка 30000 английских слов (куда входит и Oxford 5000).  

К репозиторию приложены следующие списки:  
1000 слов,  
2000 слов,  
Oxford 3000,  
4000 слов,  
Oxford 5000,  
6000 слов,  
7000 слов,  
10000 слов,  
20000 слов,  
30000 слов.

Парсинг сайта Кембриджа осуществляется аналогичным образом благодаря классу ParserSiteCambridge.
