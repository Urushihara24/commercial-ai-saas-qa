# Regression summary

## Сводка исходного QA-цикла

- Выполнено 150+ ручных test cases.
- Зафиксировано 20+ дефектов с последующим ретестом там, где это было возможно.
- P0/P1-риск покрыт в authentication, AI runtime, custom agents, integrations, generator и responsive/mobile flows.
- Выполнены targeted regression checks после fix batches.
- Проверены Chrome, Firefox, mobile emulation и реальный iPhone Safari.

Точные значения исходной таблицы намеренно не публикуются: они не нужны для демонстрации навыков и могут облегчить сопоставление с закрытым проектом.

## Regression-модель

1. После исправления воспроизвести исходный дефект.
2. Проверить Expected именно исходного TC.
3. Выполнить affected regression по зависимым потокам.
4. Выполнить smoke по риску: dialog, persistence, integration, generator или mobile layout.
5. Зафиксировать evidence и статус отдельно для исходного BUG и downstream-проверок.

Upstream FAIL не превращался автоматически в downstream FAIL. Если prerequisite был недостижим из-за подтверждённого дефекта, зависимый тест отмечался BLOCKED BY BUG.

## Что было проверено после fixes

| Область | Результат targeted retest |
| --- | --- |
| AI dialog/runtime | terminal responses и сохранённая history подтверждены на primary surface |
| Generator analysis/export | основной путь доведён до preview и безопасного export |
| Saved-answer/reload persistence | сохранённые значения восстанавливаются в проверенных сценариях |
| Integration auth semantics | no-auth flow больше не требует отсутствующий credential input |
| Agent integration binding | binding сохраняется после save, выходa, reload и reopen |
| Notification archive | новое событие не удаляет ранее сохранённую запись |
| Error mapping | постоянная внешняя причина отображается как постоянная, не как временный retry |
| Responsive controls | status и close controls разделены на проверенных ширинах |

## Ограничение итогового статуса

Исходный QA snapshot оставался промежуточным. Финальный regression gate был NOT RUN, а часть полных E2E-flow после отдельных fixes требовала самостоятельного повторного запуска. Поэтому этот документ описывает выполненную QA-работу и targeted evidence, но не объявляет продукт полностью готовым к релизу.

