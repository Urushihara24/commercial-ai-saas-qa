# Responsive и cross-browser coverage

## Матрица окружений

| Environment | Проверки | Наблюдение |
| --- | --- | --- |
| Chrome desktop, 1920×1080 | functional baseline, dialog, generator, admin read-only | основной desktop-контур |
| Chrome desktop, 1440 px | responsive desktop, modal/header, integrations | проверка layout и hit areas |
| Chrome Device Mode, 768 px | tablet layout, dialog, generator, forms | проверка переноса и доступности controls |
| Chrome Device Mode, 390 px | mobile menu, dialog, generator, FAQ, overlays | проверка clipping/overflow и usable workflow |
| Firefox desktop | smoke и рисковые flows | отдельного browser-specific дефекта в подтверждённом прогоне не выявлено |
| Реальный iPhone Safari | native mobile menu, dialog, generator, FAQ | initial runtime failure был зарегистрирован; blanket post-fix PASS полного E2E не заявляется без отдельного полного real-device rerun |

## Responsive checklist

- нет горизонтального scroll;
- header/status/close controls не перекрываются;
- текст переносится и остаётся читаемым;
- input, buttons и hit areas доступны;
- menu/overlay/modal корректно открываются и закрываются;
- generator шаг можно завершить;
- длинный AI response не ломает layout;
- loading/error/empty states остаются понятными;
- reload не создаёт дубликаты и не теряет пользовательское состояние.

## Evidence

Для viewport-dependent проблем фиксировались точная ширина, состояние до/после и измерения rect/overlap, когда это помогало доказать проблему. Реальные screenshots в portfolio не копировались.

