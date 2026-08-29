# Oppstartsplan — activity-data

Arbeidsdokument. Kryss av underveis, endre det som ikke stemmer.
Sist oppdatert: 2026-08-25 (v8)

**Om dette dokumentet:** ligger i repoet på
`https://raw.githubusercontent.com/mariusje/activity-data/main/OPPSTART.md`.
Claude kan lese det derfra, men ikke skrive til det — oppdateringer skjer ved at
Claude lager en ny versjon eller beskriver endringen, og du eller Claude Code
committer den.

**Struktureringsprinsipp:** beslutninger står der handlingen skjer, begrunnelser
ligger samlet bakerst. Du skal aldri måtte bla framover for å vite hva du gjør nå.

**Rekkefølgen er en avhengighetskjede.** Del 2 må være ferdig og verifisert før
Del 3. Ikke hopp.

---

## Del 0 — Avklaringer

### Avgjort

- **Nytt repo, ikke videreutvikling.** ✔
  Eksisterende sykkelkart-løsning ble AI-generert i store bolker, koden er ikke
  under kontroll, og den tekniske løsningen er svak.

- **Navn: `activity-data`.** ✔
  Bevisst kjedelig arbeidsnavn. Låser verken datakilde, aktivitetstype eller form.
  Produktnavn utsettes til det finnes et produkt.

- **GitHub-bruker: `mariusje`.** ✔
  Repo: `https://github.com/mariusje/activity-data`

- **Offentlig repo.** ✔
  Gjør at Claude kan lese filene direkte via rå-URL uten synkronisering.
  **Merk:** når Strava-tokens eller faktiske GPS-data havner i repoet, må det
  gjøres privat. Da bortfaller rå-URL-metoden, og Del 3.2 må skrives om til
  GitHub-integrasjon.

- **Språk: filnavnet følger innholdets språk.** ✔

  | Hva | Språk |
  |---|---|
  | Kode, kommentarer, identifikatorer, commits, docstrings | Engelsk |
  | `PROJECT.md`, `DECISIONS.md`, `QUESTIONS.md`, `AGENTS.md` | Engelsk |
  | `LOGGBOK.md` | **Norsk** — både navn og innhold |
  | Chat med Claude, og dette dokumentet | Norsk |

  Claude Code speiler språket i konteksten sin — norske instruksjoner + engelsk
  kode gir blandingsprodukter. Loggboka er refleksjon, ikke dokumentasjon, og
  blir mer presis på morsmålet.

  **Konsekvens:** du prompter på norsk, men må be eksplisitt om at *leveransen*
  til repo-filene skrives på engelsk. Det ligger i trådpromptene.

  Bonus: engelske filnavn unngår `Ø` og `Å`, som må prosentkodes i rå-URL-er.

- **Overordnet mål: læring.** ✔
  Med et reelt ønske om at det kan bære frem mot noe kommersielt.
  **Kommersialisering er også læring** — formalitetene rundt App Store,
  distribusjon, personvern og vilkår er kunnskap i seg selv.

### Gjenstår

- [ ] **Hva tar du med fra sykkelkart?**
  Ikke koden. Men `LOGGBOK.md` og erfaringene er fortsatt relevante.
  Beslutning: _______________

---

## Del 1 — Hvor filene lever

| Sted | Hva | Merknad |
|---|---|---|
| **Repoet** (lokal mappe + GitHub) | md-filene, koden | Én kilde til sannhet |
| **Prosjektinstruksjoner** | Stående regler + rå-URL-er | Gjelder alle tråder |
| **Prosjektkunnskap** | Opplastede filer | Unngå — lager duplikater |

**Prinsipp: ingen kopier.** Filene lever kun i repoet. Claude leser derfra.

### Tre måter Claude kan få tilgang — én er valgt

| Metode | Alltid fersk | Privat repo | Innsats |
|---|---|---|---|
| **Rå-URL i prosjektinstruksjoner** ← valgt | Ja | Nei | Sett opp én gang |
| GitHub-integrasjon i prosjektkunnskap | Nei (snapshot) | Ja | «Sync now» etter hver push |
| Manuell opplasting | Nei (kopi) | Ja | Last opp på nytt hver gang |

### Viktig teknisk detalj

Claude kan **kun hente URL-er som faktisk står i samtalekonteksten.** En adresse
Claude gjetter seg til ved å bytte filnavn i en kjent URL, blir avvist.

Derfor må prosjektinstruksjonene inneholde de **ferdig utfylte** URL-ene. Da
ligger de i konteksten i hver tråd, og henting virker.

Legger du til en ny md-fil senere: legg URL-en inn i instruksjonene, ellers når
ikke Claude den.

---

## Del 2 — Sett opp repoet FØRST

Må være ferdig, pushet og verifisert før Del 3.

### 2.1 Opprett på GitHub ✔

- [x] Repository `activity-data` opprettet
- [x] Synlighet: Public
- [x] GitHub-bruker: `mariusje`
- [ ] README
- [ ] `.gitignore` for Python

### 2.2 Klon lokalt ✔

```
git clone https://github.com/mariusje/activity-data.git
cd activity-data
```

### 2.3 Opprett filene

Alle på `main`. Innholdet under er det du limer inn.

**Eierskap:**

| Fil | Språk | Hvem skriver |
|---|---|---|
| `PROJECT.md` | Engelsk | Utkast fra Claude → du redigerer og limer inn |
| `DECISIONS.md` | Engelsk | Utkast fra Claude → du limer inn |
| `QUESTIONS.md` | Engelsk | Du, fortløpende |
| `LOGGBOK.md` | Norsk | **Du, manuelt. Alltid.** |
| Kode | Engelsk | Claude Code |

Claude i chatten kan aldri skrive til repoet ditt. Claude Code kan.

---

**`PROJECT.md`** — ankeret. Hva dette er, hvem det er for, hva som er utenfor
scope. Fylles ut i tråd 1. Opprett med kun dette:

```markdown
# activity-data

Working title. Scope to be defined in thread 1.

## What this is

## Who it is for

## Explicitly out of scope

## Branching

- Documentation lives on `main`.
- Code is developed on feature branches, one per phase, merged via PR.
```

---

**`DECISIONS.md`** — beslutningslogg:

```markdown
# Decisions

One entry per decision. Newest at the bottom.

## Template

## [Date] — [Short title]
**Decision:** what was decided
**Alternatives considered:** what was rejected
**Rationale:** why
**Status:** current / revised [date]
```

---

**`QUESTIONS.md`** — parkeringsplass. Opprett med de kjente punktene inne:

```markdown
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

## Skill candidates (do not create yet — note when triggered)
- End-of-thread routine: repeated every thread, well-defined procedure.
  Strongest candidate. Reassess after 3-4 threads.
- Training-data domain knowledge that has to be re-explained each time.
- Project-specific code patterns too detailed for AGENTS.md.
```

---

**`LOGGBOK.md`** — norsk:

```markdown
# Loggbok

Én oppføring per arbeidsøkt. Skrives for hånd, ikke av AI.

## Mal

## [Dato] — [Tråd/fase]
1. Hva jeg gjorde:
2. Hva jeg forventet:
3. Hva som skjedde:
4. Hva jeg ville formulert annerledes:
5. Lærdom:
```

Punkt 4 er der læringen sitter. Den mister all verdi hvis en AI formulerer den.

---

**`OPPSTART.md`** ✔ — dette dokumentet, allerede i repoet.

**`AGENTS.md`** — **opprettes ikke nå.** Den skal skrives etter tråd 5, når du
vet hva som faktisk skal bygges. Innhold i Del 6.

- [ ] `PROJECT.md`
- [ ] `DECISIONS.md`
- [ ] `QUESTIONS.md`
- [ ] `LOGGBOK.md`

### 2.4 Branching-strategi

**Standard branch: `main`.**

| Type arbeid | Hvor |
|---|---|
| Dokumentasjon | Rett på `main` |
| Kode | Feature-branch per fase → PR → merge til `main` |

**Hvorfor dokumentasjon rett på main:** rå-URL-ene peker på
`.../activity-data/main/PROJECT.md`. Ligger en oppdatert beslutning i en
feature-branch, ser ikke Claude den.

**Hvorfor feature-branches for kode:** gir et sted å rulle tilbake fra når en fase
går galt, og PR-en tvinger frem at du leser din egen diff. Å faktisk lese diffen
er hele poenget denne gangen — forrige prosjekt havnet ute av kontroll fordi
store bolker gikk inn uten at du kjente dem.

Navngiving: `phase-1-strava-import`, `phase-2-aggregation`.

Solo-arbeid, så PR-en er ikke for andres review. Den er et lesepunkt for deg selv
før koden treffer `main`.

### 2.5 Commit, push og verifiser

```
git add .
git commit -m "Initial project structure"
git push
```

- [x] **Rå-URL-metoden er verifisert** — Claude leste `OPPSTART.md` direkte fra
      `https://raw.githubusercontent.com/mariusje/activity-data/main/OPPSTART.md`
- [ ] Verifiser tilsvarende for `PROJECT.md` når den er pushet

---

## Del 3 — Sett opp Claude-prosjektet

**Forutsetning: filene fra 2.3 er opprettet og pushet.**

### 3.1 Opprett prosjektet

- [ ] `claude.ai/projects` → «+ New Project»
- [ ] Navn: `activity-data` (Claude ser ikke navn/beskrivelse — kun for deg)

### 3.2 Sett prosjektinstruksjoner

Klikk «Set project instructions». Denne limes inn som den er:

```
Dette prosjektet handler om utvikling av et treningsdata-verktøy (activity-data).
Overordnet mål er læring, med et sekundært ønske om at det kan bli
noe kommersialiserbart på sikt.

Prosjektfilene ligger i et offentlig GitHub-repo, på branch main. Hent ved behov:
- PROJECT.md:    https://raw.githubusercontent.com/mariusje/activity-data/main/PROJECT.md
- DECISIONS.md:  https://raw.githubusercontent.com/mariusje/activity-data/main/DECISIONS.md
- QUESTIONS.md:  https://raw.githubusercontent.com/mariusje/activity-data/main/QUESTIONS.md
- OPPSTART.md:   https://raw.githubusercontent.com/mariusje/activity-data/main/OPPSTART.md
- AGENTS.md:     https://raw.githubusercontent.com/mariusje/activity-data/main/AGENTS.md
  (AGENTS.md finnes ikke ennå — opprettes senere)

Hent PROJECT.md og DECISIONS.md ved starten av enhver tråd som gjelder
retning, arkitektur eller planlegging.

Språk:
- Chatten går på norsk.
- Alt du skriver som skal INN i repoet — PROJECT.md, DECISIONS.md,
  QUESTIONS.md, AGENTS.md, kode — skal være på engelsk, uavhengig av
  hvilket språk vi snakker.
- LOGGBOK.md er på norsk, og den skriver jeg selv. Ikke tilby utkast til den.

Rollefordeling:
- Denne chatten brukes til tenking: idémyldring, arkitekturbeslutninger,
  trykktesting av forslag, retrospektiv.
- Claude Code brukes til all faktisk koding.
- Ikke skriv kode her med mindre jeg eksplisitt ber om det.

Arbeidsform:
- Motsi meg når du er uenig. Jeg er ute etter motstand, ikke bekreftelse.
- Jeg formulerer mine egne prompts først — spar på dem før de går til Claude Code.
- Hold deg til trådens scope. Si fra hvis vi driver av.

Ved slutten av en tråd, når jeg ber om det: skriv et ferdig utkast til
oppføring i DECISIONS.md på engelsk, som jeg kan lime rett inn.
```

- [ ] Limt inn og lagret

**Merk:** URL-ene må stå ferdig utfylt. Claude kan ikke konstruere en adresse selv
— den må finnes i konteksten. Legger du til nye md-filer senere, må URL-en inn
i denne lista.

### 3.3 Test

- [ ] Start tråd 1 og be Claude hente `PROJECT.md` som første handling
- [ ] Bekreft at innholdet stemmer med det du la inn i 2.3
- [ ] Virker det ikke: bytt til GitHub-integrasjon — klikk «+» i
      prosjektkunnskap-panelet til høyre → legg til fra GitHub → velg md-filene.
      Husk da «Sync now» etter hver push.

---

## Del 4 — Trådene

Én tråd per tema. Ikke én evigvarende megatråd.

**Modellvalg står i hver trådoverskrift.** Begrunnelsen ligger i Del 8.
Haiku brukes ikke i noen av disse — ingen er mekanisk arbeid.
Du kan bytte modell midt i en tråd; konteksten følger med.

**Avslutningsrutinen for hver tråd står i Del 5.** Les den før du starter tråd 1,
så vet du hva tråden skal ende i.

---

### Tråd 1 — Avgrensning — **Opus**

**Forutsetning:** Del 2 og 3 ferdig.
**Sluttprodukt:** `PROJECT.md` fylt ut, på engelsk.

**Åpningsprompt — utkast:**

```
Hent PROJECT.md fra repoet først, så vi begge ser hva som står der.

Denne tråden handler kun om å avgrense hva dette prosjektet skal være.
Ikke foreslå kode, teknologi eller arkitektur.

Utgangspunkt: jeg vil bygge noe innen treningsdata. Utover det er det åpent.
Jeg har GPS- og aktivitetsdata fra Strava. Overordnet mål er læring, men jeg
ønsker ideelt noe som byr på noe som ikke allerede finnes.

Start med å stille meg spørsmål framfor å foreslå løsninger. Jeg vil at du
graver i hva jeg faktisk savner når jeg ser på treningsdataene mine —
ikke hva som er teknisk mulig.

Utfordre meg. Hvis en idé allerede løses godt av Strava eller Garmin, si det
rett ut framfor å være høflig.

Vi snakker norsk, men når vi til slutt skal fylle ut PROJECT.md, skriver du
det ferdige innholdet på engelsk.
```

**Hva som gjør denne tråden god:**
- Be om spørsmål før forslag. Ellers får du tjue ideer og null retning.
- **Nøkkelspørsmålet:** hva gjør dette som Strava/Garmin ikke allerede gjør?
- Ikke godta et tynt svar på det. Det er greit at svaret er «ingenting, dette er
  et læringsprosjekt» — men da *vet* du det, og valgene videre blir andre.

---

### Tråd 2 — Idémyldring — Sonnet

**Forutsetning:** `PROJECT.md` fylt ut og pushet til `main`.
**Sluttprodukt:** `PROJECT.md` oppdateres, resten til `QUESTIONS.md`.

**Åpningsprompt — utkast:**

```
Hent PROJECT.md fra repoet først.

Denne tråden handler kun om idégenerering innenfor rammene der.
Ikke foreslå teknologi eller arkitektur.

Jeg vil ha få, gode ideer framfor mange. Foreslå maks 5, og gå så i dybden
på de 2-3 jeg peker ut.

Let spesielt etter det store plattformer strukturelt ikke vil bygge:
- smale brukergrupper som ikke er verdt det for dem
- kryssing av datakilder de ikke har tilgang til
- spørsmål de ikke er interessert i å stille

For hver idé jeg peker ut: si hva som er det svakeste ved den,
ikke bare hva som er lovende.

Vi snakker norsk, men alt som skal inn i repo-filene skriver du på engelsk.
```

**Hva som gjør denne tråden god:**
- Tak på antall ideer. Ubegrenset idégenerering føles produktivt og er det ikke.
- Be eksplisitt om svakheter. Ellers får du bare oppside.
- Flaskehalsen er aldri mangel på ideer — den er å bestemme hva du *ikke* bygger.

---

### Tråd 3 — Plattform — Sonnet

**Forutsetning:** tråd 2 avsluttet, `DECISIONS.md` oppdatert på `main`.

- [ ] Mobil vs. web vs. lokalt verktøy
- [ ] Bør stort sett falle ut av tråd 1 og 2 — hvis ikke, mangler noe der
- [ ] Ta med: hvilken plattform lærer du mest av? Hva er lettest å distribuere senere?
- [ ] → `DECISIONS.md`

---

### Tråd 4 — Teknologi + arkitektur — **Opus**

**Forutsetning:** plattformvalg tatt.

- [ ] Én tråd, ikke to. På denne størrelsen henger de sammen.
- [ ] Datamodell, lagring, avhengigheter
- [ ] → `DECISIONS.md`

---

### Tråd 5 — Fasedeling — Sonnet

**Forutsetning:** teknologivalg tatt.

- [ ] Del utviklingen i små, testbare biter
- [ ] Hver fase: ett mål, én leveranse, ett valideringspunkt
- [ ] Hver fase = én feature-branch
- [ ] → faseplan i repoet

**Etter tråd 5, før første kodeøkt:** skriv `AGENTS.md` (Del 6).

---

## Del 5 — Rutiner for hver tråd

### Ved start
- [ ] «Hent PROJECT.md og DECISIONS.md fra repoet først.»
- [ ] Sett scope eksplisitt: «Denne tråden handler kun om [X]. Ikke foreslå [Y].»
- [ ] Velg modell fra trådoverskriften i Del 4

### Underveis
- [ ] Off-topic → skriv i `QUESTIONS.md`, ikke forfølg det i tråden

### Ved slutt

**1. Be om utkast:**
> «Skriv et ferdig utkast til oppføring i DECISIONS.md for denne tråden, på
> engelsk. Bruk malen: Decision / Alternatives considered / Rationale / Status.
> Gi meg kun markdown-teksten, så jeg kan lime den rett inn.»

**2. Kopier** markdown-teksten fra svaret.

**3. Lim inn i `DECISIONS.md`** — i det lokale repoet, på `main`, nederst under
tidligere oppføringer. Les gjennom og rett det som ikke stemmer. Dette er *din* logg.

**4. Skriv loggbokoppføring** i `LOGGBOK.md`, på norsk, på `main`.
**Dette gjør du selv, for hånd. Ikke be om utkast.**
Punkt 4 i malen er den viktigste.

**5. Commit og push til `main`:**
```
git checkout main
git add DECISIONS.md LOGGBOK.md QUESTIONS.md
git commit -m "Thread [N]: [short description]"
git push
```

Rå-URL-ene peker på `main`. Ligger beslutningen i en feature-branch, ser ikke
neste tråd den.

**6. Ferdig.** Ingen synkronisering nødvendig.

---

## Del 6 — Kodedisiplin (`AGENTS.md`)

**Opprettes etter tråd 5, før første kodeøkt.** Engelsk.

Målet denne gangen: **kjenne koden**, ikke bare ha den.
Store AI-genererte bolker skjer ikke fordi Claude Code er ivrig — det skjer fordi
ingenting i oppsettet stopper den.

Regler som skal inn:

- [ ] **Språk:** `All code, comments, identifiers, commit messages and
      docstrings in English.`
      Med denne på plass kan du prompte på norsk uten at det lekker inn i koden.
- [ ] **Plan før kode, hver gang**
      «Lag en plan. Ikke implementer ennå.»
      Les planen, marker feil, send tilbake: «adresser notatene, ikke implementer ennå».
      Gjenta til planen er riktig. *Da* implementerer du.
- [ ] **Én enhet om gangen**
      Ikke «bygg importmodulen» — men «skriv funksjonen som parser én aktivitet,
      med tester, og stopp der».
      Er diffen for stor til at du orker å lese den nøye, var oppgaven for stor.
- [ ] **Forklar-tilbake-testen**
      Etter hver bit: lukk skjermen, forklar for deg selv hva koden gjør.
      Klarer du det ikke → be Claude Code gå gjennom den linje for linje.
- [ ] **Commit per bit**, feature-branch per fase
- [ ] **Testing er en betingelse, ikke en fase**
      Tester følger med hver oppgave. Legges de til slutt, får du et etterslep
      du aldri tar igjen.

---

## Del 7 — Skills

**Skills er atferdskorreksjoner, ikke kunnskapslagring.** De lages når du har
måttet korrigere den samme tingen gjentatte ganger — tommelfingerregelen er tre
repetisjoner.

Fase 2 i sykkelkart illustrerte dette: du forventet å måtte korrigere
H3-aggregeringen, det ble ikke nødvendig, og dermed ble det ingen skill. Riktig
konklusjon. En skill uten forutgående friksjon er gjetning.

**Ikke lag skills på forhånd.** Vent på friksjonen. Kandidatene ligger notert i
`QUESTIONS.md` fra 2.3.

### To ulike steder skills kan bo

| Sted | Hva | Når |
|---|---|---|
| **Claude Code** (`.claude/skills/` i repoet) | Kodeatferd | Når du korrigerer samme kodeting 3× |
| **Denne chatten** (globale skills) | Arbeidsflyt og metodikk | Når en prosedyre gjentas på tvers av prosjekter |

### Eksisterende skills som er relevante

- `sdd-navigator` — når du er usikker på hvilken SDD-skill som passer
- `sdd-domain-skill-extractor` — når du skal skrive de første domeneskillene
- `sdd-skill-health-check` — kvartalsvis, eller når skills føles utdaterte
- `context-engineering-audit` — vurder etter at `AGENTS.md` finnes

### Grensen mot `AGENTS.md`

`AGENTS.md` er stående regler som alltid gjelder. Skills utløses situasjonelt.
Kort og alltid relevant → `AGENTS.md`.
Krever mer forklaring og gjelder bare noen ganger → skill.

Ikke start med skills. `AGENTS.md` dekker mer enn du tror i starten.

---

## Del 8 — Modellvalg: begrunnelse

Selve valget står i trådoverskriftene i Del 4. Her er hvorfor.

### Chat-trådene

**Tråd 1 — Opus.** Kanskje kontraintuitivt, siden det «bare er snakk». Men alt
annet henger på denne tråden. En tråd 1 som lander på en tynn premiss gir deg
fire påfølgende tråder som er godt gjennomført på feil grunnlag. Du trenger også
reell motstand her — at modellen faktisk sier «det løser Strava allerede» framfor
å bygge videre på det du foreslår.

**Tråd 4 — Opus.** Den klassiske: valg du må leve med, der feil koster ombygging.

**Tråd 2, 3 og 5 — Sonnet.** Idégenerering, plattformvalg og fasedeling er arbeid
der du har sterke meninger selv og trenger en kompetent motpart, ikke maksimal
tenkekraft. Tråd 3 bør dessuten stort sett være avgjort av tråd 1 og 2 — krever
den tung tenkning, mangler noe lenger opp.

**Merker du at svarene blir for medgjørlige i en Sonnet-tråd:** bytt til Opus og
fortsett i samme tråd.

### Claude Code

| Modell | Bruk til |
|---|---|
| **Sonnet** | Standard. Det meste. |
| **Opus** | Når det å ta feil er dyrt: arkitektur, datamodell, valg du må leve med |
| **Haiku** | Kun ekte mekanisk arbeid |

Lærdom fra sykkelkart fase 4: «liten oppgave» og «mekanisk oppgave» er ikke det
samme. Norge/Italia-problemet så ut som en fargejustering, men var et designvalg.
Haiku klarte det ikke.

På Pro betaler du ikke per token. Ikke velg ned modell for å spare penger du
ikke bruker.

---

## Åpne spørsmål

- [x] ~~Virker rå-URL-metoden?~~ Ja, verifisert med `OPPSTART.md`.
- [ ] Er `sykkelkart` avsluttet, eller lever det parallelt som referanse?
- [ ] Skal `AGENTS.md` leses av chatten, ikke bare Claude Code?
      URL-en ligger allerede i instruksjonene — ta stilling når fila finnes.

---

## Sjekkliste — status

**Del 2 — repo**
1. [x] Offentlig repo `activity-data` opprettet
2. [x] Klonet lokalt
3. [x] `OPPSTART.md` pushet og verifisert lesbar
4. [ ] README og `.gitignore` for Python
5. [ ] `PROJECT.md`, `DECISIONS.md`, `QUESTIONS.md`, `LOGGBOK.md` med innhold fra 2.3
6. [ ] Commit og push til `main`

**Del 3 — Claude-prosjekt**
7. [ ] Opprett prosjekt `activity-data`
8. [ ] Lim inn prosjektinstruksjoner (3.2 — ferdig utfylt, klar til bruk)
9. [ ] Start tråd 1 (Opus) og test filhenting som første handling
