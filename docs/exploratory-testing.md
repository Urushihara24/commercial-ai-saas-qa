# Exploratory testing

Exploratory testing применялось как time-boxed проверка рисков, которые нельзя было полностью выразить одним happy-path TC.

## Charters

### 1. AI runtime и terminal states

Проверялись длительное ожидание, отсутствие ответа, повторная отправка, сохранение результата и поведение после reopen. Это привело к выделению runtime defect как отдельного Critical/P0 риска, а не к смешению его с UI layout.

### 2. Persistence и reload

Проверялись сохранённые ответы generator-а, введённые значения текущего шага, duplicate prompt после reload и применение custom-agent settings в новом dialog. Соседние проявления фиксировались раздельно, если у них различались Expected или causal sequence.

### 3. Custom integrations

Проверялись auth semantics, валидность HTTP-style specification, connection flow, безопасное сохранение binding и повторное открытие агента. Auth-none и binding persistence оформлялись как разные defect classes.

### 4. Notification/event history

Проверялась целостность архива после появления нового события: append/order/retention предыдущей записи. Для проверки не выполнялись реальные платежные действия.

### 5. Error communication

Сопоставлялись внешний status/error code, реальная устойчивость причины и текст, который видит пользователь. Внешняя недоступность не объявлялась BUG без нарушения SaaS-side Expected.

### 6. Responsive interaction

Проверялись не только загрузка страницы, но и hit areas, overlays, dialogs, footer/header, clipping, overlap, horizontal scroll и доступность generator controls на узких ширинах.

## Результат exploratory-подхода

Исследовательские проверки расширили defect discovery за пределы обязательных TC: были обнаружены дополнительные проблемы в notification history, disabled-agent UX, integration form и error mapping. В публичный репозиторий вынесены только шесть representative classes.

