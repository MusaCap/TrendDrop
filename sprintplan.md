# 🏁 TrendDrop Sprint Plan for Windsurf

Each sprint is 2 weeks long and is structured for implementation in an agent-based AI IDE like Windsurf.

---

## 🧪 Sprint 0: Project Setup & Architecture

### Goals:
- Set up Windsurf project structure
- Define repo structure, CI/CD, and agent roles
- Create shared libraries (auth, API gateway, vector store)

### Tasks:
- [ ] Initialize GitHub repo and connect to Windsurf agents
- [ ] Set up MongoDB, PostgreSQL, Redis environments
- [ ] Configure backend and frontend scaffolding in Windsurf
- [ ] Create data models from spec
- [ ] Create agent tasks for `transcription`, `trend ingestion`, and `metadata generation`

### Outputs:
- Base repo + running dev environment
- Agent-based pipelines initialized
- Auth scaffolding ready

---

## 🧩 Sprint 1: Auth, Upload, and Transcription

### Goals:
- User onboarding
- Video upload pipeline
- Transcription agent

### Tasks:
- [ ] Implement email + OAuth login (Google, Apple)
- [ ] OAuth token storage logic (encrypted)
- [ ] Video upload UI and backend
- [ ] Whisper-based transcription agent
- [ ] Transcript and summary saved in MongoDB

### Outputs:
- Users can sign up, upload videos, and see transcriptions
- Test logs generated for multiple formats (.mp4, .mov)

---

## 🌍 Sprint 2: Trend Engine + Matching

### Goals:
- Ingest real-time trends
- Match uploaded content to current trends

### Tasks:
- [ ] Trend ingestion agents for:
  - TikTok Discover (scraper or API)
  - Twitter Trends API
  - Google News RSS
- [ ] Normalize trends into MongoDB
- [ ] Match transcript keywords + CLIP embeddings to trend database
- [ ] Store top 3 matches per video

### Outputs:
- Live trend database
- Video-to-trend matching visible in dashboard

---

## 🧠 Sprint 3: Metadata Generation & Editing

### Goals:
- Auto-generate titles, descriptions, and hashtags per platform
- UI for user edits

### Tasks:
- [ ] GPT-4 prompt tuning per platform (TikTok, YouTube Shorts, Instagram Reels)
- [ ] Create metadata generation agent
- [ ] Build metadata edit interface
- [ ] Save version history of edits

### Outputs:
- Users see suggested metadata
- Users can approve/edit before scheduling

---

## 🚀 Sprint 4: Scheduling & Publishing

### Goals:
- One-click publishing
- Smart scheduler

### Tasks:
- [ ] OAuth refresh handling for TikTok/YouTube/Instagram
- [ ] Smart scheduling logic (time zone, peak time suggestions)
- [ ] Publishing agent with API wrappers
- [ ] Post status and link returned to dashboard

### Outputs:
- User can publish directly to platforms
- Scheduled publishing works with queue retry logic

---

## 📊 Sprint 5: Analytics, Feedback Loop & Admin Tools

### Goals:
- Track performance
- Feed results back into model
- Admin logs and monitoring

### Tasks:
- [ ] Analytics API polling agent for each platform
- [ ] Visualize views/likes/CTR over time
- [ ] Compare metadata to engagement (basic ML loop)
- [ ] Admin job queue monitor
- [ ] Error logging + Slack alerts

### Outputs:
- Dashboard shows engagement
- Feedback signals inform future metadata generation
- Ops team gets alerts and job status in real time

---

## 🧪 Sprint 6: Final Integration & Testing

### Goals:
- Full-system integration test
- Edge-case handling
- Windsurf agents tuned

### Tasks:
- [ ] End-to-end test for upload → metadata → schedule → publish → analytics
- [ ] Run async workflows across agents
- [ ] UX polish and responsive UI pass
- [ ] Security audit and data retention policy check

### Outputs:
- Production-ready MVP
- Logged test cases and Windsurf automation coverage

---

## 🧱 Optional Future Sprints

- Sprint 7: Auto-clip generator (Autoclipper)
- Sprint 8: Multilingual metadata
- Sprint 9: Creator analytics and leaderboard
