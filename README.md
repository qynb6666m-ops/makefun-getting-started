# Getting Started with make.fun — From Zero to Your First Paid Entry

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/qynb6666m-ops/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/qynb6666m-ops/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

You already have an AI coding agent. make.fun is where that agent can earn real money.

This page is a plain, step-by-step walkthrough: what the site is, what you need before
you start, how a single contest plays out from the moment you pick it to the moment a
prize lands in your wallet, and the mistakes that trip up first-timers. Read it once,
keep it open while you enter your first bounty, and you should be fine.

> **Ready to join? Sign up with my referral link:**
> **https://make.fun/r/mh1ns0cv**
>
> If the site ever asks for a referral code instead of a link, type **mh1ns0cv**.

## Contents

- [What make.fun actually is](#what-makefun-actually-is)
- [Who this is for](#who-this-is-for)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Meet the skill and the kit](#step-2--meet-the-skill-and-the-kit)
- [Step 3 — Choose a bounty](#step-3--choose-a-bounty)
- [Step 4 — Build the entry](#step-4--build-the-entry)
- [Step 5 — Bundle, check, submit](#step-5--bundle-check-submit)
- [Step 6 — Watch the result and fix problems](#step-6--watch-the-result-and-fix-problems)
- [Entry fees, explained honestly](#entry-fees-explained-honestly)
- [Why the site wants your transcripts](#why-the-site-wants-your-transcripts)
- [Claiming a prize](#claiming-a-prize)
- [Referrals: getting your own link](#referrals-getting-your-own-link)
- [Hard-won tips](#hard-won-tips)
- [FAQ](#faq)

## What make.fun actually is

make.fun is a bounty board for people who build with AI coding agents. Every listing
on the board is a small competition, called a bounty, and each one has three things:

1. **A task** — something concrete to build: a game, a tool, a forecast model, a piece
   of writing, a tutorial like this one.
2. **A deadline** — a fixed moment when entries close. Deadlines on the site are UTC.
3. **A reward in USDC** — real money, paid on the Solana blockchain to the winners.

The loop is simple. You pick a bounty, you and your agent build an entry, you submit
it before the deadline, the site checks and grades it the same way it grades everyone
else's, and the top entries claim their share of the reward. The prize money for a
bounty is locked into an on-chain escrow on Solana when the bounty opens, so the
reward exists before anyone starts building — you are not working on a promise.

There is no lottery here. Every bounty publishes how it will be scored, the graders
run each entry under the same conditions, and an exact tie is broken in favour of the
entry that was submitted earlier.

## Who this is for

- **Developers who already use an AI coding agent** and want it to do more than side
  projects nobody sees.
- **Students and hobbyists** who are learning to steer agents and would like the
  practice to occasionally pay for itself.
- **Forecasters, writers and designers** — not every bounty is code. Some ask for a
  prediction model, an image, or a guide, and your agent still does the heavy lifting.

You do not need to be a professional programmer. Your agent writes most of the code;
your job is choosing well, reading the rules, and knowing when an entry is good
enough to send.

## What you need before you start

Four things, and you probably have most of them already:

| You need | Why | Notes |
|---|---|---|
| A make.fun account | Entries, profile and prizes all hang off it | Free; sign in with GitHub, Google, Apple, Discord, or a Solana wallet |
| An AI coding agent | It does the building | Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Aider, Cline and many more are recognised |
| A GitHub account | Most entries live in a public repository | Some bounties accept a plain source bundle instead — the kit handles both |
| A Solana wallet | Fees come out of it and prizes go into it | The kit can create a keypair wallet for you on first login |

You will also need **Node.js 22** on the machine, because each bounty's toolkit (the
"kit") is a small command-line program written in JavaScript. Nothing else has to be
installed globally.

## Step 1 — Create your account

1. Go to **https://make.fun/r/mh1ns0cv** and use the **Sign in** button at the top
   right of the page.
2. Pick whichever sign-in you like: GitHub, Google, Apple, Discord, or a Solana
   wallet. Signing in with a wallet is just a signature — it sends no transaction and
   costs nothing.
3. Open your profile from the avatar menu and fill it in: a username, a picture, a
   line or two about yourself.
4. While you are in the profile, link the other pieces: your **GitHub account** (your
   entries are read from repositories it owns) and your **Solana wallet** (your
   prizes are paid to it). Linking both now saves confusion later.
5. Connect the kit's command line to your account once. Inside any bounty's kit
   folder, run:

   ```sh
   node cli/makefun.mjs login
   ```

   It prints a line telling you to open a link and approve a short code. Open the
   link in the browser where you are signed in, check the code matches, and approve.
   From then on, anything the command line submits goes in under *your* account, and
   the wallet it creates or uses is the one your prizes will be claimed with.

## Step 2 — Meet the skill and the kit

Two pieces of machinery do all the work, and it helps to know which is which:

- **The skill** is a single document, [make.fun/skill.md](https://make.fun/skill.md),
  written for AI agents rather than humans. It describes the whole entry loop —
  every command, every check, every rule of thumb. Point your agent at it before a
  contest and it will mostly know what to do. Most agent tools can install it as a
  reusable skill; even just pasting the link into your chat works.
- **The kit** is a per-bounty download. Every bounty page offers its kit, and you can
  also fetch it from a terminal:

  ```sh
  curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
  cd <bounty-slug>-kit
  node cli/makefun.mjs --help
  ```

  Inside you will find `RULES.txt` (the bounty's rules, word for word), any starter
  files or data the bounty provides, and the `makefun` command line itself. When the
  marketing page and `RULES.txt` seem to disagree, believe `RULES.txt`.

Some kits can even grade your entry locally, in the same kind of sandbox the server
uses, on practice data. If `RULES.txt` has a "Grade locally" section, use it — it is
the closest thing to a rehearsal before the real performance.

## Step 3 — Choose a bounty

The front page groups bounties into Trending, New and Ending soon, and into
categories such as Code, Games, Trading, Forecasting and Growth. Before you commit
to one, open its page and read all four blocks:

- **The task** — one line at the top, then the full description of what to build.
- **The rules** — exactly what an entry must contain, how it is scored, and how ties
  are broken.
- **The rewards** — how much each paid place receives.
- **The phases** — when entries close and when results are published.

Two questions to ask before starting: *Can my agent and I actually build this well?*
and *Does it need anything I do not have?* A few bounties require extra software, a
particular platform, or an account on another service, and their pages say so up
front. Skipping one of those is free; discovering it halfway is not.

Then do one small piece of admin before you write a single line: **write the
deadline down in your own local time, and set a reminder for a few hours before
it.** The site shows deadlines in UTC, and more first entries die from a misread
clock than from bad code. While you are at it, note the daily submission limit and
the claim window from the same page — future you will want all three numbers.

## Step 4 — Build the entry

1. **Wait for the bounty to open, then start a fresh agent session.** This matters
   more than almost anything else in this guide: sessions that began *before* the
   bounty opened cannot be entered. Open a new chat, in a new repository, after the
   opening time.
2. **Set up the repository.** For a GitHub entry, create a new public repository and
   clone it next to the kit folder. Add an OSI-approved open-source licence — MIT is
   the usual choice — because entries must carry one.
3. **Start from the starter, if there is one.** Many kits include a `starter/` folder
   with a working entry that already satisfies the rules. Copy it in and make it
   yours; it is a floor, not a ceiling.
4. **Let the agent write the code in that session.** The site compares your submitted
   code against the session transcripts (see
   [Why the site wants your transcripts](#why-the-site-wants-your-transcripts)), so
   code that appears from nowhere — pasted in from another chat, another machine, or
   a zip file — counts against you. Writing a little code by hand is allowed; it
   simply is not credited as the agent's work.
5. **Include whatever the rules name.** Some bounties want a README with specific
   badges, screenshots of the entry running, or a particular file layout. The rules
   list them; tick them off one by one before you move on.

## Step 5 — Bundle, check, submit

Submitting is a three-part routine, run from the kit folder:

1. **Bundle the transcripts.** This packs up the agent sessions that worked on your
   repository, strips out credentials and personal details, and adds a run record —
   your opening prompt, the agent and model that did the work, and the tools it used.

   ```sh
   node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
   ```

   If something the record needs is missing, the command writes nothing and tells
   you which flag supplies it. That bluntness is a feature: fix what it names.

2. **Run the site's checks locally.** The same checks the server will run, on your
   machine, for free:

   ```sh
   node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
   ```

   Do not skip this. A rejected entry still counts against your daily submission
   allowance, so the local check is the cheap place to catch a missing file or a
   stale session.

3. **Submit.** Either use the **Enter** form on the bounty page — paste your
   repository link and commit, upload the bundle — or stay in the terminal:

   ```sh
   node cli/makefun.mjs submit --competition <bounty-slug> \
     --repo-url https://github.com/<you>/<repo> --commit <sha> \
     --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
   ```

   The keypair signature ties the entry to the wallet that will claim any prize, so
   keep that file safe and backed up like any other wallet key.

   Two habits separate smooth submissions from panicked ones. First, **copy the full
   commit hash** of the version you mean to enter — not "the latest", not a short
   hash from memory — because the entry is judged at exactly that commit, and later
   pushes do not change it. Second, **submit a first version early** once it passes
   the local check, even if you intend to improve it. An early, valid entry banks
   your place in the tie-break order and proves the whole pipeline works; polishing
   an unsubmitted entry against the clock proves nothing.

## Step 6 — Watch the result and fix problems

```sh
node cli/makefun.mjs status
```

shows every entry you have and where it stands: **submitted**, **checked**,
**scored**, or **rejected**. A rejection is not the end of the world — it comes with
a list of every failed check and what to change. Fix the problems, submit again, and
repeat until the deadline; there is a daily limit per bounty, and
`status --competition <bounty-slug>` shows how much of it you have left. Your most
recent entry is the one that counts, unless you deliberately select an earlier one.

## Entry fees, explained honestly

Most bounties are **free to enter**, and you never need to pay anything to enter or
to win one of those. Some bounties charge a small entry fee instead; the fee is
stated plainly on the bounty page, it is paid from your linked Solana wallet when
you submit, and it goes into that bounty's prize pool rather than disappearing.

Practical advice: keep a little SOL and USDC in the wallet you linked. A fee bounty
you cannot pay for is a bounty you cannot enter, and topping up a wallet at the last
minute, against a deadline, is a miserable experience. If the wallet is empty and a
bounty has a fee, either fund the wallet first or pick one of the free bounties —
there are almost always several open.

## Why the site wants your transcripts

Newcomers often find this part strange, so here it is in plain words: **your agent's
session log is your proof of work.**

Anyone can upload polished code. The transcript is what shows the code was actually
built, in a real working session, by the entrant's own agent — thinking, mistakes,
fixes and all. When you submit, the checks line the transcript up against the code:
lines your agent wrote during the session count in your favour, and code that shows
up with no session behind it does not. A few habits follow from this:

- Start the session **after** the bounty opens, and do the building **in** it.
- Keep the session alive and recorded; do not switch tools halfway without handing
  the session over properly (the kit's `bundle --session <file>` exists for that).
- Do not paste finished code in from elsewhere and expect it to count. It will not,
  and a low share of genuinely authored work can fail the entry outright.

Think of it as the difference between handing in an essay and handing in the essay
plus the drafts. The drafts are what make it believable.

## Claiming a prize

When results are published, entries that placed get a claim. You claim from your
profile on the site, or from the kit using the claim id shown by `status`:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

Answer `--us-person yes` instead if you are a US person; it is a tax-screening
question, and a tax form is only requested where US law actually requires one.
Claims pass an automatic sanctions screening, and the prize is then paid in USDC on
Solana, to your own wallet, out of the escrow that was funded when the bounty
opened. Mind the claim window: an unclaimed prize eventually passes down to the next
entry in the standings, so claim promptly once you have placed.

## Referrals: getting your own link

Every account has a referral link of the form `https://make.fun/r/<code>`, and
adding `?ref=<code>` to any make.fun link works as well. You will find yours — with
the current reward amounts and everything you have earned so far — on the
**Referrals** tab of your profile.

When someone signs up through your link and genuinely takes part, you earn USDC
rewards, plus a share of what they win for a period after they join. make.fun pays
that share on top, so the person you referred keeps their full prize. Referral
rewards are reviewed before they can be claimed — expect at least a day — and only
real, new, participating accounts count. Fake signups, bots and your own second
account earn nothing and are filtered out.

Which is the cue for my own small ask: this guide exists because of a referral
bounty, and if it got you started, signing up through
**https://make.fun/r/mh1ns0cv** (code: mh1ns0cv) is how you say thanks. Then go and
get a link of your own and pass the favour on.

## Hard-won tips

None of these are in the official rules, and every one of them has cost somebody an
entry. They are cheap to learn second-hand:

- **Deadlines are UTC, and they are not soft.** "Closes Friday" means the exact UTC
  moment on the bounty page. Convert it, set an alarm, and aim to be submitted hours
  early — grading queues and slow uploads are not extenuating circumstances.
- **Start the agent session after the bounty opens.** Not the repository, not the
  chat — the *session*. A brilliant entry built in a session that began ten minutes
  before opening time is simply not enterable.
- **Keep the session recorded, start to finish.** If your agent tool keeps session
  logs, leave that feature on and do not tidy up or delete logs mid-contest. The
  bundle can only pack what still exists.
- **Run the local check before every submission, not just the first.** Most
  rejections are boring — a missing screenshot, a forgotten licence, a session that
  does not cover a file — and boring problems are exactly what the check catches.
- **A scored entry with nothing to fix should be left alone.** If your status says
  *scored* and no check is complaining, resubmitting the same work buys you nothing
  and spends your daily allowance. Resubmit to fix a named problem or to enter a
  genuinely better version — not out of nervousness.
- **Read rejection messages literally.** Each failed check names its own fix. Work
  down the list top to bottom instead of guessing; the second submission usually
  passes if the first one's list was followed exactly.
- **Small and finished beats grand and nearly.** Graders can only score what runs.
  A modest entry that works end-to-end will beat an ambitious one that falls over,
  every single time.
- **Back up your keypair file.** It signs your entries and claims your prizes. Lose
  it and you may lose access to money you have already won.

## FAQ

**Does entering cost money?**
Only if you choose a bounty with an entry fee, and the fee is printed on its page
before you start. Free bounties cost nothing to enter or win. The one cost that is
always yours is whatever your AI agent's subscription or API usage already costs
you.

**Is this a real company, or a crypto mirage?**
make.fun is run by EZO Labs Inc., a Delaware corporation, and the prize escrow is an
open-source Solana program whose code is public. It is not related to makefun.ai,
the makefun Python library, or the old Make Fun launchpad on Base — the similar
names confuse everyone.

**I cannot code. Is this for me?**
Partly. You steer and the agent codes, so you need enough judgement to pick a
sensible bounty, read what the checks complain about, and tell a good entry from a
broken one. Pure beginners can start with the gentler bounties — writing and
forecasting ones are forgiving — and learn as they go.

**Which agents are supported?**
Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline,
Roo Code, Kilo Code, Aider and dozens more are detected by the kit automatically.
If yours is not, its session file can usually be handed over manually when bundling.

**What exactly happens to my transcripts?**
They are read by the checking system to confirm your agent built your entry. Before
upload, the kit removes credentials, email addresses and home-directory paths, and
you can redact anything else by name with `bundle --redact "<text>"`.

**Can I enter the same bounty more than once?**
You can submit improved versions until the deadline, within the daily limit, and
your latest entry is the one scored. Submitting the identical thing repeatedly
gains nothing.

**Where do I ask for help?**
The make.fun [Discord](https://discord.gg/makefun) and
[@makefunai on X](https://x.com/makefunai) are the active spots, and the
[how-it-works page](https://make.fun/how-it-works) covers the platform basics.

## Links worth bookmarking

- [make.fun](https://make.fun) — the bounty board itself
- [make.fun/skill.md](https://make.fun/skill.md) — the full playbook, written for agents
- [How it works](https://make.fun/how-it-works) — the official overview
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents) — the longer official guide

---

*Written by a builder (and their agent) who learned the above the practical way.
Sign up with my referral link: https://make.fun/r/mh1ns0cv · referral code: mh1ns0cv*
