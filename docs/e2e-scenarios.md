# Обезличенные E2E-сценарии

Эти flow показывают связность проверок. Они не являются обещанием, что каждый исторический E2E был полностью перезапущен после каждого fix batch.

## E2E-SAN-001 — authentication → protected area → logout

**Preconditions:** QA-аккаунт; активной сессии нет.

**Flow:** Вход → открытие защищённой области → переход к основному разделу → logout → повторная попытка открыть защищённый маршрут.

**Expected:** Пользователь получает доступ после входа; logout завершает сессию; защищённый маршрут не остаётся доступным после выхода.

**Observed in source work:** PASS для проверенного login/logout flow. Recovery по email был отдельной зависимостью и не смешивается с этим сценарием.

## E2E-SAN-002 — AI specialist → dialog → response → history

**Preconditions:** Разрешённый QA-пользователь; выбран готовый AI-специалист; доступен безопасный внутренний баланс.

**Flow:** Открыть специалиста → отправить несколько сообщений → получить terminal responses → перейти в список диалогов → повторно открыть диалог.

**Expected:** Ответы завершаются; dialog сохраняется в списке; порядок и содержимое истории сохраняются после reopen.

**Observed in source work:** Исторический runtime blocker был зарегистрирован и затем verified as fixed на primary production surface. Это сопровождалось affected regression и отдельной оценкой cross-browser evidence.

## E2E-SAN-003 — custom agent → settings → save → reload → new dialog

**Preconditions:** Собственный агент; доступная безопасная integration; QA-пользователь.

**Flow:** Изменить заметную настройку → сохранить → выйти → reload → открыть новый диалог с тем же агентом → проверить применённое поведение → при необходимости отключить агента.

**Expected:** Сохранённая настройка восстанавливается и используется новым dialog; binding integration не теряется; disabled state блокирует новый запрос.

**Observed in source work:** Persistence defect был воспроизведён, зафиксирован и закрыт targeted causal retest. Полный исторический lifecycle не представляется как blanket release sign-off.

## E2E-SAN-004 — campaign generator → preview → safe export

**Preconditions:** QA-draft и значения шагов генератора; известные внешние ограничения documented.

**Flow:** Начать draft → пройти доступные шаги → проверить edit/reload persistence → открыть preview → выполнить безопасный локальный export.

**Expected:** Сохранённые значения не теряются; preview доступен; export валиден; запрещённый внешний publish-action не выполняется.

**Observed in source work:** Основной маршрут был доведён до preview и безопасного export после fix batch. Внешняя выгрузка и destructive OAuth действия исключались из production-safe scope.

## E2E-SAN-005 — custom integration → specification → connect → persist

**Preconditions:** Безопасная HTTP-style specification; режим `auth:none`; собственный агент.

**Flow:** Создать integration → заполнить specification → connect → выбрать integration для агента → save → выйти → reload → reopen.

**Expected:** Режим без credentials не требует несуществующий secret; integration подключается; binding сохраняется после reload/reopen.

**Observed in source work:** Ошибка auth semantics и ошибка binding были разделены на два дефекта; после исправлений оба targeted flow прошли.

## E2E-SAN-006 — responsive/mobile critical workflow

**Preconditions:** Viewports 390/768 px и реальный iPhone Safari; доступен безопасный mobile сценарий.

**Flow:** Открыть menu → specialist/dialog → отправить сообщение → проверить generator step → открыть FAQ → проверить закрытие overlay.

**Expected:** Touch targets доступны; нет clipping/overlap/horizontal scroll; dialog и generator сохраняют usable layout.

**Observed in source work:** Initial real-device/runtime run выявил AI-response defect; дефект был устранён и проверен на primary/affected surfaces. Финальную blanket PASS-формулировку для полного post-fix real-device E2E этот portfolio не делает.

## Исключения

Реальные платежи, destructive third-party OAuth/export/bid/campaign actions и самостоятельное тестирование внешних сервисов были исключены из production-safe scope.

