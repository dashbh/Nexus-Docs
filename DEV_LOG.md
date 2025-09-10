# Nexus Project Development Log 📈

This file is a running journal of daily progress.  
Each entry: **Date → What I did → What’s pending → Next task**  

---
## Completed Work (Prefilled Log) ✅

### Nexus-BE 🖥️

* Created **pnpm turborepo monorepo** with base microservices & packages
   * Services: `gateway`, `trading`, `findata`, `notification`
   * Packages: `@nexus/types`, `@nexus/validation`, `@nexus/utils`, `@nexus/config`, `@nexus/errors`, `@nexus/proto`
* Connected microservices via **TCP transport**, with **gateway exposed over HTTP**
* Setup **Turbo** for dependency install & build ⚡
* Services currently serve **static JSON responses**
* Deployment workflow: 🚀
   * GitHub Actions build on PR creation
   * On merge → builds packages, creates artifact with Makefile, pushes to EC2 via rsync
   * After push → `pnpm install` runs on EC2, `pm2` restarts services
* EC2 connection secured via **GitHub Action environment variables** 🔐
* **pm2** used for process management (only `gateway` exposed on port 3000, others internal)
* No database connection integrated yet ❌

### Nexus-FE 💻

* Created **Next.js 14 + TypeScript repo**, deployed to **Vercel**
* Integrated stack: **TailwindCSS, shadcn/ui, Redux Toolkit, RTK Query**
* Pages implemented: 📄
   * `/login`: Basic authentication form
   * `/portfolio`: Holdings, current value, P&L
   * `/market`: Real-time stock prices & data
   * `/orders`: Order history with sorting, filtering, actions
* UI currently uses:
   * **Mock JSON server endpoints** for local dev 🔧
   * **Nexus-BE mock JSON endpoints** for Vercel deployment
* Basic functionality in place, but components are **large + need breakdown/refactoring** ⚠️

---

## 📅 Daily Log

```
### 2025-09-10
✅ Completed
- [BE] Setup mock json for all services 🗄️
- [FE] Configured env variable in vercel to point to EC2 url for API's 🔧
- [Infra/CI/CD] Verified GitHub Actions pipeline ✅
- [Notes/Issues] N/A ⚠️

🎯 Next
- Implement CRUD APIs with DB Connection
```
