## Описание проекта

Проект реализует задачу сегментации изображений с использованием архитектуры U-Net . Модель обучается на датасете Covid19 Radiography Database , который содержит рентгеновские изображения легких и соответствующие им маски для выделения областей, связанных с заболеванием. Проект демонстрирует использование библиотек TensorFlow и Keras для создания и обучения модели, а также визуализацию результатов сегментации.
* * *
Загрузка и подготовка данных :
Датасет загружается с платформы Kaggle через библиотеку opendatasets.
Изображения и маски разделяются на обучающую и тестовую выборки.
Выполняется нормализация изображений (пиксели приводятся к диапазону [0, 1]) и масок (значения ограничиваются диапазоном [0, num_classes - 1]).
* * *
Аугментация данных :
Используется библиотека albumentations для увеличения разнообразия обучающего набора (например, повороты, изменения яркости, масштабирования).
* * *
Построение модели U-Net :
Реализовано классическое архитектурное решение U-Net, состоящее из кодировщика (сжатие данных) и декодировщика (восстановление масок).
Кодировщик использует свертки и пулинг для извлечения признаков, а декодировщик восстанавливает детали с помощью транспонированных сверток и латеральных соединений.
* * *
Обучение модели :
Модель обучается на 15 эпохах с использованием функции потерь sparse_categorical_crossentropy и оптимизатора Adam.
Сохраняется только лучшая модель с минимальной ошибкой на проверочной выборке.
* * *
Оценка результатов :
Строится график точности и потерь для анализа производительности модели.
Для тестовой выборки выводятся исходные изображения, оригинальные маски и предсказанные маски для визуальной оценки качества сегментации.
