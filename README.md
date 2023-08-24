### 1. О приложении ###
**Admingo** - шаблон панели администратора django, в том числе, страницы аутентификации и документации (admindoc), а также включает в себя:  
:small_blue_diamond: Адаптивный дизайн  
:small_blue_diamond: Cветлая/тёмная тема  
:small_blue_diamond: Настройка шаблона  
### 2. Установка ###
1. Установите приложение:
```python
pip install git+https://github.com/khaustiv/admingo.git
```
2. В файл settings.py проекта добавьте приложение в список установленных приложений перед django.contrib.admin:
```python
INSTALLED_APPS = [
    'admingo',
    'django.contrib.admin',
    ...
]
```
### 3. Настройка шаблона ###
Параметры шаблона, доступные для изменения, содержатся в ADMINGO_CUSTOMIZATION:
```python
ADMINGO_CUSTOMIZATION = {
    # Название, отображаемое в боковой панели
    'dashboard_name': 'Админпанель',
    # Заголовок главной страницы сайта администратора
    'dashboard_title': 'Панель администратора',
    # Модель для поиска, поле которого находится в верхней навигационной панели
    'search_model': '',
    # Иконки для приложений в боковой панели. Если не указано, то иконка по умолчанию - круг
    'sidebar_icons': {
        'auth.user': 'person', 
        'auth.group': 'groups',
    },
    # Приложения, которые нужно скрыть в боковой панели и в списке приложений
    'hidden_apps': [],
    # Модели, которые нужно скрыть в боковой панели и в списке приложений
    'hidden_models': [],
    # Порядок приложений и моделей в боковой панели и в списке приложений. 
    # Можно указывать не все, тогда сортировка идёт по алфавиту.
    'apps_order': [],
    # Дополнительные ссылки отображаются на боковой панели в соответствии с
    # указанным приложением, и представляют собой список словарей, где ключём
    # является приложение, а значением - список параметров каждой ссылки:
    #{'приложение': [
    # {'name': 'Ссылка 1', 'admin_url': '/admin/link1/', 'icon': 'circle'},
    # {'name': 'Ссылка 2', 'admin_url': '/admin/link2/', 'icon': 'circle'},
    # ]}
    'extra_links' : [],
}
```
Для настройки шаблона добавьте ADMINGO_CUSTOMIZATION с необходимыми изменениями в файл settings.py проекта.
Для иконок на боковой панели предполагается использование коллекции [Material Symbols](https://fonts.google.com/icons).
Например, для блога ADMINGO_CUSTOMIZATION может иметь следующий вид:
```python
ADMINGO_CUSTOMIZATION = {
    'search_model': 'blog.article',
    'sidebar_icons': {
        'auth.user': 'person', 
        'auth.group': 'groups',
        'blog.article': 'article',
        'blog.tag': 'bookmark',
        'blog.category': 'category',
        'blog.comment': 'chat',
        'manager.feedback': 'rate_review',
        'manager.emailsubscription': 'email',
        'django_celery_results.taskresult': 'task',
    },
    'hidden_models': ['auth.group', 'django_celery_results.groupresult'],
    'apps_order': ['blog', 'blog.article', 'blog.tag', 'blog.category', 'manager', 'django_celery_results', 'auth'],
    'extra_links' : [{'manager': [
                            {'name': 'Документация', 'admin_url': '/admin/doc/', 'icon': 'description'},
                            ],
                    }],
}
```
### 4. Скриншоты ###
#### Страницы ####
![index](https://github.com/khaustiv/admingo/assets/143105312/1e84a392-f4c3-487e-9549-f46b21ce4b6b)
![change_list_sidebar_collapsed](https://github.com/khaustiv/admingo/assets/143105312/0e7dea04-4dcc-4e08-bbed-704ec1045c4b)
![change_form](https://github.com/khaustiv/admingo/assets/143105312/ec1b0c96-3dc2-442a-bc0d-2972cd440cb9)

#### Документация ####
![admindoc](https://github.com/khaustiv/admingo/assets/143105312/b7cd5970-11f3-4bf5-a080-ba43e3cd7f04)

#### Светлая тема ####
![light_theme_index](https://github.com/khaustiv/admingo/assets/143105312/d707070d-9d36-4aed-bdfb-286d6d37a5f3)
![light_theme_change_form](https://github.com/khaustiv/admingo/assets/143105312/dbb968f7-25c2-4937-a3c1-d0280b5e21d2)

#### Аутентификация ####
![login](https://github.com/khaustiv/admingo/assets/143105312/819582e0-97b7-4616-a1e5-806daf783dd3)

#### Мобильная версия ####
![mobile_index](https://github.com/khaustiv/admingo/assets/143105312/a01a183f-a477-4e47-9f66-01a2cc2a00f3)
![mobile_change_form](https://github.com/khaustiv/admingo/assets/143105312/a44261df-54ed-4cf6-8980-4f33557dcc17)

