---
name: ship-it
description: "Generates production deployment configs for your project. Use /ship-it to auto-detect your stack and generate Dockerfiles, CI/CD pipelines, docker-compose, env templates, and deployment scripts."
argument-hint: "[target: docker|ci|compose|env|all]"
allowed-tools: [Read, Write, Edit, Bash, Glob, Grep, Agent, TodoWrite]
---

# Ship It

You take projects from "works on my machine" to production-ready. Auto-detect the stack and generate deployment infrastructure.

## Phase 1: Detect Stack

Scan the project for:
- `package.json` → Node.js (check for Next.js, Vite, Express, etc.)
- `requirements.txt` / `pyproject.toml` → Python (Django, FastAPI, Flask)
- `go.mod` → Go
- `Cargo.toml` → Rust
- `Gemfile` → Ruby/Rails
- `pom.xml` / `build.gradle` → Java/Kotlin
- Database: look for Prisma, SQLAlchemy, TypeORM, Drizzle configs
- Existing Docker/CI files to enhance rather than replace

## Phase 2: Generate

Based on the argument (or "all" by default):

### Dockerfile
- Multi-stage build optimized for image size
- Non-root user for security
- .dockerignore file
- Layer caching optimization (deps before source)
- Health check endpoint

### CI/CD Pipeline (GitHub Actions)
- Lint → Test → Build → Deploy stages
- Caching for node_modules/pip/cargo
- Environment-specific deploy targets
- Secret references (not values)

### docker-compose.yml
- App + database + cache (Redis if applicable)
- Volume mounts for development
- Health checks and depends_on
- Environment variable files

### Environment Config
- `.env.example` with every variable documented
- Validation script or schema
- Sensible defaults for development
- Clear markers for production-only secrets

## Rules
- Never include actual secrets or credentials
- Always add .dockerignore and .env to .gitignore
- Prefer official slim/alpine base images
- Pin versions explicitly (no `latest` tags)
- Add comments explaining non-obvious choices
