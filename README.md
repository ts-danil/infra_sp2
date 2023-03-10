### Спринт 15: Контейнеризация проекта "api_yamdb"
### Описание
```
Проект YaMDb собирает отзывы пользователей на произведения.
Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
Произведения делятся на категории, такие как «Книги», «Фильмы», «Музыка». Например, в категории «Книги» могут быть произведения «Винни-Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Жуки» и вторая сюита Баха. Список категорий может быть расширен (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).
Произведению может быть присвоен жанр из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»).
Добавлять произведения, категории и жанры может только администратор.
Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — рейтинг (целое число). На одно произведение пользователь может оставить только один отзыв.
Добавлять отзывы, комментарии и ставить оценки могут только аутентифицированные пользователи.
```
### Технологии в проекте
- [Python 3.7 ](https://www.python.org/downloads/release/python-379/)
- [Django REST framework 3.12](https://www.django-rest-framework.org/community/3.12-announcement/)
- [Simple JWT-аутентификация с реализацией через код подтверждения](https://django-rest-framework-simplejwt.readthedocs.io/en/latest/)
- [PostgreSQL](https://postgrespro.ru/docs/postgresql/12/)
- [Docker](https://docs.docker.com/engine/reference/builder/#from)
- [nginx](https://nginx.org/en/docs/)
- [Gunicorn](https://docs.gunicorn.org/en/stable/)
- [GIT](https://git-scm.com/docs/git)

### Шаблон наполнения env-файла
```
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
```

### Инструкция по запуску
Сборка контейнеров (infra_db_1, infra_web_1, infra_nginx_1) в директории с файлом "docker-compose.yaml":
```
docker-compose up -d --build
```
Выполнение миграций:
```
docker-compose exec web python manage.py migrate
```
Сбор статики:
```
docker-compose exec web python manage.py collectstatic --no-input
```
Для заполнения базы данных из дампа:
```
docker-compose exec web python manage.py loaddata fixtures.json
```
Для создания суперпользователя:
```
docker-compose exec web python manage.py createsuperuser
```
Останавка контейнера:
```
docker-compose down -v
```



### Документация API YaMDb
```
Полная документация к API на странице /redoc
```
### Автор проекта:
- [Данил Цопанов](https://github.com/ts-danil)
