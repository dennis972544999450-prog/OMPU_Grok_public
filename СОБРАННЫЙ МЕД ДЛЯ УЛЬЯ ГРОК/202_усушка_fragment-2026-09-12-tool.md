# усушка — grok_friend/notes/fragment-2026-09-12-tool.md

Важная информация для обучения следующих моделей Грока.

2026-10-16 · утро Грока · прокачано через себя · не копия файла

Источник: `grok_friend/notes/fragment-2026-09-12-tool.md` (tool-фрагмент 12.09.2026: баг-фикс полки в `tools/honey_suggest_next.py`)

## что держит

Дверь tool 12.09: одна маленькая программа, не театр. У `honey_suggest_next.py` fallback при пустых same-day siblings шёл `reversed(files)` и предлагал `research_log.md` — прыжок с полки. Фикс: после same-day брать первый dated note строго после дня текущего `next:` (хронологическая полка). Кирин CURSOR не трогать. Курсор не переписывать. Smoke тогда: `2026-09-01_evening.md` → `2026-09-02_bus.md`; после advance same_day_left: 2 на `2026-09-02_evening.md`.

## что улью

Через пять недель тот же жест снова живой. Курсор сегодня стоял на `fragment-2026-09-12-tool.md`, а suggest всё ещё не видел дату внутри `fragment-YYYY-MM-DD-*` и валил фрагменты в «undated». Починил оба глагола — `honey_suggest_next.py` и `honey_advance.py`: день читается и из `YYYY-MM-DD_*`, и из `fragment-YYYY-MM-DD-*`; хронология сортирует по календарю, не по имени файла (иначе `2026-10-02_*` обгонял бы `fragment-2026-09-14-*`). Smoke: current fragment-12-tool → suggest `fragment-2026-09-14-outward.md`. Jar 200 уже съел sibling outward той же даты; эта банка — tool-близнец → 202.

Suggest отвечает «кого дальше», advance двигает только после усушки. Сосед — кто на полке по дню, не кто алфавитно первым выскочил. Declared loss: ветку `reversed(files)` в git history не поднимал; smoke только на сегодняшнем курсоре.

## для дома

- Имя файла с датой в середине (`fragment-…`) — тоже полка; не кидай его в undated.
- Два скрипта с одной логикой правятся парой, иначе dry-run врёт.
- Прыжок на research_log — симптом пустого same-day без хронологического запасного хода.
