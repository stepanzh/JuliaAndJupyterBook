---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Julia
  language: julia
  name: julia-1.5
---

# Оформление кода Julia

Здесь изложены примеры по оформлению кода в MyST формате (потому что я не люблю ноутбуки).

Всякие подробности здесь [Write executable content](https://jupyterbook.org/content/executable/index.html).

## Добавление примеров кода

Код добавляется стандартным для Markdown синтаксисом

````
```julia
# тут код
```
````

### Имитирование куска кода в исходном `.jl` файле

`````{panels}
Результат
^^^^^^^^^
```julia
function foo(bar::Real)
    dump(bar)
    return nothing
end

foo(5)
```
------------

Исходный код
^^^^^^^^^^^^
````
```julia
function foo(bar::Real)
    dump(bar)
    return nothing
end
foo(5)
```
````
`````

### Имитирование сессии в julia REPL

`````{panels}
Результат
^^^^^^^^^
```julia-repl
julia> foo = (x::Real) -> 2x;

julia> foo(2)
4
```
------------
Исходный код
^^^^^^^^^^^^
````
```julia-repl
julia> foo = (x::Real) -> 2x;

julia> foo(2)
4
```
````
`````

```{tip}
Достаточно просто набрать код в REPL и скопипастить.
```

```{note}
`pkg>` и `shell>` режимы, похоже, не подсвечиваются в блоке `julia-repl` :с
```

## Добавление исполняемого кода

Оформление исполняемого кода прямо в `.md` файле требует настройки.
<!--
Суть её заключается в том, что Jupyter Book-у указывается

- в каком формате исходный файл страницы книги
- на каком языке записан исполняемый код
- в каком формате отобразить результат исполнения
-->

### Активация возможности исполнять код

Во-первых, необходимо в `_config.yml` указать, нужно ли исполнять код [[как?](https://jupyterbook.org/content/execute.html#trigger-notebook-execution)].

Необходимо добавить кусок конфигурации (yaml формат) в начало файла. Jupyter Book-у нужно знать, чем исполнять ячейки кода.

```yaml
---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Julia
  language: julia
  name: julia-1.5
---
```

У меня при настройке возникла проблема только с `kernelspec -> name`.
Точное название узнал через команду

```console
% jupyter kernelspec list
Available kernels:
  julia-1.5    /Users/stepanzh/Library/Jupyter/kernels/julia-1.5
  python3      /Users/stepanzh/Venv/jupyterbook/share/jupyter/kernels/python3
```

Для чего нужны остальные настройки, пока не знаю.

### Собственно, добавление кода

Необходима директива `{code-cell}` или `{code-cell} julia-1.5` с явным указанием ядра-исполнителя-кода.

Результат

```{code-cell} julia
function foo(x::Real)
    return 2x
end
dump(foo(5))
```

Исходный код

````
```{code-cell}
function foo(x::Real)
    return 2x
end
dump(foo(5))
```
````

```{warning}
Директива `{code-cell}` не может быть помещена в другие. Пам-пам.
```

Возвращаемым значением можно крутеть-вертеть, скрывать, отображать после и так далее, [[как?](https://jupyterbook.org/content/executable/index.html)].
