<div align="center">

# Daily Assistant

**An encrypted personal planner with modules that opens in any browser and works offline.**

[![Checks](https://github.com/Egor-Shast-rezka/daily_assistant/actions/workflows/ci.yml/badge.svg)](https://github.com/Egor-Shast-rezka/daily_assistant/actions/workflows/ci.yml)
![Python 3.12](https://img.shields.io/badge/python-3.12-3776AB?logo=python&logoColor=white)
![Platforms](https://img.shields.io/badge/platforms-Linux%20%7C%20Windows%20%7C%20Android%20%7C%20iOS-6c63ff)
![Interface](https://img.shields.io/badge/interface-English%20%7C%20Russian-f08a7e)
![Encryption](https://img.shields.io/badge/data-end--to--end%20encrypted-3aa57a)

**English** | [Русский](README.ru.md)

</div>

---

## About

Daily Assistant is one place for everything that happens in a day: classes,
meals, habits, tasks, purchases, sleep and reminders. At its centre is a
calendar that works as a single timeline, and every part of the
application publishes into it, so a whole day is seen at once instead of
being spread over a dozen separate apps.

It is built for one person and the people they share a household with, and
it treats that data as private. Everything a user writes is encrypted with
a key derived from their password; the server stores only ciphertext and
service metadata, and nothing can be read without logging in.

Development started on **4 November 2026**.

## Why

- **One timeline instead of many apps.** The schedule, the nutrition plan,
  habits and deadlines live in one calendar, with one search and one set of
  reminders.
- **Your data stays yours.** The application runs on your own machine or
  home server; even a stolen disk or a leaked backup reveals nothing.
- **Any device, no app store.** It opens in a browser and installs on the
  home screen as a progressive web app, including on iOS.
- **Suggestions, not surprises.** Smart features propose changes, and the
  user confirms them.

## Features

### Calendar and day

- Day, week, month and year views with a live clock and a clear split of
  weekdays and weekends.
- Events, repeating series with single, following and whole-series edits,
  and layers with their own colours that can be hidden or shared.
- Individual cards in the day view give direct access to edit each event,
  occurrence and dated task.
- Day notes with four importance levels, a day journal and templates for
  events and whole days.
- Inbox lists for ideas, purchases and to-dos; any item moves onto a day or
  an exact time. The Inbox is itself a module built on the public extension
  points.
- Full-text search over all records, performed on encrypted data without a
  plaintext index on disk.
- Reminders on events, series and tasks with defaults per layer and quiet
  hours, delivered as push notifications even when the browser is closed;
  each message is encrypted for one browser, so the push service sees only
  ciphertext. An event may have no clock time: its reminder then arrives a
  chosen number of days before its date. A morning summary of the day, an evening call to fill in the day
  and its survey, and "do not disturb" for a few hours.
- On an iPhone, notifications for the application added to the Home
  Screen. A Telegram bot as an optional second channel that carries only
  the word "Reminder" and the time, never a title.

### Documents

Private files with folders, tags, date and type filters, keyword search and
an adjustable storage quota. Originals and PDF previews are stored in
individually encrypted chunks. Browser media support includes seeking;
explicitly selected files can be read offline. Markdown and LaTeX files
have formatted previews. Office preview conversion
requires the isolated Linux tools described in the
[Documents module](modules/documents/README.md).

### Weather and sky

Forecasts by hour, day and quarter of an hour, air quality, the planetary
K index and radar frames for the user's places, from free sources that
need no key; coordinates leave the server rounded to about a kilometre.
Sunrise, twilight, the Moon, eclipses seen from home and meteor shower
peaks are computed on the server without the network. Notices warn of rain
or snow an hour ahead, a high UV index, the first frost, thunderstorms, an
eclipse tomorrow and a possible aurora, and sky events can go into a
calendar layer. The Weather workspace offers detailed conditions for today
and daily outlooks for a week and a month. Interactive temperature, rain
and UV charts adapt to the space available in movable, resizable cards.
The browser can supply its location with permission. The calendar's weather
panel and the Weather workspace show the Sun, the Moon and upcoming sky events alongside radar
and satellite frames. Event cards include forecasts for the event's
location. Details are in the [weather module](modules/weather/README.md).

### Everyday modules

- Alarms at an exact minute and reminders by place in a native build.
- Nutrition: a product base with prices from several store chains, meal
  plans optimised for calories, nutrients, vitamins and budget, an evening
  check-in and gentle correction.
- Pantry with expiry dates, a smart shopping list and expense tracking with
  budgets.
- Habit tracker, sleep and energy log, automatic task scheduling into free
  time slots, weekly reviews and charts.
- [Schedule import](modules/schedule/README.md) previews lessons and
  deadlines from text, Telegram messages and spreadsheets, uploaded CSV,
  Excel and ICS files, and approved HTTPS pages. Calendar entries are saved
  after confirmation.
- Chat with a language model through a local server, a protected VPS,
  Google Colab or any OpenAI-compatible API. The administration panel
  controls task routes and fallback order. Heavy work can wait in an
  encrypted queue for a provider to return. Private histories are encrypted. Both
  chat modes support
  formatted answers, text attachments, and optional access to the calendar,
  weather or web for the current question.
- Quick entry in the browser or a linked Telegram chat prepares a review
  for calendar entries, reminders and Inbox notes. The owner can allow
  selected sources, review a batch of changes and confirm or reverse it.
  The administration panel tracks gateway limits, estimated API costs,
  cache hits and encrypted transcripts.

### Module system

- Modules are written and signed by the owner and installed from a local
  catalog; each one shows what it asks for, and every account gives it
  layers one by one, for reading or for writing.
- A module adds fragments and its own pages with forms the core draws and
  checks, evening survey sections, settings built from its manifest,
  background jobs, notification channels, summary lines, a section of the
  administration panel and AI tools for assistants; a changing tool only
  proposes and waits for confirmation.
- Modules run as isolated processes, as containers of the home server or
  on another machine such as Colab, which connects with short-lived
  certificates of its own authority and a heartbeat; space keys never
  leave the application.
- A software kit with a module template, a core emulator for tests and a
  reference for every extension point; versions of the module interface
  follow semantic versioning.

### Accounts and sharing

- Light, dark and six colored interface themes with a separate color palette.
- Animated background with up to eight colors, adjustable size and intensity.
- Several accounts with the roles owner, administrator and user; new people
  join through one-time invitation codes and choose their own password.
- Layers shared between accounts with keys sealed for each receiver.
- Registered devices with a device list and one-click revocation.
- Interface in English and Russian, with dates and numbers in the user's
  locale.

### Administration panel

- A separate application on its own port with its own login and a
  mandatory second factor, reachable only from the home network.
- Sessions, users and devices, the audit journal, failed logins, blocked
  addresses, backups and system health in one place, without access to the
  content of anyone's records.
- Alarms for series of failed logins, automatic blocks, traffic spikes,
  restarts and stale backups; devices per platform, logins per day, the
  mode and the limits of the installation.

## Security

- **Encryption at rest.** Argon2id turns the password into an unlock key;
  the master key, space keys and per-record keys form a hierarchy, and
  records are sealed with AES-256-GCM bound to their identity.
- **Nothing before login.** A visitor sees only a password field: no name,
  no description, no version, and the same answer for every refused
  request. A public site can hide even that behind a door: only browsers
  that opened a one-time link from the panel see anything at all.
- **Second factor.** TOTP codes, mandatory for the administration panel and
  for every account of a public site, where an account is created with its
  factor; people join with a one-time invitation code.
- **Automatic key rotation.** Space keys and data keys are replaced every
  30 days and immediately when access is withdrawn or a device is revoked.
- **Own certificate authority.** The home network uses short-lived
  certificates that renew themselves, mutual TLS between internal services
  and a root limited to the home network.
- **Sealed backups.** Scheduled backups are encrypted for the owner and
  open only with the owner's password or printed recovery key. Each copy
  is also mirrored off the server machine, to a flash drive, a second disk
  or a cloud folder, and checked there byte for byte.
- **Web protection.** Rate limits, growing delays after failed logins, an
  automatic day-long block of an address after a series of them,
  CSRF tokens, a strict content security policy and validated input on
  every route; typical attacks and a request flood are part of the test
  suite, and a known vulnerability in a dependency stops the build.
- **Isolated modules.** A module reads only the spaces whose keys it was
  given, runs restricted by Landlock and seccomp, reaches the network only
  through the core's proxy to the domains it declared, and shows markup that
  cannot run code in the browser.

The full threat model is in [docs/THREAT_MODEL.md](docs/THREAT_MODEL.md).

## Platforms

| How it runs | Where | What it gives |
|---|---|---|
| On your own computer | Linux, Windows | Data and keys never leave the machine |
| Home server | A Linux machine with Docker; any device of the home network | Phone and computer share the same data without the internet |
| Public site | A virtual private server with its own domain and a Let's Encrypt certificate; the administration panel stays off the internet | Access from anywhere, from any browser |

On top of the site, the progressive web app installs on the home screen of
Android, iOS, Windows and Linux and opens already loaded days offline.

## Technology

| Area | Choice |
|---|---|
| Language | Python 3.12 for all application code |
| Web | FastAPI, Uvicorn, Jinja2 templates, HTMX |
| Storage | SQLite with record-level encryption; PostgreSQL for the sync server |
| Cryptography | `cryptography`, PyNaCl, argon2-cffi |
| Deployment | Docker Compose, Caddy, an own certificate authority |
| Quality | pytest, Playwright, ruff, strict mypy; CI on Linux and Windows |

## Project structure

| Directory | Purpose |
|---|---|
| [core](core/README.md) | Core library: keys, encrypted storage, accounts, calendar, search, backups |
| [web](web/README.md) | The browser application and progressive web app |
| [admin](admin/README.md) | The administration panel |
| [deploy](deploy/README.md) | Home server and public VPS: certificate authority, Caddy, Docker Compose, backups |
| [push](push/README.md) | Push sender: delivers the sealed reminder queue to the browsers' push services and to linked Telegram chats |
| [inference](inference/README.md) | Model providers, the sealed channel to the Colab model server and its notebook |
| [server](server/README.md) | Synchronisation server that stores only ciphertext |
| [workers](workers/README.md) | Background jobs and external integrations |
| [host](host/README.md) | Module host: isolated processes, the gate of remote modules, the core emulator |
| [modules](modules/README.md) | Built-in modules: Documents, Inbox, Weather and sky, and the example module |
| [sdk](sdk/README.md) | Contract for writing modules |
| [prototypes](prototypes/README.md) | Isolated technology experiments |
| [docs](docs/README.md) | Architecture, decisions, threat model and development guide |

## Documentation

- [Architecture and design](docs/VISION.md)
- [Architecture decision records](docs/ADR.md)
- [Module specification](docs/MODULES.md)
- [Threat model](docs/THREAT_MODEL.md)
- [Development, running and checks](docs/DEVELOPMENT.md)
- [Running the home server](deploy/README.md)
- [Security policy](SECURITY.md)
