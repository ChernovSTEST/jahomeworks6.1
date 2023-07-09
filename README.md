[![Build status](https://ci.appveyor.com/api/projects/status/aoua188kddmu590w?svg=true)](https://ci.appveyor.com/project/ChernovSTEST/jahomeworks6-1)

# Домашнее задание к занятию «2.4. BDD»

В качестве результата пришлите ссылки на ваши GitHub-проекты в личном кабинете студента на сайте [netology.ru](https://netology.ru).

Все задачи этого занятия нужно делать **в разных репозиториях**.

**Важно**: если у вас что-то не получилось, то оформляйте issue [по установленным правилам](../report-requirements.md).

**Важно**: не делайте ДЗ всех занятий в одном репозитории. Иначе вам потом придётся достаточно сложно подключать системы Continuous integration.

## Как сдавать задачи

1. Инициализируйте на своём компьютере пустой Git-репозиторий.
1. Добавьте в него готовый файл [.gitignore](../.gitignore).
1. Добавьте в этот же каталог код ваших автотестов.
1. Сделайте необходимые коммиты.
1. Добавьте в каталог `artifacts` целевой сервис (`app-ibank-build-for-testers.jar`).
1. Создайте публичный репозиторий на GitHub и свяжите свой локальный репозиторий с удалённым.
1. Сделайте пуш — удостоверьтесь, что ваш код появился на GitHub.
1. Удостоверьтесь, что в AppVeyor сборка выполняется: запускается тестируемый сервис и тесты. При отсутствии багов в сервисе сборка должна быть зелёной.
1. Поставьте бейджик сборки вашего проекта в файл README.md.
1. Ссылку на ваш проект отправьте в личном кабинете на сайте [netology.ru](https://netology.ru).
1. Задачи, отмеченные как необязательные, можно не сдавать, это не повлияет на получение зачёта.
1. Если вы обнаружили подозрительное поведение SUT, похожее на баг, создайте описание в issue на GitHub. [Придерживайтесь схемы при описании](../report-requirements.md).
1. Если в проекте реализован тест или тесты, направленные на поиск описанных в issues багов тестируемого сервиса, то такие тесты будут падать до исправления багов сервиса, сборка в AppVeyor будет красной.

## Настройка CI

Настройка CI осуществляется аналогично предыдущему заданию. Поскольку у вас и так специальная тестовая сборка, то ничего в самом сервисе делать не нужно.

## Задача №1: Page Object's

Вам необходимо добить тестирование функции перевода с карты на карту. Разработчики пока реализовали возможность перевода только между своими картами, но уже хотят, чтобы вы всё протестировали.

Для этого они не поленились и захардкодили вам целого одного пользователя:
```
* login: 'vasya'
* password: 'qwerty123'
* verification code (hardcoded): '12345'
* cards:
    * first:
        * number: '5559 0000 0000 0001'
        * balance: 10 000 RUB
    * second:
        * number: '5559 0000 0000 0002'
        * balance: 10 000 RUB
```

После логина, который уже мы сделали на лекции, вы получите список карт:

![](pic/cards.png)

Нажав на кнопку «Пополнить», вы перейдёте на страницу перевода средств:

![](pic/transfer.png)

При успешном переводе вы вернётесь назад на страницу со списком карт.

Это ключевой кейс, который нужно протестировать.

Нужно, чтобы вы через Page Object's добавили доменные методы:
* перевода с определённой карты на другую карту энной суммы,
* проверки баланса по карте со страницы списка карт.

**Вы можете познакомиться с некоторыми подсказками [по реализации этой задачи](balance.md)**.

P.S. Чтобы вам было не скучно, мы добавили порядком багов, поэтому как минимум один issue в GitHub у вас должен быть 😈

<details>
    <summary>Подсказка</summary>

    Обратите внимание на то, что ваши тесты должны проходить целиком, то есть весь набор тестов. Мы, как всегда, заложили там небольшую ловушку, чтобы вам не было скучно 😈
    
    Не закладывайтесь на то, что на картах для каждого теста всегда одна и та же фиксированная сумма, подумайте, как работать с SUT так, чтобы не приходилось её перезапускать для каждого теста.
</details>