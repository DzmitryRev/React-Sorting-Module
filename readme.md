Sorter v1.0

Плагин для сортировки.

Возвращает одну! активную кнопку.
Предназначено для сортировки по различным параметрам.

Применение:
Входящие параметры Sorter:

1.  Компонент Sorter принимает callback, принимающий 1 аргумент.
    (Если callback не передан - будет ошибка)
    Предполагается, что в качестве колбэка будет передаваться функция Dispatch
2.  В качестве children компонента Sorter передаем критерии (компонент: "Criterion")
    Если не добавить Criterion - ошибка не сработает, но теряется целесообразность использования данного модуля.
3.  Не обязательной свойство className.

Входящие параметры Criterion:

1.  Компонент Criterion принимает обязательное свойство "name", в который следует указать
    название для кнопки, которое не будет повторяться с полями "name" других Criterion. (Это не тексторвый контент кнопки!)
    Если все же поля name повторятся - сработает ошибка!
2.  В качестве children передается текстовый контент для кнопки.
3.  Необязательное свойство active. Добавляйте его одному из ваших Criterion со значением true, если вы хотите чтобы одна из кнопок
    уже была активна при загрузке приложения.
    Так как модуль предполагает максимально одну активную кнопку, то ЕСЛИ ПЕРЕДАТЬ НЕСКОЛЬКО CRITERION СВОЙСТВА ACTIVE={TRUE} - РАБОТАТЬ
    БУДЕТ ТОЛЬКО ПОСЛЕДНИЙ!
4.  Не обязательное свойство className.
    !!! Criterion должен быть вложен непосредственно в Sorter, иначе Criterion не будет работать.

Рекомендации по обработке ответа:

1.  Создать новый useState
    Example: const [test, setTest] = useState("")
2.  Передаем setTest в Sorter
    <Sorter handlerChange={setTest} className="my-class-name">
    <Criterion name="cheaper" active={true}>cheaper</Criterion>
    <Criterion name="faster">faster</Criterion>
    </Sorter>
3.  Создать useEffect для отслеживания изменения test
    useEffect(() => {
    console.log(test) ----> тут помещаем функцию для обработки наших данных в соответсвии с выбранным фильтром!
    }, [test])

Стилизация:
Рекомендации по легкой стилизации:
Скорее всего ваши кнопки (Criterion) будут иметь одинаковую стилизацию, предлагаю вам один вариант легкой стилизации без лишних классНеймов:

Стиль для контейнера:
.sorter {
...
}

Стиль для критерия:
.sorter>criterion {
...
}
Стиль для последнего критерия:
.sorter>criterion:last-child {
...
}
Стиль для первого критерия:
.sorter>criterion:first-child {
...
}
Стиль для активного критерия:
.sorter>.active{
...
}

Готово!

version 1.1

1.  Сделать проверку свойства active
2.  Задать стилизацию Criterion
3.  Задать стандартный стиль для активного состояния
4.  Тип для диспатча Criterion
5.  Версия для JS
