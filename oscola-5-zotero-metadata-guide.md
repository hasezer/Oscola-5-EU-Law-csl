# OSCOLA 5 in Zotero — metadata entry guide

Companion to `oscola-5th-edition.csl`. Every rule below is what the style expects; if a field is left empty, that element simply disappears from the citation.

---

## 1. EU legislation → Zotero item type **Statute**

| OSCOLA element | Zotero field | Example |
|---|---|---|
| Full title incl. type + number | **Name of Act** | `Council Directive 2002/60/EC of 27 June 2002 laying down specific provisions for the control of African swine fever` |
| `[year]` | **Date Enacted** | `2002` |
| OJ series | **Code** | `OJ` |
| Series letter + issue | **Code Number** | `L192` |
| First page | **Pages** | `27` |
| Short form for later footnotes | **Short Title** | `Rome I Regulation` |

**Output:** `Council Directive 2002/60/EC of 27 June 2002 laying down specific provisions for the control of African swine fever [2002] OJ L192/27.`

Same pattern for EU treaties and protocols — only the series letter changes:

> `Consolidated Version of the Treaty on European Union [2020] OJ C202/1 ('Maastricht Treaty').`

**Pinpoints:** in the Word/LibreOffice citation dialog set the locator type to *Article* or *Section* and type `3(1)` → `…, art 3(1)`.

**UK / domestic statutes:** leave **Code**, **Code Number** and **Pages** empty. The year lives inside the Name of Act, so nothing else is printed: `Human Rights Act 1998, s 15(1)(b).`

**Assimilated EU law (OSCOLA 5, 2.4.9):** type `Assimilated` at the front of the Name of Act, leave Code empty, and put the amending SI in the Name of Act as OSCOLA shows.

---

## 2. International treaties → **Statute** + one line in *Extra*

In the **Extra** field, the very first line must be:

```
Type: treaty
```

This switches the item to the CSL `treaty` type and changes the whole output shape.

| OSCOLA element | Zotero field | Example |
|---|---|---|
| Treaty title (+ parties, if bilateral) | **Name of Act** | `Convention Relating to the Status of Refugees` |
| adopted … | **Date Enacted** | `28 July 1951` |
| entered into force … | **Extra:** `Original-date: 1954-04-22` | |
| Series volume | **Code Number** | `189` |
| Series | **Code** | `UNTS` |
| First page | **Pages** | `137` |
| Short form | **Short Title** | `Refugee Convention` |

**Extra field looks like this:**
```
Type: treaty
Original-date: 1954-04-22
```

**Output:** `Convention Relating to the Status of Refugees (adopted 28 July 1951, entered into force 22 April 1954) 189 UNTS 137 ('Refugee Convention').`

For bilateral treaties, type the parties into the Name of Act exactly where OSCOLA prints them, e.g. `Agreement on Trade (Israel–Jordan)`.

---

## 3. Cases → Zotero item type **Case**

One template covers CJEU, ECtHR, ICJ, ICC and arbitral tribunals. What matters is *which fields you leave empty*.

| Zotero field | What goes in it | Printed |
|---|---|---|
| **Docket Number** | `Case C-403/03` (type the word "Case") | before the case name |
| **Case Name** | party names only — this is what gets italicised | italic |
| **Extra:** `Genre: (Merits) (Judgment)` | phase / type of decision | roman, after the name |
| **Court** | `ECtHR`, `ACHPR` … | after the name |
| **Reporter Volume / Reporter / First Page** | report or identifier information | in that order |
| **Date Decided** | only where OSCOLA prints a date in brackets | `(15 June 2009)` |

### The five patterns

**CJEU / General Court** — ECLI replaces the old ECR reference:
- Docket Number `Case C-403/03`, Case Name `Schempp v Finanzamt`, Reporter `EU:C:2005:446`, **Date Decided empty**
- → `Case C-403/03 Schempp v Finanzamt EU:C:2005:446 [19].`

**ICJ** — the year is part of the report reference, so put it in Reporter Volume:
- Reporter Volume `[2021]`, Reporter `ICJ Rep`, First Page `71`, **Date Decided empty**
- → `Application of the … (Qatar v UAE) (Preliminary Objections) (Judgment) [2021] ICJ Rep 71.`

**ECtHR:**
- Court `ECtHR`, Reporter `App Nos 8019/16, 43800/14 and 28525/20`, Date Decided `25 January 2023`
- → `Ukraine and the Netherlands v Russia (Jurisdiction and Admissibility) (Decision) [GC] ECtHR App Nos … (25 January 2023) [826].`

**ICC / criminal tribunals:**
- Reporter `ICC-01/05-01/08`, Date Decided `15 June 2009`
- → `Prosecutor v Bemba (Decision on the Confirmation of Charges) ICC-01/05-01/08 (15 June 2009).`

**Arbitral tribunals:**
- Reporter `ICSID Case No ARB/01/8`, Date Decided `12 May 2005`
- → `CMS Gas Transmission Company v Argentina Republic (Merits) (Award) ICSID Case No ARB/01/8 (12 May 2005).`

**Pinpoints:** set the locator type to *Paragraph* → `[19]`. Judgment paragraphs are the only pinpoints that take square brackets.

---

## 4. Academic and secondary sources

| Source | Zotero type | Notes |
|---|---|---|
| Book | Book | Publisher must be entered as OSCOLA abbreviates it (`OUP`, `CUP`, `Hart Publishing`), **not** "Oxford University Press". Delete the Place field — OSCOLA never prints it. |
| Chapter | Book Section | Editors go in the Editor field; the style writes `in … (eds), Title`. |
| Journal article | Journal Article | Put the OSCOLA abbreviation in **Journal Abbr** (`ILJ`, `EL Rev`, `CML Rev`). Volume empty → the style switches to `[2012] Crim LR 100`. |
| Book review | Journal Article | Add `Genre: book review` in **Extra** → prints `(book review)` at the end. |
| Thesis | Thesis | 5th edn italicises thesis titles. Type = `MPhil thesis`, University = `University of Oxford`. |
| Command paper | Report | Report Number `CP 815` → `(CP 815, 2023)`. Leave it empty for ordinary reports and the publisher + year print instead. |
| Newspaper | Newspaper Article | Do **not** fill Place — 5th edn dropped the city of publication. |
| Website / blog | Web Page / Blog Post | See below. |
| Lecture or speech | Presentation | Type = `Speech at the Carbon Expo Conference`, Place = `Cologne`. |
| Generative AI output | Document | Author `ChatGPT`, Title `response to 'Explain X'`, Publisher `OpenAI`, Date. |

### Websites — the one rule that changed most

OSCOLA 5 prefers a persistent link (Perma.cc) or a DOI, and **drops the access date** when you use one.

- **DOI present** → printed as `DOI: 10.17176/…`, no angle brackets, no access date. Put it in the DOI field (or `DOI: …` in Extra for types without the field).
- **Perma.cc link** → put it in URL and **clear the Accessed field**. The style only prints `accessed …` when Accessed is filled.
- **Ordinary URL** → leave Accessed filled; you get `<url> accessed 16 July 2023`.

Zotero fills Accessed automatically, so clearing it is a deliberate step each time.

---

## 5. Things the style handles automatically

- **No more `ibid`.** Later footnotes render as `Craig (n 12) 360.` using the real footnote number. Legislation and treaties use the short form alone: `Rome I Regulation.`
- Four or more authors → first author + `and others`.
- Bibliography inverts names and initialises forenames (`Zweigert K and Kötz H`), repeats the same author as `——`, and drops the closing full stop.

## 6. Things it cannot do

- **Tables of Cases and Legislation.** CSL produces one flat bibliography. Generate it, then cut the legal items into separate tables manually, or keep cases and legislation in a separate Zotero collection and export that collection on its own.
- **Short-form case names.** Fill **Short Title** with `Schempp` so later footnotes read `Schempp (n 6) [22]` rather than repeating the full name.
- **Automatic OJ / law report abbreviations.** Whatever you type is what prints, so keep abbreviations consistent from the start.
