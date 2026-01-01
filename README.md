# go-devops-mastery

This is just my personal playground where I’m teaching myself Go + DevOps the hard way.

Right now (Dec 2025) I’m a complete beginner who only knows how to:
- Run `go run main.go`
- Make a tiny HTTP server that prints stuff
- Send JSON with curl

I started with Next.js/tRPC and got super confused because I never understood what was happening under the hood.  
So I decided to throw away all the magic and start from zero with Go backend + DevOps.

## What’s inside right now
Honestly, almost nothing yet:
- One folder with a very small Go server (just learning how HTTP, JSON, and goroutines work)
- A simple cpu-hog experiment with basic graceful shutdown and half-written code

## My other repo (where the real thing is growing)
→ https://github.com/Sushil911/chaosboard  
(that’s my mini Litmus Chaos project. Still super basic, but it’s the main thing I’m working on)

## Why this repo exists
So I can:
- Look back in 6 months and see the actual progress
- Show future employers or LFX reviewers that I actually learned things step by step

No fancy words, no fake progress.  
Just a guy from Nepal learning in public, one tiny commit at a time.

If you’re also grinding Go or DevOps and want to say hi, open an issue or DM me on X (@Sushil911). I’d love tips.

Still at the beginning.  
See you at the finish line someday.

– Sushil, December 2025

## Update: 23 Days Progress (December 8, 2025 – December 31, 2025)

December 2025 has ended, and it's been 23 days since I started learning DevOps + Backend in Go seriously. I've studied on around 18 days (78% consistency), with an average of 4–5 hours per day (max 8 hours, min 2 hours). The last few days were especially intense, and I learned more in them than in the first 19 combined.

Total estimated hours: ~90–100. Progress was linear at first with some plateaus (due to skipped days), but it accelerated sharply in the last week as concepts started connecting.

### What I've Learned
- **Go Backend**: Built a pure stdlib HTTP server with JSON API. Learned goroutines for background work, mutex for thread-safety, signal handling for graceful shutdown, BoltDB for embedded persistence.
- **Chaos Experiments**: Implemented cpu-hog (spin CPU), memory-hog (allocate RAM), disk-fill (write tmp files). Fire-and-forget execution with status updates.
- **Code Organization**: Refactored to proper packages (`internal/` layout) — makes code readable and maintainable.
- **DevOps Core**:
  - Multi-stage Dockerfile with dependency caching (copy go.mod first → fast builds).
  - Development stage with hot-reload (air + .air.toml).
  - Production stage using distroless nonroot (secure, tiny image).
  - Separate Docker Compose for dev (volumes + hot-reload) and prod (no volumes, restart policy).
- **Monitoring**: Prometheus metrics endpoint with custom counters (HTTP requests, durations, chaos total/active). prometheus.yml for scraping. Full stack with Grafana for dashboards.
- **Theoretical**: Data flow: App → /metrics → Prometheus scrapes → Grafana visualizes. Healthchecks, non-root users, Docker caching layers.

### Additional learnings(for my own OIDC compatible authentication server and zanzibar inspired authorization server )
- Deep dive into networking fundamentals: DNS resolution process (recursive resolver, root → TLD → authoritative), TCP three-way handshake, ports (well-known vs ephemeral), HTTP request-response cycle, TLS basics.
- OAuth 2.0 grant types in detail (Authorization Code, Implicit (deprecated), Client Credentials, Device Code, Refresh Token) and why Authorization Code + PKCE is the gold standard.
- PKCE (Proof Key for Code Exchange): code_verifier, code_challenge (S256 vs plain), full flow, and how it prevents code interception attacks.
- OpenID Connect (OIDC): Authentication layer on OAuth 2.0, ID Token (JWT with claims), discovery endpoint, JWKS, token endpoint, userinfo.
- Clear separation of Authentication (who you are – OIDC) vs Authorization (what you can do – later Zanzibar/SpiceDB).
- Tokens deep dive: ID Token (always JWT), Access Token (often JWT), Refresh Token (opaque), differences from session tokens.
- Real-world flow: "Login with Google" style redirects, state/nonce for security, PKCE integration.
- Wrote and published a detailed Hashnode article explaining OIDC + PKCE combined flow (step-by-step, security benefits, use cases for SPAs/mobile). Link: https://sushilbasyal.hashnode.dev/how-oidc-and-pkce-works-combinely
- Planned architecture for upcoming projects: OIDC microservice (user reg/login, token issuance, OTEL, Docker), Zanzibar-style authZ with SpiceDB, Form Builder SaaS, Advanced RAG with Inngest workflows.

### Challenges & Lessons(Chaosboard)
- Early days were slow due to skipped days — lost momentum.
- Docker caching and multi-stage builds confused me at first, but now I understand why they save so much time.
- Debugging compose networks and ports took time, but learned to use `docker compose logs`.
- No frameworks forced me to understand net/http deeply — slower but worth it.

### Challenges & Lessons(Auth server)
- The last 10 days diving into auth protocols (OAuth 2.0, OIDC, PKCE) felt overwhelming at first — so many endpoints, tokens, and security details. Spent hours just drawing flows on paper.
- Finally understood the real difference between Authentication (who you are – OIDC, ID Token) and Authorization (what you can do – Zanzibar/SpiceDB). This cleared up weeks of confusion.
- Writing the Hashnode article on OIDC + PKCE forced me to organize everything — best learning hack ever.
- Theory clicks way faster when you know you’re about to build it.

### Future Plans(Chaosboard)
- Build full Grafana dashboards for chaos metrics.
- Add more chaos types (network-latency, pod-kill).
- Write proper tests (`go test` with coverage).
- Set up GitHub Actions CI/CD (lint + test + build + Trivy scan).
- Deploy to Kubernetes (Minikube + manifests).
- Contribute to Meshery/LitmusChaos for LFX prep.

### Future Plans(Auth server)
- Start the real OIDC microservice in Go: fork zitadel/oidc, replace in-memory with Postgres, add registration/login, enforce PKCE, Dockerize, add OTEL tracing.
- Next: SpiceDB/Zanzibar authorization microservice (relationship tuples, recursive checks).
- Then Form Builder SaaS and Advanced RAG — all secured by my own auth system.

This is real progress — not hype. Excited for the next 30 days.