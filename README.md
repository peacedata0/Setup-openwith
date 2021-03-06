[![Build Status][travis-badge]][travis-link]
[![GitHub release][release-badge]][release-link]

Скрипт **Setup-openwith** для электронных книг PocketBook с прошивкой 5.x, настраивающий **Дополнительное меню настроек "Открыть с помощью"**
==================================================
**Новое меню дополнительных настроек появится в настройках "Персонализация" -> "Открыть с помощью".**

Интерфейс скрипта Setup-openwith и настроенного нового меню являются мультиязычными, насколько позволяет имеющаяся локализация PocketBook.
Скрипт создавался независимым от модели и прошивки PocketBook, но отлаживался только на PocketBook 650.

Описание настроечного скрипта Setup-openwith
---------------------------------------------
- Установка скрипта производится копированием файла Setup-openwith.app в папку /applications/ во внутренней памяти устройства.
- Скрипт добавляет в меню настроек возможность настроить приложение "по умолчанию" которым будет открываться файл с указанным расширением.
- В меню добавляются расширения файлов и программы, которые на момент запуска скрипта Setup-openwith были прописаны в файлах extensions.cfg внутри прошивки и во внутренней памяти.
- При обнаружении недостающих записей в extensions.cfg во внутренней памяти устройста, скрипт предлогает добавить все поддерживаемые расширения следующих обнаруженных дополнительных программ:
  * [Cool Reader 3](https://github.com/blchinezu/pocketbook-coolreader/releases)
  * [Pbimageviewer](http://www3.telus.net/rkomar/pbimageviewer/) (включая 7z.so)
  * [KOReader](https://github.com/koreader/koreader/releases)
 >! В этом случае список расширений в меню настроек и в файле extensions.cfg будет отсортирован по алфавиту.
- При обнаружении Cool reader 3, скрипт создаст две новых темы на основе текущей темы в настройках Персонализация (по умолчанию Line) с замененным виджетом "Поиск" в верхней панели управления на новый "FB2" для быстрого переключения программы по умолчанию открывающую .fb2 файлы (Coor reader 3 или встроенный FB Reader/PB Reader). Встроенный просмотрщик выбирается FB Reader (fbreader.app) или PB Reader (eink-reader.app) в зависимости от того, каким открываются .fb2 файлы на устройстве. Для изменения интерфейса нужно выбрать новую тему оканчивающуюся на OpenWith в Настройки->Персонализация->Тема. Поиском можно продолжить пользоваться через Библиотеку.
- По окончанию настройки скрипт предложит сам себя удалить. Рекомендую его оставить хотя бы на случай обновления прошивки.

>**ВАЖНО! После обновления прошивки обязательно перезапустите скрипт Setup-openwith для обновления нового меню настроек, иначе меню настроек Персонализация останется от старой прошивки и будет не корректно работать.
Для перенастройки дополнительного меню "Открыть с помощью" достаточно еще раз поверх установить скрипт Setup-openwith.**

Описание дополнительных настроек "Открыть с помощью"
-----------------------------------------------------
- Пункт меню "Применение настроек" - вносит настроенные изменения в файл extensions.cfg (находящийся во внутренней памяти устройства), указывая программу по умолчанию только в тех местах строк, где надо, не добавляя и не удаляя строк. (Если программа для открытия необходимого файла уже указана, то она перемещается на первое место, если ее нет, то программа добавляется).
- Пункт меню "Очистить историю" - удаляет файл handlers.cfg из внутренней памяти, что позволяет сбросить соответствие какой штатной программой открывалась (и будет далее открываться по умолчанию) последний раз книга.
- Пункт меню "Удалить" полностью удаляет дополнительное меню "Открыть с помощью", включая темы, содержащие в названии OpenWith. При этом extensions.cfg остается с последними примененными ранее настройками.

После настройки скрипт создает во внутренней памяти следующие файлы:
```
/mnt/ext1/system/bin/openwith_apply.app
/mnt/ext1/system/bin/openwith_clear.app
/mnt/ext1/system/bin/openwith_remove.app
/mnt/ext1/system/bin/openwith_fb2.app
/mnt/ext1/system/config/openwith.cfg
/mnt/ext1/system/config/settings/personalize.json
/mnt/ext1/system/config/settings/openwith.json
/mnt/ext1/system/themes/*-OpenWith(Reader).bpt (например /mnt/ext1/system/themes/Line-OpenWith(Reader).bpt)
/mnt/ext1/system/themes/*-OpenWith(CR3).bpt (например /mnt/ext1/system/themes/Line-OpenWith(CR3).bpt)
```
Для ручного удаления дополнительного меню "Открыть с помощью", достаточно удаления этих файлов.

[travis-badge]:https://travis-ci.org/Lighting/Setup-openwith.svg?branch=master
[travis-link]:https://travis-ci.org/Lighting/Setup-openwith
[release-badge]:https://img.shields.io/github/release/Lighting/Setup-openwith.svg
[release-link]:https://github.com/Lighting/Setup-openwith/releases/latest
