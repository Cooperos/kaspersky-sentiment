# Kaspersky Setiment

Задача, выполняемая в рамках тестового задания.

### Задача

* Предлагается разработать алгоритм сентимент-анализа для упоминаний компаний на русском языке.
Основная сложность заключается в том, что сентимент необходимо выставлять именно для контекста упоминании компании (бренда), а не общий сентимент упоминания.
* В качестве тестового датасета необходимо использовать приложенный датасет (ru_data_text.xlsx): колонка sentence – предложение-упоминание, колонка object –сущность, относительно которой необходимо рассчитать сентимент, колонка tonality – true сентимент.
* Необходимо добавить описание разработанного подхода.

### Ход решения

1. Загрузка и предобработка данных:

Данные были загружены стандартными средствами Pandas. В качестве предобработки преобразовал тональность в числовые метки, а текст нормализовал, удалил стоп-слова и преобразовал название компаний в метки [COMPANY]

2. Формирование модели:

Были рассмотрены 4 (3 и одна из них с улучшением) модели для выполнения задания: Логистическая регрессия с использованием TF-IDF для векторизации текста, LSTM и ее двунаправленная версии и RuBert.

3. Итоги по работе с моделями:

* Логистическая регрессия показала низкие результаты точности, предположительно из-за малого объема данных.
* LSTM с последовательностями слов также не смогла обеспечить приемлемую точность.
* RuBERT показал лучшие результаты по сравнению с другими моделями, благодаря дообучению с учетом специальных токенов для указания на компании.

Модель RuBERT показала наилучшую производительность и была выбрана для окончательного использования.

### Quick start

1. Клонировать репозиторий `git clone https://github.com/Cooperos/kaspersky-sentiment`
2. Установить зависимости `pip install -r requirements.txt`
3. Запишите переменные окружения в `.env` согласно `env.example`
4. Запустить файл `notebook.ipynb`