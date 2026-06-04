---
theme: seriph
background: https://unsplash.com/photos/eFbxYl9M_lc/download?force=true&w=1920
title: Métadonnées et FAIRness
info: |
  ## Comment ajouter des métadonnées pour vos logiciels de recherche
  Un atelier pour mettre en place, maintenir et publier vos métadonnées

  Plus d'infos sur [Codemetasoft](https://w3id.org/codemetasoft)
  Basé sur les ressources EVERSE RSQKit et le project Codemetasoft.
class: text-center
drawings:
  persist: false
transition: slide-left
mdc: true
duration: 60min
layout: cover
aspectRatio: 16/9
download: true
---

# Métadonnées et logiciel de recherche

Plan

1. Métadonnées et FAIRness
2. TP : générer votre codemeta.json
3. Maintenance
4. TP : installer une CI pour contrôler ses métadonnées
5. Publication de notre logiciel de recherche


---

# C'est quoi une métadonnée ?

- donnée structurée qui donne du contexte, des caractéristiques sur un autre élément

Métadonnées pour image : horodatage, lieu, appareil photo utilisé, auteur, ...
Métadonnées pour un livre : auteur, éditions, nombre de pages, thèmes abordés, langue, format, ...

Métadonnées permet 
- décrire
- catégoriser
- informer (instructions pour utilisation)

---

# Métadonnées pour le logiciel et principe FAIR

level: 2
---

# The Missing Dimension: FAIRness

<div class="grid grid-cols-2 gap-8">
<div>

## What is FAIR?

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

- FAIR ⊂ Quality Software
- FAIR ensures **discoverability** & **reusability**
- Quality includes **correctness**, **performance**, **testing**

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
<ul class="list-none p-0 space-y-1">
  <li v-click><b>F1.</b> Assigned unique & persistent ID (DOI)</li>
  <li v-click class="ml-3 opacity-80 border-l-2 pl-2"><b>F1.1.</b> IDs for different components</li>
  <li v-click class="ml-3 opacity-80 border-l-2 pl-2"><b>F1.2.</b> IDs for different versions</li>
  <li v-click><b>F2.</b> Described with rich metadata</li>
  <li v-click><b>F3.</b> Metadata explicitly points to ID</li>
  <li v-click><b>F4.</b> Metadata are searchable & indexable</li>
</ul>
</div>

<div class="p-3 border border-green-200 rounded-lg bg-green-50/30 dark:bg-green-900/10">
<h3 class="text-green-600 font-bold mb-1 flex items-center gap-2"><carbon:cloud-download /> A.ccessible</h3>
<p class="mb-2 italic opacity-70">Retrievable via standard protocols.</p>
<ul class="list-none p-0 space-y-1">
  <li v-click><b>A1.</b> Retrievable by ID using standard protocols</li>
  <li v-click class="ml-3 opacity-80 border-l-2 pl-2"><b>A1.1.</b> Open, free & universal protocol</li>
  <li v-click class="ml-3 opacity-80 border-l-2 pl-2"><b>A1.2.</b> Auth/Auth procedure where needed</li>
  <li v-click><b>A2.</b> Metadata persists even if software is gone</li>
</ul>
</div>

<div class="p-3 border border-purple-200 rounded-lg bg-purple-50/30 dark:bg-purple-900/10">
<h3 class="text-purple-600 font-bold mb-1 flex items-center gap-2"><carbon:connect /> I.nteroperable</h3>
<p class="mb-2 italic opacity-70">Exchange data and interact via APIs.</p>
<ul class="list-none p-0 space-y-1">
  <li v-click><b>I1.</b> Meets community standards for exchange</li>
  <li v-click><b>I2.</b> Includes qualified references to other objects</li>
</ul>
</div>

<div class="p-3 border border-orange-200 rounded-lg bg-orange-50/30 dark:bg-orange-900/10">
<h3 class="text-orange-600 font-bold mb-1 flex items-center gap-2"><carbon:recycle /> R.eusable</h3>
<p class="mb-2 italic opacity-70">Understandable, modifiable, and buildable.</p>
<ul class="list-none p-0 space-y-1">
  <li v-click><b>R1.</b> Rich and accurate attributes</li>
  <li v-click class="ml-3 opacity-80 border-l-2 pl-2"><b>R1.1.</b> Clear and accessible License</li>
  <li v-click class="ml-3 opacity-80 border-l-2 pl-2"><b>R1.2.</b> Detailed provenance & history</li>
  <li v-click><b>R2.</b> References to other software</li>
  <li v-click><b>R3.</b> Meets domain-relevant community standards</li>
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

# Générer son codemeta.json

---