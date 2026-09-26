# Open questions

Parked items. Do not pursue mid-thread — write here and move on.

## Commercialisation (revisit only when there is something to commercialise)
- Strava API terms for commercial use, including naming rules
- GDPR: GPS traces are personal data. Home address is readable from a
  frequency map. Must be solved before the first external user.
- Product name: trademark (Patentstyret/EUIPO) → domain → App Store → PyPI/npm.
  Trademark first — the only one that can force a rename after launch.
- App Store: developer account, cost, review process, privacy policy
- Alternatives: web service, subscription, open source + paid hosting
- Repo must go private before real user data. Raw-URL access then breaks;
  switch project instructions to the GitHub integration.
- If the repo is renamed: update the raw URLs in the project instructions.

## Product (open from thread 1)
- Mobile or web — decide in the platform thread.
- A possible game-like feature — no concrete idea yet. Parked until the rest
  is clearer.

## Architecture (take up in the architecture thread)
- Data source: Garmin device files, Garmin account export, Strava bulk archive
  or Strava API — which ones, and in what role. Check the current Strava API
  Agreement: the version effective 2024-11-11 limits display to the owning
  user and bans use of API data in AI/ML models.
- Ongoing ingestion: Connect IQ was checked on 2026-09-21 and cannot read saved
  FIT files or upload files. The Garmin Activity API needs partner approval;
  current status and fees are unverified.
- Data at hand: Garmin device files 2014–2025 with gaps, Strava archive
  (downloaded), Garmin account export (ordered, pending).

## Skill candidates (do not create yet — note when triggered)
- End-of-thread routine: repeated every thread, well-defined procedure.
  Strongest candidate. Reassess after 3-4 threads.
- Training-data domain knowledge that has to be re-explained each time.
- Project-specific code patterns too detailed for AGENTS.md.