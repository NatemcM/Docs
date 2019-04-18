---
title: "OnLoadWebDocument"
translation: "extending-modx/plugins/system-events/onloadwebdocument"
---

## Событие: OnLoadWebDocument

Запускается непосредственно перед отправкой ответа и после загрузки ресурса.

Служба: 5 - Template Service Events
Группа: Нет

## Параметры события

Нет. На ресурс можно ссылаться через `$modx->resource`.

## Возвращаемые значения

Любые значения, возвращаемые этим событием, будут записываться в журналы как ошибки.

## Использование

_\* Часть этого может быть не точной, потому что я тестирую это методом проб и ошибок._

Это событие можно использовать для установки параметров ресурса во время выполнения или для ведения журнала. Например:

``` php
// Set all pages to be uncached (for debugging)
$modx->resource->set('cacheable', 0);
// Or switch the template
$modx->resource->set('template', 6);
// Alternate syntax
$modx->resource->template = 6;
```

Обратите внимание, что изменение параметров ресурса во время загрузки страницы _first_ (до кэширования ресурса) приведет к записи этих параметров в файл кэша. Например. изменение шаблона на этом этапе приведет к тому, что ресурс `_content` будет хранить содержимое нового ссылочного шаблона.

После того, как страница была кэширована (то есть _не_ первая загрузка страницы), вы можете добавить или добавить содержимое (или полностью перезаписать его), изменив свойство `_content`.

``` php
$modx->resource->_content = 'Content override';
```

## Смотри также

- [System Events](extending-modx/plugins/system-events "System Events")
- [Plugins](extending-modx/plugins "Plugins")