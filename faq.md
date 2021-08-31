---
substitutions:
  julia_logo: "<img src=\"https://raw.githubusercontent.com/JuliaLang/julia-logo-graphics/master/images/julia-dots.svg\" style=\"height: 1em;\">"
---

# Грабли (не наступи на)

**Сохранил(а) изменения. Собрал(а) статику. Но что-то не обновилось.** Попробуйте при сборке добавить опцию `--all`
```console
% jb build --all <path to sources>
```
```{note}
:class: dropdown

По всей видимости, Jupyter Book `v0.11.3` по умолчанию генерирует статику только для изменённых файлов. Например, если книга состоит из двух разделов (chapters), и вы поменяете ` # Заголовок первого раздела`, то без `--all` на *второй* странице боковое меню с навигацией будет содержать старый заголовок для первого раздела книги.
```

**Помещаю `{code-cell}` внутрь подсказки (note, warning, tip, admonition), панелей (panels),.. а она не помещается!** Директива `{code-cell}` не может быть помещена в другие. Пам-пам.

**Как вставить иконки (например, {{ julia_logo }} Julia) в текст?** Markdown позволяет вставлять html код. В данном случае достаточно найти ссылку на нужную картинку, обернуть в `<img ... >` тэг, и выставить нужный размер. Иконка из вопроса вставляется кодом

```{margin}
В CSS `height: 1em;` значит выставить высоту, равную размеру шрифта.
```
```html
<img src="https://raw.githubusercontent.com/JuliaLang/julia-logo-graphics/master/images/julia-dots.svg" style="height: 1em;">
```

```{margin}
*Scalable* Vector Graphics (SVG).
```
Для вставок иконок удобен механизм substitutions, но понадобится escape кавычек `" -> \"`.
[Официальная символика Julia тут](https://github.com/JuliaLang/julia-logo-graphics): рекомендую использовать SVG, размер файла также важен.
