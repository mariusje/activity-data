# activity-data

Working title. Scope agreed in thread 1 (2026-09-26).

## Goals

After one year, the project has been worth it if:

1. I have become better at using AI in software and product development.
2. I have a product or solution to keep working on, or have completed
   something sensible — at minimum useful to me.
3. The work has involved fun or interesting tasks.

Bonuses, not requirements: a path towards a sellable product or new ideas in
that direction, and general learning.

## What this is

A standalone application — mobile or web — for exploring my own training
data, in the same family as intervals.icu and Dreeve. It does not depend on
external BI tools.

It offers:

- **Free-form reporting** within the contents of a star schema. Measures such
  as distance, time, average speed, power and average power, broken down and
  filtered by year, month, week, day, time of day, weekday, activity type,
  gear and more, and compared against earlier periods. I choose the
  breakdowns and filters myself to find the most interesting view.
- **Maps.** Activities shown on a map, including which routes overlap,
  filtered heatmaps and similar views.
- **A simple, clean interface.** When simplicity and freedom conflict,
  freedom wins.

Why build this when intervals.icu and Dreeve exist: partly because I want to
build it myself, and partly for the freedom in reporting and maps.

Training data is the working domain because I have interest and knowledge in
it, I have my own data, and I can see the outlines of possible products in it.
The domain is not locked.

## Who it is for

At minimum myself. Other users are a bonus, not a requirement.

## Explicitly out of scope

- External BI tools (such as Power BI) that the user has to install.

## Branching

- Documentation lives on `main`.
- Code is developed on feature branches, one per phase, merged via PR.
