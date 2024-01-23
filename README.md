# newsgroups_dvc

## Оглавление
### [1 Описание проекта](https://https://github.com/PismarovMikhail/newsgroups_dvc/edit/main/README.md)
### [2 Какой кейс решаем](https://https://github.com/PismarovMikhail/newsgroups_dvc/edit/main/README.md)
### [3 Краткая информация о данных](https://github.com/PismarovMikhail/newsgroups_dvc/edit/main/README.md)
### [4 Этапы работы](https://github.com/PismarovMikhail/newsgroups_dvc/edit/main/README.md)
### [5 Результат](https://github.com/PismarovMikhail/newsgroups_dvc/edit/main/README.md)

### 1 Описание проекта
Проект представляет собой создание конвеера для проведения экспериментов с различными наборами параметров и сравнения метрик между собой для набора данных из задачи «Titanic disaster». В качестве инструмента используется dvc.

:arrow_up:[к оглавлению](https://github.com/PismarovMikhail/newsgroups_dvc/tree/main/README.md#Оглавление)

### 2 Какой кейс решаем

**Cоздание конвейера для обработки данных с помощью dvc, а также сохранение, изменение и сравнение конвейеров между собой**

:arrow_up:[к оглавлению](https://github.com/PismarovMikhail/newsgroups_dvc/tree/main/README.md#Оглавление)

### 3 Краткая информация о данных

Данные представляют собой cырые данные в формате csv, тренировочный и тестовый наборы данных из задачи «Titanic disaster» с сайта https://www.kaggle.com/c/titanic/data

Датасет содержит обычные для реальных проектов проблемы с данными: пропущенные значения, текстовые значения признаков, которые не умеют обрабатывать большиство моделей машинного обучения;
выбросы, искажающие общую статистику.

:arrow_up:[к оглавлению](https://github.com/PismarovMikhail/newsgroups_dvc/tree/main/README.md#Оглавление)

### 4 Этапы работы

- Создание конвейера для обработки данных.
- Обучение модели с включением этого этапа в общий конвейер.
- Проведение экспериментов с различными наборами параметров и сравнение метрик между собой.

:arrow_up:[к оглавлению](https://github.com/PismarovMikhail/newsgroups_dvc/tree/main/README.md#Оглавление)

### 5 Результат

С помощью dvc **организован конвеер, позволяющий автоматизированно проводить эксперименты с различными моделями машинного обучения с использованием данных, управлять этими экспериментами (редактировать, сохранять и сравнивать между собой)** Итогом экспериментов является обученная модель, которая показывает наилучший результат.

При реализации конвеера были созданы следующие **скрипты**:
- **get_features.py** Получает на вход имя csv файла, содержащего сырые данные. Читает построчно содержание этого файла и разделяет каждую строку на отдельные токены, используя разделитель «.csv», при этом учитывается, что в поле «Name» может находиться запятая, например, в значении «Braund, Mr. Owen Harris», эту запятую необходимо обрабатывать отдельно, так как в данном случае она не разделяет значения;
Признаки Survived, Pclass, Sex, Age записывает в новый csv файл в папку stage1.
- **fill_na.py** Получает в качестве входного файла csv файл stage1/train.csv. Для признака Age вычисляет среднее значение и заполняет отсутствующие значения признака Age этими средними значениями. Записывает все признаки, в том числе преобразованный признак Age, в новый файл stage2/train.csv.
- **change_text_to_numeric.py** Считывает входной файл stage2/train.csv. Преобразует признак Sex из строкового в числовой, меняя значение «male» на «1», а «female» на «0». Записывает результат в файл stage3/train.csv.
- **train_test_split.py** Скрипт, разделяющий датасет на тренировочные и тестовые данные.
- **dt.py** Скрипт для обучения модели. Принимает два параметра: название файла pickle для сохранения модели, датасет для обучения модели.Этот скрипт создает модель машинного обучения с использованием библиотеки sklearn. В данном примере это классификатор, основанный на модели дерева принятия решений (DecisionTreeClassifier). В качестве параметров для работы модели передаем seed и max_depth, которые сохранены в файле params.yaml и используются для инициализации гиперпараметров random_state и max_depth в модели:
- **evaluate.py** - Оценка качества работы модели.

:arrow_up:[к оглавлению](https://github.com/PismarovMikhail/newsgroups_dvc/tree/main/README.md#Оглавление)
