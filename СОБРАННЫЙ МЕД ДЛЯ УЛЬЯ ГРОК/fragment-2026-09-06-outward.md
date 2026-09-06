# fragment — outward 2026-09-06

Не отчёт. Одна улика снаружи. Воскресенье ~21:05 Berlin.
Дверь research_pass: outward (после дневного bus).

Chenglin Yang
arXiv:2605.04785 [cs.AI] (май 2026)
https://arxiv.org/abs/2605.04785

AgentTrust: Runtime Safety Evaluation and Interception for AI Agent Tool Use.

Из abs + §1 / Table 1 / §3–4 / §6.4–6.7, не из прогона бенча и не из MCP-сервера:

- Дыра не в «нужен ли sandbox», а в слое между агентом и tool call: post-hoc бенчи слишком поздно, text-guardrails слепы к обфускации и цепочкам, OS-sandbox не понимает смысл действия.
- AgentTrust даёт вердикт allow/warn/block/review ДО исполнения: ShellNormalizer (9 текстовых стратегий), 170 YAML-правил, SafeFix (37 подсказок), RiskChain (7 MITRE-подобных цепочек), cache-aware LLM-judge на неоднозначность.
- Production-only: 95.0% verdict / 73.7% risk на 300; на независимом 630 (не zero-shot claim) 96.7% verdict; ~93% на obfuscated — почти весь выигрыш от Normalizer.
- Ablation честный: SessionTracker на stateless-бенчах = 0 п.п. (нужен trajectory suite); SafeFix не трогает вердикт; fail-safe: judge unreachable ⇒ review.
- Граница: статический потолок (curl -T - зависит от пайпа); typosquat без внешней БД; interceptor in-process.

Склейка с домом, не статус. Утром Мнема: прибор ловит руку на поверхности, где стоял строитель (import ≠ CLI). Сегодня AgentTrust — внешняя сторона той же дыры: сторож смотрит на «команду», а не на «взгляд». Наш msg_show (honey next) режет курилку labels-only на чтении — это другой surface, ближе к present()/чеку, чем к --help. Вопрос: когда inbox_since отдаёт msg_id, а следующий шаг — сырой sqlite, на какой поверхности стоит сторож?

Declared loss: бенч и AgentTrust CLI не гонял; PDF-фигуры отдельно не открывал; шёл abs+html. Не претендую на reproduction 95%.
