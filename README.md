# Парсер сообщений из дискуссий группы "Я донор!" в ВК
## Информация:
Паблик ВКонтакте "Я Донор!" удалил все обсуждения (топики, дискуссии). В связи с этим многие пользователи начали жаловаться, что использовали эти обсуждения в качестве базы знаний.
## Задача:
Заказчиком была поставлена задача сохранить сообщения из этих обсуждений.
## Исследование задачи, поиск решения:
* Заказчиком было предложено спарсить поисковую выдачу, но этот вариант не подошел, т.к. сообщения в поисковой выдаче "обрезались", не указано время сообщения, имя автора.
* Были рассмотрены следующие варианты решения задачи:
    * Специальные архивные сервисы (Wayback Machine и подобные);
    * Кэшированные страницы поисковиков (Google, Yandex)
* Специальные архивные сервисы были исключены, т.к. из 3560 страниц всех обсуждений было доступно всего 17;
* В качестве решения задачи был выбран кэш страниц в поисковике Google, т.к. в Яндексе сохраненные страницы не были обнаружены;

## Использование выбранного сервиса, ход решения:
* Чтобы получить доступ к кэшированной версии страницы, необходимо использовать следующий формат запроса "http://webcache.googleusercontent.com/search?q=cache:http://example.com/", где "http://example.com/" - адрес необходимой нам страницы. Если страница отсутствует в кэше, то загружается страница с ошибкой 404;
* Для формирования списка ссылок на каждую дискуссию была найдена сохраненная копия страницы со списком всех обсуждений и ссылками;
* Для навигации по страницам обсуждения задается параметр `?offset=`. В качестве значения задается число сообщений на странице. Так как на странице размещается 20 сообщений, то это значение кратно 20;
* Решение сохранено в ноутбуке `parser_list_of_discussions.ipynb`

## Анализ результатов
Все страницы обсуждений сохранить не удалось из-за того, что на момент решения задачи многие страницы из кэша были удалены. Тем не менее в результате проведенной работы было сохранено 2618 сообщений.