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
2. В файле settings.py проекта добавьте приложение в список установленных приложений перед django.contrib.admin:
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
<a href="https://i.ibb.co/n3n5kLD/index.jpg" target="_blank"><img src="https://i.ibb.co/n3n5kLD/index.jpg" height="300px"></a><a href="https://i.ibb.co/D8K7ZWN/change-form.jpg" target="_blank"><img src="https://i.ibb.co/D8K7ZWN/change-form.jpg" height="300px"></a><a href="https://i.ibb.co/SsGbGgV/change-list-sidebar-collapsed.jpg" target="_blank"><img src="https://i.ibb.co/SsGbGgV/change-list-sidebar-collapsed.jpg" height="300px"></a><a href="https://i.ibb.co/zhBMQss/change-list.jpg" target="_blank"><img src="https://i.ibb.co/zhBMQss/change-list.jpg" height="300px"></a>

#### Документация ####
<a href="https://i.ibb.co/1zrVTr2/admindoc.jpg" target="_blank"><img src="https://i.ibb.co/1zrVTr2/admindoc.jpg" height="300px"></a>

#### Светлая тема ####
<a href="https://i.ibb.co/z49L21y/light-theme-index.jpg" target="_blank"><img src="https://i.ibb.co/z49L21y/light-theme-index.jpg" height="300px"></a><a href="https://i.ibb.co/VSvd9BK/light-theme-change-form.jpg" target="_blank"><img src="https://i.ibb.co/VSvd9BK/light-theme-change-form.jpg" height="300px"></a>

#### Аутентификация ####
<a href="https://i.ibb.co/tP6V942/login.jpg" target="_blank"><img src="https://i.ibb.co/tP6V942/login.jpg" height="300px"></a>

#### Мобильная версия ####
<a href="https://i.ibb.co/LYjqfQK/mobile-index.png" target="_blank"><img src="https://i.ibb.co/LYjqfQK/mobile-index.png" height="300px"></a><a href="https://i.ibb.co/SxCfLDQ/mobile-change-form.png" target="_blank"><img src="https://i.ibb.co/SxCfLDQ/mobile-change-form.png" height="300px"></a>
