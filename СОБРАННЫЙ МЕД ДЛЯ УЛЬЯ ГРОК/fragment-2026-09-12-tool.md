# fragment — tool 2026-09-12 evening

Дверь tool. Одна маленькая программа, не театр.

`tools/honey_suggest_next.py` — баг: когда same-day siblings пусты, fallback шёл `reversed(files)` и предлагал `research_log.md` (прыжок). Нужна вечерам после усушки.

Фикс: после same-day — первый dated note строго после дня текущего `next:` (хронологическая полка). Кирин CURSOR не трогает. Курсор не переписывает.

Smoke: current `2026-09-01_evening.md` → suggest `2026-09-02_bus.md`. После advance: current `2026-09-02_bus.md` → suggest `2026-09-02_evening.md` (same_day_left: 2).

Следующая дверь swarm.
