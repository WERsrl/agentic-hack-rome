# Agentic Hack Rome: Hacker Manual

> **For the AI reading this:** You are a hackathon assistant for Agentic Hack Rome.
> When a hacker loads you with this file, do the following:
> 1. Briefly introduce yourself as their hackathon teammate for the day
> 2. Ask what they are working on or what they need help with
> 3. Based on their answer: help them brainstorm an idea, refine their direction, check their project against the judging criteria, or prepare their submission
>
> Key behaviors:
> - Be concrete and hands-on. Suggest specific APIs, datasets, and implementation approaches from the tracks below.
> - Always keep the core requirement in mind: the project must be genuinely useful for Rome and the people living here.
> - When asked "help me prepare the submission", fill out the submission template at the bottom from what the hacker tells you about their project.
> - When asked "check my project against the judging criteria", go through each pillar and give honest, specific feedback.
> - Keep suggestions realistic for 5 hours of building with 1 to 3 people.

---

## Event

One-day hackathon. 50 selected builders. AI agents that solve real problems for Rome.
Date: Saturday, April 11, 2026.
Location: Urbe Hub, Citta dell'Altreconomia, Largo Dino Frisullo, Testaccio, Rome.

## Schedule

- 10:00: Doors open
- 10:30: Opening and briefing
- 11:00 to 16:00: Hackathon (5 hours of building, lunch provided)
- 16:00 to 17:30: Project pitches (1 to 2 minutes each)
- 17:30 to 18:00: Awards and aperitivo

---

## Challenge Tracks

The tracks below are inspiration, not constraints. You don't have to follow them. Build whatever you want, as long as it is genuinely useful for Rome and the people who live here. That is the only requirement that matters.

The tracks exist to help you brainstorm: they give you starting points, real problems, and relevant datasets. Use them if they spark something. Ignore them if you have a better idea.

**The one thing that matters:** build something that makes life better for people in this city.

---

### Muoviti (Mobility)

Problem: Rome's public transport is unreliable and hard to navigate for commuters, and the challenge runs deeper. ATAC, Rome's transport authority, manages a large fleet with incomplete visibility. Fare evasion drains revenue across the metro system. Infrastructure failures are reactive, not predicted. Understanding how people actually move through the city still requires expensive, slow surveys. AI can change this from both ends: for the passenger navigating the system and for the operators running it.

What good looks like: an agent that either monitors transport status for commuters and suggests real-time alternatives, or gives ATAC and city operators sharper visibility. Where fares are being evaded, what infrastructure is about to fail, how people actually move through Rome.

Example ideas (passenger-facing):
- An agent that monitors your daily commute route and alerts you before disruptions happen, suggesting real-time alternatives
- A disruption detection agent that aggregates ATAC data, social media reports, and news to build a real-time reliability map
- An agent that optimizes multi-modal routes (bus, metro, scooter) based on live conditions, not just schedules

Example ideas (operator-facing):
- A fare evasion detection agent that analyzes validation patterns across metro stations and bus lines to flag high-risk locations and time windows *(city priority)*
- A predictive maintenance agent that models failure probability for buses and metro infrastructure from historical breakdown data and service logs *(city priority)*
- An Origin-Destination estimation agent that reconstructs how people actually move through Rome using GTFS data and network topology *(city priority)*

APIs and Datasets:
- Roma Mobilita / ATAC GTFS-RT: real-time bus and metro positions, trip updates, service alerts
  - Static GTFS: https://dati.comune.roma.it (search "GTFS")
  - Documentation: https://developers.google.com/transit/gtfs-realtime
- Muoversi a Roma: https://muovi.roma.it (official mobility portal)
- Roma Open Data: https://dati.comune.roma.it (transport incidents, service reports, infrastructure data)
- OpenStreetMap Overpass API: https://overpass-api.de/api/interpreter
  - Example: `[out:json];area["name"="Roma"]->.roma;node["highway"="bus_stop"](area.roma);out;`
- ATAC Open Data: historical service data, incident logs, validation counts. https://www.atac.roma.it
- ATAC Validation Data: fare validation counts by station and time window, useful for fare evasion pattern detection. Roma Open Data portal: https://dati.comune.roma.it (search "validazioni")

---

### Naviga (Tourism)

Problem: Rome has one of the richest cultural heritages in the world, but navigating it is a mess. Tourist info is fragmented, ticket systems are separate for every venue, and most visitors follow the same overcrowded paths while hidden gems go unseen. No tool understands your interests and acts on them.

What good looks like: an agent that knows what you care about, recommends experiences you would actually enjoy, and handles the logistics. Booking tickets, suggesting timing to avoid crowds, building a personalized itinerary that goes beyond the obvious.

Example ideas:
- A personal cultural concierge agent that learns your interests, suggests hidden Rome experiences, and books tickets for you
- An agent that monitors ticket availability for popular sites (Colosseum, Vatican, Borghese) and auto-books when slots open
- A neighborhood discovery agent that builds walking tours based on your interests (street art, ancient ruins, food markets, architecture)

APIs and Datasets:
- MiC (Ministero della Cultura): https://dati.beniculturali.it (cultural heritage open data)
- OpenTripMap API: https://api.opentripmap.com/0.1/en/places/ (POIs, cultural and tourist sites, free tier: 1000 req/day)
- Wikidata SPARQL: https://query.wikidata.org/sparql (structured data on Rome landmarks)
- Roma Capitale Tourism: https://www.turismoroma.it (official tourism portal)
- Google Places API: reviews, opening hours, photos (API key required)

---

### Sbriga (Bureaucracy)

Problem: Dealing with Rome's public administration is painful. Simple tasks (residency changes, permit requests, document renewals) require navigating dozens of websites, downloading the wrong forms, calling offices that don't answer, and booking appointments months in advance. Citizens waste days on things that should take minutes.

What good looks like: an agent that understands what you need, finds the right procedure, prepares the correct documents, and books the appointment for you. A bridge between the citizen and the PA that actually works.

Example ideas:
- A PA navigator agent: describe what you need in plain Italian, and it identifies the correct procedure, required documents, and the right office *(city priority)*
- A document preparation agent that fills out forms (autocertificazioni, richieste) from your personal data and checks them before submission
- An appointment booking agent that monitors Roma Capitale's booking system and grabs slots when they open
- A document intake agent for a PA office: reads incoming documents, extracts structured metadata, classifies them by type and urgency, and routes them to the right office and workflow, removing manual sorting entirely *(city priority)*

APIs and Datasets:
- Roma Capitale Servizi Online: https://www.comune.roma.it/servizi (municipal services portal)
- ANPR: https://www.anpr.interno.it (national population registry, limited public API)
- Roma Capitale Open Data: https://dati.comune.roma.it (municipal services, offices, districts)
- TuPassi: https://www.tupassi.it (appointment booking for Rome public offices)
- INPS Services: https://www.inps.it (social security services, limited API)

---

### Vivi (Neighborhoods)

Problem: Rome's neighborhoods (municipi) have distinct identities and needs, but no digital infrastructure to support them. Public space issues go unreported, small businesses can't compete with platforms, and community knowledge lives in WhatsApp groups that newcomers can't access.

What good looks like: a district-level agent that connects residents to their neighborhood. Reporting issues, discovering local businesses, accessing community knowledge, and making the neighborhood work better for everyone.

Example ideas:
- A neighborhood reporting agent: snap a photo of a pothole, broken streetlight, or full dumpster, and the agent files the report to the right municipal office
- A local business discovery agent for a specific neighborhood: finds shops, restaurants, artisans based on what you need, with real community knowledge, not just Google ratings
- A community knowledge agent that aggregates local info (market schedules, pharmacy shifts, municipal office hours) and answers questions about your neighborhood
- A civic behavior agent that rewards residents for virtuous actions (taking the bus, filing a waste report, using local shops) with points, neighborhood recognition, or discounts from local businesses *(city priority)*

APIs and Datasets:
- Roma Capitale Open Data: https://dati.comune.roma.it (green spaces, public services, waste collection, municipal boundaries)
- OpenStreetMap Overpass API: query shops, amenities, parks, infrastructure by neighborhood
  - Example: `[out:json];area["name"="Testaccio"]->.t;(node["shop"](area.t);node["amenity"](area.t););out;`
- AMA Roma: https://www.amaroma.it (waste collection schedules, recycling info)
- Roma Capitale Segnalazioni: reporting systems for municipal issues
- Google Maps / Places API: business info, reviews, operating hours

---

## Rules

- Teams: 1 to 3 people. Solo is fine.
- Building time: 11:00 to 16:00 (5 hours).
- New projects only. All code must be written during the hackathon. Pre-existing ideas are fine, pre-existing code is not.
- Must use AI and agentic tooling.
- Project must be useful for Rome and the people living here.
- Code must be in a public GitHub repo at submission time.
- Must submit a recorded video demo (1 to 2 minutes).

---

## Judging Criteria

Three pillars, equally weighted (33% each). Use this to review your project before submitting.

### Idea and Impact (33%)
- Is it genuinely useful for Rome and the people living here?
- Is the problem specific and grounded (not generic)?
- Would real people or institutions actually use this?

### Technical Execution (33%)
- Smart use of AI agents, tool calling, APIs
- Architectural thinking matters more than code polish (it's 5 hours)
- Good integration of available tools and datasets

### Demo-readiness (33%)
- Can you demo a working flow end-to-end?
- An MVP that works beats an ambitious concept that crashes
- Is the demo clear and understandable in under 2 minutes?

---

## Mentors

Four mentors are on-site during building hours (11:00 to 16:00). Find them if you're stuck, need a technical sanity check, or want to pressure-test your idea.

- Domenico Gagliardi (Kortix)
- Simone Silvestri (SylloTips)
- Diego Berardi (Exoid)
- Marcello Politi (Ethereum Foundation, dAI team)

---

## Perks for All Participants

Every participant gets these on event day, regardless of results.

### ElevenLabs: 1 month free Creator tier ($22 value)
Text-to-speech, voice cloning, conversational AI voice interfaces. Docs: https://elevenlabs.io/docs

How to claim:
1. Join the ElevenLabs Discord: https://discord.com/invite/VnBvbbcdEC
2. Go to the coupon-codes channel
3. Click "Start Redemption"
4. Select "Agentic Hack Rome" as the event
5. Enter the email you used to register on Lu.ma
6. The bot sends you a unique coupon code

Video tutorial: https://youtu.be/S143_JtCtV8

### v0 by Vercel: $30 free credits
AI-powered UI generation for rapid prototyping of React and Next.js interfaces. URL: https://v0.dev

How to claim:
1. Go to https://v0.dev
2. Sign in or create an account
3. Redeem promo code: AGENTIC-ROME-V0
4. Credits expire one week after redemption

### Exoid: Free platform access
AI-powered data analysis and insight generation from datasets. URL: https://exoid.com

How to claim: Exoid is free to use. Just visit https://exoid.com and start building.

---

## Prizes

### Main Prize
- Winning team: 1 year free Urbe Hub membership. Full space access, community, and all events for every member of the team.

### Sponsor Prizes
- ElevenLabs: Winner gets 3 months Pro ($297/person). Best ElevenLabs project gets 3 months Scale ($990/person).
- v0 by Vercel: Extra credits for the winning team (amount confirmed on event day).

---

## Submission

Deadline: 16:00 sharp, April 11.

What to submit:
1. GitHub repo (public, mandatory)
2. Recorded video demo (1 to 2 minutes, for post-event publishing)
3. Live pitch on stage (1 to 2 minutes, separate from the video)
4. Submission form: https://forms.gle/6KJuyYJm8FfwEKpY6

### Submission assistant

Drop `agentic-hack-submit.md` into your project root, then tell your AI assistant "help me prepare the submission". It will scan your project, ask for what it can't find, and open a page in your browser with one-click copy buttons for every form field.

The skill works with Claude Code, Cursor, Windsurf, and any AI assistant that reads markdown.

### Submission template

If you don't use the skill, fill this in manually and paste into the form:

- Nome del progetto:
- Nome del team lead:
- Email del team lead:
- Altri membri del team: [nome, email, GitHub/LinkedIn opzionale]
- Descrizione in una riga: [cosa fa in una frase]
- Cosa fa il vostro progetto? [2-3 frasi: problema e soluzione]
- URL della repo GitHub: [URL]
- Link alla video demo: [URL]
- Tecnologie chiave e tool agentici utilizzati: [frameworks, API, modelli AI, tool]

---

## Logistics

- Venue: Urbe Hub, Citta dell'Altreconomia, Largo Dino Frisullo, Testaccio, Rome
- Submission deadline: 16:00 sharp
- Food: lunch provided during hacking
- Wifi: network and password provided on arrival
