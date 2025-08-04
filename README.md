# 🌀 Windsurf + Kilo Agent Workflow

This project follows a dual-agent AI architecture:

- **Windsurf** builds in iterative Patch/Batch cycles—generating code, tests, and docs.
- **Kilo** handles CI/CD, enforcing clean commits, version tags, and deploying to Vercel.

---

## 🚀 Available Slash-Commands (in Cascade)

| Command               | Description                          |
|-----------------------|--------------------------------------|
| `/pipeline`           | Scaffold Kilo CI/CD and version pipeline |
| `/plan-feature-set`   | Define patch‑N features and IM tasks |
| `/batch-start-N+1`    | Scaffold a new batch & patch folder, create windsprint branch |
| `/release-sync`       | Finalize batch, branch next sprint, invoke feature planning |

---

## 📁 Project Structure

src/
docs/
├─ guidelines.md
├─ batches/
└─ patches/
.windsurfrules.md (optional)
.gitignore
package.json
END_GOAL.md
README.md

---

## 🔁 Workflow Summary

1. Run `/pipeline` → generates `.github/workflows/kilo-pipeline.yml`
2. Create features via `/plan-feature-set`, `/batch-start-N+1`
3. Merge finished windsprint branch → Kilo runs CI/CD → deploys
4. After deploy, run `/release-sync` → generates next batch & patch
5. Repeat until `END_GOAL.md` is fully checked off.

---

## 🧩 GitHub Secrets & Variables

Your repo needs to define:
- Secrets: `VERCEL_TOKEN`, `NPM_TOKEN`
- Variables: `VERCEL_ORG_ID`, `VERCEL_PROJECT_ID`

These are used by Kilo for semantic-release + Vercel deployment.
