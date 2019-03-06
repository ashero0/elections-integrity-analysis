

```python
import pandas as pd
import numpy as np
import os
#from pandas import Series, DataFrame, Panel
#from datetime import datetime
```


```python
#import plotly.plotly as py
#import cufflinks as cf
#How to measure influence and diversity 
#network of followers 
```


```python
#from matplotlib import pyplot
```


```python
filename = './data/ira_users_csv_hashed.csv'
```


```python
users = pd.read_csv(filename, dtype = {
    "tweetid": str,
    "userid": str,
    "user_display_name": str,
    "user_screen_name": str,
    "user_reported_location": str,
    "user_profile_description": str,
    "user_profile_url": str,
    "follower_count": str,
    "following_count": str,
    "account_creation_date": str,
    "account_language": str,
    "tweet_text": str,
    "tweet_time": str,
    "tweet_client_name": str,
    "in_reply_to_tweetid": str,
    "in_reply_to_userid": str,
    "quoted_tweet_tweetid": str,
    "is_retweet": bool,
    "retweet_userid": str,
    "retweet_tweetid": str,
    "latitude": str,
    "longitude": str,
    "quote_count": str,
    "reply_count": str,
    "like_count": str,
    "retweet_count": str,
    "hashtags": str,
    "urls": str,
    "user_mentions": str,
    "poll_choices": str,
})
```


```python
print(len(users))
```

    3608
    


```python
#users.account_language
```


```python
users.columns

```




    Index(['userid', 'user_display_name', 'user_screen_name',
           'user_reported_location', 'user_profile_description',
           'user_profile_url', 'follower_count', 'following_count',
           'account_creation_date', 'account_language'],
          dtype='object')




```python
#russia['tweet_time']
```


```python
#russia['tweet_record_time'] = pd.to_datetime(russia['tweet_time'], format ='%Y-%m-%d %H:%M')
```


```python
#russia['tweet_record_time']
```


```python
#time = []
```


```python
#for i in russia['tweet_record_time']:
#    time.append(i.time())
    #print(i.time())
```


```python
#russia['time'] = time
```


```python
#hour =[]
```


```python
#for i in russia['time']:
#    hour.append(i.hour)
    #print(i.time())
```


```python
#russia['hour'] = hour
```


```python
#russia.longtitude
```


```python
#cf.set_config_file(offline=False, world_readable=True, theme='ggplot')

#russia.iplot(x='time',kind='scatter') 
```


```python
#russia['hour'].hist(bins = 30)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x2576d8387b8>




![png](output_19_1.png)



```python
#russia['hour'].plot()
#pyplot.show()
```


```python
import matplotlib
import matplotlib.pyplot as plt
```


```python
pd.crosstab(index=users['user_reported_location'],   columns="count").sort_values(by=['count'], ascending=False).head(50)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>col_0</th>
      <th>count</th>
    </tr>
    <tr>
      <th>user_reported_location</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>USA</th>
      <td>670</td>
    </tr>
    <tr>
      <th>Москва</th>
      <td>206</td>
    </tr>
    <tr>
      <th>United States</th>
      <td>116</td>
    </tr>
    <tr>
      <th>Atlanta</th>
      <td>73</td>
    </tr>
    <tr>
      <th>Санкт-Петербург</th>
      <td>66</td>
    </tr>
    <tr>
      <th>US</th>
      <td>65</td>
    </tr>
    <tr>
      <th>Питер</th>
      <td>62</td>
    </tr>
    <tr>
      <th>Россия</th>
      <td>55</td>
    </tr>
    <tr>
      <th>Moscow</th>
      <td>48</td>
    </tr>
    <tr>
      <th>New York, USA</th>
      <td>42</td>
    </tr>
    <tr>
      <th>МSK</th>
      <td>38</td>
    </tr>
    <tr>
      <th>Новосибирск</th>
      <td>38</td>
    </tr>
    <tr>
      <th>Москва, Россия</th>
      <td>37</td>
    </tr>
    <tr>
      <th>Новгород</th>
      <td>36</td>
    </tr>
    <tr>
      <th>NY</th>
      <td>33</td>
    </tr>
    <tr>
      <th>Омск</th>
      <td>31</td>
    </tr>
    <tr>
      <th>Germany</th>
      <td>30</td>
    </tr>
    <tr>
      <th>LA</th>
      <td>29</td>
    </tr>
    <tr>
      <th>Boston</th>
      <td>24</td>
    </tr>
    <tr>
      <th>New York</th>
      <td>19</td>
    </tr>
    <tr>
      <th>New York, NY</th>
      <td>18</td>
    </tr>
    <tr>
      <th>Санкт-Петербург, Россия</th>
      <td>18</td>
    </tr>
    <tr>
      <th>Чебоксары</th>
      <td>17</td>
    </tr>
    <tr>
      <th>Russia</th>
      <td>16</td>
    </tr>
    <tr>
      <th>Atlanta, GA</th>
      <td>16</td>
    </tr>
    <tr>
      <th>Los Angeles</th>
      <td>16</td>
    </tr>
    <tr>
      <th>سوريا</th>
      <td>16</td>
    </tr>
    <tr>
      <th>Syria</th>
      <td>15</td>
    </tr>
    <tr>
      <th>Chicago</th>
      <td>12</td>
    </tr>
    <tr>
      <th>Казань</th>
      <td>12</td>
    </tr>
    <tr>
      <th>Екатеринбург</th>
      <td>11</td>
    </tr>
    <tr>
      <th>Moscow, Russia</th>
      <td>11</td>
    </tr>
    <tr>
      <th>СПБ</th>
      <td>11</td>
    </tr>
    <tr>
      <th>СПб</th>
      <td>10</td>
    </tr>
    <tr>
      <th>Washington, DC</th>
      <td>10</td>
    </tr>
    <tr>
      <th>France</th>
      <td>10</td>
    </tr>
    <tr>
      <th>Philadelphia</th>
      <td>10</td>
    </tr>
    <tr>
      <th>دمشق</th>
      <td>10</td>
    </tr>
    <tr>
      <th>SPB</th>
      <td>9</td>
    </tr>
    <tr>
      <th>Phoenix</th>
      <td>8</td>
    </tr>
    <tr>
      <th>spb</th>
      <td>8</td>
    </tr>
    <tr>
      <th>Estados Unidos</th>
      <td>8</td>
    </tr>
    <tr>
      <th>Волгоград</th>
      <td>8</td>
    </tr>
    <tr>
      <th>Chicago, IL</th>
      <td>8</td>
    </tr>
    <tr>
      <th>Нижний Новгород</th>
      <td>8</td>
    </tr>
    <tr>
      <th>Тверь</th>
      <td>7</td>
    </tr>
    <tr>
      <th>Houston, TX</th>
      <td>7</td>
    </tr>
    <tr>
      <th>Miami, FL</th>
      <td>7</td>
    </tr>
    <tr>
      <th>Texas, USA</th>
      <td>7</td>
    </tr>
    <tr>
      <th>Киев</th>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>




```python
users['location'] = users.user_reported_location.replace({  'Волгоград':'Volgograd, Russia','Egypt':'N/A, Egypt',
                                                            'Ростов':'Rostov-on-Don, Russia','Baltimore, MD':'Baltimore, United States','London':'London, England','Jacksonville':'Jacksonville, United States',
                                                            'Moscow':'Moscow, Russia', 'Петербург':'Saint Petersburg, Russia','New York City':'New York, United States', 'Arizona':'Phoenix, United States',
                                                            'Germany':'N/A, Germany','Санкт-Петербург, Россия':'Saint Petersburg, Russia','Нижний Новгород':'Nizhny Novgorod, Russia','Тверь':'Tver, Russia','Киев':'Kiev, Ukraine',
                                                            'دمشق':'Damascus, Syria','spb':'SPB','Estados Unidos':'N/A, United States','Estados Unidos':'Volgograd, Russia',
                                                            'Казань':'Kazan, Russia','Екатеринбург':'Yekaterinburg, Russia', 'СПБ':'Saint Petersburg, Russia','СПб':'Saint Petersburg, Russia','Washington, D.C.': 'Washington DC, United States',
                                                            'Houston, TX':'Houston, United States','Miami, FL': 'Miami, United States','Texas, USA':'Texas, United States','Washington': 'Washington DC, United States',
                                                            'France': 'N/A, France','Phoenix':'Phoenix, United States','Chicago, IL':'Chicago, United States','Washington, DC': 'Washington D.C, United States',
                                                            'Philadelphia':'Philadelphia, United States'  ,'Chicago':'Chicago, United States','Washington, D.C': 'Washington DC, United States',
                                                            'Чебоксары':'Cheboksary, Russia', 'سوريا':'N/A, Syria','Syria':'N/A, Syria', 'New-York':'New York, United States', 
                                                            'Atlanta' :'Atlanta, United States','LA' :'Los Angeles, United States','Los Angeles' :'Los Angeles, United States','Los Angeles, CA' :'Los Angeles, United States',
                                                            'Boston':'Boston, United States','Омск':'Omsk, Russia','New York, NY':'New York, United States',
                                                            'New York':'New York, United States', 'NY':'New York, United States', 'Новгород':'Veliky Novgorod, Russia', 
                                                            'Москва, Россия':'Moscow, Russia','Новосибирск': 'Novosibirsk, Russia', 'Россия' :'N/A, Russia' ,'Russia' :'N/A, Russia' ,
                                                            'New York, USA' :'New York, United States'   ,'Atlanta, GA' :'Atlanta, United States',
                                                            'Lichfield\t':'Lichfield, England', 'Istanbul via Liverpool': 'Liverpool, England', 'United States':'N/A, United States', 
                                                            'US':'N/A, United States', 'USA':'N/A, United States', 'Москва':'Moscow, Russia',
                                                            'Моscow':'Moscow, Russia', 'Санкт-Петербург':'Saint Petersburg, Russia', 'Питер':'Saint Petersburg, Russia'})
```


```python
users['location'] = users.location.replace({'N/A, Egypt':'Cairo, Egypt', 'N/A, Syria':'Damascus, Syria', 'N/A, France':'Paris, France', 'N/A, Germany':'Berlin, Germany'    ,'N/A, Russia':'Moscow, Russia'  ,'N/A, United States':'Washington, D.C., United States','Washington DC, United States':'Washington, D.C., United States', 'Washington D.C, United States':'Washington, D.C., United States' })
```


```python
location_count = pd.crosstab(index=users['location'],   columns="count").sort_values(by=['count'], ascending=False)
```


```python
#location_count = pd.crosstab(index=users['location'])
```


```python
location_count.reset_index(level=0, inplace=True)

```


```python
#location_count[location_count['location'] != 'МSK']['location'].unique()
```




    array(['N/A, United States', 'Moscow, Russia', 'Saint Petersburg, Russia',
           'New York, United States', 'Atlanta, United States', 'N/A, Russia',
           'Los Angeles, United States', 'Novosibirsk, Russia',
           'Veliky Novgorod, Russia', 'Omsk, Russia', 'N/A, Syria',
           'N/A, Germany', 'Boston, United States', 'Chicago, United States',
           'SPB', 'Cheboksary, Russia', 'Volgograd, Russia',
           'Phoenix, United States', 'Kazan, Russia', 'Yekaterinburg, Russia',
           'Philadelphia, United States', 'Damascus, Syria', 'N/A, France',
           'Washington DC, United States', 'Washington D.C, United States',
           'London, England', 'Nizhny Novgorod, Russia', 'Kiev, Ukraine',
           'N/A, Egypt', 'Houston, United States', 'Texas, United States',
           'Tver, Russia', 'Miami, United States', 'Rostov-on-Don, Russia',
           'Portland', 'Dallas', 'Jacksonville, United States', 'Псков',
           'Сочи', 'Baltimore, United States', 'Вологда', 'Detroit', 'Тула',
           'Newcastle', 'Липецк', 'NYC', 'Nashville', 'Мурманск', 'Colorado',
           'California', 'Cleveland, OH', 'МСК', 'Пермь', 'Красноярск',
           'Houston', 'msk', 'سورية', 'Российская Федерация', 'Брянск',
           'Italia', 'America', 'Выборг', 'San-Francisco', 'New Jersey',
           'Birmingham', 'Київ', 'Miami', 'Калининград', 'Dresden, Sachsen',
           'Новосиб', 'Тула, Россия', 'Kansas, USA', 'Саратов',
           'Новосибирск, Россия', 'РФ', 'Симферополь', 'Madison',
           'Deutschland', 'NH', 'Florida', 'Hollywood', 'Manhattan, NY',
           'St.Petersburg', 'Краснодар', 'россия', 'Alaska', 'CA', 'Воронеж',
           'California, USA', 'Amman', 'омск', 'SF', 'AL',
           'Berlin, Deutschland', 'Beirut', 'Baton Rouge, LA', 'Москва ',
           'Coventry', 'New Orleans, LA', 'Киров', 'Manchester',
           'St Louis, MO', 'MSK', 'MN', 'New Jersey, USA',
           'Волгоград, Россия', 'San Diego, CA', 'Louisville', 'Белгород',
           'United Kingdom', 'Архангельск', 'Россия ', 'Washington D.C',
           'Ростов-на-Дону, Россия', 'Wonderland', 'ny', 'San Francisco',
           'Петрозаводск', 'SPb', 'Memphis, TN', 'Ohio', 'Нижний', 'Orlando',
           'Ostin', 'Pennsylvania', 'NJ', 'Perm, Russia', 'Philadelphia, PA',
           'Курск', 'Кронштадт', 'Richmond, VA', 'Коломна', 'Омск, Россия',
           'Montana', 'Minnesota', 'Minneapolis, MN', 'НН', 'Kuwait',
           'Петроград', 'Тольятти', 'Тула, Тульская область', 'حماة', 'حلب',
           'Сочи, Россия', 'Georgia, USA', 'Georgia', 'ATL',
           'Frankfurt am Main, Deutschland', 'اللاذقية', 'Albuquerque',
           'العراق', 'Ekaterinburg, Russia', 'Düsseldorf, Deutschland',
           'Украина', 'حمص', 'Dallas, Texas', 'Уфа', 'Хабаровск',
           'Columbia, SC', 'спб', 'Челябинск', 'питер', 'мск', 'Ярославль',
           'москва', 'Brooklyn', 'Brooklyn, NY', 'Hamburg, Deutschland',
           'Brussel, België', 'ID', 'Серпухов', 'Jackson', 'Севастополь',
           'Kansas City, MO', 'Italy', 'لبنان', 'Кострома', 'Елец',
           'сжигай толерантный рай,слышишь', 'Иркутск', 'Иваново',
           'Запорожье', 'Житомир', 'piter', 'portland', 'ул. Ленина',
           'Краснодар ', 'Екатеринбург...', 'уфа', 'Екатеринбург ', 'ЕКБ',
           'Донецк, Россия', 'Донецк', 'хогвортс', 'russia', 'Калининград ',
           'сейчас орел', 'Кольский п-в', 'Кингисепп', 'Котлас',
           'moscow city', 'mother America', '♠Питер♠', 'novgorod', 'мой мир',
           'новгород', 'Кемерово', 'nyc', 'новосибирск', '☼Новосибчик☼',
           'ростов-я-тону', 'Калуга, Россия', 'Калуга', 'saint P.',
           'Калининград, Россия', 'Днепр, Украина', 'saint p.', 'Днепр',
           'syria', 'st.petersburg', 'المملكة الأردنية الهاشمية', 'Беларусь',
           'Башкартостан', 'Барнаул, Россия', 'Архангельск, Россия', 'بيروت',
           'st/petersburg', 'temple hills, md', 'Дмитров', 'Артем ', 'Адлер',
           'Ё-бург', 'vladik', 'united states', 'utah', 'usa', 'عمان',
           'Бутово', 'Ватноград', 'Великий Новгород', 'Вильнюс - Москва',
           'us', 'Грозный', 'saint-petersburg', 'ширкино', 'sin city',
           'Вся Россия', 'Воронеж, Россия', 'الأردن', 'الدمام',
           'Волгодонск, Россия', 'الدولة الإسلامية', 'Волгоград, Вася!',
           '★москва', 'مصر', 'Владик ДВФУ', 'Красноярск ', 'Витебск',
           'Самара', 'Я везде', 'екб', 'Тверское подворье', 'Потсдам',
           'Покровское', 'Смоленск', 'Подольск', 'Сочи ', 'los angeles',
           'Перово', 'Спб', 'Пенза', 'ПЕТЕРБУРГ', 'Орел', 'Сраратов',
           'Стамбул', 'Одинцово', 'Одесса', 'Нягань', 'Стокгольм',
           'Новосибирск ', 'Таллин ', 'Таллин, Санкт-Петербург', 'Тамань',
           'Прага', 'Сибирь матушка', 'Сестрорецк, Россия',
           'Россия Санкт-Петербург', 'Санкт-Петербург ', 'С.Петербург',
           'С-Пб', 'Рязань', 'Ростов-на-Дону', 'Ростов-На-Дону',
           'Россия, Москва', 'Санкт-петербург', 'Россия, Казань', 'Саранск',
           'Пушкин', 'Саратов )))', 'Саров', 'Раша', 'Работа))', 'Пятигорск',
           'Северная столица', 'Пхеньян', 'Пушкино',
           'Пушкин, Санкт-Петербург', 'Ташла', 'Томск', 'Красти Бургер ',
           'Новокузнецк, Россия', 'Манила', 'Магадан', 'МСКВА', 'Челны',
           'Люберцы', 'Челябинск ', 'Черемухи', 'Луцк',
           'Чеченская республика, Россия', 'Луганск', 'Луга', 'Чита',
           'Лос-Питербургос', 'СПБГПУ', 'Ярославль ', 'Ярославль, Россия',
           'Ленинград', 'амфетаминовая столица', 'баку', 'днищний дновгород',
           'Кременчуг', 'Мариуполь', 'Чебоксары, Россия', 'Мечта', 'Москва♥',
           'Новгород - СПб', 'Третий Рим', 'Нижний Новогород',
           'Туапсе, Москва', 'Тува', 'Набережные Челны, Россия', 'Мінск',
           'Ульяновск', 'Москоу-сити', 'Москва Златоглавая ', 'Мечтовиль',
           'Москва Белокаменная', 'Хабаровск, Россия', 'Москва - столица',
           'Москва - Самара', 'Москва - Лондон', 'Ханты-Мансийск',
           'Москва (СССР - Россия)', 'ЦАО', 'Моска', 'moscow', '\tAustin',
           'katamandu', 'Krasnoyarsk, Russia', 'Kiel, Schleswig-Holstein',
           'Kansas', 'KN', 'Johnson City, New York', 'Jersey', 'Jackson, MS',
           'Itala, Sicilia', 'Islamic States of America', 'Irkutsk',
           'INDIANAPOLIS, USA', 'I AM A CITIZEN OF THE UNIVERSE',
           'Hessen, Deutschland', 'Guanica zona urbana, PR, USA',
           'Grove City, Ohio', 'Greensboro', 'Green village, OH, USA',
           'Greece', 'Garden City, NY', 'Frankfurt am Main, Hessen',
           'Fowler, California', 'Florida, USA', 'Flint, MI', 'Ferguson, MO',
           'Fattyland', 'Erfurt, Deutschland',
           'Eldorado at Santa Fe, NM, USA', 'El Paso, Texas', 'Krasnoyarsk',
           'Köln, Deutschland', 'jacksonville', 'La Junta, Colorado',
           'Missouri, USA', 'Milwaukee, WI', 'Millville village, OH, USA',
           'Milano, Lombardia', 'Michigan', 'Miami, USA', 'Mesa', 'Menisotta',
           'Memphis', 'Manama, Bahrain', 'Man', 'Magdeburg, Deutschland',
           'Macon, GA', 'MSK SAO', 'Lyon', 'Love Town', 'Louisiana',
           'Los-Angeles', 'Los Gatos, California', 'Los Angeles ',
           'Los Alamos', 'London, UK ', 'Liverpool', 'Liberty City',
           'Lebanon', 'Las Vegas', 'Lafayette, LA', 'Druid Hills, GA',
           'Downtown, Atlanta', 'Douglas, United States', 'Detroit, Michigan',
           'Boston, MA', 'Black America', 'Baltimore',
           'Baldwinsville, New York', 'Az-Zarqa', 'Austin, TX', 'Austin',
           'Aurora, Illinois', 'Atlanta, Georgia', 'Arizona, USA', 'Amerika',
           'All Over Texas', 'Aleppo', 'Albuquerque, NM', 'Adler', 'AZ',
           'ATL, GA', 'ARIZONA', 'AMERICA', '2148', '#РусскийМир',
           ' Santa Barbara, California', ' Milford, Ohio', ' Mexico',
           ' Kansas ', ' East Aurora, New York',
           ' Bloomfield Hills, Michigan', 'Boston, USA',
           'Bremen, Deutschland', 'Brkln', 'City of Cleveland, USA',
           'Destin, Florida', 'Denver, CO', 'Delaware, USA', 'Damascus',
           'Dallas, TX', 'Cromwell', 'Crimea, Russia', 'Cosmopolitanism',
           'Columbus, Ohio', 'Cleve', 'City of San Antonio, TX',
           'City of Phoenix, Arizona', 'Cincinnati, OH', 'Bronx, NY',
           'Cincinnati', 'Chicago ', 'Chester, PA', 'Chelyabinsk, Russia',
           'Chelyaba', 'Charleston, SC', 'Ch', 'Camden, NJ', 'Cairo, Egypt',
           'Buffalo ', 'Brunswick, ME, USA', 'Brookhaven, GA', 'Mn',
           'Mohnton, PA', 'Montgomery', 'Saint-Peterburg', 'U.S.A',
           'Troy, Alabama', 'Tomsk', 'The Big Apple', 'Texas',
           'Tennessee, USA', 'Tallahassee', 'TN', 'THE US',
           'Stuttgart, Deutschland', 'Stonewall, TX', 'Stavropol, Russia',
           'Stanwood city, WA, USA', 'StLouis', ' Albuquerque', 'St.P.',
           'St. Petersburg', 'St-Petersburg', 'St-P', 'South Carolina, USA',
           'Seattle, WA', 'Seattle ', 'Santa Monica', 'San Francisco, CA',
           'San Diego, United States', 'San Diego', 'Salt Lake City',
           'UC Davis', 'UK', 'USA, Atlanta', 'Wisconsin, USA', 'italia',
           'hood', 'garage ', 'dreamland', 'cанкт-петербург',
           'cleveland / ohio', 'brooklyn', 'belgorod', 'arkansas', 'alabama',
           'Zarqa, Jordan', 'ZM', 'Winchester, Virginia', 'USA, FL',
           'Wichita, KS', 'Whitehall, Ohio', 'Weeki Wachee, Florida', 'WA',
           'Volgograd', 'Venice, California', 'Velikiy Novgorod, Russia',
           'Vegas', 'Utah', 'Usa', 'Universe', 'Ufa, Russia',
           'Salem, Massachusetts', 'Saint-P.', 'Montgomery, Ohio', 'Saint-P',
           'Oklahoma', 'Ohio, USA', 'Oakland, CA', 'OH', 'North Port, FL',
           'North Dakota', 'North Carolina', 'Nizhniy Novgorod, Russia',
           'Newport', 'Newhustle', 'Newark, NJ', 'New York City ',
           'New Orleans', 'New Orlean', 'New Haven', 'New Hampshire',
           'New - York', 'Nevada', 'Nebraska, USA', 'NYC ', 'NY City', 'NM',
           'München, Bayern', 'Murmansk, Russia', 'Murica', 'Msk',
           'Moscow-City', 'Oklahoma City', 'Oklahoma, PA', 'Oklahoma, USA',
           'Rancho Rinconada, CA, USA', 'Saint Petersburg',
           'Saarbrücken, Deutschland', 'SPb♥○•°•☆', 'Russian Empire',
           'Russia, Moscow', 'Rostov-na-Donu, Russia', 'Rostock, Deutschland',
           'Riverside', 'Rhode island', 'Rhode Island',
           'Republic of Chechnya, Russia', 'Redwood City, California',
           'Raleigh, North Carolina', 'Old Bridge, New Jersey', 'Queens, NY',
           'Poland', 'Pittsburgh, US', 'Pittsburgh, PA', 'Pittsburgh',
           'Philly', 'Philadelhia', 'Penza', 'Paris, France', 'Paris',
           'Orlando, FL', 'Oliva Pizza & Pasta // Amman', '✴Новгород✴'],
          dtype=object)




```python
most_frequent = location_count[(location_count['count'] > 5) & (location_count['location'] != 'МSK') & (location_count['location']!='SPB')]
```


```python
most_frequent['country'] = [str(x).split(',')[-1].strip() for x in most_frequent['location']]
```

    c:\users\lizda\appdata\local\programs\python\python37-32\lib\site-packages\ipykernel_launcher.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      """Entry point for launching an IPython kernel.
    


```python
#most_frequent.location = most_frequent.location.replace({'N/A, Egypt':'Cairo, Egypt', 'N/A, Syria':'Damascus, Syria', 'N/A, France':'Paris, France', 'N/A, Germany':'Berlin, Germany'    ,'N/A, Russia':'Moscow, Russia'  ,'N/A, United States':'Washington, D.C., United States','Washington DC, United States':'Washington, D.C., United States', 'Washington D.C, United States':'Washington, D.C., United States' })
```

    c:\users\lizda\appdata\local\programs\python\python37-32\lib\site-packages\pandas\core\generic.py:5096: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      self[name] = value
    


```python
most_frequent
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>col_0</th>
      <th>location</th>
      <th>count</th>
      <th>country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Washington, D.C., United States</td>
      <td>871</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Moscow, Russia</td>
      <td>373</td>
      <td>Russia</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Saint Petersburg, Russia</td>
      <td>178</td>
      <td>Russia</td>
    </tr>
    <tr>
      <th>3</th>
      <td>New York, United States</td>
      <td>124</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Atlanta, United States</td>
      <td>89</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Los Angeles, United States</td>
      <td>51</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Damascus, Syria</td>
      <td>41</td>
      <td>Syria</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Novosibirsk, Russia</td>
      <td>38</td>
      <td>Russia</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Veliky Novgorod, Russia</td>
      <td>36</td>
      <td>Russia</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Omsk, Russia</td>
      <td>32</td>
      <td>Russia</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Berlin, Germany</td>
      <td>30</td>
      <td>Germany</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Boston, United States</td>
      <td>24</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Chicago, United States</td>
      <td>20</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Cheboksary, Russia</td>
      <td>17</td>
      <td>Russia</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Volgograd, Russia</td>
      <td>16</td>
      <td>Russia</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Phoenix, United States</td>
      <td>15</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Kazan, Russia</td>
      <td>12</td>
      <td>Russia</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Yekaterinburg, Russia</td>
      <td>11</td>
      <td>Russia</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Paris, France</td>
      <td>11</td>
      <td>France</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Philadelphia, United States</td>
      <td>10</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>22</th>
      <td>London, England</td>
      <td>10</td>
      <td>England</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Cairo, Egypt</td>
      <td>8</td>
      <td>Egypt</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Nizhny Novgorod, Russia</td>
      <td>8</td>
      <td>Russia</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Tver, Russia</td>
      <td>7</td>
      <td>Russia</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Texas, United States</td>
      <td>7</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Kiev, Ukraine</td>
      <td>7</td>
      <td>Ukraine</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Houston, United States</td>
      <td>7</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Miami, United States</td>
      <td>7</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>30</th>
      <td>Rostov-on-Don, Russia</td>
      <td>6</td>
      <td>Russia</td>
    </tr>
  </tbody>
</table>
</div>




```python
countries_cnt = most_frequent.groupby(['country']).sum().sort_values(by='count', ascending = False)
```


```python
countries_cnt.reset_index(level=0, inplace=True)
```


```python
from geopy.geocoders import Nominatim
```


```python
geolocator = Nominatim(user_agent="twitter_bot_analysis")
```


```python
countries_cnt['long'] = [geolocator.geocode(str(x)).longitude for x in countries_cnt['country']]
```


```python
countries_cnt['lat'] = [geolocator.geocode(str(x)).latitude for x in countries_cnt['country']]
```


```python
countries_cnt
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>col_0</th>
      <th>country</th>
      <th>count</th>
      <th>long</th>
      <th>lat</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>United States</td>
      <td>1225</td>
      <td>-100.445882</td>
      <td>39.783730</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Russia</td>
      <td>734</td>
      <td>97.745306</td>
      <td>64.686314</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Syria</td>
      <td>41</td>
      <td>39.049411</td>
      <td>34.640186</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Germany</td>
      <td>30</td>
      <td>10.423447</td>
      <td>51.083420</td>
    </tr>
    <tr>
      <th>4</th>
      <td>France</td>
      <td>11</td>
      <td>1.888334</td>
      <td>46.603354</td>
    </tr>
    <tr>
      <th>5</th>
      <td>England</td>
      <td>10</td>
      <td>-0.540240</td>
      <td>52.795479</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Egypt</td>
      <td>8</td>
      <td>29.267547</td>
      <td>26.254049</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Ukraine</td>
      <td>7</td>
      <td>31.271832</td>
      <td>49.487197</td>
    </tr>
  </tbody>
</table>
</div>




```python
# import the library
import folium

# Make an empty map
m = folium.Map(location=[0,0], zoom_start=2)
 
# I can add marker one by one on the map
for i in range(0,len(countries_cnt)):
   folium.Circle( location=[countries_cnt.iloc[i]['lat'], countries_cnt.iloc[i]['long']],      popup=countries_cnt.iloc[i]['country'] + ' : ' + str(countries_cnt.iloc[i]['count']),
      radius=float(countries_cnt.iloc[i]['count']*1000),      color='crimson',    fill_color='crimson',  fill=True).add_to(m)
 
# Save it as html
m.save('mymap_countries.html')

```


```python
#from geopy import geocoders
#import geocoder
#gn = geocoder.geonames('New York', key='lizdao')

#print( gn.geocode("United States"))
```

    Status code 401 from http://api.geonames.org/searchJSON: ERROR - 401 Client Error: Unauthorized for url: http://api.geonames.org/searchJSON?q=New+York&fuzzy=1.0&username=lizdao&maxRows=1
    


```python
most_frequent['long'] = [geolocator.geocode(str(x)).longitude for x in most_frequent['location']]
most_frequent['lat'] = [geolocator.geocode(str(x)).latitude for x in most_frequent['location']]
```

    c:\users\lizda\appdata\local\programs\python\python37-32\lib\site-packages\ipykernel_launcher.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      """Entry point for launching an IPython kernel.
    c:\users\lizda\appdata\local\programs\python\python37-32\lib\site-packages\ipykernel_launcher.py:2: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      
    


```python
most_frequent
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>col_0</th>
      <th>location</th>
      <th>count</th>
      <th>country</th>
      <th>long</th>
      <th>lat</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Washington, D.C., United States</td>
      <td>871</td>
      <td>United States</td>
      <td>-77.036563</td>
      <td>38.895009</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Moscow, Russia</td>
      <td>373</td>
      <td>Russia</td>
      <td>37.617494</td>
      <td>55.750446</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Saint Petersburg, Russia</td>
      <td>178</td>
      <td>Russia</td>
      <td>30.316229</td>
      <td>59.938732</td>
    </tr>
    <tr>
      <th>3</th>
      <td>New York, United States</td>
      <td>124</td>
      <td>United States</td>
      <td>-73.987156</td>
      <td>40.730862</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Atlanta, United States</td>
      <td>89</td>
      <td>United States</td>
      <td>-84.390185</td>
      <td>33.749099</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Los Angeles, United States</td>
      <td>51</td>
      <td>United States</td>
      <td>-118.242767</td>
      <td>34.053683</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Damascus, Syria</td>
      <td>41</td>
      <td>Syria</td>
      <td>36.309581</td>
      <td>33.513070</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Novosibirsk, Russia</td>
      <td>38</td>
      <td>Russia</td>
      <td>82.923451</td>
      <td>55.028217</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Veliky Novgorod, Russia</td>
      <td>36</td>
      <td>Russia</td>
      <td>31.275786</td>
      <td>58.520986</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Omsk, Russia</td>
      <td>32</td>
      <td>Russia</td>
      <td>73.371529</td>
      <td>54.991375</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Berlin, Germany</td>
      <td>30</td>
      <td>Germany</td>
      <td>13.388860</td>
      <td>52.517037</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Boston, United States</td>
      <td>24</td>
      <td>United States</td>
      <td>-71.058291</td>
      <td>42.360253</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Chicago, United States</td>
      <td>20</td>
      <td>United States</td>
      <td>-87.624421</td>
      <td>41.875562</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Cheboksary, Russia</td>
      <td>17</td>
      <td>Russia</td>
      <td>47.244960</td>
      <td>56.130719</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Volgograd, Russia</td>
      <td>16</td>
      <td>Russia</td>
      <td>44.516804</td>
      <td>48.710678</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Phoenix, United States</td>
      <td>15</td>
      <td>United States</td>
      <td>-112.077346</td>
      <td>33.448587</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Kazan, Russia</td>
      <td>12</td>
      <td>Russia</td>
      <td>49.124227</td>
      <td>55.782355</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Yekaterinburg, Russia</td>
      <td>11</td>
      <td>Russia</td>
      <td>60.608250</td>
      <td>56.839104</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Paris, France</td>
      <td>11</td>
      <td>France</td>
      <td>2.351499</td>
      <td>48.856610</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Philadelphia, United States</td>
      <td>10</td>
      <td>United States</td>
      <td>-75.163575</td>
      <td>39.952415</td>
    </tr>
    <tr>
      <th>22</th>
      <td>London, England</td>
      <td>10</td>
      <td>England</td>
      <td>-0.127647</td>
      <td>51.507322</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Cairo, Egypt</td>
      <td>8</td>
      <td>Egypt</td>
      <td>31.243666</td>
      <td>30.048819</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Nizhny Novgorod, Russia</td>
      <td>8</td>
      <td>Russia</td>
      <td>44.003506</td>
      <td>56.328571</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Tver, Russia</td>
      <td>7</td>
      <td>Russia</td>
      <td>35.920828</td>
      <td>56.858675</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Texas, United States</td>
      <td>7</td>
      <td>United States</td>
      <td>-99.512099</td>
      <td>31.816038</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Kiev, Ukraine</td>
      <td>7</td>
      <td>Ukraine</td>
      <td>30.524104</td>
      <td>50.450064</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Houston, United States</td>
      <td>7</td>
      <td>United States</td>
      <td>-95.367697</td>
      <td>29.758938</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Miami, United States</td>
      <td>7</td>
      <td>United States</td>
      <td>-80.193659</td>
      <td>25.774266</td>
    </tr>
    <tr>
      <th>30</th>
      <td>Rostov-on-Don, Russia</td>
      <td>6</td>
      <td>Russia</td>
      <td>39.716486</td>
      <td>47.224695</td>
    </tr>
  </tbody>
</table>
</div>




```python
#location = geolocator.geocode("United States")
```


```python
#location.longitude
```




    -100.4458825




```python
#print((location.latitude, location.longitude))
```

    (39.7837304, -100.4458825)
    


```python
import sys
sys.version
```




    '3.6.6 (v3.6.6:4cf1f54eb7, Jun 27 2018, 03:37:03) [MSC v.1900 64 bit (AMD64)]'




```python

```

most_frequent.groupby(['country'],as_index = False).sum().pivot('country').fillna(0)



```python
#users['location'] = users['user_reported_location'].str.lower().str.strip().str.replace('[^a-zA-Z0-9,._]','')
```


```python
#users[['user_reported_location','location']] 
```


```python
#pd.crosstab(index=users['location'],   columns="count").sort_values(by=['count'])
```


```python
#russia.user_reported_location = russia.user_reported_location.replace({'Lichfield\t':'Lichfield, England', 'Istanbul via Liverpool': 'Liverpool, England' })
```


```python
# import the library
import folium

# Make an empty map
m = folium.Map(location=[0,0], zoom_start=2)
 
# I can add marker one by one on the map
for i in range(0,len((most_frequent))):
   folium.Circle( location=[most_frequent.iloc[i]['lat'], most_frequent.iloc[i]['long']],      popup=most_frequent.iloc[i]['location'] + ' : ' + str(most_frequent.iloc[i]['count']),
      radius=float(most_frequent.iloc[i]['count']*500),      color='crimson',    fill_color='crimson',  fill=True).add_to(m)
 
# Save it as html
m.save('mymap.html')

```
