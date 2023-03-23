# <center> Изучение поплавкового уровнемера </center>
## Оглавление
1. [Описание проекта](#Описание-проекта)
2. [Описание данных](#Описание-данных)
3. [Зависимости](#Используемые-зависимости)
4. [Установка проекта](#Установка-проекта)
5. [Использование проекта](#Использование)
6. [Авторы](#Авторы)
7. [Выводы](#выводы)

## Описание проекта

**Принцип действия поплавкового уровнемера с ультразвуковым каналом связи** 

<center> <img src=art/levelGaugeDesign.png> </center>

Прибор состоит из головки прибора (1) с блоком электроники, металлической штанги (2) с фторопластовым покрытием и поплавка (3), двигающегося вдоль штанги.

Измерение уровня основано на измерении времени распространения ультразвукового импульса от поплавка чувствительного элемента в нижней части головки прибора до головки прибора.

Внутри штанги (2) находится стальная проволока с катушкой возбуждения, импульс тока в которой создает магнитное поле вдоль штанги. В подвижном поплавке, находящемся на границе раздела двух сред, находится постоянный магнит. В месте расположения поплавка (3), засчёт эффекта магнитострикции, возникает импульс крутильной деформации, который распространяется по проволоке вдоль штанги и фиксируется чувствительным пьезоэлементом в головке прибора.

В головке прибора (1) вычисляется время о момента формирования импульса тока, создающего магнитное поле, до момента приёма импульса упругой деформации.


**Данный проект** направлен на построение градуировочной характеристики поплавкового уровнемера ДУУ2 на основе данных прямых измерений уровня жидкости в резервуаре.

**О структуре проекта:**
* [data](./data) - папка с исходными табличными данными
* [art](./art) - папка с изображениями, необходимыми для проекта 
* [plotly](./plotly) - папка с графиками, для возможности их просмотра в браузере
* [floatLevelGaugeChar.ipynb](./floatLevelGaugeChar.ipynb) - jupyter-ноутбук, содержащий основной код проекта, в котором расчитываются основные статистические характеристики измерений и строится градуировочная характеристика
* [requirements.txt](./requirements.txt) - файл с версиями используемых модулей, для воспроизводимости кода

## Описание данных
В этом проекте используются данные прямых измерений уровня жидкости в резервуаре, установленного при помощи линейки по сравнению с показаниями уровнемера.

Для каждого значения уровня представлены 6 измерений уровнемером (3 повторных для прохода уровнемера вверх(от наибольшего уровня к наименьшому) и 3 для прохода вверх(от наименьшего уровня к наибольшему)).

__Важный момент - уровень измеренный линейкой(составляет столбцы исходной таблицы) представлены в сантиметрах, в значения, полученные с уровнемера - в миллиметрах.__

Файл с данными можно найти [здесь](./data/directMeasurement.csv).

## Используемые зависимости
* Python (3.11.1):
    * [pandas (1.5.3)](https://pandas.pydata.org)
    * [plotly (5.13.0)](https://plotly.com/python/)

## Установка проекта

```
git clone https://github.com/StartrexII/CalibrationFloatLevelGauge.git
```

## Использование
* Расчет статистических показателей представлен в jupyter-ноутбуке floatLevelGaugeChar.ipynb.

* Градуировочная характеристика представлена [html-файлом floatLevelGaugeChar.html (открывается в браузере)](plotly/floatLevelGaugeChar.html 'Ссылка на файл с графиком').

## Авторы

* [Егор Орлов](https://vk.com/liquidlogic)

## Выводы

В результате расчета и построения характеристики понятно, что уровнемеры ультразвуковые - очень точные устройства, погрешность прямых измерений которых составляет порядка нескольких миллиметров (в нашем случае стандартное отклонение составило не более 3мм), что совершенно не критично при измерении высоты жидкости в резервуаре, которая может составлять более 10 метров.