# newsgroups_dvc

## Оглавление
### [1 Описание проекта](https://https://github.com/PismarovMikhail/newsgroups_dvc/edit/main/README.md)
### [2 Какой кейс решаем](https://https://github.com/PismarovMikhail/newsgroups_dvc/edit/main/README.md)
### [3 Краткая информация о данных](https://github.com/PismarovMikhail/newsgroups_dvc/edit/main/README.md)
### [4 Этапы работы](https://github.com/PismarovMikhail/newsgroups_dvc/edit/main/README.md)
### [5 Результат](https://github.com/PismarovMikhail/newsgroups_dvc/edit/main/README.md)

### 1 Описание проекта
Проект представляет собой создание конвеера для проведения экспериментов с различными наборами параметров и сравнения метрик между собой 
при классификации набора данных 20newsgroups. Чтобы упростить этап оценки, будем использовать только две категории. В качестве инструмента используется dvc.

:arrow_up:[к оглавлению](https://github.com/PismarovMikhail/newsgroups_dvc/tree/main/README.md#Оглавление)

### 2 Какой кейс решаем

**Cоздание конвейера для обработки данных с помощью dvc, а также сохранение, изменение и сравнение конвейеров между собой**

:arrow_up:[к оглавлению](https://github.com/PismarovMikhail/newsgroups_dvc/tree/main/README.md#Оглавление)

### 3 Краткая информация о данных

Этот набор данных представляет собой коллекцию документов группы новостей. Коллекция из 20 групп новостей стала популярным набором данных для экспериментов с текстовыми приложениями методов машинного обучения, такими как классификация текста и кластеризация текста [https://www.kaggle.com/datasets/crawford/20-newsgroups]

Имеется 20 файлов, содержащих по одному документу на каждую группу новостей. В этом наборе данных дубликаты сообщений были удалены, а исходные сообщения содержат всего 18828 сообщений. Каждое сообщение в файле представляет собой текст некоторого документа группы новостей, который был опубликован в этой группе новостей.
Каждое новое сообщение в связанном файле начинается с четырех заголовков:

Группа новостей: alt.newsgroup

Идентификатор_документа: xxxxxx

От: Кот

Тема: Мяу-мяу-мяу

Организация

### Список 20 групп новостей::

comp.graphics

comp.os.ms-windows.misc

comp.sys.ibm.pc.hardware

comp.sys.mac.hardware

comp.windows.x rec.autos

rec.motorcycles

rec.sport.baseball

rec.sport.hockey sci.crypt

sci.electronics

sci.med

sci.space

misc.forsale talk.politics.misc

talk.politics.guns

talk.politics.mideast talk.religion.misc

alt.atheism

soc.religion.christian

:arrow_up:[к оглавлению](https://github.com/PismarovMikhail/newsgroups_dvc/tree/main/README.md#Оглавление)

### 4 Этапы работы

Создание ковеера со следующими этапами работы:

- cбор данных;
- преобразование данных;
- обучение модели;
- gроведение экспериментов с различными наборами параметров и сравнение метрик между собой.

:arrow_up:[к оглавлению](https://github.com/PismarovMikhail/newsgroups_dvc/tree/main/README.md#Оглавление)

### 5 Результат

С помощью dvc **организован конвеер, позволяющий автоматизированно проводить эксперименты с различными моделями машинного обучения с использованием данных, управлять этими экспериментами (редактировать, сохранять и сравнивать между собой)** Итогом экспериментов является обученная модель, которая показывает наилучший результат.

При реализации конвеера были созданы следующие **скрипты**:
- **prepare.py** Coбирает данные и сохраняет их в формате csv (файлы train.csv и test.scv входят в .gitignore) в папке data/prepared.
- **featurize.py** Получает в качестве входных файлы train.csv и test.scv и с помощью TfidfVectorizer, который принимает текстовые данные и выполняет как извлечение функций из пакета слов, преобразует их файлы формата pickle (train.pkl и test.pkl) внутри папки data/features.
- **train.py** По лучает на вход файлы train.pkl и test.pkl, обучает модель (model.pkl) и сохраняет ее в папку data/models
- **evaluate.py** - Оценка качества работы модели. Результато являеются значения записанные в файлах scores.json и plots.json

:arrow_up:[к оглавлению](https://github.com/PismarovMikhail/newsgroups_dvc/tree/main/README.md#Оглавление)
