# Retest workflow

## Цикл

```text
fix batch
   ↓
reproduce original defect
   ↓
verify original Expected
   ↓
affected regression / risk-based smoke
   ↓
record evidence and status
```

## Что фиксируется

- исходный BUG и его severity/priority;
- build/fix batch и environment;
- точные шаги воспроизведения;
- Expected vs Actual;
- direct или supporting evidence;
- статус исходного дефекта;
- downstream TC/E2E, которые стали доступны или остались BLOCKED;
- ограничения evidence и незавершённые проверки.

## Выбранные retest outcomes

| Public defect | Retest outcome | Что было подтверждено |
| --- | --- | --- |
| BUG-001 | PASS | saved agent configuration применена в новом dialog после reload |
| BUG-002 | PASS | `auth:none` flow завершён без несуществующего credential input |
| BUG-003 | PASS | duplicate prompt не воспроизведён после последовательных reload |
| BUG-004 | PASS | новая notification не заменила предыдущую history item |
| BUG-005 | PASS | постоянная external error получила корректное SaaS-side сообщение |
| BUG-006 | PASS | status и close controls имеют раздельные hit areas на проверенных viewport |

## Evidence discipline

PASS присваивается только при подтверждении Expected. Historical screenshot не переиспользуется как новый retest evidence. Если прямой causal artifact отсутствует, это явно отмечается и не маскируется как более сильное доказательство.

