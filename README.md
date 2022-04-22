# RNN-vs-CNN

## Ведение

Этот небольшой эксперемент выполнясня мной в качаестве решения тестовой задачи для поступления на базовые кафедры МФТИ ИППИ РАН и ВЦ РАН.
В статье "Quasi-Recurrent Neural Networks" (https://arxiv.org/abs/1611.01576) рассматривалась новая архитектура нейронной сети для решения задач NLP. В статье удтвержданось, что новая модель обучается быстрее страндартных LSTM и показывает аналогичные результаты. Я решил это проверить. Кроме того в эксперимент я включил обычные RNN и CNN. При выполнении задачи частично использовался код семинара по RNN образовательного поекта Deep Learning School (https://www.dlschool.org).

## Эксперимент

В эксперименте я сравнивал модели по времени обучения и точности классификации на датасете ag_news от HuggingFace. Он состоит из небольших газетных статей, новости в которых делятся на четыре класса: "World, Sports, Business, Sci/Tech".

### CNN

<img src="https://user-images.githubusercontent.com/77685420/164813999-ac0e9282-9a68-4ca5-a101-8d9d0d880818.png" width="560" height="360">
<img src="https://user-images.githubusercontent.com/77685420/164814015-544dd15b-4f88-4c72-8b12-082bf9dff875.png" width="560" height="360">

На графиках видно, что после пятой эпохи сеть начала переобучаться, поэтому для итоговых результатов были взяты результаты модели на пятой эпохе.


### LSTM

<img src="https://user-images.githubusercontent.com/77685420/164814958-3ccc55fb-2333-4070-85fe-267ddcd9e842.png" width="560" height="360">
<img src="https://user-images.githubusercontent.com/77685420/164815008-c1487e5e-58de-4708-9cf4-c034e4608e9d.png" width="560" height="360">

### RNN

<img src="https://user-images.githubusercontent.com/77685420/164815055-4556d051-ceed-4fc6-807f-b4dd3070d11c.png" width="560" height="360">
<img src="https://user-images.githubusercontent.com/77685420/164815066-67737273-6b39-4cad-afbd-55a3725a92d5.png" width="560" height="360">

На графиках видно, что сеть не смогла обучиться, предположительно из-зи затухания градиента.

### QRNN

К сожалению, не получилось воспользоваться библиотекой, предоствляемой авторорами статьи.

## Результаты

![image](https://user-images.githubusercontent.com/77685420/164815158-3b9c0aa6-904a-4b6b-8180-ea37b9dfa102.png)

Результаты показывают, что CNN тоже может хорошо решать некоторые задачи с последовательным входом, а так же быстрее обучается. Действительно, даже одно (определённое) слово в статье помогает достаточно точно определить её тематику, а его взаимоствязь с другими уде не так важна. Однако, не стоит забывать, что так можно рассуждать лишь в некоторых задачах, и LSTM остаётся основной архитектурой для решегия задач NLP.
