Исполняемый файл: load_data.py<br>
<br>

-----------------
ТЗ:<br>
Берем список учебных заведений отсюда: https://github.com/Hipo/university-domains-list-api<br>
Обрабатываем:<br>
Разбить учебные заведения по группам – Колледж, Университет и Институт. Под тип заведения добавим колонку. Если не удаётся определить тип – оставляем поле пустым.<br>
Убрать колонки, содержащие ссылки (web_pages и domains).<br>
Загружаем в базу PostgreSQL. Расписание – каждый день в 3 ночи.<br>
Загрузка должна быть инкрементальная, то есть при повторном запуске не затираем таблицу в постгресе транкейтом и перезагружаем. А загружаем только новые записи.<br>
Важно, чтобы код соответствовал бест практисам аирфлоу.<br>
https://www.youtube.com/watch?v=zVzBVpbgw1A<br>
https://airflow.apache.org/docs/apache-airflow/stable/best-practices.html<br>
<br>

-----------------
<br>

<br>


Ниже README из https://github.com/Hipo/university-domains-list-api:<br>

<br>


University Domains and Names API
=================================



### An API and JSON list contains domains, names and countries of most of the universities of the world.


Provides a search endpoint you can search for an autocomplete for university name or/and filter by country.

Feel free to update the list from [university-domains-list](https://github.com/hipo/university-domains-list)



## SEARCH FROM OUR PUBLIC API
-----------------

    http://universities.hipolabs.com
    
    http://universities.hipolabs.com/search?name=middle
    
    http://universities.hipolabs.com/search?name=middle&country=turkey
    

## API Search Endpoint

### Request
    /search?name=Middle


### Response
    [
    {
    web_page: "http://www.meu.edu.jo/",
    country: "Jordan",
    domain: "meu.edu.jo",
    name: "Middle East University"
    },
    {
    web_page: "http://www.odtu.edu.tr/",
    country: "Turkey",
    domain: "odtu.edu.tr",
    name: "Middle East Technical University"
    },
    {
    web_page: "http://www.mtsu.edu/",
    country: "USA",
    domain: "mtsu.edu",
    name: "Middle Tennessee State University"
    },
    {
    web_page: "http://www.mga.edu/",
    country: "USA",
    domain: "mga.edu",
    name: "Middle Georgia State College"
    },
    {
    web_page: "http://www.mdx.ac.uk/",
    country: "United Kingdom",
    domain: "mdx.ac.uk",
    name: "Middlesex University"
    },
    {
    web_page: "http://www.middlebury.edu/",
    country: "USA",
    domain: "middlebury.edu",
    name: "Middlebury College"
    }
    ]

### Request
    /search?name=Middle&country=Turkey


### Response
    [
    {
    web_page: "http://www.odtu.edu.tr/",
    country: "Turkey",
    domain: "odtu.edu.tr",
    name: "Middle East Technical University"
    }
    ]

## Pagination
To paginate requests, we can use the limit and offset parameters. This allows to fetch limited data.

### Request
    /search?name=Middle&limit=1

### Response
    [
    {
    web_page: "http://www.meu.edu.jo/",
    country: "Jordan",
    domain: "meu.edu.jo",
    name: "Middle East University"
    }
    ]

### Request
    /search?name=Middle&offset=1&limit=1

### Response
    [
    {
    web_page: "http://www.odtu.edu.tr/",
    country: "Turkey",
    domain: "odtu.edu.tr",
    name: "Middle East Technical University"
    }
    ]

## API Update Endpoint
If the university dataset changes, the API won't automatically update it. Use this endpoint to force a refresh.

### Request
    /update

### Response
    {
        'status': str,
        'message': str
    }

## Run the Project

- Clone Project 
`git clone https://github.com/Hipo/university-domains-list-api.git`
- Setup and activate your virtual environment
- Install requirements
`pip install -r requirements.txt`
- Run server `python app.py`



## Contribution
Please contribute to this list! We need your support to keep this list up-to-date.
Do not hesitate to fix any wrong data. It is extremely easy. Just open a PR, or create an issue. 


### Created and maintained by [Hipo](http://www.hipolabs.com)
