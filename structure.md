git 3309ef44e5c50b53270201077cb1e9b0afb4d45a

---

# Структура приложения

- [Введение](#introduction)
- [Корневая папка](#the-root-directory)
- [Папка приложения](#the-app-directory)
- [Изменения названия неймспейса](#namespacing-your-application)

<a name="introduction"></a>
## Introduction

Дефолтная структура приложения Laravel спроектирована таким образом, чтобы стать удобной отправной точкой и для маленьких, и для больших приложений. И, разумеется, вы можете изменить эту структуру и организовать приложение так, как вам нравится - Laravel не накладывает почти никаких ограничений на то, где именно должен находиться тот или иной класс - лишь бы Composer смог его загрузить.

<a name="the-root-directory"></a>
## Корневая папка

В корне свежеустановленного фреймворка вы можете видеть следующие папки:

`app` - здесь, как вы догадываетесь, располагается собственно ваше приложение. Ниже мы рассмотрим папку подробнее.

`bootstrap` - содержит файлы, которые осуществляют первоначальную загрузку (bootstraping) фреймворка и настраивают автозагрузку классов.

`config` - здесь находятся конфигурационные файлы приложения.

`database` - это папка для файлов миграций БД и "посева" данных 

`public` - является DocumentRoot домена вашего приложения и содержит статические файлы - css, js, изображения и т.п.

`resources` - здесь находятся вьюхи (Views), файлы локализации и, если таковые имеются, рабочие файлы LESS, SASS и js-приложения на фреймворках типа ФтпгдфкОЫ или Ember, которые потом собираются внешним инструментом в папку `public`

`storage` - эта папка должна иметь права для записи в неё извне и в ней Laravel хранит скомпилированные Blade-шаблоны, файлы сессии, файловый кэш и другие сгенерированные файлы, нужные для работы.

`test` - это папка для юнит-тестов

`vendor` - в эту папку Composer устанавливает пакеты, прописанные в composer.json

<a name="the-app-directory"></a>
## Папка приложения

В папке `app` находятся классы вашего laravel-приложения. По умолчанию, эта папка имеет неймспейс `App` и классы в неё автозагружаются согласно [стандарту PRS-4](http://www.php-fig.org/psr/psr-4/). Вы можете сменить это имя при помощи artisan-команды `app:name`.

Внутри находятся три папки: `Console`, `Http` и `Providers`. Первые две папки, как следует из названия, предоставляют API к вашему приложению по протоколам CLI (командная строка) и HTTP (работа через браузер). В `Console` находятся классы artisan-команд, а в `Http` - контроллеры, фильтры и реквесты, т.е. классы валидации пользовательского ввода. Такой подход должен подтолкнуть новичков к отходу от общепринятого, но вредного подхода писать весь код в контроллерах, и абстрагировать логику приложения от метода обращения к нему.

> **Примечание:** В папке `app` можно генерировать соответствующие классы командами `make:controller`, `make:filter`, `make:request`, `make:console` и `make:provider`.

<a name="namespacing-your-application"></a>
## Изменения названия неймспейса

Как сказано выше, по умолчанию неймспейс, в котором располагается приложение Laravel называется `App`. Вы можете сменить его соответствующей командой:

	php artisan app:name SocialNet

Во всех файлах классов в папке `app` название корневого неймспейса будет изменено на `SocialNet`