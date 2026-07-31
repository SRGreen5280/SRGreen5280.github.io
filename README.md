# ATS Parse Inspector

**See your resume the way ten applicant tracking systems actually read it.**

🔗 **Live tool:** https://SRGreen5280.github.io

Applicant tracking systems (ATS) don't look at a resume's layout — they strip it to a plain text stream and map that text into database fields: name, contact, employers, titles, dates, skills. When the formatting fights that process, fields get dropped, merged, or misassigned, and a qualified candidate silently drops out of the ranking before a human ever sees the resume.

This tool shows exactly where that mapping breaks — per platform — and rebuilds a clean, parseable version.

## What it does

- **Parser's-eye view.** Reconstructs the field map a parser would build from your resume (name, contact, section order) so you can see what the recruiter's system actually captures.
- **Per-platform read.** Grades your resume against ten current systems — Workday, Taleo, iCIMS, SuccessFactors, Greenhouse, Lever, SmartRecruiters, Ashby, Jobvite, and Bullhorn — weighted by each one's documented strictness. Taleo and Workday are the unforgiving extremes; Greenhouse, Lever, and Ashby are the lenient ones.
- **Specific, fixable issues.** Flags non-standard section headers, multi-column layouts, icon and skill-bar glyphs, seasonal or non-US date formats, contact info likely trapped in a header/footer, and more — each with the reason it breaks and the exact fix.
- **Keyword coverage.** Compares your resume against a specific job posting and surfaces the terms you're missing. Targets are drawn from the posting you paste — never a generic word list.
- **Clean rebuild.** Generates a ready-made prompt that reformats your resume into single-column plain text with standard headers and MM/YYYY dates.

## How it works

A single self-contained HTML file — no build step, no framework, no backend. All analysis runs client-side in the browser, so nothing you paste ever leaves your machine. Reading uploaded `.docx` files is the only network call ([mammoth.js](https://github.com/mwilliamson/mammoth.js) from a CDN); everything else works offline.

## A deliberate limit

The tool fixes how a *machine* reads a resume — layout, headers, dates, character encoding. It never recommends removing or anglicizing a name, or dropping affiliations, languages, or credentials that signal a candidate's background. None of that improves parsing, and "whitening" a resume is not what these systems require. Where a legacy parser mishandles non-Latin characters, the guidance is to *add* a romanized form alongside the original, never to replace it.

## Run it locally

No install needed. Clone or download the repo and open `index.html` in any browser.

```
git clone https://github.com/SRGreen5280/SRGreen5280.github.io.git
cd SRGreen5280.github.io
open index.html
```

## Notes

A personal project. Parser behavior is modeled from publicly documented 2026 ATS quirks and is meant as guidance, not a guarantee — the safe strategy is to optimize for the strictest parser, which is what the scoring does.
