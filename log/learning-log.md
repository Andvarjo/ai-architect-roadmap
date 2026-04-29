# Learning Log

> Daily-ish journal across the 26-week AI Architect roadmap. One entry per study day. Brief: what I touched, what clicked, what didn't, open questions.

---

## 2026-04-27 (Mon) — Day 1 / Week 1

**Theme:** LangGraph básico — kickoff.

### What I did
- Bootstrapped this repo (`ai-architect-roadmap`) — README with the full 26-week TOC, base structure (`/log`, `/notes`, `/adrs`, `/specs`, `/runbooks`, `/compliance`, `/week-XX-*/`), `.gitignore`, and Week 1 placeholder.
- Made Cowork the daily mentor for the run: it pulls today's block from `roadmap-daily.md`, tracks progress in `progress.md`, and writes here.
- Watched the LangChain "Introduction to LangGraph" intro and wrote 5 takeaways in `/notes/langgraph-intro.md`. _(filled in at end of session)_

### What clicked
Día 1 fue todo plumbing — repo, README con TOC de 26 semanas, estructura de carpetas, commit inicial. La claridad de ver el plan completo mapeado a un repo público hace que los próximos 6 meses se sientan concretos, no abstractos.

### What didn't / open questions
- El video de LangGraph quedó pendiente — rolea a mañana.
- Push pendiente desde la terminal local (el sandbox no tiene SSH keys, intencional).

### Tomorrow
- `git push -u origin main` (1 min) → repo público vivo en GitHub.
- Intro video LangGraph + 5 notas en `/notes/langgraph-intro.md` (30 min).
- Tutorial: basic chatbot en LangGraph → `01-basic-chatbot.py` (90 min).

---

## 2026-04-28 (Tue) — Day 2 / Week 1

**Theme:** LangGraph básico — agente real y mucho más rápido de lo planeado.

### What I did
- En lugar de seguir el plan (basic chatbot tutorial, 90 min), tomé el curso completo **LangGraph Essentials (Python)** de LangChain Academy — 6 lecciones, terminé con un email triage agent funcionando.
- El agente: clasificador de intent (OpenAI directo dentro de un node), branching por intent, `interrupt()` nativo para human-in-the-loop en intents sensibles.
- Notas estructuradas por lección en `notes/langgraph-intro.md` (state, reducers + paralelismo, memory + thread_id, interrupt).
- Cleanup del repo: clone del curso (415 MB) movido al `.gitignore` para que quede en local pero no en GitHub. Bueno hacerlo ahora antes del primer push.

### What clicked
- Material del Día 3 (StateGraph + tools) y Día 4 (conditional edges / branching) ya quedó cubierto. La parte de HITL del Día 2 de la Semana 2 también — `interrupt()` + checkpointer encajan limpio.
- Decisión: clasificador dentro del node, no como tool node. Es lógica determinística interna del pipeline, no una capacidad que el LLM elige usar. Mantenerla como node es más simple y lee mejor en el grafo.
- `interrupt()` nativo > rolear un "wait for input" custom: integra con el checkpointer, pause/resume serializa estado solo, y resumir desde otro worker funciona sin esfuerzo extra.

### What didn't / open questions
- El timeout de `interrupt()`: ¿qué pasa si el humano nunca responde? ¿Hay ruta default? Pendiente.
- Para el classifier node, ¿estructurar el output con un schema Pydantic en vez de parsear OpenAI manualmente? Probar la próxima sesión.
- ¿A qué escala deja de servir `InMemorySaver`? ¿Cuándo pasamos a SQLite/Postgres? Pendiente — Semana 2 tiene persistence, ahí se aclara.

### Tomorrow
Como ya cubrí branching + HITL ahead of schedule, los días miércoles y jueves cambian de scope:

- **Mié:** escribir mi propia versión mínima (~80 LoC, clean, no notebook clutter) del email triage agent en `/week-01-langgraph-basics/email-triage-agent.py`. Esta es la pieza que cuenta para portfolio.
- **Jue:** README sólido para `/week-01-langgraph-basics/` explicando flow + design choices, contestar las 3 open questions de hoy (timeouts en interrupt, structured outputs, scaling de saver).
- **Vie:** review semanal + push + 1 párrafo de aprendizaje en este log.

---
