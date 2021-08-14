
## Задание с использованием Postman и Charles proxy

<br><a href="https://github.com/Evergaarden/charles_proxy/blob/main/Charles_breakpoint%26rewrite_settings.xml">Charles_breakpoint&rewrite_settings.xml</a> - настройки  

<br><a href="https://github.com/Evergaarden/charles_proxy/blob/main/Charles_session_with_breakpoints%26rewrite.chls">Charles_session_with_breakpoints&rewrite.chls</a> - сохраненная сессия с запросами

<br><a href="https://github.com/Evergaarden/charles_proxy/blob/main/Charles_postman_collection.json">Charles_postman_collection.json</a> - коллекция запросов Postman, которая использовалась для подмены трафика 

<br> **Список задач:**

#### `Ex_0:` Сфокусироваться на ниже перечисленных запросах

Protocol: http
IP: 162.55.220.72
Port: 5005



#### `Ex_1:` Подменить url в Charles чтобы в запросе ушло имя которые вы вписали в Postman, а вернулось то, которое вы подставили в Charles

<br> **Request:**
 <br> Method: GET
 <br> EndPoint: /get_method
 <br> Request url params: 
 
 ```
 ?name=str&age=int
 ```

<br>**Response:**
<br>Array
```
["str", "str"]
```



#### `Ex_2:` Подменить body в Charles так чтобы в запросе ушла salary которую вы вписали в Postman, а в u_salary_1_5_year цифра вернулась меньше оригинальной из запроса

<br>**Request:**
<br>Method: POST
<br>EndPoint: /user_info_3
<br>Request form data: 

    name: str
    age: int
    salary: int

**Response:** 
<br>JSON

          {"name": "name",
          "age": age,
          "salary": salary,
          "family": {"children": [["Alex", 24], ["Kate", 12]],
          "u_salary_1_5_year": salary * 4}}
          


#### `Ex_3:` Подменить параметры запроса в Charles так, чтобы в Postman пришел ответ где другое name, daily_food > weight из запроса, а daily_sleep < weight из запроса

<br>**Request:**
<br>Method: GET
<br>EndPoint: /object_info_1
<br>Request url params: 
 
    ?name=str&age=int&weight=int

**Response:** 
<br>JSON

          {"name": "name",
          "age": age,
          "daily_food": weight * 0.012,
          "daily_sleep": weight * 2.5}



#### `Ex_4:` Сделать через Charles так, чтобы сервер вернул 500 ошибку

<br>**Request:**
<br>Method: GET
<br>EndPoint: /object_info_3
<br>Request url params: 
 
    name: str
    age: int
    salary: int

**Response:**
<br>JSON

         {'name': name,
          'age': age,
          'salary': salary,
          'family': {'children': [['Alex', 24], ['Kate', 12]],
                     'pets': {'cat':{'name':'Sunny',
                                     'age': 3},
                              'dog':{'name':'Luky',
                                     'age': 4}},
                     'u_salary_1_5_year': salary * 4}
          }



#### `Ex_5:` Сделать через Charles так, чтобы сервер вернул 405 ошибку

<br>**Request:**
<br>Method: GET
<br>EndPoint: /object_info_4
<br>Request url params: 

    name: str
    age: int
    salary: int

**Response:**
<br>JSON

          {'name': name,
          'age': int(age),
          'salary': [salary, str(salary * 2), str(salary * 3)]}



#### `Ex_6:` Сделать через Charles так, чтобы в Postman вернулся ответ, в котором qa_salary_after_1.5_year переименовано в qa_salary_after_1.5_month

**Request:**
<br>Method: POST
<br>EndPoint: /user_info_2
<br>Request form data: 

    name: str
    age: int
    salary: int

**Response:**
<br>JSON

          {'start_qa_salary': salary,
          'qa_salary_after_6_months': salary * 2,
          'qa_salary_after_12_months': salary * 2.7,
          'qa_salary_after_1.5_year': salary * 3.3,
          'qa_salary_after_3.5_years': salary * 3.8,
          'person': {'u_name': [user_name, salary, age],
                     'u_age': age,
                     'u_salary_5_years': salary * 4.2}}


