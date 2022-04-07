# Рекомендации для разработчиков

## Общие сведения

Разработка ведётся под [Erlang/OTP][1] версии 24 или выше.

В качестве основного инструмента для сборки, анализа исходного кода и запуска тестов используется [rebar3][2]. Рекомендуется использовать [GNU Make][3] для автоматизации рутинных операций и организации привычной среды для новых разработчиков.

Управление зависимостями в rebar3 предполагает более тесное использование центрального репозитория пакетов [hex.pm](https://hex.pm), поэтому при поиске подходящих зависимостей следует посетить этот репозиторий в первую очередь.

Для написания функциональных тестов предпочтительно использовать [common_test][4], а для написания простых модульных тестов для различных библиотек и фрагментов приложений допускается использовать [eunit][5]. Все тестовые сценарии должны быть написаны с учётом изолированной среды их исполнения, иными словами, с расчётом на то, что любые внешние зависимости и сервисы недоступны, либо эфемерны.

В качестве инструмента статического анализа настоятельно рекомендуется использовать [dialyzer][6] и [xref][7].

При подготовке production ready сборок проектов следует использовать функционал релизов, предоставляемый [relx][8].

Дабы исключить различные шероховатости, связанные с форматированием кода и различием в предпочтениях по этому вопросу у разных разработчиков, мы используем [erlfmt][13], который берёт на себя исключительное право диктовать единое форматирование в рамках проекта и следит за его соблюдением.

Чтобы не начинать каждый раз с пустого листа, рекомендуется взять любезно заготовленные [шаблоны проектов для rebar3][9]. В них кроме всего перечсиленного выше демонстрируется работа с [thrift][10] и [woody][11], поверх которых построено межсервисное взаимодействие в системе, а также с [Github Actions][12], который мы используем в качестве инструмента CI.

## Безопасность

При разработке ПО важно уделять внимание к подходам, позволяющим сделать это ПО безопасным.
Необходимо руководствоваться следующими материалами:

1. [Предотвращение XXE](XXE-prevention-guideline.md)

## Для дальнейшего ознакомления

1. [Инструментарий](tooling.md)
1. [Написание исходного кода](code-style.md)
1. [Внесение изменений](contributing.md)
1. [Работа с системой контроля версий](working-with-vcs.md)
1. [Подготовка релиза](preparing-release.md)

[1]: https://erlang.org
[2]: https://rebar3.org
[3]: https://www.gnu.org/software/make/
[4]: http://www.erlang.org/doc/man/common_test.html
[5]: http://erlang.org/doc/apps/eunit/chapter.html
[6]: http://www.erlang.org/doc/apps/dialyzer/dialyzer_chapter.html
[7]: http://www.erlang.org/doc/apps/tools/xref_chapter.html
[8]: https://github.com/erlware/relx
[9]: https://github.com/valitydev/erlang-templates
[10]: https://thrift.apache.org/
[11]: https://github.com/valitydev/woody_erlang
[12]: https://github.com/valitydev/erlang-workflows
[13]: https://github.com/WhatsApp/erlfmt