# STUDENT.RF
Bilingual (RU/EN) prototype of a single-window admission platform for Russian universities and colleges. Compare programs, build one portfolio, apply to up to five programs at once and track statuses. One self-contained HTML file — no build step, no dependencies.



# Student.RF

**Admission to Russian universities — in one account.**
Find a program, build one portfolio, submit applications and track results.

[English](README.md) · [Русский](README.ru.md)

![Status](https://img.shields.io/badge/status-interactive%20prototype-blue)
![Dependencies](https://img.shields.io/badge/dependencies-none-success)
![i18n](https://img.shields.io/badge/i18n-RU%20%7C%20EN-informational)

---

## The problem

Applying to Russian universities and colleges today means assembling the same set of
documents again and again, one institution at a time. Requirements live on dozens of
separate websites, cut-off scores and deadlines are published as PDF orders, and an
applicant aiming at five programs in different cities ends up with five parallel
processes and no single place to see where each one stands.

The state portal Gosuslugi already solves part of this — identity, verified documents
and electronic submission. What it does not do is help you *choose*: there is no program
search across institutions, no side-by-side comparison, no reusable achievement
portfolio and no English interface.

## What this is

An interactive prototype of a single-window admission platform. It covers the whole path
from "I don't know where to apply" to "I am enrolled":

- **Catalog of universities and colleges** — programs with cut-off scores, state-funded
  places, tuition, entrance exams, required documents and deadlines. Filters by type,
  city and free-text search.
- **Program comparison** — save up to five programs and compare them side by side on
  city, cut-off score, places, tuition, dormitory and deadline.
- **Unified portfolio** — one set of documents and achievements, attached to every
  application automatically. Personal data and exam results come from state registries
  rather than manual input.
- **One application, up to five programs** — a four-step wizard with priority ordering,
  a document check assembled from the requirements of every selected program, and
  confirmation.
- **Status tracking** — a five-stage progress rail (submitted → document check →
  ranking list → decision → enrollment), application history, and actions the applicant
  can take directly from a status.
- **Bilingual interface** — full RU/EN switch, including institution names, programs,
  documents, statuses and dates.

## Three design decisions worth pointing at

**One next step, never a list.** The home screen shows exactly one action with its
deadline — upload a document, give enrollment consent, submit an application. The block
recalculates itself as the situation changes. Admission fails on missed single steps,
not on missing information.

**The status rail is the same everywhere.** The same five-stage element appears on the
home screen, in the application list and in the application card, so the applicant reads
one visual language instead of decoding a new status widget on every page.

**Every number carries its source.** Cut-off scores, place counts and deadlines are
shown with the document they came from and the date they were last verified, and
official data is visually distinguished from reference data. A platform that people
trust with a life decision has to be auditable.

## Running it

```bash
git clone https://github.com/<user>/student-rf.git
cd student-rf
open student-rf.html      # or just double-click the file
```

No build step, no server, no package manager, no internet connection required. The whole
prototype is one self-contained HTML file: markup, styles, state and mock data.

## Tech notes

Vanilla JavaScript, no frameworks and no dependencies — deliberately, so the prototype
opens anywhere and survives being emailed as an attachment. State lives in a single
object; screens are pure functions returning HTML strings; the i18n layer keeps every
string as a `[ru, en]` pair so the two languages cannot drift apart. Dates and currency
are formatted per locale. Layout is responsive down to phone width.

All data is mock data declared at the top of the script — institutions, programs,
applications and the user are fictional and easy to edit without touching the markup.

## Status and roadmap

This is a **prototype**, not a working service. Nothing is stored, sent or submitted.

| Stage | Scope |
|-------|-------|
| **v1 — Admission** *(current)* | Catalog, comparison, portfolio, applications, statuses, RU/EN |
| v1.1 — Admission office | Incoming applications, document verification, ranking lists |
| v2 — Student account | Activities and volunteer hours, then grades and timetable via integrations |

Grades, timetables, rooms and teachers are intentionally **out of scope for v1**: they
turn the product into a campus information system, duplicate what every institution
already runs, and dilute the one job this platform has.

## Disclaimer

Not affiliated with Gosuslugi, the Ministry of Science and Higher Education, or any of
the institutions named in the demo data. The platform is designed as a complement to
existing state infrastructure, not a replacement for it. All institutions, applications,
scores and users shown in the prototype are fictional.

## License

MIT
