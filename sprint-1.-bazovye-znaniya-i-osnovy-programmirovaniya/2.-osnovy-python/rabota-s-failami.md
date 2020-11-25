# Работа с файлами

### Чтение всего файла

Для начала нам понадобится файл с несколькими строками текста. Пусть это будет текстовый файл с текстом-заполнителем "lorem ipsum".

Следующая программа открывает этот файл, читает его и выводит содержимое на экран

```python
with open('file.txt') as file_object:
    contents = file_object.read()

print(contents)
```

Начнем с функции open\(\). Чтобы выполнить любые операции с файлом - даже просто вывести его содержимое, - сначала необходимо открыть файл. Функция open\(\) получает один аргумент: имя открываемого файла. Python ищет файл с указанным именем в каталоге, в котором находится файл текущей программы. В данном примере выполняется программа main.py, поэтому Python ищет файл file.txt в каталоге, в котором храниться main.py.

Функция open\(\) возвращает объект, представляющий файл. В данном случае open\('file.txt'\) возвращает объект, представляющий файл file.txt. Python сохраняет этот объект в переменной file\_object, с которым мы будем работать позднее в программе.

Конструкция с ключевым словом with закрывает файл после того, как надобность в нем отпадает. Обратите внимание: в этой программе есть вызов open\(\), но нет вызова close\(\). Файлы можно открывать и закрывать явными вызовами open\(\) и close\(\); но если из-за ошибки в программе команда close\(\) останется невыполненной, то файл не будет закрыт. На первый взгляд это не страшно, но некорректное закрытие файлов может привести к потере или порче данных. А если функция close\(\) будет вызвана слишком рано, программа попытается работать с закрытым \(то есть недоступным\) файлом, что приведет к новым ошибкам. Не всегда можно заранее определить, когда нужно закрывать файл, но с приведенной конструкцией Python сделает это за вас. Вам остается лишь открыть файл и работать с ним так, как требуется, надеясь на то, что Python закроет его автоматически при завершении блока with.

После того, как в программе появится объект, представляющий файл file.txt, во второй строке программы используется функция read\(\), которая читает всё содержимое файла и сохраняет его в одной длинной строке в переменной contents. При выводе значения contents на экране появляется всё содержимое файла

```text
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce urna dolor, hendrerit at rhoncus id, pretium vel libero. Proin tristique viverra lectus, hendrerit egestas orci dapibus sed. Aliquam ac odio sit amet justo imperdiet porttitor. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia curae; Sed molestie vulputate ante sit amet ultricies. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Vestibulum non odio sed augue condimentum commodo sit amet ac justo.

Proin mi libero, commodo vel mollis in, mattis eu purus. Integer eu sapien sit amet libero sagittis mollis. Maecenas interdum sodales turpis, rhoncus malesuada sem suscipit vel. Cras ut molestie magna. Pellentesque ac diam nec diam fringilla gravida id et risus. Pellentesque semper massa mauris, quis volutpat ex aliquam non. Mauris ornare dolor eget auctor luctus. Duis condimentum tempor molestie. Proin non nibh gravida magna vestibulum commodo id ut magna. Phasellus interdum est nec faucibus ultrices.

```

Единственное различие между выводом и исходным файлом - лишняя пустая строка в конце вывода. Откуда она взялась? Функция read\(\) возвращает ее при чтении, если достигнут конец файла. Если вы хотите удалить лишнюю пустую строку, включите вызов функции rstrip\(\) в вызове функции print\(\)

```python
with open('file.txt') as file_object:
    contents = file_object.read()

print(contents.rstrip())
```

Функция rstrip\(\) удаляет все пропуски в конце строки.

### Пути к файлам

Если передать функции open\(\)

