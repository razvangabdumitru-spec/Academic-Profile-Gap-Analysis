# Academic Profile Gap Analysis

This gist compares the stored memory profile for Junteng Liu against the AcademicPages template (academicpages/academicpages.github.io). It lists which template sections are covered by the memory data, which are partially covered, which are missing, maps template fields to memory keys, and provides a completeness percentage and recommendation per section.

## Template sections examined
- About page (_pages/about.md)
- Publications (_publications and _pages/publications.html)
- Talks (_talks and _pages/talks.html)
- Teaching (_teaching and _pages/teaching.html)
- CV / Resume (_data/cv.json and _pages/cv.md)
- Navigation (_data/navigation.yml)
- Authors (_data/authors.yml)
- Portfolio (_portfolio)
- Posts/blog (_posts)
- Talks map / Talkmap (_pages/talkmap.html, talkmap folder)
- UI text and other config (_data/ui-text.yml, _config.yml)

---

## 1) Sections with complete data in memory

Note: "Complete" means all primary fields used by AcademicPages for that section are present in memory observations.

- Publications
  - Template expected fields: title, authors, venue, year, url/code, notes/abstract
  - Memory data present: multiple publications with titles, years, authors, venue (for some), and code repo mentions
  - Mapping:
    - template.title -> memory publication name
    - template.authors -> memory publication observations listing authors
    - template.year -> memory publication observations (e.g., 2024, 2025)
    - template.venue -> memory publication observations (EMNLP 2024, ICML 2024, NeurIPS 2023; some are "Arxiv")
    - template.url/code -> memory observation like "Has GitHub code repository"

Completeness estimate: 90% -> Recommendation: Ready

---

## 2) Sections with partial data in memory

- About page / Bio
  - Template fields: name, title/position, affiliation, email, bio text, photo, research interests, education list, social links
  - Memory data present: name (Junteng Liu), position (PhD candidate at HKUST), affiliations (HKUST, SJTU), email, research interests, education (PhD and B.Eng.), social links (GitHub, Google Scholar, X), awards (Zhiyuan Honor Scholarship), publications list
  - Missing: photo, detailed bio narrative (there are short observations but no long about paragraph), ORCID, location, personal website URL (unless GitHub used)
  - Mapping:
    - template.name -> Junteng Liu
    - template.title -> "First-year PhD candidate at HKUST NLP Group"
    - template.affiliation -> Hong Kong University of Science and Technology
    - template.email -> jliugi@connect.ust.hk
    - template.research_interests -> observations on LLM Reasoning, VLM hallucination, truthfulness
    - template.education -> Ph.D. in Computer Science (2024-Present), B.Eng. (2020-2024)
    - template.social.github -> GitHub: Vicent0205
  - Completeness: 70% -> Recommendation: Needs attention

- CV / Resume
  - Template fields (cv.json): name, contact, education entries, employment entries, awards, skills, links, summary, sections for publications, talks, teaching
  - Memory data present: education, internships (employment), awards, contact email, publications; missing: structured skills list, detailed dates for intern positions (some have ranges), summary/objective, teaching experience
  - Mapping: education -> B.Eng., Ph.D.; employment -> Research Intern entries; awards -> Zhiyuan Honor Scholarship
  - Completeness: 60% -> Recommendation: Needs attention

- Talks
  - Template fields: title, event, date, slides/video links, abstract, co-speakers
  - Memory data present: none specific (no talks listed)
  - Completeness: 0% -> Recommendation: Skip (or Needs attention if you have talks to add)

- Teaching
  - Template fields: course title, institution, term, description, materials
  - Memory data present: none
  - Completeness: 0% -> Recommendation: Skip

- Portfolio / Projects
  - Template fields: project title, description, link, images, tags
  - Memory data present: some GitHub repos for publications and code (Vision4Chart, Universal_Truthfulness_Hyperplane)
  - Missing: project descriptions, images, stand-alone project pages
  - Mapping: project.title -> repo names; project.link -> GitHub URLs
  - Completeness: 40% -> Recommendation: Needs attention

- Navigation & Authors
  - Template fields: navigation entries, author metadata (name, bio, email, photo, links)
  - Memory data: name, email, short bio observations, GitHub link
  - Missing: author photo, full author YAML fields
  - Completeness: 50% -> Recommendation: Needs attention

- Talks map
  - Template fields: talk mapping data
  - Memory data: none
  - Completeness: 0% -> Recommendation: Skip

---

## 3) Sections with no corresponding data in memory

- Teaching (_teaching)
- Talks details (_talks)
- Portfolio details (_portfolio) beyond publication code repos
- Blog posts (_posts)
- UI text overrides (_data/ui-text.yml) — not needed
- Comments config (_data/comments/*)

---

## Field-level mapping (selected important template fields)

- authors.yml (template): expects author id with fields like name, email, affiliation, bio, avatar, links
  - memory keys: "Junteng Liu" entity; observations containing email, affiliations, research interests, GitHub, Google Scholar
  - Missing: avatar/photo, full bio text, ORCID, location

- cv.json: fields like "education" (institution, degree, start/end dates), "employment" (title, institution, start/end, description), "awards" (title, year), "publications" (ids)
  - memory mapping: education and employment entries exist but are not structured; awards exist; publications exist
  - Missing: structured dates for internships (some present), skills, summary, links to slides

- publications (folder): expects individual publication markdown files or metadata
  - memory mapping: publication titles, coauthors, venues, years, code repo existence — these can be converted

---

## Orphan data items (memory data not fitting template sections)
- Professor Junxian He (as separate Person entity) — fits as an advisor; can be mentioned in About/advisor section
- Zifei Shan, Prof. Yu Cheng — advisors/mentors/co-authors; could appear in collaborators section
- Google Scholar URL and X handle — map to social links

---

## Summary table

| Section | Completeness | Recommendation |
|---|---:|---|
| Publications | 90% | Ready |
| About / Bio | 70% | Needs attention |
| CV / Resume | 60% | Needs attention |
| Portfolio / Projects | 40% | Needs attention |
| Authors / Navigation | 50% | Needs attention |
| Talks | 0% | Skip |
| Teaching | 0% | Skip |
| Talks map | 0% | Skip |
| Blog posts | 0% | Skip |

---

If you'd like, I can now:
- Create the actual YAML/JSON files for this template filled with your memory data (authors.yml, _data/cv.json, publications entries), or
- Open a PR on a repo to add these files, or
- Export the mapping to a CSV for manual editing.
