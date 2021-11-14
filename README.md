# WildHack_Tags 👗 
---------------------------------------------------

Данные проект был разработан с целью решения задачи Поисковые теги для WildHack. 

Здесь вы можете найти нашу [презентацию](https://docs.google.com/presentation/d/1Gz2pAfyW4l21TmB5ZuAHKxu-zdVjQ2Bwt1iS5XAPKEg/edit?usp=sharing).

Поисковые теги должны были выполнять следующие функции:

- уточнение (кофта → тёплая кофта)

- похожи товары (кофта → кардиган) 

- дополняющая (айфон → чехол для айфона)

Для каждой из данных проблем был разработан отдельный пайплайн.

--------------------------------------------------------------------

## Уточняющие теги

Для данного типа тегов была разработана следующая формула:

[название товара] [аттрибут 1] [аттрибут 2] ... [аттрибут n]

Алгоритм генерации тегов: 

1. После предобработки запроса идентифицировать, какой товар из каталога *Wildberries* пользователь хочет найти

Товаром считается последнее звено в цепочке из категорий:
  например, Женщинам / Одежда / Брюки / **Капри**
  
2. Сгенерировать подмножество корректных тегов, содержащий название товара и/или его аттрибуты

3. Выбрать 3-7 уточняющих тегов


В рамках данной задачи предстояло также решить, что будет источником данных для генерации тегов. Поэтому для уточняющих тегов было предложено два решения:
- [naive_clustering](https://github.com/Nina-Konovalova/WildHack_Tags/blob/main/specifying_tag_generation_naive_clustering.ipynb) -> кластеризация запросов из датасета с историей поиска и генерация тегов из смежных кластеров
- [attribute_clustering](https://github.com/Nina-Konovalova/WildHack_Tags/blob/main/specifying_tag_generation_attribute_clustering.ipynb) -> кластеризация значений каждого из аттрибутов отдельно и генерация с помощью предложенной выше формулы

-------------------------------------------------------------

## Тег похожие товары

Для того, чтобы подробнее ознакомиться с кодом программы - необходимо запустить последнюю ячейку `Final whole tag creation process.`:

[WildHack_similar_tags.ipynb](https://github.com/Nina-Konovalova/WildHack_Tags/blob/main/WildHack_similar_tags.ipynb)

Данное решение базируется на следующей идее:

1) В качетсве датасета использутеся датасет с поисковыми запросами.
2) Поисковые запросы проходили стандартную предобработку.
3) С помощью модели [fasttext](https://fasttext.cc/) cоздавались эмбеддинги для каждого слова датасета.
4) Слова объединялись в кластеры.

Далее каждое новое слово (словосочетание) проходило аналогичную предобработку и с помощью алгоритмов машинного обучения адресуется в нужный кластер. Из нужного кластера выбирались самые близкие по косинусному расстоянию слова.


--------------------------------------------------------------------


## Дополняющие теги

Идея решения:

1) Необходимо сформировать кластеры из "комлектов" (примеры элементов, которые могли бы входить в состав одного комплекта: юбка белая летняя, туфли на шпильке, шарф-платок белый, ... или элементы комплекта: айфон 10, чехол на айфон 10, беспроводные наушники, ...)
2) В качестве датасета использовать уже сформированные пользовательские корзины, в которых названия товаров закодированы некоторыми тегами.
3) Далее для формирования кластера тегов по некоторому запросу необходимо выбрать все корзины, содержащие теги с данным товаром и просуммировать позиции. Большая часть позиций будет распределена равномерно, однако дополняющие товары сформируют пики, которые можно определить используя статистическую гипотезу для критерия выброса. Теги соответствующие этим пикам можно считать дополняющими тегами для исходных.


-------------------------------------------------------------------

## Веб-сервис 	:computer:
Также был разработан [веб-сервис](https://tags-padre-pio-xiii.herokuapp.com/) для возможности продемонстрировать результаты

## Результаты

<p align="center">
  <img src="https://github.com/Nina-Konovalova/WildHack_Tags/blob/main/pictures/clar.png" >
  <img src="https://github.com/Nina-Konovalova/WildHack_Tags/blob/main/pictures/sim.png" >
</p>

----------------------------------------------------------------------
## Дополнительно

1) [data](https://github.com/Nina-Konovalova/WildHack_Tags/tree/main/data) - данные, использовавшиеся для решения задачи поиска похожих товаров
----------------------------------------------------------------------

## Команда

:woman: Эльвира Плyмите

:girl: Асель Ермекова

:curly_haired_woman: Альбина Клепач

:red_haired_woman: Нина Коновалова

