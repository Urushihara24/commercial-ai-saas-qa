# Sample test cases

## TC-SAN-001 — authentication и logout

- **Area:** Authentication
- **Priority:** P0
- **Preconditions:** Пользователь зарегистрирован; активной сессии нет.
- **Steps:** Открыть страницу входа; выполнить вход валидными QA-данными; открыть protected area; выполнить logout.
- **Expected Result:** После входа открывается protected area; после logout защищённый маршрут снова требует авторизацию; сессия не восстанавливается самопроизвольно.

## TC-SAN-002 — ответ AI в диалоге

- **Area:** AI dialog/runtime
- **Priority:** P0
- **Preconditions:** Доступен разрешённый QA-пользователь с положительным внутренним балансом; выбран готовый AI-специалист.
- **Steps:** Открыть диалог; отправить короткое текстовое сообщение; дождаться terminal state; проверить содержимое ответа и состояние composer.
- **Expected Result:** Сообщение отображается; AI возвращает содержательный terminal response; бесконечное состояние ожидания и ложный success отсутствуют.

## TC-SAN-003 — сохранение истории диалога

- **Area:** AI dialog / persistence
- **Priority:** P1
- **Preconditions:** В диалоге уже есть одно завершённое сообщение и ответ.
- **Steps:** Отправить второе сообщение; вернуться к списку диалогов; снова открыть тот же диалог.
- **Expected Result:** Оба сообщения и ответа сохранены в правильном порядке; повторное открытие не создаёт новый пустой диалог и не теряет историю.

## TC-SAN-004 — сохранённая настройка собственного агента применяется в новом диалоге

- **Area:** Custom AI agent
- **Priority:** P1
- **Preconditions:** Авторизованный QA-пользователь; собственный агент доступен для редактирования.
- **Steps:** Изменить одну заметную настройку агента; сохранить; выйти из редактора; выполнить reload; открыть новый диалог с тем же агентом.
- **Expected Result:** После reload настройка сохранена и применяется в новом диалоге; значение не откатывается к предыдущему состоянию.

## TC-SAN-005 — integration с `auth:none`

- **Area:** Custom integration
- **Priority:** P1
- **Preconditions:** Подготовлена безопасная HTTP-style specification, не требующая credential input.
- **Steps:** Создать integration; выбрать режим без авторизации; заполнить specification; запустить подключение; проверить результат.
- **Expected Result:** Подключение завершается без запроса отсутствующих credentials; ошибка показывается только при нарушении фактических требований specification.

## TC-SAN-006 — binding integration к собственному агенту

- **Area:** Custom agent / integration
- **Priority:** P1
- **Preconditions:** Integration создана и доступна QA-пользователю; собственный агент открыт в редакторе.
- **Steps:** Выбрать integration; сохранить настройки агента; выйти; выполнить reload; снова открыть агента.
- **Expected Result:** Binding сохраняется и отображается при повторном открытии; подключённая integration доступна агенту в рамках разрешённого сценария.

## TC-SAN-007 — edit предыдущего ответа генератора

- **Area:** Campaign generator
- **Priority:** P1
- **Preconditions:** В черновике генератора есть сохранённый ответ шага.
- **Steps:** Нажать «Изменить» у предыдущего ответа; проверить поле редактирования; подтвердить исходное или новое значение; продолжить.
- **Expected Result:** Поле содержит сохранённое значение; подтверждение изменяет только целевой шаг и не очищает уже сохранённые данные.

## TC-SAN-008 — persistence текущего шага после reload

- **Area:** Generator / reload persistence
- **Priority:** P1
- **Preconditions:** В текущем шаге введено уникальное QA-значение, но маршрут ещё не завершён.
- **Steps:** Ввести значение; убедиться, что оно отображается; выполнить reload; снова открыть тот же draft/step.
- **Expected Result:** Значение восстанавливается после reload; текущий вопрос не дублируется в истории; пользователь может продолжить flow.

## TC-SAN-009 — mobile menu на 390 px

- **Area:** Responsive
- **Priority:** P0
- **Preconditions:** Viewport установлен ровно в 390 px; открыта публичная или protected page.
- **Steps:** Открыть mobile menu; нажать на пункт; закрыть menu; проверить страницу после закрытия.
- **Expected Result:** Menu и пункты доступны; overlay исчезает после закрытия; горизонтального scroll, clipping и зависшего overlay нет.

## TC-SAN-010 — dialog layout на узком viewport

- **Area:** Responsive / AI dialog
- **Priority:** P0
- **Preconditions:** Viewport 390 px; выбранный AI-специалист доступен.
- **Steps:** Открыть dialog; проверить panel, composer, кнопку отправки и history; отправить короткое сообщение.
- **Expected Result:** Критичные controls не перекрыты и не обрезаны; ответ можно прочитать; клавиатура/viewport не блокируют основной workflow.

## TC-SAN-011 — Firefox cross-browser dialog smoke

- **Area:** Cross-browser
- **Priority:** P1
- **Preconditions:** Desktop Firefox; разрешённые QA-данные; выбранный AI-специалист.
- **Steps:** Открыть продукт; перейти в dialog; отправить сообщение; дождаться ответа; вернуться в список.
- **Expected Result:** Основные элементы и runtime flow работают так же, как в поддерживаемом Chrome; browser-specific console/runtime failure отсутствует.

## TC-SAN-012 — real iPhone Safari mobile smoke

- **Area:** Real-device mobile
- **Priority:** P0
- **Preconditions:** Реальный iPhone; Safari в portrait; доступен разрешённый QA-сценарий.
- **Steps:** Проверить menu; открыть dialog; выполнить сообщение; проверить generator step; раскрыть FAQ.
- **Expected Result:** Touch controls доступны; viewport не обрезает критичные элементы; ключевой mobile workflow может быть завершён без iOS-specific blocker.

## TC-SAN-013 — mapping постоянной внешней ошибки

- **Area:** Error handling / integration
- **Priority:** P1
- **Preconditions:** Тестовая среда возвращает известную постоянную ошибку доступности внешнего provider-а.
- **Steps:** Запустить шаг, зависящий от provider-а; зафиксировать внешний status/error code; сравнить сообщение SaaS с типом причины.
- **Expected Result:** Пользователь получает точное сообщение о постоянной причине и понятное дальнейшее действие; ошибка не маркируется как кратковременная, если retry не изменит результат.

