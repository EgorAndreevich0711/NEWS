# skillfactory_News_Portal
В нём должно быть? </br>

## Модель Author</br>
Модель, содержащая объекты всех авторов.</br>
Имеет следующие поля:</br>
- cвязь «один к одному» с встроенной моделью пользователей User;</br>
- рейтинг пользователя. Ниже будет дано описание того, как этот рейтинг можно посчитать.</br>

## Модель Category</br>
Категории новостей/статей — темы, которые они отражают (спорт, политика, образование и т. д.). </br>
Имеет единственное поле: название категории.</br>
Поле должно быть уникальным (в определении поля необходимо написать параметр unique = True).</br>

## Модель Post</br>
Эта модель должна содержать в себе статьи и новости, которые создают пользователи. Каждый объект может иметь одну или несколько категорий.</br>
Соответственно, модель должна включать следующие поля:</br>
- связь «один ко многим» с моделью Author;</br>
- поле с выбором — «статья» или «новость»;</br>
- автоматически добавляемая дата и время создания;</br>
- связь «многие ко многим» с моделью Category (с дополнительной моделью PostCategory);</br>
- заголовок статьи/новости;</br>
- текст статьи/новости;</br>
- рейтинг статьи/новости.</br>

## Модель PostCategory</br>
Промежуточная модель для связи «многие ко многим»:</br>
- связь «один ко многим» с моделью Post;</br>
- связь «один ко многим» с моделью Category.</br>

## Модель Comment</br>
Под каждой новостью/статьёй можно оставлять комментарии, поэтому необходимо организовать их способ хранения тоже.</br>
Модель будет иметь следующие поля:</br>
- связь «один ко многим» с моделью Post;</br>
- связь «один ко многим» со встроенной моделью User (комментарии может оставить любой пользователь, необязательно автор);</br>
- текст комментария;</br>
- дата и время создания комментария;</br>
- рейтинг комментария.</br>
***
Эти модели должны также реализовать методы:</br>

## - like() ,</br> - dislike(),</br> - preview(),</br> - [update_rating() ](#anchor1)

Методы like() и dislike() в моделях Comment и Post, которые увеличивают/уменьшают рейтинг на единицу.</br>
Метод preview() модели Post, который возвращает начало статьи (предварительный просмотр) длиной 124 символа и добавляет многоточие в конце.</br>
Метод update_rating() модели Author, который обновляет рейтинг пользователя, переданный в аргумент этого метода.</br>
Он состоит из следующего:
<a id='anchor1'>
- суммарный рейтинг каждой статьи автора умножается на 3;</br>
- суммарный рейтинг всех комментариев автора;</br>
- суммарный рейтинг всех комментариев к статьям автора.</br>
</a>

##  Подготовить файл, в котором написать список всех команд, запускаемых в Django shell.</br>

Сделать в консоли Django?</br>

1. Создать двух пользователей (с помощью метода User.objects.create_user('username')).</br>
2. Создать два объекта модели Author, связанные с пользователями.</br>
3. Добавить 4 категории в модель Category.</br>
4. Добавить 2 статьи и 1 новость.</br>
5. Присвоить им категории (как минимум в одной статье/новости должно быть не меньше 2 категорий).</br>
6. Создать как минимум 4 комментария к разным объектам модели Post (в каждом объекте должен быть как минимум один комментарий).</br>
7. Применяя функции like() и dislike() к статьям/новостям и комментариям, скорректировать рейтинги этих объектов.</br>
8. Обновить рейтинги пользователей.</br>
9. Вывести username и рейтинг лучшего пользователя (применяя сортировку и возвращая поля первого объекта).</br>
10. Вывести дату добавления, username автора, рейтинг, заголовок и превью лучшей статьи, основываясь на лайках/дислайках к этой статье.</br>
11. Вывести все комментарии (дата, пользователь, рейтинг, текст) к этой статье.</br>
