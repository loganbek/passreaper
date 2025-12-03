# PassReaper — Targeted Password Profiling & OSINT‑Driven Wordlist Generator

_All references to the project now use the name **PassReaper**._

# ROADMAP.md

## Vision
Build an automated, OSINT-driven, hyper-targeted password list generator that pulls from CUPPS-like profiling, CeWL-style crawling, public-data harvesting, breach data parsing, and human-behavior templates. Output should be highly customizable, reproducible, and usable by red-team operators ethically.

## Milestones

### **1. Foundational Architecture**
- Define core modules:  
  - **Profile Engine** (names, birthdays, relationships, hobbies)  
  - **OSINT Engine** (social media, public records, company info)  
  - **Scraper Engine** (CeWL-style site crawler)  
  - **Harvester Engine** (emails, domains, usernames)  
  - **Mutator Engine** (l33t, symbols, date combinations)  
  - **Bias Engine** (predict likely human choices)
- Decide on programming language (Python recommended).
- Choose folder structure & CI/CD framework.

### **2. CUPPS-Style Profile Builder**
- Prompt user or import JSON with target details.
- Auto-fill based on OSINT queries.
- Handle multiple targets.

### **3. OSINT Integration**
- Integrate APIs or scraping modules for:  
  - Social networks (public)  
  - LinkedIn-style roles/companies  
  - Public breach data (local offline DB only—avoid illegal live scraping)
- Pull hobby keywords, pets, events, locations.

### **4. Web Crawler (CeWL-like)**
- Input: URL or list of URLs.
- Output: keyword dump with optional weighting.
- Add filters for: nouns, verbs, emails, numbers.

### **5. Wordlist Generator Core**
- Combine: profile data + OSINT + crawled words + templates.
- Add ranking for likelihood.
- Include rule-based and pattern-based expansions.
- Export: txt, gz, json metadata.

### **6. Mutator Engine**
- Add permutations:  
  - Common symbol swaps  
  - Date combinations  
  - Prefix/suffix patterns  
  - “Password psychology” variants
- Add scoring to reduce bloat.

### **7. CLI + GUI**
- Simple CLI: `targetgen --profile user.json --osint --crawl https://site.com --out wordlist.txt`
- Optional lightweight GUI.

### **8. Agent Integration**
- Provide AGENT_CONTEXT.md for AI assistants.
- Set up a dev-agent and OSINT-agent workflow.

### **9. Testing & Benchmarks**
- Test against known wordlist sizes.
- Compare to CUPP, CeWL, Mentalist, Crunch.

### **10. Packaging & Release**
- Dockerfile
- PyPI packaging
- Signed releases

---

# README.md

## Ultimate Targeted Password List Generator (UTPLG)
A next-generation, OSINT-enhanced password wordlist generator that fuses:
- CUPPS-style profiling  
- CeWL-like scraping  
- OSINT gathering  
- Human-behavior password modeling  
- Smart mutation & ranking

### **Why this tool?**
Most wordlist tools are good at one thing. This one combines *all of them* so you produce extremely targeted lists with minimal effort.

### **Features**
- Auto-collects personal, social, and contextual target info
- Crawls websites to extract weighted keywords
- Gathers relevant emails, handles, domains
- Builds persona-based password templates
- Produces high-quality, small-but-effective wordlists
- Fully scriptable
- Agent-friendly design for extension

### **Quick Start**
```bash
targetgen --profile victim.json --osint --crawl https://targetsite.com --out wordlist.txt
```

### **Installation**
```bash
git clone https://github.com/yourrepo/utplg
cd utplg
pip install -r requirements.txt
```

### **Modules Overview**
- `/core` – generation & mutation logic
- `/osint` – harvesting modules
- `/crawler` – CeWL-like page miner
- `/profiles` – target schema & builder
- `/agents` – AI agent orchestration files

### **Ethical Use Disclaimer**
This tool is for **authorized security testing only**.
Never use it against systems you do not own or have written permission to assess.

---

# AGENT_CONTEXT.md

## Purpose
This file tells AI agents how to assist in building, improving, and extending the project.

## Agent Roles

### **1. Dev Agent**
Responsibilities:
- Generate code for modules, classes, and functions.
- Improve architecture & reduce complexity.
- Build CLI and GUI logic.
- Write documentation.

### **2. OSINT Agent**
Responsibilities:
- Suggest new OSINT data sources.
- Improve scraping logic.
- Generate templates for keyword extraction.
- Map personas to behavioral password patterns.

### **3. Security Agent**
Responsibilities:
- Ensure ethical boundaries.
- Verify no disallowed OSINT sources are used.
- Check for abuse vectors.
- Recommend safe configurations.

### **4. Testing Agent**
Responsibilities:
- Suggest unit, integration, and benchmark tests.
- Validate correctness of wordlist generation.
- Analyze wordlist size vs. effectiveness.

## Agent Guidelines
- Keep all outputs modular.
- Prefer simple, auditable logic.
- Document reasoning in comments, not commit messages.
- When expanding a module, reference the ROADMAP.md.

## Development Principles
- Simplicity > complexity.
- Transparency > magic.
- Ethical use only.
- Speed + relevance over massive lists.

---

End of document.


## CLI Examples
Here are some example commands for **PassReaper**:

```bash
# Run a full OSINT + profiling + mutation pipeline
passreaper --target "John Doe" --output wordlist.txt

# Run only CUPP-style persona profiling
passreaper profile --name "John Doe" --birthyear 1994 --pets "Rex"

# Run OSINT collection only
passreaper osint --email johndoe@example.com --domains example.com

# Scrape a target website like CeWL
passreaper crawl --url https://targetsite.com --depth 3 --output site_words.txt

# Combine OSINT + crawl + custom mutations
passreaper hybrid --handle johndoe --url https://targetblog.com --mutators elite,dates

# Generate 10k most-likely passwords from a target profile
passreaper shortlist --target "John Doe" --max 10000 --output shortlist.txt
```

