---
theme: seriph
background:
title: Métadonnées et FAIRness
titleTemplate: '%s - Métadonnées et FAIRness'
author: Tom François
info: |
  ## Comment ajouter des métadonnées pour vos logiciels de recherche
  Un atelier pour mettre en place, maintenir et publier vos métadonnées

  Plus d'infos sur [Codemetasoft](https://w3id.org/codemetasoft)
  Basé sur les ressources EVERSE RSQKit et le project Codemetasoft.
class: text-center
base: /presentations/jdev26/
layout: image
image: ./binaries/landingpage.png
drawings:
  persist: false
transition: slide-left
mdc: true
duration: 60min
aspectRatio: 16/9
download: true
---

---

## Plan

<div class="space-y-2 text-left max-w-2xl mx-auto">

<div class="rounded-2xl border border-slate-300 bg-slate-100/80 p-4 shadow-sm dark:border-slate-700 dark:bg-slate-900/70">
  <div class="flex items-start gap-3">
    <span class="text-2xl mt-1">📌</span>
    <div>
      <div class="font-semibold text-base">1. FAIRness and Metadata</div>
      <div class="text-sm opacity-75">Concepts and why metadata matters</div>
    </div>
  </div>
</div>

<div class="rounded-2xl border border-emerald-300 bg-emerald-50/90 p-4 shadow-sm dark:border-emerald-500 dark:bg-emerald-950/30">
  <div class="flex items-start gap-3">
    <span class="text-2xl mt-1">💻</span>
    <div>
      <div class="font-semibold text-base">2. Tutorial: generate a codemeta.json</div>
      <div class="text-sm opacity-75">Hands-on step for your laptop</div>
    </div>
  </div>
</div>

<div class="rounded-2xl border border-slate-300 bg-slate-100/80 p-4 shadow-sm dark:border-slate-700 dark:bg-slate-900/70">
  <div class="flex items-start gap-3">
    <span class="text-2xl mt-1">📌</span>
    <div>
      <div class="font-semibold text-base">3. Maintaining metadata up to date</div>
      <div class="text-sm opacity-75">Best practices for keeping metadata current</div>
    </div>
  </div>
</div>

<div class="rounded-2xl border border-emerald-300 bg-emerald-50/90 p-4 shadow-sm dark:border-emerald-500 dark:bg-emerald-950/30">
  <div class="flex items-start gap-3">
    <span class="text-2xl mt-1">💻</span>
    <div>
      <div class="font-semibold text-base">4. Tutorial: install a CI to check metadata</div>
      <div class="text-sm opacity-75">Set up automated metadata validation</div>
    </div>
  </div>
</div>

<div class="rounded-2xl border border-slate-300 bg-slate-100/80 p-4 shadow-sm dark:border-slate-700 dark:bg-slate-900/70">
  <div class="flex items-start gap-3">
    <span class="text-2xl mt-1">📌</span>
    <div>
      <div class="font-semibold text-base">5. Publication</div>
      <div class="text-sm opacity-75">How to publish and archive your software</div>
    </div>
  </div>
</div>

</div>

---
layout: center
class: text-center
---

# FAIRness and Metadata for Research Software

---

## What is FAIR?

<div class="grid grid-cols-2 gap-8">
<div>

<v-click>

4 principles for data objects:

- **F**indable - Easy to discover by humans & machines
- **A**ccessible - Retrievable via standard protocols
- **I**nteroperable - Exchange data through standards
- **R**eusable - Usable and modifiable by others

</v-click>

<div v-click class="mt-4 p-4 bg-yellow-50 dark:bg-yellow-900 rounded">
FAIRness is about discoverability and reusability
</div>

</div>
<div>

<v-click>

## FAIR vs Quality

- FAIR ⊂ Software Quality
- FAIR ensures **discoverabilty** & **reusability**
- Quality includes **correctness**, **performances**, **testing**

</v-click>

</div>
</div>

<!-- ---

## FAIR in Practice

<v-clicks>

- 📄 **Proper documentation** (README, docs)
- ⚖️ **Clear licensing** (MIT, Apache, GPL)
- 📋 **Metadata files** (codemeta.json, CITATION.cff)
- 📦 **Package repositories** (PyPI, Conda)
- 🏛️ **Archiving** (Zenodo, Software Heritage)
- 🔗 **Persistent identifiers** (DOIs)

</v-clicks> -->

---
zoom: 0.85
---

# FAIR Principles for Research Software (FAIR4RS)

<div class="grid grid-cols-2 gap-4 text-[11px] mt-4">

<div class="p-3 border border-blue-200 rounded-lg bg-blue-50/30 dark:bg-blue-900/10">
<h3 class="text-blue-600 font-bold mb-1 flex items-center gap-2"><carbon:search /> F.indable</h3>
<p class="mb-2 italic opacity-70">Easy for humans and machines to find.</p>
<ul v-click class="list-none p-0 space-y-1">
  <li><b>F1.</b> Assigned unique & persistent ID (DOI)</li>
  <li class="ml-3 opacity-80 border-l-2 pl-2"><b>F1.1.</b> IDs for different components</li>
  <li class="ml-3 opacity-80 border-l-2 pl-2"><b>F1.2.</b> IDs for different versions</li>
  <li><b>F2.</b> Described with rich metadata</li>
  <li><b>F3.</b> Metadata explicitly points to ID</li>
  <li><b>F4.</b> Metadata are searchable & indexable</li>
</ul>
</div>

<div class="p-3 border border-green-200 rounded-lg bg-green-50/30 dark:bg-green-900/10">
<h3 class="text-green-600 font-bold mb-1 flex items-center gap-2"><carbon:cloud-download /> A.ccessible</h3>
<p class="mb-2 italic opacity-70">Retrievable via standard protocols.</p>
<ul v-click class="list-none p-0 space-y-1">
  <li><b>A1.</b> Retrievable by ID using standard protocols</li>
  <li class="ml-3 opacity-80 border-l-2 pl-2"><b>A1.1.</b> Open, free & universal protocol</li>
  <li class="ml-3 opacity-80 border-l-2 pl-2"><b>A1.2.</b> Auth/Auth procedure where needed</li>
  <li><b>A2.</b> Metadata persists even if software is gone</li>
</ul>
</div>

<div class="p-3 border border-purple-200 rounded-lg bg-purple-50/30 dark:bg-purple-900/10">
<h3 class="text-purple-600 font-bold mb-1 flex items-center gap-2"><carbon:connect /> I.nteroperable</h3>
<p class="mb-2 italic opacity-70">Exchange data and interact via APIs.</p>
<ul v-click class="list-none p-0 space-y-1">
  <li><b>I1.</b> Meets community standards for exchange</li>
  <li><b>I2.</b> Includes qualified references to other objects</li>
</ul>
</div>

<div class="p-3 border border-orange-200 rounded-lg bg-orange-50/30 dark:bg-orange-900/10">
<h3 class="text-orange-600 font-bold mb-1 flex items-center gap-2"><carbon:recycle /> R.eusable</h3>
<p class="mb-2 italic opacity-70">Understandable, modifiable, and buildable.</p>
<ul v-click class="list-none p-0 space-y-1">
  <li><b>R1.</b> Rich and accurate attributes</li>
  <li class="ml-3 opacity-80 border-l-2 pl-2"><b>R1.1.</b> Clear and accessible License</li>
  <li class="ml-3 opacity-80 border-l-2 pl-2"><b>R1.2.</b> Detailed provenance & history</li>
  <li><b>R2.</b> References to other software</li>
  <li><b>R3.</b> Meets domain-relevant community standards</li>
</ul>
</div>

</div>

<div class="mt-4 text-[13px] opacity-50 italic">
Chue Hong, N. P. et al. (2022). FAIR Principles for Research Software (FAIR4RS Principles). <a href="https://doi.org/10.1038/s41597-022-01710-x
">DOI: 10.15497/RDA/00068</a>
</div>

---
zoom: 1.
---

# FAIR4RS in Practice

Translating abstract principles into concrete tools and files in your repository.

<div class="grid grid-cols-2 gap-4 text-[11px] mt-4">

<!-- F.INDABLE -->
<div class="p-3 border border-blue-200 rounded-lg bg-blue-50/30 dark:bg-blue-900/10">
<h3 class="text-blue-600 font-bold mb-1 flex items-center gap-2"><carbon:search /> F.indable</h3>
<ul class="list-none p-0 space-y-2">
  <li v-click>
    <b class="text-blue-700 dark:text-blue-300">Repository & Identifiers</b>
    <div class="opacity-80">Public Git repo + DOI (Zenodo/Figshare) or SWHID</div>
  </li>
  <li v-click>
    <b class="text-blue-700 dark:text-blue-300">Standard Metadata</b>
    <div class="opacity-80"><code>codemeta.json</code> and <code>CITATION.cff</code> files</div>
  </li>
  <li v-click>
    <b class="text-blue-700 dark:text-blue-300">Indexing</b>
    <div class="opacity-80">Register in PyPI, Conda-forge, or domain registries</div>
  </li>
</ul>
</div>

<!-- A.CCESSIBLE -->
<div class="p-3 border border-green-200 rounded-lg bg-green-50/30 dark:bg-green-900/10">
<h3 class="text-green-600 font-bold mb-1 flex items-center gap-2"><carbon:cloud-download /> A.ccessible</h3>
<ul class="list-none p-0 space-y-2">
  <li v-click>
    <b class="text-green-700 dark:text-green-300">Software Access</b>
    <div class="opacity-80">HTTPS/SSH for clones, <code>pip install</code> for users</div>
  </li>
  <li v-click>
    <b class="text-green-700 dark:text-green-300">Metadata Longevity</b>
    <div class="opacity-80">Archiving in Zenodo ensures metadata stays even if repo disappears</div>
  </li>
</ul>
</div>

<!-- I.NTEROPERABLE -->
<div class="p-3 border border-purple-200 rounded-lg bg-purple-50/30 dark:bg-purple-900/10">
<h3 class="text-purple-600 font-bold mb-1 flex items-center gap-2"><carbon:connect /> I.nteroperable</h3>
<ul class="list-none p-0 space-y-2">
  <li v-click>
    <b class="text-purple-700 dark:text-purple-300">Standard Formats</b>
    <div class="opacity-80">Use CSV, JSON, HDF5, or community-specific standards</div>
  </li>
  <li v-click>
    <b class="text-purple-700 dark:text-purple-300">Qualified References</b>
    <div class="opacity-80">Reference other tools/data using their DOIs</div>
  </li>
  <li v-click>
    <b class="text-purple-700 dark:text-purple-300">Controlled vocabularies</b>
    <div class="opacity-80">Standard terminology/Domain ontologies</div>
  </li>
</ul>
</div>

<!-- R.EUSABLE -->
<div class="p-3 border border-orange-200 rounded-lg bg-orange-50/30 dark:bg-orange-900/10">
<h3 class="text-orange-600 font-bold mb-1 flex items-center gap-2"><carbon:recycle /> R.eusable</h3>
<ul class="list-none p-0 space-y-2">
  <li v-click>
    <b class="text-orange-700 dark:text-orange-300">Documentation</b>
    <div class="opacity-80">Rich <code>README.md</code>, usage examples, and API docs</div>
  </li>
  <li v-click>
    <b class="text-orange-700 dark:text-orange-300">Legal Terms</b>
    <div class="opacity-80">Include a <code>LICENSE</code> file (MIT, Apache, GPL)</div>
  </li>
  <li v-click>
    <b class="text-orange-700 dark:text-orange-300">Community & Provenance</b>
    <div class="opacity-80"><code>CONTRIBUTING.md</code> and <code>CHANGELOG.md</code></div>
  </li>
</ul>
</div>

</div>

---
level: 2
---

# Software Metadata

<div class="grid grid-cols-2 gap-6">

<div>

## What is Metadata?

<v-click>

Structured data describing your software:

</v-click>

<v-click>

- 📝 Name, version, description
- 👥 Authors, contributors
- ⚖️ License
- 🔗 Repository URL
- 🐍 Programming language
- 📦 Dependencies
- 📄 Documentation links

</v-click>

<div v-click class="mt-4 p-3 bg-blue-50 dark:bg-blue-900 rounded text-sm">
💡 Machine-readable metadata enables discoverability & automation
</div>

</div>

<div>

<v-click>

## Why It Matters

</v-click>

<v-click>

- 🔍 **Findability** - Search engines can discover it
- 🤖 **Automation** - Tools can process it
- 🔄 **Interoperability** - Different platforms understand it
- 📚 **Archives** - Zenodo, Software Heritage can ingest it
- 📖 **Citation** - Automatic citation generation

</v-click>

<div v-click class="mt-4 p-3 bg-purple-50 dark:bg-purple-900 rounded text-sm">
Different use cases need different metadata:<br>
<ul>
<li>Citation: Authors, DOI</li>
<li>Replication: Dependencies, versions</li>
<li>Discovery: Keywords, description</li>
</ul> 
</div>

</div>
</div>

<div class="abs-br m-6 text-sm opacity-50">
Source: RSQKit - Software Metadata
</div>

<!--
Metadata is the key to making software FAIR. It bridges human and machine understanding.
-->

---
zoom: 0.85
---

# Metadata Standards

<div class="grid grid-cols-2 gap-6 text-sm">

<div>

## Common Standards

<v-clicks>

<div>

### CodeMeta
- JSON-LD format
- Based on Schema.org
- `codemeta.json`
- Widely supported (Zenodo, Software Heritage)

</div>
<div>

### Citation File Format (CFF)
- YAML format
- Academic citation
- `CITATION.cff`
- GitHub native support (Shows a button "Cite this repository" automatically)
- Zenodo support
- Specifies preferred citation

</div>
</v-clicks>

</div>

<div v-after>

## Comparison

| Feature | CodeMeta | CFF |
|---------|----------|-----|
| Format | JSON-LD | YAML |
| Purpose | General | Citation |
| GitHub Support | Via API | Native |
| Human Readable | Medium | High |
| Machine Readable | ✔︎ | ✔︎ |

<v-click>

## Best Practice

**Use both!**
- `codemeta.json` for comprehensive metadata
- `CITATION.cff` for citation
- Plus language-specific files

</v-click>

</div>

</div>

<div class="abs-br m-6 text-sm opacity-50">
Source: RSQKit - Software Metadata
</div>

<!--
Different standards serve different purposes. Using multiple standards increases discoverability.
-->

---
zoom: 1
---

# CodeMeta example

<div class="grid grid-cols-12 gap-6">

<div class="col-span-8">

`codemeta.json`

```json
{
  "@context": "https://doi.org/10.5063/schema/codemeta-2.0",
  "@type": "SoftwareSourceCode",
  "name": "My Research Software",
  "description": "A tool for scientific data analysis",
  "version": "1.0.0",
  "author": [{
    "@type": "Person",
    "givenName": "Jane",
    "familyName": "Doe",
    "email": "jane@example.org",
    "affiliation": {
      "@type": "Organization",
      "name": "University of Example"
    }
  }],
  "license": "https://spdx.org/licenses/MIT",
  "programmingLanguage": "Python",
  "codeRepository": "https://github.com/user/repo"
}
```

</div>


</div>


<div class="abs-br m-6 text-sm opacity-50">
Source: https://codemeta.github.io/
</div>

<!--
CodeMeta is machine-readable and widely supported. Create it once, reuse everywhere.
-->
---

# Codemetasoft project
<div class="grid grid-cols-2 gap-6 text-sm">

  <div style="text-align: left;">

  

  **funded by**: [OSCARS](https://oscars-project.eu/)

  #### partners 
  - Universidad Politécnica de Madrid
  - Laboratoire d'Annecy de Physique des Particules (LAPP, CNRS)  
  </div>

  <img src="./binaries/logos/codemetasoft_logo.png" />

</div>



<div class="grid grid-cols-2 gap-6 text-sm">

<div v-click style="text-align: left;">

### Goals of the project

- Ease the adoption of Research Software metadata & good practices
- Automate metadata propagation and interoperability
- Propose suggestions for researchers

</div>


<div v-click style="text-align: left;">

### Tools

- [Autocodemeta](https://autocodemeta.linkeddata.es/) => Create codemeta.json from scratch
- [RSMetacheck](https://github.com/SoftwareUnderstanding/RsMetaCheck) => analyze your metadata
- [sw-metadata-bot](https://github.com/SoftwareUnderstanding/sw-metadata-bot) => publish RSMetacheck analysis

</div>

</div>

<div class="abs-br m-6 text-sm opacity-50">
https://w3id.org/codemetasoft/
</div>

---
layout: center
class: text-center
---

# Tutorial

---

## Tutorial 1 : Generate a codemeta.json


<div class="grid grid-cols-12 gap-6">

<div class="col-span-8">

### Instructions

- Go on https://autocodemeta.linkeddata.es/
- Provide your **public** url repository (Github or Gitlab)

<div v-click class="mt-1 p-5 bg-blue-50 dark:bg-blue-900 rounded text-sm">

💡 **Sample repository**:
- https://github.com/SoftwareUnderstanding/sw-metadata-bot

</div>

<v-click>

- check suggested `codemeta.json`
- add manual inputs
  - publication if any
  - funding
  - contributors list

</v-click>

</div>



<div v-click class="col-span-4">

### Conclusion


- commit your `codemeta.json`

</div>
</div>

---
layout: center
class: text-center
---

# Metadata Maintenance


---

# Metadata maintenance

<div class="grid grid-cols-1 md:grid-cols-2 gap-6">

<div class="space-y-4">

## Situation

During development: ⏳

<div v-click>

- new contributor fixed a bug
- dependencies updated
- ...
</div>

<div v-click>

Metadata need to be updated:
  - modificationDate
  - contributors list
  - version number
  - dependencies requirements
  - changelog
  ...

</div>
</div>

<div class="space-y-4">
<div v-click>

## Problem

- ⏳ Manual updates cost time and prone to error
- 🧨 Risk of stale or inconsistent metadata
</div>

<div v-click>

## Solution ?
  Create automatic process ?
</div>
</div>

</div>
---

# RSMetacheck

`https://github.com/SoftwareUnderstanding/RsMetaCheck`

<div v-click>

## Features

- 🧩 Repository metadata analysis (based on [`SoMeF`](https://github.com/KnowledgeCaptureAndDiscovery/somef))
- ❗ Detects pitfalls or warnings in metatadata files.
- ⚙️ Configurable via `.rsmetacheck.yml`

</div>

<div v-click>

## How to use it

### locally:
  - 🛠️ `pip install rsmetacheck`
  - ▶️ `rsmetacheck --input $CI_PROJECT_URL`
### in Continuous Integration pipeline
- 🔁 Use dedicated Github Action / GitLab CI

</div>

<div v-click>

💡 Good for maintainers

</div>

---

## sw-metadata-bot

`https://github.com/SoftwareUnderstanding/sw-metadata-bot`

<div v-click>

- 📰 Publish RSMetacheck results as issues
- 👀 Eventually, *dependabot* for metadata : create automatic PR

</div>

<div class="grid grid-cols-1 md:grid-cols-2 gap-4">

<div v-click style="text-align: left;">

### Issue creation

- 📝 Issue from RSMetacheck analysis

[issue example](https://github.com/SoftwareUnderstanding/RsMetaCheck/issues/76)

<img src="./binaries/swmetadatabot_report_issue.png" />
</div>

<div v-click style="text-align: left;">

### Dashboard

- 📊 Web report for metadata status
- 👀 Monitor progress over time

[web report](https://softwareunderstanding.github.io/sw-metadata-bot-monitor-web/)

<img src="./binaries/swmetadatabot_web_report.png" />

</div>

</div>

---

# Current Stage

`RSMetacheck` and  `sw-metadata-bot`

<div v-click class="mt-1 p-4 bg-yellow-50 dark:bg-yellow-900 rounded">

⚠️ still in beta stage: 
- some false positive
- some suggestions not accurate
</div>

<div v-click class="mt-1 p-4 bg-orange-50 dark:bg-yellow-900 rounded">

feedback are welcome as [sw-metadata-bot issues](https://github.com/SoftwareUnderstanding/sw-metadata-bot/issues/new?template=feedback.yml)

</div>

<div v-click class="mt-4 p-1 bg-green-50 dark:bg-yellow-900 rounded">

future : create a GitHub action to generate PR with automatic fixes.
</div>


---
layout: center
class: text-center
---

# Tutorial


---
zoom:0.5
---

## Tutorial 2 
- add RSMetaCheck to your repo
  - add github action -> [rs-metacheck-action](https://github.com/SoftwareUnderstanding/rs-metacheck-action)
  - **or** add a step in your gitlab-ci pipeline -> [gitlab-ci snippet](https://rsmetacheck.readthedocs.io/en/latest/usage/#gitlab-cicd)  
- (or) subscribe to the bot

---

### Add RSMetacheck in your CI


```yaml
name: RsMetaCheck Validation

on:
  push:
    branches: ["main"]
  pull_request:
    branches: ["main"]

jobs:
  analyze-metadata:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v6

      - name: Run RsMetaCheck
        uses: SoftwareUnderstanding/rs-metacheck-action@0.3.1
        # optional arguments
        with:
          pitfalls_output: "./pitfalls_outputs" 
          verbose: "false"
```

https://github.com/marketplace/actions/rsmetacheck

---

### Add RSMetacheck in your CI
for gitlab:

in `.gitlab_ci.yml`

```yaml
rsmetacheck:
  image: python:3.11
  stage: test
  script:
    - pip install rsmetacheck
    - somef configure -a
    - rsmetacheck --input $CI_PROJECT_URL
  artifacts:
    paths:
      - pitfalls_outputs/
      - somef_outputs/
      - analysis_results.json
    when: always
    expire_in: 1 week
```

---

### Subscribe to the bot

https://github.com/SoftwareUnderstanding/sw-metadata-bot/issues/new?template=subscribe.yml


---
layout: center
class: text-center
---

# Publication

---
level: 2
---

# Software Publication ≠ Code Hosting

<div class="grid grid-cols-2 gap-8">

<div>

## Code Hosting (GitHub/GitLab)

<v-click>

- ✅ Version control
- ✅ Collaboration
- ✅ Issue tracking
- ✅ Code review

</v-click>

<div v-click class="mt-4 p-3 bg-yellow-50 dark:bg-yellow-900 rounded text-sm">
⚠️ This is a great start, but not enough!
</div>

</div>
<div>
<v-click>

## Full Publication Includes

- 📄 **Documentation** - README, guides
- ⚖️ **License** - Legal reuse terms
- 📋 **Metadata** - Findability
- 🏷️ **Citation** - Academic credit
- <v-mark color="yellow">📦 Packaging - Easy installation</v-mark>
- <v-mark color="yellow">🔖 Releases - Version management</v-mark>
- <v-mark color="yellow">🏛️ Archiving - Long-term preservation</v-mark>

</v-click>

</div>

</div>

<div v-click class="mt-6 p-4 bg-blue-50 dark:bg-blue-900 rounded">
💡 Publishing is the finale touch to make your software FAIR
</div>

<div class="abs-br m-6 text-sm opacity-50">
Source: RSQKit - Publishing Software
</div>

<!--
Putting code on GitHub is step one. Full publication requires several additional components.
-->

---
level: 2
---

# Why Archive Software?

<div class="grid grid-cols-2 gap-6">

<div>

## The Problem

<v-clicks>

**GitHub/GitLab are NOT archives:**
- Commercial platforms
- Can change policies
- Repositories can be deleted
- URLs can break
- No guarantee of permanence

</v-clicks>

<div v-click class="mt-4 p-4 bg-red-50 dark:bg-red-900 rounded text-sm">
⚠️ What happens to your research software in 10 years?
</div>

</div>

<div>
<v-click>

## A Solution: Archiving
</v-click>
<v-clicks>

**True archives provide:**
- 🏛️ **Long-term preservation** (decades)
- 🔒 **Persistent identifiers** (DOIs)
- 📋 **Metadata preservation**
- 🔍 **Discoverability** in academic systems
- ✅ **Trustworthy** repositories
- 🌐 **Integration** with citation systems

</v-clicks>

</div>

</div>

<div class="abs-br m-6 text-sm opacity-50">
Source: RSQKit - Archiving Software
</div>

<!--
Archiving ensures your software remains accessible for the long term, essential for reproducibility.
-->


---
level: 2
---

# Software Archives

<div class="grid grid-cols-2 gap-6 text-sm">

<div>

## Zenodo

<v-clicks>

- **General-purpose** archive
- CERN-hosted (Europe)
- **Free** and open
- **DOI** for each version
- **GitHub integration**
- Supports all file types
- Part of OpenAIRE

### Good For:
- Software
- Datasets
- Supplementary materials

</v-clicks>

</div>

<div>

## Software Heritage

<v-clicks>

- **Universal** software archive
- UNESCO-supported
- Preserves all public source code
- **Software Heritage identifier** (SWHID)
- Automatic archiving
- link from HAL
- Complete Git history preserved -> better granularity of identifiers

### Good For:
- Software
- Being able to cite a specific part or commit of a software

</v-clicks>

</div>

</div>

<div v-click class="mt-6 p-4 bg-blue-50 dark:bg-blue-900 rounded">
💡 Recommendation: Use at least one 
</div>

<!--
Zenodo and Software Heritage serve complementary purposes. Both are free and trustworthy.
-->

---

# Demo Software Heritage

- [SH sw-metadata-bot](https://archive.softwareheritage.org/browse/origin/directory/?origin_url=https://github.com/SoftwareUnderstanding/sw-metadata-bot&visit_type=git)


---

## Conclusion



---
zoom: 0.8
layout: end
---

# Resources and Further Learning

<div class="grid grid-cols-2 gap-6 text-sm">

<div>

## EVERSE RSQKit

<div style="text-align: left;">

- [RSQKit Home](https://everse.software/RSQKit/)
- [FAIR Research Software](https://everse.software/RSQKit/pages/research_software/fair_research_software.html)
- [Publishing Software](https://everse.software/RSQKit/pages/tasks/publishing_software.html)
- [Software Metadata](https://everse.software/RSQKit/pages/tasks/software_metadata.html)
- [Licensing](https://everse.software/RSQKit/pages/tasks/licensing_software.html)
- [Archiving](https://everse.software/RSQKit/pages/tasks/archiving_software.html)

</div>

## Codemetasoft Tools

<div style="text-align: left;">

- [Codemetasoft project page](https://w3id.org/codemetasoft)
- [Autocodemeta](https://autocodemeta.linkeddata.es/)
- [RSMetacheck](https://github.com/SoftwareUnderstanding/RsMetaCheck)
- [sw-metadata-bot](https://github.com/SoftwareUnderstanding/sw-metadata-bot)

</div>

</div>

<div>

## Guides & Documentation

<div style="text-align: left;">

- [FAIR4RS Principles](https://doi.org/10.15497/RDA00068)
- [Software Citation Principles](https://www.force11.org/software-citation-principles)
- [Zenodo Help](https://help.zenodo.org/)
- [Software Heritage](https://www.softwareheritage.org/)
- [Semantic Versioning](https://semver.org/)

</div>

## Other Tools

<div style="text-align: left;">

- [Choose a License](https://choosealicense.com/)
- [CodeMeta Generator](https://codemeta.github.io/codemeta-generator/)
- [CFF Initializer](https://citation-file-format.github.io/cff-initializer-javascript/)
- [howfairis](https://github.com/fair-software/howfairis)
- [Zenodo](https://zenodo.org/)

</div>

</div>

</div>

<div class="mt-8 text-center">

### Questions?

tom.francois@lapp.in2p3.fr

</div>

<div class="abs-br m-5 text-sm opacity-50">
presentation inspired from <a href="https://vuillaut.github.io/lectures/software_publication/">Software Publication lecture - S3 school - Thomas Vuillaume</a> ; Thank You !
</div>

<!--
These resources will help you continue on your journey to FAIR research software.
-->

---

## Backup Slides

---

## Publish on Zenodo

Zenodo is not using codemeta.json natively

it requires converting `codemeta.json` content to `.zenodo`

<div class="grid grid-cols-2 gap-6 text-sm">

<div style="text-align: left;">

### GitHub

CodeMeta2Zenodo action

GitHub-Zenodo integration OR eossr snippet in CI

</div>

<div style="text-align: left;">

### GitLab

eossr snippet in CI (CodeMeta -> Zenodo + Publication)

</div>

</div>