<!-- ============================== HERO ============================== -->

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api?username=SecolDevs&show_icons=true&count_private=true&include_all_commits=true&hide_border=true&bg_color=0d1117&title_color=CC342D&icon_color=CC342D&text_color=c9d1d9&custom_title=GitHub%20stats" />
  <img align="right" width="400" alt="GitHub stats" src="https://github-readme-stats.vercel.app/api?username=SecolDevs&show_icons=true&count_private=true&include_all_commits=true&hide_border=true&bg_color=ffffff&title_color=CC342D&icon_color=CC342D&text_color=24292f&custom_title=GitHub%20stats" />
</picture>

<h1>Sebastian Colón</h1>

<h3>Sr. Software Engineer · AI Engineer</h3>

📍 Colombia &nbsp;·&nbsp; 🏠 Remote &nbsp;·&nbsp; 🗣️ English & Spanish

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=18&duration=2800&pause=800&color=CC342D&vCenter=true&width=400&height=32&lines=LLM+agents+%26+tool+use;Retrieval%3A+vector+%2B+graph;Speech%2C+voice+%26+video+AI;Evals%2C+guardrails+%26+LLMOps" alt="LLM agents & tool use · Retrieval: vector + graph · Speech, voice & video AI · Evals, guardrails & LLMOps" />

I design and ship **production AI systems**: agents, retrieval, and speech and video generation, along with the full-stack platforms they run on. I've been putting LLMs into production since early 2023.

**5 yrs** shipping &nbsp;·&nbsp; **1,000+** merged PRs &nbsp;·&nbsp; **1,700+** commits &nbsp;·&nbsp; **40+** repos

<!-- Add your links here, e.g.
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/your-handle)
[![Portfolio](https://img.shields.io/badge/Portfolio-CC342D?style=flat-square&logo=googlechrome&logoColor=white)](https://your-site.com)
-->

<br clear="right"/>

<!-- ========================== ACHIEVEMENTS ========================== -->

### 🏆 Achievements

<table>
  <tr>
    <td align="center" width="25%">
      <a href="https://github.com/SecolDevs?tab=achievements"><img src="assets/achievements/pull-shark-gold.png" width="76" alt="Pull Shark x4" title="Pull Shark x4: 1,024+ merged pull requests" /></a><br/>
      <b>Pull Shark</b> <code>x4</code><br/>
      <sub>Gold · 1,024+ merged PRs</sub>
    </td>
    <td align="center" width="25%">
      <a href="https://github.com/SecolDevs?tab=achievements"><img src="assets/achievements/pair-extraordinaire-silver.png" width="76" alt="Pair Extraordinaire x3" title="Pair Extraordinaire x3: co-authored merged pull requests" /></a><br/>
      <b>Pair Extraordinaire</b> <code>x3</code><br/>
      <sub>Silver · co-authored PRs</sub>
    </td>
    <td align="center" width="25%">
      <a href="https://github.com/SecolDevs?tab=achievements"><img src="assets/achievements/quickdraw.png" width="76" alt="Quickdraw" title="Quickdraw: closed an issue or PR within 5 minutes" /></a><br/>
      <b>Quickdraw</b><br/>
      <sub>Fast turnaround</sub>
    </td>
    <td align="center" width="25%">
      <a href="https://github.com/SecolDevs?tab=achievements"><img src="assets/achievements/yolo.png" width="76" alt="YOLO" title="YOLO: merged a pull request without review" /></a><br/>
      <b>YOLO</b><br/>
      <sub>Shipped it</sub>
    </td>
  </tr>
</table>

---

## 🤖 AI Engineering

<table>
  <tr>
    <td width="33%" valign="top">
      <b>🧠 Agents & tool use</b><br/>
      <sub>Planner and executor loops, typed tools, policy gates, human-in-the-loop approval, context compression, MCP servers.</sub>
    </td>
    <td width="33%" valign="top">
      <b>🔎 Retrieval & grounding</b><br/>
      <sub>Hybrid vector, keyword and knowledge-graph retrieval, code-aware indexing, citation-backed generation.</sub>
    </td>
    <td width="33%" valign="top">
      <b>🎙️ Speech, voice & video</b><br/>
      <sub>Long-form transcription with diarization, voice-cloned TTS, AI-directed video and motion graphics.</sub>
    </td>
  </tr>
  <tr>
    <td width="33%" valign="top">
      <b>🧪 Evals & guardrails</b><br/>
      <sub>Real-model eval suites, output filters, schema validation, redaction, SSRF-safe tools.</sub>
    </td>
    <td width="33%" valign="top">
      <b>💸 LLMOps & cost</b><br/>
      <sub>Per-request token and cost tracking, budget ceilings, rate limiting, graceful degradation.</sub>
    </td>
    <td width="33%" valign="top">
      <b>🧩 Multi-provider</b><br/>
      <sub>OpenAI, Anthropic, DeepSeek, OpenRouter and ElevenLabs, via LangChain, LangGraph and the AI SDK.</sub>
    </td>
  </tr>
</table>

**Highlights**

- 🤖 Built an **autonomous coding agent** that plans, writes code and tests, and opens pull requests. It has **340+ commits** in production repositories.
- 📚 Shipped **LLM content generation** grounded in retrieved, cited sources, with human review before anything is published.
- 🎬 Built **speech and generative-video pipelines**: hour-long recordings to diarized transcripts, and text to voiced, rendered video.
- 🔌 Made a SaaS product **AI-native** with an OAuth 2 provider and an **MCP server**, so AI assistants can act on a user's behalf.
- ⚡ Rolled out my first LLM service in **early 2023** and have kept shipping AI features ever since.

---

## 🏛️ Reference architectures

These are the blueprints I start from when designing AI systems, generalized from years of production work. Client systems are confidential, so these show the approach, not any specific product.

<details open>
<summary><b>① Tool-gated agent runtime</b>: an agent that can act safely</summary>
<br/>

```mermaid
flowchart LR
  IN([User · event · schedule]) --> ORCH[Orchestrator<br/>explicit state machine]
  ORCH --> PLAN[Planner LLM]
  PLAN --> ROUTER{Tool router}
  ROUTER --> READ[Read tools<br/>search · retrieve · inspect]
  ROUTER --> WRITE[Write tools<br/>schema-validated]
  READ --> MEM[(Working memory<br/>compressed context)]
  MEM --> PLAN
  WRITE --> GATE{Policy gate<br/>confirm · budget · scope}
  GATE -->|allowed| ACT[Side effects<br/>APIs · data · PRs]
  GATE -->|needs a human| HITL[Review queue]
  HITL --> ACT
  ACT --> OBS[(Traces · cost · eval logs)]
```

- **The model proposes; code decides.** Read tools run freely, but every write tool passes a policy gate (confirmation, budget, permission scope) before it has side effects.
- **Explicit state machine** instead of an open-ended loop, with recursion limits and resumable steps.
- **Context compression** keeps long sessions inside the token budget without losing the plan.

</details>

<details>
<summary><b>② Grounded retrieval (hybrid RAG)</b>: answers you can trace to a source</summary>
<br/>

```mermaid
flowchart LR
  subgraph Ingestion
    SRC[Docs · web · media] --> NORM[Normalize<br/>and sanitize] --> CH[Chunk + metadata]
    CH --> EMB[Embed]
    CH --> ENT[Entity and<br/>relation extraction]
  end
  EMB --> VEC[(Vector store)]
  ENT --> KG[(Knowledge graph)]
  CH --> KW[(Keyword index)]
  Q([Query]) --> RW[Query rewrite] --> HYB{Hybrid retrieval}
  VEC & KG & KW --> HYB
  HYB --> RR[Rerank + dedupe] --> GEN[Generate<br/>with citations]
  GEN --> CHK{Grounding check}
  CHK -->|pass| OUT([Answer + sources])
  CHK -->|retry| HYB
```

- **Three retrievers, one ranking.** Vectors catch meaning, keywords catch exact names, and the graph catches relationships.
- **Citations are required, not optional.** An answer that can't point back to its sources goes back to retrieval or to a human reviewer.
- **Ingestion is part of the product.** Sanitizing, deduplicating and keeping provenance metadata matter more than the choice of embedding model.

</details>

<details>
<summary><b>③ Multimodal media pipeline</b>: speech, vision and video at scale</summary>
<br/>

```mermaid
flowchart LR
  UP([Upload · URL]) --> API[Ingest API] --> BUS[[Event bus / queue]]
  BUS --> STT[Speech-to-text<br/>chunk · align · stitch]
  BUS --> VIS[Vision<br/>OCR · moderation · tagging]
  STT & VIS --> LLM[LLM structuring<br/>summaries · scripts]
  LLM --> TTS[Text-to-speech]
  TTS --> REN[Render workers<br/>headless browser + ffmpeg]
  REN --> OBJ[(Object storage + CDN)]
  OBJ --> OUT([Players · embeds · feeds])
```

- **Stream, don't copy.** Pull only the track you need (audio for speech, frames for vision) straight from the source.
- **Chunk, align, then stitch.** Each chunk's timestamps and labels are mapped back onto one shared timeline before results are merged.
- **Rendering is just another worker.** Stateless, horizontally scalable, with frame-level tests on the output.

</details>

<details>
<summary><b>④ LLM gateway & LLMOps</b>: one control plane for every model call</summary>
<br/>

```mermaid
flowchart LR
  APPS([Apps · agents · jobs]) --> GW[LLM gateway<br/>auth · quotas · rate limits]
  GW --> RED[Redaction]
  RED --> ROUTE{Model router<br/>task · cost · latency}
  ROUTE --> P1[Frontier models]
  ROUTE --> P2[Small / open-weight models]
  ROUTE --> P3[Speech · vision models]
  P1 & P2 & P3 --> VAL[Output validation<br/>schema · policy]
  VAL --> APPS
  GW -.-> TEL[(Usage · cost · traces)]
  TEL -.-> EVAL[Eval harness<br/>regression suites]
```

- **Each task gets the cheapest model that passes its evals.** Frontier models are for the hard cases only.
- **Budgets are enforced, not just reported.** Hard ceilings per tenant or feature, with a deterministic fallback when a limit is hit.
- **Evals gate changes.** A model, prompt or provider swap ships only after the regression suite passes.

</details>

---

## 🧰 Tech stack

| | |
|---|---|
| **AI / LLM** | ![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square) ![Anthropic](https://img.shields.io/badge/Anthropic_Claude-D97757?style=flat-square&logo=anthropic&logoColor=white) ![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white) ![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logo=langgraph&logoColor=white) ![Vercel AI SDK](https://img.shields.io/badge/AI_SDK-000000?style=flat-square&logo=vercel&logoColor=white) ![MCP](https://img.shields.io/badge/Model_Context_Protocol-000000?style=flat-square&logo=modelcontextprotocol&logoColor=white) ![Whisper](https://img.shields.io/badge/Whisper_%2F_STT-412991?style=flat-square) ![ElevenLabs](https://img.shields.io/badge/ElevenLabs_TTS-000000?style=flat-square&logo=elevenlabs&logoColor=white) ![DeepSeek](https://img.shields.io/badge/DeepSeek-4D6BFE?style=flat-square) ![OpenRouter](https://img.shields.io/badge/OpenRouter-6566F1?style=flat-square&logo=openrouter&logoColor=white) ![tree-sitter](https://img.shields.io/badge/tree--sitter-2E7D32?style=flat-square) ![tiktoken](https://img.shields.io/badge/tiktoken-412991?style=flat-square) |
| **Vector & graph** | ![Qdrant](https://img.shields.io/badge/Qdrant-DC244C?style=flat-square&logo=qdrant&logoColor=white) ![pgvector](https://img.shields.io/badge/pgvector-336791?style=flat-square&logo=postgresql&logoColor=white) ![FalkorDB](https://img.shields.io/badge/FalkorDB_(graph)-FF4438?style=flat-square&logo=redis&logoColor=white) ![Elasticsearch](https://img.shields.io/badge/Elasticsearch-005571?style=flat-square&logo=elasticsearch&logoColor=white) |
| **Languages** | <img src="https://skillicons.dev/icons?i=py,ruby,ts,js,php,bash&theme=dark" alt="Python, Ruby, TypeScript, JavaScript, PHP, Bash" /> |
| **Backend** | <img src="https://skillicons.dev/icons?i=fastapi,django,flask,rails,nestjs,nodejs,express&theme=dark" alt="FastAPI, Django, Flask, Rails, NestJS, Node.js, Express" /> <br/> ![Sidekiq](https://img.shields.io/badge/Sidekiq-B1003E?style=flat-square&logo=sidekiq&logoColor=white) ![BullMQ](https://img.shields.io/badge/BullMQ-DC382D?style=flat-square&logo=redis&logoColor=white) ![Hono](https://img.shields.io/badge/Hono-E36002?style=flat-square&logo=hono&logoColor=white) ![Socket.IO](https://img.shields.io/badge/Socket.IO-010101?style=flat-square&logo=socketdotio&logoColor=white) |
| **Frontend** | <img src="https://skillicons.dev/icons?i=react,nextjs,redux,tailwind,materialui,vite&theme=dark" alt="React, Next.js, Redux, Tailwind, MUI, Vite" /> <br/> ![Remotion](https://img.shields.io/badge/Remotion-0B84F3?style=flat-square) ![GSAP](https://img.shields.io/badge/GSAP-0AE448?style=flat-square&logo=greensock&logoColor=black) ![Zustand](https://img.shields.io/badge/Zustand-443E38?style=flat-square&logo=react&logoColor=white) |
| **Data** | <img src="https://skillicons.dev/icons?i=postgres,mysql,redis,sqlite,firebase,prisma&theme=dark" alt="PostgreSQL, MySQL, Redis, SQLite, Firebase, Prisma" /> <br/> ![Drizzle](https://img.shields.io/badge/Drizzle_ORM-C5F74F?style=flat-square&logo=drizzle&logoColor=black) ![Neon](https://img.shields.io/badge/Neon-00E599?style=flat-square&logo=neon&logoColor=black) |
| **Cloud & DevOps** | <img src="https://skillicons.dev/icons?i=gcp,aws,kubernetes,docker,terraform,githubactions,vercel,nginx&theme=dark" alt="GCP, AWS, Kubernetes, Docker, Terraform, GitHub Actions, Vercel, Nginx" /> <br/> ![Cloud Run](https://img.shields.io/badge/Cloud_Run-4285F4?style=flat-square&logo=googlecloud&logoColor=white) ![GKE](https://img.shields.io/badge/GKE-4285F4?style=flat-square&logo=googlecloud&logoColor=white) ![Pub/Sub](https://img.shields.io/badge/Pub%2FSub-4285F4?style=flat-square&logo=googlecloud&logoColor=white) ![AWS Lambda](https://img.shields.io/badge/AWS_Lambda-FF9900?style=flat-square) ![CircleCI](https://img.shields.io/badge/CircleCI-343434?style=flat-square&logo=circleci&logoColor=white) ![Traefik](https://img.shields.io/badge/Traefik-24A1C1?style=flat-square&logo=traefikproxy&logoColor=white) |
| **Quality** | ![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white) ![RSpec](https://img.shields.io/badge/RSpec-CC342D?style=flat-square&logo=ruby&logoColor=white) ![Jest](https://img.shields.io/badge/Jest-C21325?style=flat-square&logo=jest&logoColor=white) ![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat-square) ![Sentry](https://img.shields.io/badge/Sentry-362D59?style=flat-square&logo=sentry&logoColor=white) |

---

## 🧱 Full-stack & platform foundation

AI features are only as good as the platform under them. I also own the rest of the stack:

- **Large production monoliths and microservices.** I keep long-lived Rails codebases healthy (version upgrades, refactors, query tuning) and build Python and Node services alongside them.
- **Multi-tenant SaaS.** Tenant isolation with Postgres row-level security, subdomain routing, and subscription billing.
- **Event-driven back ends.** Queues, background workers, webhooks with signature verification, and real-time sockets.
- **Cloud and infrastructure as code.** Terraform on AWS and GCP, Kubernetes and Cloud Run, and CI/CD across staging, preprod and production.
- **Payments and integrations.** Stripe, Mercado Pago, Shopify, Twilio, and accounting, ad-server and messaging APIs.

---

## 🧠 How I build

- 🔒 **The model writes, code decides.** LLMs never change state directly. Typed tools, validation and human review sit in between.
- 💸 **Cost is a feature.** Token tracking, budget ceilings, and a deterministic fallback when a model is unavailable or over budget.
- 🧪 **Evals before vibes.** Every prompt, model or provider change runs against regression suites built from real-model outputs.
- 🛡️ **Secure by default.** SSRF guards, signed webhooks, rate limiting, redaction, and no secrets in repos.
- 📝 **Write it down.** Architecture docs, ADRs, runbooks, and `AGENTS.md` / `CLAUDE.md` files so humans and AI agents both onboard fast.
- 🤝 **AI-augmented workflow.** I work with Claude Code, Cursor and MCP every day, and I build the tooling that makes teams faster with them.

---

## 💼 Experience

| Period | Domain | Focus |
|---|---|---|
| **2022 – present** | 📰 Media & ad-tech SaaS | AI and full-stack engineering on a large production platform: retrieval-grounded LLM content, speech and generative video, agentic developer tooling, MCP integrations, and the Python and Node AI services around them on GCP. |
| **2022 – 2025** | 🏋️ Vertical SaaS (fitness) | Full-stack product work, AWS infrastructure as code, and an early LLM service (2023). |
| **2022** | 🛒 E-commerce | TypeScript back end and front ends, payments, and real-time features. |
| **2025** | 🚚 Logistics | Optimization service built on linear programming. |
| **2024 – present** | 🚀 Independent studio | AI-first SaaS products for Latin American markets, including conversational agents, multi-tenant platforms and local payments. |

---

## 📈 GitHub activity

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://streak-stats.demolab.com?user=SecolDevs&hide_border=true&background=0D1117&stroke=30363D&ring=CC342D&fire=CC342D&currStreakLabel=CC342D&currStreakNum=C9D1D9&sideNums=C9D1D9&sideLabels=8B949E&dates=8B949E" />
  <img width="49%" alt="GitHub streak" src="https://streak-stats.demolab.com?user=SecolDevs&hide_border=true&background=FFFFFF&stroke=D0D7DE&ring=CC342D&fire=CC342D&currStreakLabel=CC342D&currStreakNum=24292F&sideNums=24292F&sideLabels=57606A&dates=57606A" />
</picture>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-activity-graph.vercel.app/graph?username=SecolDevs&bg_color=0d1117&color=c9d1d9&title_color=CC342D&line=CC342D&point=f0f6fc&area=true&area_color=CC342D&hide_border=true&custom_title=Contribution%20activity" />
  <img width="100%" alt="Contribution activity graph" src="https://github-readme-activity-graph.vercel.app/graph?username=SecolDevs&bg_color=ffffff&color=24292f&title_color=CC342D&line=CC342D&point=24292f&area=true&area_color=CC342D&hide_border=true&custom_title=Contribution%20activity" />
</picture>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/SecolDevs/SecolDevs/output/github-snake-dark.svg" />
  <img width="100%" alt="Contribution snake animation" src="https://raw.githubusercontent.com/SecolDevs/SecolDevs/output/github-snake.svg" />
</picture>

</div>

<!--
Most of my work happens in private org repositories. For the charts above to reflect it:
GitHub → Settings → Public profile → Contributions & activity → enable "Include private contributions on my profile".
The snake is regenerated every 12 hours by .github/workflows/snake.yml (output branch: `output`).
Achievement badges are local copies in assets/achievements/. Swap the image and tier when one levels up.
-->

---

<div align="center">
<sub>Building AI systems that are useful, affordable, and safe to let act.</sub>
</div>
