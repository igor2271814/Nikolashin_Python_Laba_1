<a href="https://git.io/typing-svg"><img src="https://readme-typing-svg.herokuapp.com?font=Bowlby+One&size=60&pause=1000&random=false&width=1400&height=90&lines=Welcom+to+laboratory+work+on+Python!" alt="Typing SVG" /></a>
<p><b>На этой странице будут выкладываться лабораторные работы по дисциплине ИТиП</b></p>
<h1>Лобараторная работа №1</h1>
<ul>
  <li><a href="Data">Обзор данных</a></li>
  <li><a href="Visual_Data">Предобработка и визуализация данных</a></li>
</ul>
<p>Первая часть задания звучит так:</p>
<ol>
  <li><p> Импортируйте библиотеку pandas</p></li>
  <li><p> Импортируйте библиотеку matplotlib.pyplot as plt</p></li>
  <li><p> Импортируйте библиотеку Numpy</p></li>
  <li><p> Прочитайте файл и сохраните его в любой переменной</p></li>
  <li><p> Выведите на экран первые 10 строк таблицы</p></li>
  <li><p> Одной командой выведите информацию о таблице</p></li>
  <li><p> Выведите типы данных по датасету одной командой</p></li>
  <li><p> Выведите количество строк и колонок одной командой</p></li>
  <li><p> Выведите на экран название колонок.</p></li>
  <li><p> С помощью isna посмотрите есть ли пропущенные значения, выведите количество по каждой колонке</p></li>
  <li><p> Проверьте данные на наличие дубликатов. Если есть дубликаты, удалите их.
Какой тип данных доминирует в датасете? Есть ли пропущенные значения и если да, то в каких колонках? </p></li>
</ol>
<h2 id="Data">Обзор данных</h2>
<h3>Выполнение заданий 1 - 5</h3>

```python
    import pandas as pd # Импорт библиотек. Задание 1
    import matplotlib.pyplot as plt # Импорт библиотек Задание 2
    import numpy as np # Импорт библиотек Задание 3
    
    data = pd.read_csv('Airpollution.csv') # Чтение данных. Задание 4
    result = data.head(10) # Запись первых 10-ти ячеек
    print ("First 10 row:")
    print (result) # Вывод данных. Задание 5
```
<p>Вывод программы:</p>

```
First 10 row:
                    Country              City  AQI Value  \
0        Russian Federation        Praskoveya         51   
1                    Brazil  Presidente Dutra         41   
2                     Italy   Priolo Gargallo         66   
3                    Poland         Przasnysz         34   
4                    France          Punaauia         22   
5  United States of America       Punta Gorda         54   
6                   Germany        Puttlingen         62   
7                   Belgium             Puurs         64   
8        Russian Federation        Pyatigorsk         54   
9                     Egypt            Qalyub        142   

                     AQI Category  CO AQI Value CO AQI Category  \
0                        Moderate             1            Good   
1                            Good             1            Good   
2                        Moderate             1            Good   
3                            Good             1            Good   
4                            Good             0            Good   
5                        Moderate             1            Good   
6                        Moderate             1            Good   
7                        Moderate             1            Good   
8                        Moderate             1            Good   
9  Unhealthy for Sensitive Groups             3            Good   
...
6               62                        Moderate  
7               64                        Moderate  
8               54                        Moderate  
9              142  Unhealthy for Sensitive Groups
```
<h3>Выполнение заданий 6 - 9</h3>

```python
import pandas as pd # Импорт библиотек
import matplotlib.pyplot as plt # Импорт библиотек
import numpy as np # Импорт библиотек

data = pd.read_csv('Airpollution.csv') # Чтение данных
print ("Base info:")
data.info() # Вывод информации по таблице. Задание 6
print ("Type info:")
print (data.dtypes) # Вывод информации о типе данных. Задание 7
print ("Len info:")
print (data.shape) # Вывод информации о кол-ве стор и колонок. Задание 8
print ("Colums info:")
print (data.columns.values) # Вывод названий колонок. Задание 9
```
<p>Вывод программы:</p>

```
Base info:
<class 'pandas.DataFrame'>
RangeIndex: 23463 entries, 0 to 23462
Data columns (total 12 columns):
 #   Column              Non-Null Count  Dtype 
---  ------              --------------  ----- 
 0   Country             23036 non-null  object
 1   City                23462 non-null  object
 2   AQI Value           23463 non-null  int64 
 3   AQI Category        23463 non-null  object
 4   CO AQI Value        23463 non-null  int64 
 5   CO AQI Category     23463 non-null  object
 6   Ozone AQI Value     23463 non-null  int64 
 7   Ozone AQI Category  23463 non-null  object
 8   NO2 AQI Value       23463 non-null  int64 
 9   NO2 AQI Category    23463 non-null  object
 10  PM2.5 AQI Value     23463 non-null  int64 
 11  PM2.5 AQI Category  23463 non-null  object
dtypes: int64(5), object(7)
memory usage: 2.1+ MB
Type info:
Country               object
City                  object
AQI Value              int64
AQI Category          object
...
Colums info:
['Country' 'City' 'AQI Value' 'AQI Category' 'CO AQI Value'
 'CO AQI Category' 'Ozone AQI Value' 'Ozone AQI Category' 'NO2 AQI Value'
 'NO2 AQI Category' 'PM2.5 AQI Value' 'PM2.5 AQI Category']
```
<h3>Выполнение заданий 10 - 11</h3>

```python
import pandas as pd # Импорт библиотек
import matplotlib.pyplot as plt # Импорт библиотек
import numpy as np # Импорт библиотек

data = pd.read_csv('Airpollution.csv') # Чтение данных
missing_value_count = data.isna().sum() # Запись пропущенных значений в каждом столбце. Задание 10

print ("Missing value count:")
print (missing_value_count)
print ("Duplicated value count:")
print (data.duplicated())
new_data = data.drop_duplicates()

print ("After drop duplicates:")
print (new_data.duplicated())
```
<p>Вывод программы:</p>

```
Missing value count:
Country               427
City                    1
AQI Value               0
AQI Category            0
CO AQI Value            0
CO AQI Category         0
Ozone AQI Value         0
Ozone AQI Category      0
NO2 AQI Value           0
NO2 AQI Category        0
PM2.5 AQI Value         0
PM2.5 AQI Category      0
dtype: int64
Duplicated value count:
0        False
1        False
2        False
3        False
4        False
         ...  
23458    False
23459    False
23460    False
23461    False
...
23460    False
23461    False
23462    False
Length: 23463, dtype: bool
```
**В датасете доминирует object. Это можно понять из вывода данных:**


```python
Data columns (total 12 columns):
 #   Column              Non-Null Count  Dtype 
---  ------              --------------  ----- 
 0   Country             23036 non-null  object
 1   City                23462 non-null  object
 2   AQI Value           23463 non-null  int64 
 3   AQI Category        23463 non-null  object
 4   CO AQI Value        23463 non-null  int64 
 5   CO AQI Category     23463 non-null  object
 6   Ozone AQI Value     23463 non-null  int64 
 7   Ozone AQI Category  23463 non-null  object
 8   NO2 AQI Value       23463 non-null  int64 
 9   NO2 AQI Category    23463 non-null  object
 10  PM2.5 AQI Value     23463 non-null  int64 
 11  PM2.5 AQI Category  23463 non-null  object
```

**Пропущенные значения были:**  
Country               427  
City                    1
