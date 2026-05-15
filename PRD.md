# Squash Platform — PRD

> The platform ships under Ahad's existing **ARProformance** brand (squash-
> focused — see `BRAND.md`). "SquashIQ" was rejected at kickoff (transcript
> 16:06); the multi-sport ambition is real but stays a later, separately-
> branded play — squash is the wedge, not the ceiling.

Sources: kickoff transcript with Ahad Raza (2026-05-10), four FigJam boards
("Athlete workflows", "Coaching workflows", assessment sub-flow,
"Parent/Guardian flows") on the SquashIQ Workflows board, a prototype-review
transcript with Ahad (2026-05-10 evening — see §11), and `BRAND.md` (the
ARProformance design system, shared 2026-05-15).

UX framing draws on Cooper, *About Face* (4e) and Tidwell, *Designing
Interfaces* (2e/3e). Specific references are inline.

---

## 1. Vision

An athlete management system with an *ARProformance* coaching lens. It
replaces the scattered surface area today's coaches use (Gmail drafts,
WhatsApp, Notion, ad-hoc Google Docs, ChatGPT for brainstorming) with a single
mobile-first surface for planning sessions, capturing notes, assigning work,
and tracking athlete development. Squash is the wedge market; the data model
and flows should generalize to other 1:1 / small-group coached sports.

The "ARProformance coaching lens" is a goal-setting + assessment framework Ahad
uses in practice — Vision → Outcome Goals → Process Goals, paired with
assessment across physical / mental / technical / tactical dimensions. It is
not a content library or curriculum; it is the structured way the platform
asks coaches and athletes to think.

## 2. Problem

Ahad's current workflow (transcript 15:57–16:05):

- Session plans live as a single ever-growing **Gmail draft**, dated entries
  appended chronologically, because Gmail is "the first most convenient thing
  that comes to my mind … I'm on it all the time."
- Post-session reflection, Zoom AI summaries, athlete videos, WhatsApp
  check-ins, Notion experiments, and occasional ChatGPT brainstorms are all
  separate surfaces. Nothing reconciles them.
- Homework follow-up is inconsistent: "Do I check in with every single person?
  No." Coaches' prospective memory is the only thing tracking outstanding work.
- Most other coaches do even less: hand off a verbal "do your homework, see
  you next week," with no persistent thread.

About Face Ch 12 (Eliminating Excise) names the central thesis: every minute
a coach spends *reconstructing context* between sessions is excise — work that
doesn't advance the coaching goal. The product's job is to make that excise
go away.

## 3. Goals & non-goals

### Goals
- Reduce coach admin time per athlete per week
- Centralize planning, notes, assignments, and progress for both sides
- Give athletes a single surface for goals, upcoming sessions, outstanding
  work, feedback, and progress
- Give parents/guardians a passive, read-mostly view of their child's plan
  and progress
- Mobile-first; usable court-side, one-handed, on patchy reception

### Non-goals (initial release)
- Video analysis tooling (annotation, AI shot tagging, drawing on frames)
- Payments / billing (flagged in Figma but explicitly deferred — see §10)
- Multi-sport at launch; architecture must not block it but UI is squash-tuned
- Tournament management / live scoring
- Coach discovery / marketplace
- LMS-style admin for academies (rosters, invoicing, CRM)

## 4. Personas

About Face Ch 3.

### 4.1 Coach — primary
Manages a roster of private students and group clinic regulars. Plans the
night before, refines court-side. Phone-heavy with occasional laptop use.

- **End goals**: deliver a well-prepared session in minimum prep time;
  remember why each student is working on what they're working on.
- **Experience goals**: feel organized; stop chasing students for missing work.
- **Life goals**: get evenings back; see students improve faster.

Posture (About Face Ch 9): **transient** on mobile (glance + dictate),
**sovereign** on desktop (Sunday lesson planning across the whole roster).

### 4.2 Athlete — primary
Receives session plans, completes assigned work (video clips, written
reflections), sees their own goals and progress. Today: WhatsApp + verbal
handoffs; nothing persistent.

Posture: transient mobile. Opens app, looks at "what am I doing today / what's
outstanding," acts, closes.

### 4.3 Parent / Guardian — secondary
Wants visibility into child's upcoming sessions, what's planned, and how
they're progressing. Read-mostly. May need scheduling / billing controls later.

### 4.4 Anti-persona
The coach who wants a full CRM + invoicing + roster-management console. Not
who we're optimizing for.

## 5. Key user journeys

Mapped from the four FigJam boards.

### 5.1 Coach: onboard a new athlete

1. Add athlete to repository
2. Optionally schedule a skill assessment
3. Pick assessment type(s) (multi-select): skill + fitness, self-awareness
   questionnaire, video match analysis
4. System generates default assessment from template, or coach authors custom
5. Conduct assessment (on-court or off-court depending on type), record results
6. Results saved against athlete profile
7. Prompt: build out vision + outcome goals + process goals

Alternate ordering: goals first → prompted to conduct assessment.

Pattern (Tidwell Ch 2): **Wizard** with an **Escape Hatch** (Ch 3) — assessment
realistically spans multiple sittings, so the flow must resume cleanly.

### 5.2 Coach: plan + deliver a private lesson

1. Athletes → pick athlete → "Create new session"
2. Session builder shows a context rail: top outcome goals, top process goals
   (max 3, per the FigJam sticky), recent notes from the last few sessions
   (coach + athlete)
3. Coach picks an **intended focus** for the session
4. Optional: apply or save a template structured around drills / exercises
5. Save or Start
6. During / after session: add notes (typed or voice-dictated)
7. Session logs to athlete timeline

Pattern (Tidwell Ch 5): context rail is a **Two-Panel Selector** or **List
Inlay**. The context rail is the highest-leverage piece of UX in the whole
product — it's what replaces the Gmail draft scroll-back.

### 5.3 Coach: plan + deliver a group clinic

1. Schedule → "Group lesson"
2. Pick the players in the clinic
3. Pick or build a session (same builder as private lesson)
4. Edit
5. "Start the group clinic now" or "Save session" for later
6. During clinic:
   - List of all enrolled players (regardless of attendance — coach marks
     attendance live)
   - Per-player notes (text or voice dictation)
   - Optional: assign players to specific courts (later-phase)
7. End → send each player their own notes

### 5.4 Coach: follow up on outstanding work

- Home / per-athlete view surfaces "outstanding" items past due
- Per-task **Nudge** action sends a notification to the athlete
- Once submitted, item leaves the outstanding queue

Tidwell Ch 1 — **Prospective Memory**: the system becomes the coach's
external memory for "I asked X to send a video by Tuesday." This is what
makes the platform *more* than a notes app.

### 5.5 Athlete: day-of

1. Open home → today's session + intended focus
2. Check outstanding (homework due, reflections pending)
3. Complete what's quick now (write reflection, upload clip)
4. Post-session: receive coach notes via push + in-app

### 5.6 Athlete: long-term

- "Plan" tab: my vision, my outcome goals, current process focus
- "Progress" tab: assessment benchmarks over time, qualitative coach feedback,
  reward / streak signals for timely task completion

### 5.7 Parent / Guardian

- Home: child's upcoming schedule, recent items
- "What's being planned": read view of session plans
- "Progress": benchmarks + qualitative feedback + line chart over time

## 6. Functional requirements

### 6.1 Athlete repository (coach)
Add, edit, archive athletes. Per athlete: contact info, parent/guardian link
(if minor), assessment history, vision, goals (outcome + process), session
history, attachments, notes (shared + private — see §10).

### 6.2 Vision & goals (ARProformance framework)
- Vision: free-text, athlete's big-picture ambition
- Outcome goals: results-oriented, time-bounded (e.g., "state champion by 2027")
- Process goals: behaviors / habits / skill priorities (e.g., "backhand wrist
  stability under pace")
- Goals are referenceable from session planning and visible to athlete + parent

### 6.3 Assessments
- Default templates: skill + fitness, self-awareness questionnaire
- Categories: physical, mental, technical, tactical
- Coach can clone, customize, or author from scratch
- Multi-select assessment types per athlete
- Scoring is **per-drill, not cumulative** — a single total masks real
  per-skill improvement (transcript 20:48). Trend lines are per-drill.
- Results stored on athlete profile; feed progress chart

### 6.4 Session planning
- A coach's **own previous sessions are the primary reuse mechanism** (reusable
  across any of their students); named templates are a secondary option behind
  a dropdown. Session-level only — no multi-week program templates, since
  squash skill work is too varied for a generic plan (transcript 20:51)
- Auto-populated context rail: top outcome/process goals + recent notes
- Pick an intended focus (single vs multi — open question §10)
- Group clinic variant: draws on the cohort roster (§6.10); court assignments
  (later)

### 6.5 Session logging
- Per-athlete notes: text + voice dictation → transcription
- Quick-attach photo or short video clip
- Coach can **amend past session notes/reflections** after the fact — sessions
  are not frozen in time (transcript 21:22)
- Send notes to each athlete post-session (push + in-app)
- Attendance tracking for group clinics; clinic notes go to **all enrolled
  players, even absentees** (transcript 21:17), and drills / court assignments
  can be **pre-published** so players know the focus before arriving

### 6.6 Assignments / homework
- Coach assigns a task with a due date
- Types: written reflection, video clip upload, drill checklist
- Athlete completes in-app
- Coach reviews; reviewed items leave the outstanding queue

### 6.7 Notifications
- In-app + push (mobile)
- Triggers: new session scheduled, new notes from coach, new assignment,
  assignment overdue, coach nudge, milestone reached
- Email digest as fallback (open question §10)

### 6.8 Progress tracking
- Assessment benchmarks over time, visualized as a line chart per metric
  (Tidwell Ch 7: **Multi-Y Graph** or small multiples)
- Qualitative feedback timeline from coach
- Reward / streak signals for timely completion (FigJam sticky:
  "Reward system for timely execution of tasks")
- Long-term V5+: match-result repository, W/L vs opponents, strengths /
  weaknesses surfaced from match notes

### 6.9 Roles & permissions
- **Coach**: full read/write on their roster
- **Athlete**: read/write on own profile; read on coach's session plan; write
  notes + reflections + uploads
- **Parent/Guardian**: read-only on linked athlete, plus **message the coach**
  (transcript 21:19). Schedule / pay scope — still open §10
- Future: academy / head-coach role; multi-coach per athlete

### 6.10 Cohorts / groups
- Coach **creates a cohort once** (e.g. per term / 3-month block) rather than
  re-picking players for every group session (transcript 21:27)
- Cohort has its own page: roster, per-member performance trends, **group
  messaging**
- Group-clinic scheduling (§5.3) draws on the cohort roster
- Later-phase gamification rides on the cohort: within-cohort leaderboard,
  team-vs-team skill-assessment challenges (e.g. "4C vs River Grove"),
  player-vs-player "throw down" challenges (transcript 21:23–21:27)

## 7. UX principles

These are the lenses every screen review uses.

1. **Excise minimization** (About Face Ch 12). Every screen audited on: what
   fraction of clicks here actually move the coach toward delivering a better
   session?
2. **Goal-directed defaults** (About Face Ch 1; Tidwell Ch 8 *Good Defaults and
   Smart Prefills*). The session planner pre-fills focus from goals + recent
   notes. The athlete home pre-fills "today" from the schedule.
3. **Mobile-first, transient posture** (About Face Ch 9, Ch 19). One-handed,
   court-side, large tap targets, voice over typing where possible. Tidwell
   mobile patterns: *Bottom Navigation*, *Vertical Stack*, *Touch Tools*,
   *Generous Borders*.
4. **One surface, not five.** The product wins iff it replaces Gmail draft +
   WhatsApp + Notion + ChatGPT with a single home. Tidwell mobile:
   *Richly Connected Apps* — handoffs to phone camera / files / calendar are
   first-class.
5. **External memory for the coach** (Tidwell Ch 1 *Prospective Memory*). The
   system tracks "I asked X to do Y by Tuesday." Coaches stop holding it in
   their head.
6. **Forgiving capture** (Tidwell Ch 8 *Forgiving Format*; About Face Ch 15).
   Voice notes, half-finished session plans, partial assessments all save
   without coercion. Easy undo, no destructive modals.
7. **Overview + detail everywhere** (Tidwell Ch 7). The coach never drills
   three levels to remember why an athlete is working on backhand technique
   this month — that "why" rides along with the session view.
8. **Habituation-friendly navigation** (Tidwell Ch 1 *Habituation* /
   *Spatial Memory*). Stable bottom nav, consistent placement of "Start
   session." The coach uses this many times a day; muscle memory matters.

## 8. Information architecture (working sketch)

**Coach (mobile bottom nav)**
- **Today** — sessions today, outstanding follow-ups, quick "start session"
- **Athletes** — roster → athlete profile (Two-Panel Selector inspired)
- **Cohorts** — groups → cohort page (roster, per-member trends, group messaging)
- **Sessions** — calendar / list of past + upcoming
- **Inbox** — unsent notes, voice dictations awaiting filing, athlete uploads
  awaiting review
- **Profile / settings**

**Athlete (mobile bottom nav)**
- **Today** — next session + intended focus, outstanding items
- **Plan** — vision, goals, current process focus
- **Sessions** — past sessions with coach notes
- **Progress** — charts, milestones, streaks
- **Profile**

**Parent (mobile)**
- **Schedule**, **Plans**, **Progress** — all read-only

Tidwell Ch 2 app shape: closest to **Dashboard** with embedded **Wizards** for
onboarding and assessment.

## 9. Phasing

**V0 — skeleton (weeks 1–2)**
- Auth + roles (coach, athlete)
- Athlete CRUD on coach side
- Simple session create + text notes
- Athlete home: today's session + most-recent coach notes

**V1 — private lesson loop (weeks 3–6)**
- Vision/goals capture (ARProformance framework)
- Skill + self-awareness assessment templates
- Session planner with context rail (goals + recent notes)
- Voice dictation for notes
- "Send notes" to athlete post-session
- Push notifications

**V2 — group clinic loop**
- Cohorts: create-once groups; cohort page with per-member trends + group
  messaging
- Group clinic scheduling (off the cohort roster)
- Multi-player session logging with per-player notes
- Pre-published drills / court assignments
- Court assignments
- Attendance

**V3 — engagement loop**
- Assignments / homework with due dates
- Outstanding view + nudge action
- Reward / streak signals
- Athlete-side video upload + reflection submission

**V4 — progress + parent**
- Progress charts (line / multi-Y over assessment metrics)
- Qualitative feedback timeline
- Parent/Guardian role + views

**V5+ — deferred**
- Match repository with W/L tracking
- Multi-sport templates
- Payments
- AI-assisted suggestions ("brainstorm next session based on last 6 weeks" —
  replicates Ahad's current ChatGPT use, transcript 16:04)
- Auto-summarize remote-session Zoom transcripts into session notes

## 10. Open questions

### Product / naming
- **Closed beta scope.** ARProformance students only, or a handful of
  external squash coaches too?
- (Brand name is resolved — the platform is **ARProformance**; see §11.4.)

### Roles & users
- Academies — can a coach belong to one with a head coach above them?
  (FigJam sticky "court management for multiple athletes over a period of
  time" suggests this is on the radar.)
- Can an athlete have multiple coaches simultaneously?
- Parent role: read-only, or also schedule / cancel / pay?
- Account creation for minors — parent creates, or athlete creates and parent
  is linked? COPPA implications if any user is under 13 in the US.

### Sessions
- One intended focus per session, or multi? (FigJam says singular but multi
  may match reality.)
- Are non-group "private" lessons always 1:1, or can 2-student paired sessions
  exist outside the group-clinic flow?
- Track session duration, or only date/time start?
- Recurring sessions (weekly slot with same student)?
- (Calendar approach is resolved — in-app calendar that pushes out to
  Google/Apple, not a replacement and not a two-way import; see §11.4.)

### Assessments
- Skill + fitness items — predefined by us with ARProformance defaults,
  or fully coach-authored from day one?
- Scoring granularity — 1–5? 1–10? rubric? video-attached? (Per-drill, not
  cumulative, is settled — see §11.4 — but the scale is still open.)
- Re-assessment cadence — every N weeks, coach discretion, or both?
- Does the athlete self-score before the coach scores (for compare-and-contrast,
  reinforcing self-awareness — which is the whole point of one of the
  questionnaires)?

### Goals
- Cap at top 3 process goals (per FigJam sticky), or coach choice?
- Time-bound (target date) or open-ended?
- Edit permissions: coach only, athlete only, or both?

### Notes / capture
- Voice dictation — on-device STT or server-side (Whisper)? Affects privacy
  and offline behavior.
- Can the coach record raw audio without transcription as fallback?
- Note privacy: are coach-private notes (not shared with athlete) a
  first-class concept, or is everything shared by default?
- Per-attachment size limits (photos, video clips)?

### Homework / assignments
- Predefined assignment types only, or free-form?
- Coach review workflow — "approve" vs "acknowledge"?
- What happens when an athlete keeps missing? Auto-snooze, auto-cancel after
  N nudges?

### Notifications
- Channels: iOS push, Android push, web push, email digest? All?
- Quiet hours per user?
- Coach-level controls: can a coach set "no notifications to my athletes
  9pm–8am"?

### Video
- Storage — Supabase Storage / S3? Per-athlete size cap?
- Viewable only inside the app, or downloadable / shareable?
- Annotation on top of video — confirmed out of scope V1; when does it come back?

### Progress / analytics
- Which quantitative metrics drive the progress chart? FigJam says "metrics
  that reflect different quantitative aspects of squash" but unspecified.
- Comparative view — am I better than I was 3 months ago, or better than
  comparable players in my cohort?
- Match repository — manual entry only, or integrate with SquashLevels / PSA
  / club ranking systems?

### Payments (deferred)
- Stripe Connect for coach-direct payouts when we enable it?
- Subscription (SaaS) vs per-session billing — or both?
- Coach pays for the platform, athletes pay coaches for sessions through it,
  or athletes pay platform?

### Platform
- Web mobile vs native iOS? Transcript prefers "more focused on mobile than
  desktop." Memory note: iOS work for the user follows Apple HIG + Liquid
  Glass conventions — points toward a native iOS path eventually. Start as
  mobile web PWA?
- Offline mode (court reception is often poor) — required for V1 note capture?
- Auth — email + magic link, Apple/Google SSO, both?

### Design / brand
- The ARProformance brand kit exists and was shared — see `BRAND.md`. Tone is
  resolved there: direct, athletic, uncompromising. Confirm it carries to the
  *product* UI, not just the marketing site.
- Still needed from David: `colors_and_type.css` (the exact CSS variables) and
  a logo SVG — see `BRAND.md`.

### AI
- In-app AI session suggestion ("what's a good progression from here?"
  replicating Ahad's ChatGPT use) — V1 nice-to-have, V2, or wait until we
  have real session-history data?
- Zoom transcript → session notes auto-summarization — in scope?
- AI nudge composition (drafting the message for the coach to send when they
  hit "Nudge") — in scope?

## 11. Review round 2 — prototype walkthrough (2026-05-10 evening)

Ahad walked the 5-direction `prototype.html` and Stuti's FigJam coaching
workflows. Source: prototype-review transcript with Ahad (2026-05-10 evening,
timestamps 20:13–21:53).

### 11.1 Reactions to the five prototype directions
The direction names (Court-Side, Broadsheet, Command Deck, Locker Room,
Logbook) are throwaway V1/V2/V3 labels, not product names.

- **Court-Side** — keep the bold upfront *intended focus*, "last 3 sessions in
  his words", voice-note capture. Athlete view too busy; the "I'm here" toggle
  is redundant.
- **Broadsheet** — keep outcome goals, process goals, "what's coming up next".
  The "cycle" framing reads as too intensive for most coaches.
- **Command Deck** — the trend-line / metrics visual is liked but too busy.
  Open: *what* the trend line plots — Club Locker rating (the NA rating system;
  possible open API for rating only, not future tournaments), match W/L %, or
  assessment results over time.
- **Locker Room** — keep streaks, the "today's work" queue, due-date markers,
  the **"missions"** verbiage (week 3 of 6), the **pinned vision** view, the
  card layout. Points (+8/+18) are overkill for now.
- **Logbook** — most calendar-forward; visually closest to ARProformance.
  "Start session" does not belong in a logbook.

**Verdict:** the next prototype should be a **hybrid of Locker Room + Logbook**,
pulling in Court-Side's *intended focus* and Locker Room's pinned-vision /
top-focus-then-rest layout.

### 11.2 Cross-cutting feedback
- **"Start session" is overused.** It is a **group-clinic-only** coach action
  (capture dictated notes court-to-court). It does not belong on athlete
  screens or on every coach screen.
- **Minimal clicks → maximum result.** One-button actions wherever possible;
  a persistent bottom nav is essential on mobile.
- Several directions repeat the same content in different visual treatments —
  fine as parallel explorations, but the chosen direction must not carry that
  redundancy.

### 11.3 New / changed product decisions
- **Cohorts/groups are first-class** — see §6.10. Create-once, with a cohort
  page (roster, per-member trends, group messaging).
- **Calendar** — keep a squash-specific in-app calendar for coach and
  athlete/parent, but it **pushes out** to Google/Apple Calendar. Out is easy,
  import-in is hard; do not try to replace personal calendars.
- **Templates** — a coach's own previous sessions are the primary reuse path;
  named templates are secondary; session-level only, no multi-week programs
  (squash skill work is too varied — unlike a running plan). See §6.4.
- **Assessment scoring** — per-drill, never a single cumulative number. See §6.3.
- **Parent** — can message the coach. See §6.9.
- **Onboarding** — nothing mandatory; everything recommended/optional. New
  users get a ~30-min guided sit-down where features are toggled to what
  they'll actually use.
- **Group-clinic planning** — pre-publish drills / court assignments so players
  know the focus before arriving (today coaches scrawl it on the court glass);
  send clinic notes to **all enrolled players, even absentees**. See §6.5.
- **Gamification (later phase)** — within-cohort leaderboard, team-vs-team
  skill-assessment challenges (e.g. "4C vs River Grove"), player-vs-player
  "throw down" challenges.

### 11.4 Resolved open questions (moved out of §10)
- **Brand name** — the platform is **ARProformance** (see `BRAND.md`); "SquashIQ"
  stays rejected.
- **Brand kit exists** — David's ARProformance design system is real and was
  shared; see `BRAND.md`. Barlow Condensed + DM Sans, black/navy + a single red
  accent, sharp corners, pill buttons.
- **Assessment scoring** — per-drill, not cumulative (the *scale* — 1–5 vs
  1–10 — is still open).
- **Calendar** — in-app calendar that pushes out to Google/Apple; not a
  replacement, not a two-way import.
- **Templates** — previous-sessions-primary, named-templates-secondary,
  session-level only.
- **Parent scope** — read-only plus message-the-coach (schedule / pay still
  open).

### 11.5 Validation
4–5 coaches already want to beta test. Ahad has discussed the concept with a
Bay Area academy owner, Laura Massaro's brother (coach at a Philadelphia prep
school), and local 20–30-kid academy coaches, and pitched Nick Matthew and
Laura Massaro — all positive. Potential testimonial value.

### 11.6 Direction for the next prototype task (not in scope for this round)
- Consolidate `prototype.html` from 5 directions to **2–3**, led by the
  Locker Room + Logbook hybrid.
- **One** of the 2–3 applies the ARProformance brand (Barlow Condensed,
  black/navy + red accent — see `BRAND.md`).
- The build must be a **comprehensive, clickable end-to-end flow** for the
  **coach** and **athlete** personas — real screen-to-screen navigation, not
  isolated views — covering the §5 journeys.
- Reference: Ahad's own flow prototypes (coach-only — an athlete-onboarding
  wizard, a coaching-workflows workspace, a goals-panel A/B) at
  https://sitemap-generator--squash-iq-prototypes.netlify.app/

---

*Status: Draft 2 — incorporates the 2026-05-10 evening prototype-review session
(§11) and the ARProformance brand system (`BRAND.md`). Next: build the
comprehensive coach + athlete end-to-end prototype (2–3 visual directions, one
on the ARProformance brand), lock V0 scope, and start on data model + auth.*
