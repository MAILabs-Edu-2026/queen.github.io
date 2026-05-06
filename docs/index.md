---
layout: default
title: Home
nav_order: 1
---

# Queen

**Queen** — полный по Тьюрингу ленивый функциональный язык с ML-подобным синтаксисом, разработанный командой группы М8О-207БВ-24 Queen Anne's Revenge.

## Возможности языка

* [x] **Именованные переменные:** `let x = 1 in x`.
* [x] **Рекурсия:** `let rec fact = \n -> ... in fact 5`.
* [x] **Ленивые вычисления:** аргументы, `let` и элементы списков вычисляются при первом обращении.
* [x] **Функции:** лямбды `\x -> x + 1`, много аргументов через каррирование.
* [x] **Замыкания:** функции сохраняют окружение создания.
* [x] **Списки:** `nil`, `cons(h, t)`, `[1; 2; 3]`, `[1 .. 5]`.
* [x] **Стандартная библиотека списков:** `range`, `length`, `map`, `filter`, `fold`, `append`.
* [x] **Файловый I/O:** `readFile "path"`, `writeFile "path" content`.
* [x] **Консольный I/O:** `print expr`, `readLine`.
* [x] **Кортежи:** `(a, b)`, `fst`, `snd`, `let (a, b) = ...`.
* [x] **Условия и логика:** `if ... then ... else ...`, `&&`, `||`, `!`.
* [x] **Сопоставление списков:** `match lst with | nil -> ... | cons(h, t) -> ...`.
* [x] **Оператор конвейера:** `[1 .. 3] |> map (\x -> x * 2)`.
* [x] **Расширение VS Code:** подсветка синтаксиса для `.qx`.

## Запуск

Проект использует .NET, поэтому команды одинаково работают на всех платформах (Windows, macOS, Linux). Убедитесь, что у вас установлен **.NET 10.0 SDK**.

Затем клонируйте репозиторий и перейдите в него:
```bash
git clone https://github.com/MAILabs-Edu-2026/funcpro-coursework-queen-anne-s-revenge.git
cd funcpro-coursework-queen-anne-s-revenge/
```

Для запуска скриптов из исходников:

```bash
dotnet build queen.slnx
dotnet run --project src/queen/queen.fsproj -- run examples/factorial.qx
```

### Установка как .NET Tool глобально

Чтобы команда `queen` была доступна в системе в любом терминале, соберите проект и установите его как инструмент:

```bash
dotnet pack queen.slnx
dotnet tool install --global --add-source ./nupkg queen
```

После установки:

```bash
queen run examples/factorial.qx
queen help
```

## Пример

```queen
let rec fact = \x ->
    if x == 0 then 1
    else x * (fact (x - 1))
in fact 6
```

Результат:

```text
720
```

## Документация

* [docs](docs/index.md) — документация к языку.
* [AI.md](AI.md) — как использовался ИИ.
* [ai_logs.md](ai_logs.md) — краткие логи взаимодействия с ИИ.

ИИ использовался как вспомогательный инструмент: для идей, черновых подсказок и поиска ошибок. Итоговые решения, код и правки проверялись авторами.

## Авторы

| Имя | Роль в проекте |
|---|---|
| Мишин Дмитрий | Инициализация проекта ([queen.slnx](queen.slnx)), настройка .NET Tool ([queen.fsproj](src/queen/queen.fsproj)), разработка абстрактного синтаксического дерева ([ast.fs](src/queen/ast.fs)), написание парсера на FParsec ([parser.fs](src/queen/parser.fs)), создание [readme.md](README.md), помощь в создании документации ([docs](docs/)) |
| Понизяйкин Максим | Разработка интерпритатора ([eval.fs](src/queen/eval.fs)), создание точки входа ([main.fs](src/queen/main.fs)), создание расширения для подсветки синтаксиса для vscode [Queen VSC](https://github.com/MAILabs-Edu-2026/funcpro-coursework-queen-anne-s-revenge/releases/tag/v1.0.0) |
| Кузнецов Дмитрий | Реализация стандартной библиотеки ([stdlib.qx](lib/stdlib.qx)), написание примеров программ ([examples/](examples/)), создание документации ([docs](docs/)), помощь в создании расширения для vscode [Queen VSC](https://github.com/MAILabs-Edu-2026/funcpro-coursework-queen-anne-s-revenge/releases/tag/v1.0.0) |
