# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнил(а):
- Суворов Денис Сергеевич
- РИ-230936
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
Научиться передавать данные из Google таблицы  в Unity с помощью Python.

## Задание 1
### Расширьте варианты доступного оружия в игре. Используйте шаблон таблицы для визуализации оружия игры Save RTF.

(https://docs.google.com/spreadsheets/d/15f8zheeBaRkhGvkYZTvXnuJe1iSNnwZhQFEPs8NxkNA/edit?gid=538464424#gid=538464424)

![image](https://github.com/user-attachments/assets/7dc598a4-5dbc-463b-85be-c71ac981c974)


[balance.xlsx](https://github.com/user-attachments/files/17547258/balance.xlsx)



## Задание 2
### С помощью скрипта на языке Python заполните google-таблицу данными, описывающими выбранную игровую переменную в игре “СПАСТИ РТФ:Выживание”. Средствами google-sheets визуализируйте данные в google-таблице (постройте график / диаграмму и пр.) для наглядного представления выбранной игровой величины. Опишите характер изменения этой величины, опишите недостатки в реализации этой величины (например, в игре может произойти условие наступления эксплойта) и предложите до 3-х вариантов модификации условий работы с переменной, чтобы сделать игровой опыт лучше.

```py

import gspread
import numpy as np
import  random as rnd

gc = gspread.service_account(filename='unitydatasciense-437112-0856780b7dd1.json')
sh = gc.open("UnitySheets")
money = 0
mon = list(range(1, 11))
i = 0

while i <= len(mon):
    test = rnd.randint(2, 5)
    i += 1
    money = float(money)
    money += test
    sh.sheet1.update (('A' + str(i)), [[str(i)]])
    sh.sheet1.update (('B' + str(i)), [[str(money).replace('.',',')]])
    print(money)

```

![img](grafik.png)




## Задание 3
### Настройте на сцене Unity воспроизведение звуковых файлов, описывающих динамику изменения выбранной переменной. Например, если выбрано здоровье главного персонажа вы можете выводить сообщения, связанные с его состоянием.

## Структура проекта unity
```csharp
void Update()
    {
        // Проверяем, что данные загружены и ключ существует
        if (dataLoaded && dataset.ContainsKey("Mon_" + i.ToString()))
        {
            if (dataset["Mon_" + i.ToString()] <= 10 && !statusStart && i != dataset.Count)
            {
                StartCoroutine(PlaySelectAudioGood());
                Debug.Log(dataset["Mon_" + i.ToString()]);
            }

            if (dataset["Mon_" + i.ToString()] > 10 && dataset["Mon_" + i.ToString()] < 100 && !statusStart && i != dataset.Count)
            {
                StartCoroutine(PlaySelectAudioNormal());
                Debug.Log(dataset["Mon_" + i.ToString()]);
            }

            if (dataset["Mon_" + i.ToString()] >= 100 && !statusStart && i != dataset.Count)
            {
                StartCoroutine(PlaySelectAudioBad());
                Debug.Log(dataset["Mon_" + i.ToString()]);
            }
        }
    }

```


## Выводы

Освоил работу с таблицами через Python, научился интегрировать их в Unity и настраивать взаимодействие.





`P.s - музыка зачет))`

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
