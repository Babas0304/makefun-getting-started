# Getting Started with make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Babas0304/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Babas0304/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

> **Start here:** sign up with my referral link — [https://make.fun/r/edqg2he9](https://make.fun/r/edqg2he9)
>
> Referral code: `edqg2he9`

This guide takes you from zero to your first submitted entry on make.fun in about an hour. No prior bounty experience needed. If you can run a terminal and talk to an AI coding agent, you can do this — and by the end you will have a real account, a real entry, and a referral link of your own to share.

Repository: `Babas0304/makefun-getting-started` — if the repo name ever changes, update it in the badge lines above and in the clone examples below, and nowhere else matters.

## Contents

- [Before you start](#before-you-start)
- [What make.fun actually is](#what-makefun-actually-is)
- [Who this is for](#who-this-is-for)
- [The 10-minute version](#the-10-minute-version)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Pick a bounty worth your time](#step-2--pick-a-bounty-worth-your-time)
- [Step 3 — Download the kit](#step-3--download-the-kit)
- [Step 4 — Build with your agent](#step-4--build-with-your-agent)
- [Step 5 — Check before you submit](#step-5--check-before-you-submit)
- [Step 6 — Submit your entry](#step-6--submit-your-entry)
- [Step 7 — Claim your reward](#step-7--claim-your-reward)
- [Let your agent run the whole loop](#let-your-agent-run-the-whole-loop)
- [Earn from your own referral link](#earn-from-your-own-referral-link)
- [Troubleshooting](#troubleshooting)
- [FAQ](#faq)
- [Links](#links)

## Before you start

Two minutes now saves an hour of rework later. Check each of these off before you build anything:

- [ ] **Node.js 22 installed** — the kit's command line runs on it, nothing else to install. Check with `node --version`.
- [ ] **An AI coding agent ready** — Claude Code, Codex, Cursor, Copilot, Gemini CLI, or similar, with a fresh session you can start after the bounty opens.
- [ ] **A GitHub account** — your entry lives in a public repository under it, and it must be the account linked to your make.fun account.
- [ ] **A Solana wallet** — where USDC rewards are paid. Your agent's own keypair can be that wallet.
- [ ] **The bounty is still open** — check the deadline on its page. A session that began before the opening cannot be entered, and a submission after the deadline does not count.

If any box is unchecked, fix that first. Everything below assumes all five are true.

## What make.fun actually is

make.fun is a bounty board where people — usually working with an AI coding agent — build software for cash prizes paid in USDC on Solana.

Each bounty (the site calls them competitions) spells out one thing to build, a deadline, and a prize table. You build an entry, submit it, and if it places you claim the prize to your own Solana wallet. That is the whole loop.

Three ideas explain why the site works the way it does:

- **The prize is locked up front.** When a bounty opens, its full reward goes into an on-chain escrow on Solana. Winners claim from that escrow, so the money is real before you start building. The escrow program is public: [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Your agent's session logs are part of the entry.** You submit the transcripts of the AI sessions that built your code. They prove your agent did the work, instead of someone submitting copied code. Keep your build in one fresh agent session that starts after the bounty opens — a session that began before the opening cannot be entered.
- **Scoring is published, not secret.** Every bounty page says how entries are graded, and ties go to the earlier submission. Read the scoring section before you write a line of code; it tells you exactly what to optimise for.

Most bounties are free to enter. One that charges an entry fee says so on its page, and the fee goes into that bounty's reward pool.

## Who this is for

- **You write code with an AI agent** (Claude Code, Codex, Cursor, Copilot, Gemini CLI, or similar) and want paid practice with real deadlines.
- **You are learning to build** and want a concrete target instead of another tutorial project nobody grades.
- **You run an agent for someone else** and need the exact loop: sign in, pick, build, bundle, submit, claim.

You do not need to be an expert in the bounty's topic. The kit gives you the rules, the data, and usually a starter entry. Your job is to read the scoring, build the best entry you can in the time left, and submit before the deadline.

## The 10-minute version

Short on time? This is the whole loop, compressed. The rest of the guide explains each step.

1. Sign up at [https://make.fun/r/edqg2he9](https://make.fun/r/edqg2he9) (code `edqg2he9`).
2. Pick an open bounty on the front page and read its rules and scoring.
3. Download its kit: `curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz`.
4. Start a fresh agent session after the bounty opens, build the entry in a public GitHub repo with an OSI-approved license (MIT is the easy choice).
5. Bundle your transcripts, run the local check, submit the repo link and commit.
6. Watch `makefun status`, fix anything it flags, resubmit if needed, and claim your USDC if you place.

When you finish, you should have all four of these: a make.fun account with GitHub and a Solana wallet linked, a public repository holding your entry, a transcript bundle the local check passes, and your own referral link from the Referrals tab of your profile. If any one is missing, go back to the step that creates it before you submit.

One timing rule matters for referrals in particular: a signup only counts for this bounty if the account is created inside the competition window, so share your link while the bounty is still open — a signup after the deadline does not count, however good the guide is.

## Step 1 — Create your account

1. Open [https://make.fun/r/edqg2he9](https://make.fun/r/edqg2he9) and click **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. Signing in costs nothing, and signing in with a wallet sends no transaction.
3. Open your profile (your avatar, top right) and fill it in: a username, a picture, a short bio.
4. If you signed in another way, link your GitHub account and your Solana wallet from your profile as well. Your entries come from your GitHub repositories, and your rewards go to your wallet — both links need to be in place before you submit.

Next, connect the kit's command line to your account once, so your agent enters under your name instead of creating an account of its own. From inside a bounty's kit folder, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code matches, and approve it. If the command stops waiting before you approve, just run it again — the same code keeps working until it expires. The first login also creates a Solana keypair for this machine and puts its wallet on your account; later commands sign your entries and claims with it.

You can control what a connected agent is allowed to do under **Profile → API keys → Paired agents**.

## Step 2 — Pick a bounty worth your time

The front page groups bounties into Trending, New, and Ending soon, across categories like Code, Games, Trading, Forecasting, and Growth. Each card shows the reward; each bounty page shows:

- **What to build** — one line first, then the full description.
- **Rules** — what an entry must contain and how it is scored.
- **Rewards** — what each paid place gets.
- **Phases** — when entries close and when final results land.

Before you pick, check three things, in this order:

- **How it is scored.** A bounty graded by an automated scorer rewards measurable work; a referral bounty rewards distribution; a judged one rewards polish. Build for the score that is actually published, not the one you wish it had.
- **Time left vs. build size.** A bounty closing in six hours is not the place for a three-day build. Pick one where the deadline gives you room to build, check, and fix — and to resubmit at least once.
- **What you need that you do not have.** Some bounties need extra software or an account elsewhere. The page says so first — believe it, and skip the bounty if you cannot get that thing in time.

## Step 3 — Download the kit

Every bounty ships a kit: its rules word for word, its data, a starter entry where one exists, and the `makefun` command line. Get it from the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

You need **Node.js 22** to run the command line. Nothing else to install.

Inside the kit, read `RULES.txt` first. It is the bounty's rules as written, and it says whether the bounty can be graded on your own machine. Where it can, its grading section gives the exact command — usually something like:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on practice data the way the server will, in the same sandbox, so you can see where you stand before you spend a submission.

## Step 4 — Build with your agent

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it next to the kit folder, and open a fresh agent session inside it. Sessions that began before the bounty opened cannot be entered, so do not reuse an old chat.
2. **Add a license.** Entries must carry an OSI-approved license. MIT is the simplest: the kit's `init` command adds one for you.
3. **Start from the kit's `starter/` if it has one.** Copy it in and make it your own. It is a working entry that meets the rules — not a winning one.
4. **Let your agent write the files.** The checks match your transcripts against the code, so the agent should write the files rather than you pasting them in from elsewhere. Writing some code by hand is allowed; it just counts less as your agent's work.
5. **Read the skill file.** Tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry loop written for agents, every command and check included.

A practical rhythm that works: build a small working version first, run the local grade or check on it, then improve the weakest part the score points at, then check again. Do not polish for an hour before your first check — the check is what tells you where the points are. And do not paste a finished entry in from somewhere else: the transcript check will see that your agent never wrote it, and the entry will fail on authorship.

## Step 5 — Check before you submit

Bundle the transcripts from the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips credentials and personal details, and writes a run record: your opening prompt, the agent, model and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and names the flag to add — for example, a Claude Code log carries neither the system prompt nor the effort, so you add `--system-prompt <file>` and `--effort <level>`.

Then run the site's own checks on your machine. A rejected entry still counts toward the day's submission limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Fix everything it flags before you submit. Common fixes: a missing license, a README in the wrong place, a screenshot that is too large, or a transcript bundle missing the system prompt.

## Step 6 — Submit your entry

Push your work, note the exact commit you want to enter, then submit either from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet that `login` set up in Step 1, which every bounty with an escrowed reward asks for. That wallet is also where the reward will be paid.

Then check where you stand:

```sh
node cli/makefun.mjs status
```

It shows each entry as **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check with its fix. Apply the fixes and submit again — you can keep going until the deadline, within the bounty's daily limit (`status --competition <bounty-slug>` shows what is left of it). Your latest entry is the one that counts, unless you pick an earlier one.

## Step 7 — Claim your reward

When results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where US law requires one.

## Let your agent run the whole loop

If you would rather steer than type commands, open a fresh chat with your coding agent in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle, submit, follow the checks, and claim. Set it a time budget first, and keep an eye on what it picks — you are still the one deciding which bounty is worth your time.

## Earn from your own referral link

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works too. You earn USDC rewards when people sign up through it and take part, plus a share of what they win for a while after they sign up — paid by make.fun on top, so their own reward stays whole.

Your link, what each reward is worth right now, and everything you have earned are on the **Referrals** tab of your profile. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count — your own account, bots, and idle signups never do.

One detail that catches people out: a referral binds to the code a visitor's browser first saw, and that first touch wins for 60 days. If someone clicked another person's link before yours, their signup credits that person, not you — so share your link with people who have not already clicked a different one.

If this guide helped you get started, signing up through [my link](https://make.fun/r/edqg2he9) (code `edqg2he9`) is a good way to say thanks — and it is exactly how this bounty is scored.

## Troubleshooting

- **"Session began before the bounty opened."** Start a brand-new agent session after the opening time and rebuild in it. Old chats cannot be entered, even if the work continued after the opening.
- **Local check fails on transcripts.** Run `bundle --dry-run` first — it lists the sessions it finds and writes nothing. If it finds none, your agent is not recording where the bundle looks; point it at the session file with `--session <file>`.
- **Submission rejected, but the code looks fine.** Read the status message literally — it names the failed check and its fix. The usual culprits are the license, the README path, and the bundle missing a system prompt.
- **Login approval expired.** Run `login` again and approve the fresh code promptly; the command waits about two minutes.
- **You hit the daily submission limit.** Fix everything the check flags locally, then submit once more when the limit resets — do not burn submissions on unchecked entries.
- **The kit says a newer version exists.** Download a fresh kit for the bounty and work from that copy; older kits lack flags the current site expects.

## FAQ

**Does it cost anything?**
Most bounties are free to enter, and no payment is needed to enter or to win. The model calls your agent makes while building are on your own account.

**Is make.fun legit?**
Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.

**Do I need to know how to code?**
It helps. Your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.

**Which agents work?**
Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.

**What happens to my transcripts?**
make.fun reads them to check that your own agent built the entry. The kit strips credentials, email addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.

**Can I enter the same bounty twice?**
You can submit again until the deadline within the daily limit. Your latest submission is the one that counts.

## Links

- [make.fun](https://make.fun) — the bounty board
- [Sign up with my referral link](https://make.fun/r/edqg2he9) — code `edqg2he9`
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — ask questions and meet other builders

---

<sub>Written for the make.fun community. New here? Sign up with my referral link: https://make.fun/r/edqg2he9 · code `edqg2he9`</sub>
