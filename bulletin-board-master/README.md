# sf_e7

Учебный проект SkillFactory.

Запущен тут - http://94.103.94.54/ (Ну точнее будет запущен после проверки задания E6, когда освободится сервер)

Для того, что бы развернуть проект, нужно выполнить следующее:

-установить docker и docker compose

-git clone https://github.com/2100992/sf_e7.git

-cd sf_e7

-docker-compose build

-docker-compose up -d

## Небольшое отступление
Временно отключил кеширование, так как с ним тяжело тестировать добавление контента. Вообще странно он работает. Надо разбираться отдельно.

### Описание
0. Отображение всех объявлений: `/api/posts/` (Ответ - JSON со списком всех объявлений со статистикой и тегами)  
        Ну или `/posts/` для web интерфейса

        Можно сделать некоторую фильтрацию по объявлениям. Например:
        - /posts/?slug=car-sale
        - /api/posts/?slug=car-sale
        Или воспользоваться search из Navbar (только slug)

1. Добавление объявления с помощью POST запроса:  `/api/posts/`  
        Обрабатываются поля 'title', 'text', 'user_id', 'tags'  
        Поле 'slug' формируется из 'title'  
        Поле 'short_text' формируется из 'text'  
        Если 'user_id' пустой, подчтавляем 'anonimous'  
        Поле 'created_date' формируется автоматически  
        Если полe 'tags' не пустое, разбиваем на отдельные слова и сохраняем теги  

        Ну или всё это добавить чере web форму `/post/`


2. Получение детальной информации по объявлению по ID (GET запрос): `/api/posts/<_id>/`  
        JSON готовится вместе с комментариями и тегами  

        Ну или. : `/posts/<_id>/`  

3. Добавление тега к существующему объявлению через POST: `/api/tag/<_id>/` (_id - это ID обьявления)  
        Основное поле - 'tag'  
        Если 'user_id' пустой, подставляем 'anonimous'  
        Поле 'created_date' формируется автоматически  

4. Добавление комментария с помощью POST: `/api/posts/<_id>/`  
        (_id - это ID обьявления)  
        Обрабатываются поля 'title', 'text',  
        Если 'user_id' пустой, подставляем 'anonimous'  
        Поле 'created_date' формируется автоматически  

5. Статистика объявления: `/api/statistics/<_id>/`  



### Задание:

    - добавление объявления (возможно с тегами и комментариями) с помощью POST запроса к серверу;  
    - получение существующего объявления (с тегами и комментариями) по ID с помощью GET запроса к серверу;  
    - добавление тега к существующему объявлению с помощью POST запроса к серверу;
    - добавление комментария к существующему объявлению с помощью POST запроса к серверу;
    - статистика для данного объявления: сколько у него тегов и комментариев с помощью GET запроса к серверу.
# bulletin-board-master