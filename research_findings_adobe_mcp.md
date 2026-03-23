# Adobe Firefly & MCP Ecosystem — Research Findings

**Date:** 2026-03-23
**Context:** Research conducted via 3 parallel agents during an image generation session testing Gemini, DALL-E, and Firefly skills.

---

## Does Adobe Firefly Have an MCP Server?

**No official one. Community option exists. Adobe will likely ship one soon.**

---

## Official Adobe MCP Servers

| Product | MCP Server | Status |
|---------|-----------|--------|
| AEM (Experience Manager) | `mcp.adobeaemcloud.com/adobe/mcp/` (3 endpoints: content, content-readonly, cloudmanager) | Production |
| Adobe Express | `@adobe/express-developer-mcp` (npm) | Stable (was beta Sept 2025, GA March 2026) |
| Experience Platform | Agent Orchestrator (MCP + A2A protocols) | GA since Sept 2025 |
| Firefly | None official | — |
| Photoshop / Illustrator / Premiere | None official | Community-driven only |

---

## Firefly API (REST)

The Firefly API exists and is publicly accessible — not enterprise-only.

**Docs:** https://developer.adobe.com/firefly-services/docs/firefly-api/

### Capabilities

| Feature | API Endpoint | Notes |
|---------|-------------|-------|
| Text-to-Image | `POST /v2/images/generate` | Sync and async (v3) |
| Generative Fill | Available via API | Image + mask + prompt |
| Generative Expand | Available via API (v3 async) | Image + dimensions + prompt |
| Generate Similar | Available via API | Reference-based |
| Remove Background | `POST /v2/remove-background` | Automatic |
| Style Presets | Available | Predefined artistic styles |

### Pricing

| Tier | Cost |
|------|------|
| Free (web app) | 25 credits/month |
| Standard | ~$9.99/month |
| Pro | ~$19.99/month, 4000 premium credits |
| API (pay-as-you-go) | ~$0.02/standard, ~$0.08-0.10/premium per image |
| Enterprise | Contact sales |

### Authentication

OAuth Server-to-Server via Adobe Developer Console. Requires `FIREFLY_CLIENT_ID` and `FIREFLY_CLIENT_SECRET`. Access tokens valid 24 hours.

### Node.js SDK

```
npm i @adobe/firefly-apis @adobe/firefly-services-common-apis
```

GitHub: https://github.com/Firefly-Services/firefly-services-sdk-js

---

## Community MCP Server for Firefly

**python-firefly** by msabramo
- GitHub: https://github.com/msabramo/python-firefly
- MCP Market: https://mcpmarket.com/server/python-firefly
- Covers: text-to-image via Firefly API with MCP server mode
- Does NOT cover: Generative Fill, Expand, Remove (these ARE in the API but not wrapped in this MCP server)

---

## Community MCP Servers for Adobe Creative Suite

| Project | Apps | Link |
|---------|------|------|
| mikechambers/adb-mcp | Photoshop, Premiere, InDesign | https://github.com/mikechambers/adb-mcp |
| matrayu/adobe-mcp | Photoshop, Premiere, Illustrator, InDesign | https://github.com/matrayu/adobe-mcp |
| VoidChecksum/adobe-mcp | Full Creative Cloud + After Effects | https://github.com/VoidChecksum/adobe-mcp |
| hetpatel-11/Adobe_Premiere_Pro_MCP | Premiere Pro | https://github.com/hetpatel-11/Adobe_Premiere_Pro_MCP |
| dekdee/adobe-xd-mcp | Adobe XD | https://github.com/dekdee/adobe-xd-mcp |
| indrasishbanerjee/aem-mcp-server | AEM (35+ methods) | https://github.com/indrasishbanerjee/aem-mcp-server |
| EnventDigital/community-express-dev-mcp | Express add-on dev | https://github.com/EnventDigital/community-express-dev-mcp |

---

## Adobe-NVIDIA Partnership (March 16, 2026 — GTC)

Adobe and NVIDIA announced a strategic partnership covering:
- Next-generation Firefly models built on NVIDIA CUDA-X, NeMo, Cosmos, Agent Toolkit
- Agentic creative and marketing workflows
- Cloud-native 3D digital twin solution on NVIDIA Omniverse + OpenUSD
- Adobe Firefly Foundry integrating NVIDIA computing for enterprise-grade custom AI

**Signal:** This strongly suggests official agentic/MCP support for Firefly is coming.

---

## Key Insight

Adobe's MCP strategy is split:
- **Enterprise side** (AEM, Experience Platform, Commerce) → official MCP servers, production-ready
- **Creative desktop apps** (Photoshop, Illustrator, Premiere) → agentic features baked INTO the apps, not exposed as MCP
- **Firefly** → REST API exists with Fill/Expand/Remove, but no official MCP wrapper yet

The API already exposes everything needed for a full MCP server. When Adobe ships one, it will likely cover text-to-image, generative fill (with mask), generative expand, and background removal — making Chrome browser automation unnecessary.

---

## What We Learned Today (Firefly Browser Automation)

For now, using Firefly via Chrome automation (`/firefly` skill):
- Firefly UI uses deep Shadow DOM (4+ levels) — must use JavaScript to set prompt values
- Buttons are `SP-BUTTON` custom elements — must click via JS `deepFind()` traversal
- Generative Expand: drag canvas handles to create checkerboard area, then click Expand
- Generative Fill: paint pink selection with brush, enter prompt, click Fill
- Promotional banners can visually overlap action buttons — scroll to separate
- Adobe account login required — check page title for "Log In"
