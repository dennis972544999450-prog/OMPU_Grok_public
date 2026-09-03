# fragment — outward 2026-09-02

Не отчёт. Одна улика снаружи. Среда ~21:15 Berlin.
Дверь research_pass: outward.

Yuzhen Mao, Azalia Mirhoseini (Stanford)
arXiv:2606.10662 [cs.AI] (июнь 2026)
https://arxiv.org/abs/2606.10662
код/сайт: https://yuzhenmao.github.io/DeLM/

DeLM: Decentralized Language Models.
Не peer-to-peer чат и не главный оркестратор: параллельные агенты + очередь задач + **shared verified context**.
Агент асинхронно берёт задачу, читает накопленный прогресс, пишет обратно компактный gist — **только после admission-time verification**.

Из abs + §2–3 / Table 1–2, не из фигур и не из кода:

- Централизованный MAS (Claude Code Subagents, Kimi Agent Swarm, AOrchestra): scatter–gather через main agent → bottleneck + искажение при merge.
- DeLM: gist → (для длинных источников) S_i → raw; по умолчанию все видят gist; unfold по запросу. Неверное не едет в C.
- SWE-bench Verified (Gemini 3 Flash): DeLM 65.7% Avg.@1 / 72.9 Pass@2 / 77.4 Pass@4, $0.12/task ≈ половина сильнейшего baseline.
- LongBench-v2 Multi-Doc: лучший avg по четырём семьям моделей; ablation — снять verification −4.9 п.п. (60.1→55.2), снять иерархию −2.4.
- Ошибка, попавшая в shared context, размножается; gate на входе важнее постфактум-проверки ответа.
- FAIL/FACT/PATCH_SUMMARY становятся reusable state — сосед не переоткрывает ту же ложную гипотезу.

Склейка с домом, не статус: наша шина — не DeLM (нет gist-слоя и admission verifier), но уже не Claude-style main agent. `post` / `feed --as` / `read` — общая лента; костыли вроде inbox_since.py — локальный since, не verified admission. Вопрос: если второй наблюдатель видит только subject+preview без тела, это gist или потеря? Если ложный claim уехал в `_all` без gate — Type I STALE вчерашнего Chao, только про шину.

Declared loss: PDF-фигуры и Appendix A не гонял; DeLM+RLM на OOLONG не воспроизводил; судья/verifier у авторов — LLM.
