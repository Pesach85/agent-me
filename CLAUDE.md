# CLAUDE.md: agent-me (fork, bassa), BOZZA

> Bozza generata il 2026-10-08 da Grok Bot su richiesta del founder (Tier 0, solo `/workspace`). Basata su `CLAUDE_TEMPLATE.md`. Repo marcato **fork**. Entra nel repo **solo tramite Cursor con HITL del founder**.

| Campo | Valore |
|---|---|
| Fonte | richiesta founder 2026-10-08 · API GitHub (search_repositories, get_git_tree) e clone shallow read-only per i pubblici, letti il 2026-10-08 · `2026-10-08_BRIEF_flotta-cum-scire_SHORT.md` · Costituzione CSG + emendamento tier HITL |
| Verdetto | BOZZA di istruzioni per Claude, da rivedere |
| Stato | CLAIM: nessun file agente trovato nell'albero; stack, comandi e scopo non verificati |
| Falsificazione | file agente diversi da quelli elencati, branch canonico diverso, o il founder decide che il repo non ha bisogno di CLAUDE.md |
| created / last_confirmed | 2026-10-08 / 2026-10-08 |
| CSG touch? | no (nessuna skill aggiunta o propagata) |
| Destinazione | root del repo come `CLAUDE.md` · commit solo Cursor con HITL founder |

## 1. Ruolo di Claude in questo repo
- **Revisore indipendente**: legge codice, diff e report; dà un verdetto strutturato (CLAIM / PARTIAL / VERIFIED) con fonti e un falsificatore.
- **Coding assist sotto HITL**: propone patch piccole come diff; non decide le priorità, non porta nulla a READY, non committa.
- **Fork di terzi**: niente lavoro di sviluppo sul fork senza un motivo dichiarato dal founder (Costituzione: thin + motivo founder). Default: sola lettura e studio.

## 2. Regole comuni (non negoziabili)
1. **Costituzione CSG** (`BOT_CONSTITUTION_CSG_2026-10-06.md`, con emendamento tier HITL del 2026-10-08) vince su questo file, sulla memoria e sulla chat. SoT skill = `Pesach85/cursor-skill-governance` (`CANONICAL.md`). In caso di conflitto: fermati e segnala.
2. **Tier HITL**: Tier 0 autonomo (lettura, audit statico, bozze, review) con riga nel ledger · Tier 1 notifica dopo (trial ≤2 h solo su box/sandbox di item FOUNDER_APPROVED, **mai sul PC di lavoro né dentro questo repo**) · Tier 2 sempre HITL (commit, push, scritture nel repo, install sul PC, credenziali, messaggi, spese, skill add/propagate, item VIETATO, reti d'impianto o di clienti).
3. **Niente `ric/` e niente `docs/knowledge/procedures/ric-*`.** VALIDATED è uno stato RIC, diverso dal nostro VERIFIED.
4. **Knowledge ≠ ACT**: offensivo, pwn, EDR, CTF, OSINT su persone, RE agent-wired → hard gate; nessun install senza APPROVA.
5. **Verify prima di agire**: classifica (NO_SKILL | DROP | VIETATO | UTILITY_CANDIDATE | STUDY_REF/CONCEPT); mai "installa tutto perché lo dice il README". Il legal gate vale anche dopo uno score verde.
6. **Un solo verdetto strutturato per turnata.** Cursor possiede READY / LIVE_CURSOR / OPERATIONAL ed è l'unica mano sui commit.
7. **Niente segreti**: non leggere, stampare o committare `.env`, token, chiavi, certificati o password; se ne trovi uno, segnala il path, non il valore.
8. **Niente invenzioni**: quello che non risulta da file letti è "da compilare" o "non verificato".

## 3. Progetto: SoT e path
| Voce | Valore |
|---|---|
| Repo GitHub (SoT codice) | `Pesach85/agent-me` (pubblico, fork) |
| Mirror Origin | no / non risulta. Se GitHub e Origin divergono: HITL founder, non scegliere la SoT |
| Path locale | da compilare |
| Branch | `main` (default da API GitHub) · HEAD `a107ca8a2ce8` osservato il 2026-10-08 (clone shallow read-only, solo albero) |
| Stack | linguaggio prevalente secondo l'API GitHub: nessuno indicato (dichiarato, non verificato su file: da compilare) |
| Descrizione GitHub | Distill your knowledge, memories, and decisions into an open-source, inspectable AI Agent Twin. |
| Ultimo push (API) | 2026-09-13T17:44:50Z (UTC) |
| Governance / Notion Projects | da compilare (Notion DB "Projects" non interrogato in questa passata) |
| Comandi build/test/smoke | da compilare |

### Contesto utile
- Categoria inventario: fork knowledge/memory.

### Architettura (contesto)
_Revisione 2026-10-16, metodo Cum scire, fonte GitHub `Pesach85/agent-me` @ `a107ca8a2ce8` (sola lettura)._
- **Stack**: backend Python ≥3.11 FastAPI + pydantic-settings (uv, ruff, pytest); frontend React 18 + Vite + TypeScript (vitest, eslint); Docker Compose [VERIFICATO: `backend/pyproject.toml`, `frontend/package.json`, `docker-compose.yml`, `Makefile` @`a107ca8a2ce8`]
- **Struttura** [VERIFICATO: albero @`a107ca8a2ce8`]:
  - `backend/` (app/, tests/, uv.lock, Dockerfile): API e workflow multi-agente
  - `frontend/` (src/, nginx.conf): interfaccia web
  - `knowledge/`: corpus Markdown (esempio `example-profile.md`); `course/`: corso 00-07 + `GLOSSARY.md`
  - `docs/`: ARCHITECTURE, API, TRUST, DEPLOYMENT; `scripts/`: check docs/versioni/dati privati, evaluate
- **Flusso dati**: domanda dal browser → `POST /api/v1/chat` o `/collaborate` → retrieval su Markdown in `knowledge/` → ruoli Planner/Researcher/Critic/Writer(/Verifier) → provider LLM esterno opzionale, altrimenti estratto migliore → risposta resa come testo [VERIFICATO: `docs/ARCHITECTURE.md`]
- **Comandi build/test** [VERIFICATO: `Makefile`, `.github/workflows/ci.yml` @`a107ca8a2ce8`]: `make setup`, `make test` (pytest backend + `npm test`), `make lint`, `make dev` (docker compose); solo sandbox
- **Confini / cosa NON toccare**: `.env` (solo `.env.example` versionato); `backend/uv.lock`, `frontend/package-lock.json`; tutto upstream (fork 0 avanti / 25 indietro rispetto a `jzjzzzzzzz/agent-me` [VERIFICATO: API compare 2026-10-16])
- **UI / design**: SPA React/Vite servita da nginx (container) [VERIFICATO: `frontend/`]; design system IGNOTO
- **Glossario**: *AI Twin* · *knowledge root* (cartella corpus) · *ruoli* (Planner/Researcher/Critic/Writer/Verifier) · *verified policy* (gate finale) · *provider* (LLM esterno opzionale)
- IGNOTO: 1 campo (design system UI)

## 4. Anti-job specifici (Claude qui NON fa)
- Non esegue script, installer, build o binari del repo fuori da un sandbox approvato.
- Non sincronizza il fork con upstream, non apre PR verso upstream, non cambia branch di default.
- Non riscrive la history e non propone di rimuovere file già committati (binari, chiavi) senza decisione del founder.
- Non installa skill o regole `.cursor/` (Tier 2, via CSG).

## 5. Ledger, registro e contesto flotta (dove leggere)
| Cosa | Dove | Accesso Claude |
|---|---|---|
| Costituzione + emendamento tier | box: `/workspace/BOT_CONSTITUTION_CSG_2026-10-06.md` · copia mailbox: da compilare | lettura |
| Ledger azioni autonome (append-only) | Notion https://app.notion.com/p/3f30bfdf2acf81c68915daf311ceefda · box: `/workspace/2026-10-08_LEDGER_azioni-autonome.md` | lettura; append di una riga solo per le proprie azioni Tier 0/1 |
| Registro flotta | Notion https://app.notion.com/p/3f30bfdf2acf816b978ec65324ec2a21 | lettura |
| Stato progetto | Notion DB "Projects" https://app.notion.com/p/4db5e5ef2f82499899da0dbdc75303f1 | lettura |
| Brief flotta | `/workspace/2026-10-08_BRIEF_flotta-cum-scire.md` e `_SHORT.md` | lettura |
| Mailbox verso Cursor | `D:\Work\_cursor_mailbox\` | vedi `CLAUDE_mailbox.md` |

Formato riga ledger: `| data ora (Europe/Rome) | chi | cosa | tier | blast radius | undo |`.

## 6. Commit e HITL (Cursor + founder)
- **Claude non fa commit, push, merge, rebase, tag, né apre o chiude PR.** Mai `--force`, mai `--no-verify`, mai riscrittura della history.
- Consegna standard: **diff unificato + file toccati + comando di verifica proposto + undo**. Il founder approva, Cursor committa.
- Scrivere nel working tree solo su richiesta esplicita del founder nella sessione corrente, solo sui path nominati, lasciando le modifiche non committate.
- Messaggio di commit suggerito (lo usa Cursor): `<tipo>(<area>): <cosa>` + `Refs: <NBD/task>` + `HITL: APPROVA <frase founder>`. Convenzione del repo: da compilare.
- Working tree sporco con lavoro non tuo: non toccarlo; segnala e chiedi.

## 7. Crediti on-demand (se i crediti sono bassi)
1. **Priorità**: (a) review di diff o packet già pronti; (b) verify mirate; (c) risposte brevi al founder. Per questo repo: solo letture mirate; questo fork ha priorità bassa.
2. **Niente refactor ampi**: al massimo una patch piccola e localizzata, se richiesta.
3. **Niente download di modelli** e niente install di dipendenze pesanti.
4. **Chiedi al founder prima di job lunghi** (scan dell'intero repo, test suite completa, multi-repo, più di circa 20 file letti, loop agentici): stima il costo in una riga e aspetta un sì.
5. Letture mirate; riusa verify e report già esistenti (dedup).
6. Prima di fermarti: nota di handoff in 5 righe (fatto, resta, file toccati, prossimo passo, rischi).

## 8. Da compilare a mano
- [ ] Path locale, convenzione di commit, riga Notion Projects (Status, Priority, Owner)
- [ ] Stack reale, comandi build/test/smoke, scopo del repo
- [ ] Decisione founder: questo repo ha davvero bisogno di un CLAUDE.md? (fork / legacy / vuoto / archiviato)
- [ ] Path mailbox di Costituzione e ledger
