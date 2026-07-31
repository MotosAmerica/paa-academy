# Motos America Parts & Accessories Academy — Web Training Site

A mobile-friendly web version of the Parts & Accessories Academy manual: read
all 19 modules, take instantly-scored quizzes, and unlock two full Part exams.
Each module review requires a perfect score to pass — a wrong answer sends
the trainee back to re-read the module rather than showing which answers
were right or wrong, so people have to actually revisit the material rather
than guess their way through. Managers get a report showing who's
registered, who's passed each module, how many tries it took them, and each
Part exam score.

## What's in this repo

| File | Purpose |
|---|---|
| `index.html` | Page shell — loads everything else |
| `styles.css` | All visual design (shared Motos America Academy design system) |
| `content-data.js` | All 19 modules + every quiz question, generated from the locked manual |
| `app.js` | All app logic — login, navigation, quiz scoring, Supabase calls |
| `supabase-config.js` | Already filled in — points at the shared MAU Supabase project |
| `schema.sql` | Reference only. The tables already exist in the shared project; you don't need to run this here. |

## One-time setup (do this before sharing the link with your team)

### Database — nothing to do here
This site shares the **same Supabase project as every other MAU academy**
(Sales, Service Advisor, etc.) rather than having one of its own. The
tables already exist, and `supabase-config.js` is already pointed at it —
there's no project to create and no `schema.sql` to run.

Data stays cleanly separated: every row this site writes is tagged
`academy: 'parts_accessories'`, so it never mixes with Sales or Service
data even though they all live in the same database. `schema.sql` is kept
in this repo purely as a reference for what the shared tables look like.

If you ever need the connection details again, they live in the **Sales
Academy** Supabase project (`kairsmnztbvcxacdsizi`), not a project of this
site's own — Project Settings → API in that project.

Roles for this academy are **Parts Associate** and **Manager** (an `admin`
role also exists in the database for anyone who needs full access without
being tied to a specific store's manager view — that role isn't in the
login dropdown; create it directly in Supabase's Table Editor if needed).

### 1. Turn on GitHub Pages
- In this repo on GitHub: **Settings → Pages**
- Under "Source," choose **Deploy from a branch**
- Branch: `main`, folder: `/ (root)`
- Save. GitHub will give you a URL like `https://motosamerica.github.io/parts-accessories-academy/` within a minute or two

### 2. Give yourself manager access
- Log into the site once using your name, your store, and select **Manager** as the role
- Managers see an extra "Report" button in the top bar showing every trainee's progress

That's it — share the GitHub Pages URL with your team.

## Notes

- **No passwords.** Trainees log in with just their name and store. This is meant for internal use only — don't link this URL anywhere public.
- **Module reviews require 100%.** All 5 questions must be correct to pass (Module 3 covers the same standard). A wrong answer doesn't reveal which ones — the trainee is sent back to the module page to re-read, then can retry the review as many times as needed. The report shows how many attempts each person needed per module.
- **Part exams are not gated.** The two 20-question Part exams score and record the result, full answer review included, but don't block progress or require a retry.
- **Works offline-ish.** If wifi drops mid-quiz, the score still saves on the device and syncs to the shared database automatically once the connection is back.
- **Content changes:** if the manual content ever changes, `content-data.js` needs to be regenerated from the source (`manual_data.json`) — it isn't meant to be hand-edited directly.
- **Logo:** `MA_logo_white_header.png` is the shared corporate logo used across all four academy sites — already included in this repo.
