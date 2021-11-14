# WildHack_Tags 👗 
---------------------------------------------------

Данные проект был разработан с целью решения Tags problem для WildHack. 

Здесь вы можете найти нашу [презентацию](https://docs.google.com/presentation/d/1Gz2pAfyW4l21TmB5ZuAHKxu-zdVjQ2Bwt1iS5XAPKEg/edit?usp=sharing).

Поисковые теги должны были выполнять следующие функции:

- уточнение (кофта → тёплая кофта)

- похожи товары (кофта → кардиган) 

- дополняющая (айфон → чехол для айфона)

Для каждой из данных проблем был разработан отдельный пайплайн.

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

## Уточняющие теги

--------------------------------------------------------------------


## Дополняющие теги



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

