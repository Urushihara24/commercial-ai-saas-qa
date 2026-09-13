# QA scope

## Входит в scope

| Область | Что проверялось |
| --- | --- |
| Public/auth | доступ гостя, регистрация/вход, protected area, logout |
| AI dialog | отправка сообщений, terminal response, история, reopen, runtime states |
| Custom agents | создание, редактирование, сохранение, binding integration, disable lifecycle |
| Generator | шаги кампании, edit/reload persistence, preview, безопасный export |
| Integrations | спецификация, подключение, auth semantics, сохранение состояния |
| Admin read-only | загрузка списков, открытие существующих объектов, просмотр журнала, export |
| Responsive | 390, 768, 1440 и 1920 px; overflow, clipping, controls, dialogs |
| Browsers/devices | Chrome, Firefox, Chrome Device Mode, реальный iPhone Safari |
| Defect flow | Expected/Actual, severity, priority, evidence, retest, affected regression |

## Окружения

- Desktop Chrome: 1920×1080 и responsive width 1440 px.
- Desktop Firefox: cross-browser smoke и рисковые пользовательские сценарии.
- Chrome Device Mode: 390 px и 768 px.
- Реальный iPhone Safari: native portrait mobile smoke и critical workflow checks.

Точные версии ОС/браузеров и client-specific test data намеренно не публикуются.

## Не входит в scope

- security-аудит;
- load/performance testing;
- самостоятельное тестирование внешних сервисов;
- реальное выполнение платежей и операции payment gateway;
- destructive third-party OAuth/export/bid/campaign actions;
- state-changing admin CRUD, role mutation и глобальные billing/pricing изменения;
- отдельное desktop Safari testing;
- автоматизация, если она не подтверждена исходным QA-процессом.

Внешняя недоступность сервиса не считалась автоматически багом продукта. Проверялась только корректность взаимодействия SaaS-платформы с таким состоянием и понятность сообщения пользователю.

## Статусная модель

- **PASS** — Expected подтверждён.
- **FAIL** — Expected нарушен; есть актуальное evidence и связанный BUG.
- **BLOCKED** — сценарий нельзя завершить из-за подтверждённого blocker или отсутствующей обязательной зависимости.
- **SKIPPED** — осознанно исключён из scope с явной причиной.
- **NOT RUN** — проверка ещё не выполнена и не имеет подтверждённого blocker.

## Production safety

Использовались QA-owned данные и обратимые проверки. Расходные AI-проверки выполнялись только в разрешённом безопасном контуре. Реальные платежи, чужие production-данные и необратимые внешние действия не выполнялись.

