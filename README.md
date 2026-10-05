<div align="center">

# 🌿 Monitor Huiles Essentielles

### Base de données interactive des huiles essentielles médicinales

**554 plantes · 857 profils d'huiles · 85 341 compositions chimiques**

[![License: MIT](https://img.shields.io/badge/License-MIT-000091.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live-E1000F?style=for-the-badge&logo=github)](https://gunout.github.io/monitor-huiles-essentielles/)
[![GitHub stars](https://img.shields.io/github/stars/gunout/monitor-huiles-essentielles?style=for-the-badge&color=000091)](https://github.com/gunout/monitor-huiles-essentielles/stargazers)
[![GitHub last commit](https://img.shields.io/github/last-commit/gunout/monitor-huiles-essentielles?style=for-the-badge&color=E1000F)](https://github.com/gunout/monitor-huiles-essentielles/commits/main)
[![Data](https://img.shields.io/badge/Data-sCentInDB-fbbf24?style=for-the-badge)](https://cb.imsc.res.in/scentindb/)
[![Made in France](https://img.shields.io/badge/Made%20in-France-000091?style=for-the-badge)](https://www.gouvernement.fr/)

**[🚀 Voir la démo en ligne](https://gunout.github.io/monitor-huiles-essentielles/)** · **[📊 Explorer les données](#-structure-des-données)** · **[🔬 Sources](#-sources-scientifiques)**

</div>

---

## 📖 À propos

**Monitor Huiles Essentielles** est une interface web interactive qui permet d'explorer une vaste base de données d'huiles essentielles issues de la recherche scientifique. Elle croise :

- 🌱 **Composition chimique** (chromatographie GC-MS)
- 🧪 **Vertus thérapeutiques inférées** par apprentissage automatique
- 💊 **Thérapies documentées** dans la littérature scientifique
- 📖 **Usages traditionnels** (médecine ayurvédique, etc.)
- 🎨 **Odeur et couleur** caractéristiques

L'interface est construite dans l'esprit du **Système de Design de l'État français** (Marianne, bleu-blanc-rouge, accessibilité).

---

## ✨ Fonctionnalités

| Vue | Description |
|---|---|
| 🌿 **Plantes** | Liste complète des 554 plantes, filtrable par nom, vertu, partie |
| 📂 **Parties** | Répartition par partie utilisée (feuille, fleur, racine, graine…) |
| 🔲 **Matrice Plante×Vertu** | Tableau croisé interactif avec intensité de score |
| 📊 **Analyses** | Graphiques (camemberts, barres) sur vertus, thérapies, odeurs |
| 📈 **Top composés** | Les 25 composés chimiques les plus fréquents |
| 🔍 **Qualité** | Taux de couverture des métadonnées par source |

**Fonctionnalités transverses :**
- 🔎 Recherche instantanée (plante, composé, vertu, thérapie)
- 🎨 Thème clair / sombre
- 📥 Export CSV / JSON des résultats filtrés
- 📱 Responsive mobile / tablette
- 🇫🇷 Interface 100% française

---

## 🚀 Utilisation

### Option 1 — En ligne (recommandée)

👉 **https://gunout.github.io/monitor-huiles-essentielles/**

L'interface charge automatiquement `ScentInDB_web.json` au démarrage.

### Option 2 — En local

```bash
git clone https://github.com/gunout/monitor-huiles-essentielles.git
cd monitor-huiles-essentielles
python3 -m http.server 8000
# Ouvrir http://localhost:8000/index.html
```

### Option 3 — Glisser-déposer

Ouvrez `index.html` dans votre navigateur, puis glissez-déposez un fichier JSON dans la zone dédiée.

---

## 📊 Structure des données

### Fichiers disponibles

| Fichier | Taille | Description |
|---|---|---|
| `ScentInDB.json` | 32 Mo | Dataset brut (554 plantes, compositions) |
| `ScentInDB_enriched.json` | 63 Mo | Enrichi avec vertus inférées |
| `ScentInDB_web.json` | 52 Mo | Version allégée pour le web (sans SMILES) |
| `compound_vertus.json` | 254 Ko | Mapping composé → vertus (apprentissage) |
| `compounds_properties.json` | 10 Ko | Propriétés des 62 composés majeurs |

### Schéma JSON

```json
{
  "plant": "Lavandula angustifolia",
  "parts": ["flower|flower"],
  "therapies": ["anxiolytic activity", "anti-inflammatory activity"],
  "uses": ["perfumery", "pharmaceutical"],
  "odor_color": [
    { "part": "flower", "odor": "floral", "color": "pale yellow" }
  ],
  "vertus": ["anti-inflammatoire", "antioxydant", "calmant"],
  "vertus_inferees": {
    "anti-inflammatoire": 0.32,
    "calmant": 0.21
  },
  "oils": [
    {
      "part": "flower",
      "compound_count": 42,
      "total_percent": 96.3,
      "compounds": [
        {
          "name": "Linalool",
          "percent": 35.2,
          "formula": "C10H18O",
          "class": "Monoterpenoids"
        }
      ]
    }
  ]
}
```

---

## 🔬 Sources scientifiques

Ce projet agrège et enrichit des données issues de sources publiques et de la littérature scientifique. **Toutes les vertus attribuées sont documentaires et ne constituent pas un avis médical.**

### Base de données principale

- **[sCentInDB](https://cb.imsc.res.in/scentindb/)** — *Scent of India Database*
  Institute of Mathematical Sciences (IMSc), Chennai, Inde
  Base de référence sur les huiles essentielles de 554 plantes médicinales indiennes, 2 170 profils chimiques GC-MS.

### Littérature scientifique (vertus des composés)

Les vertus inférées s'appuient sur les publications suivantes :

| Composé | Référence |
|---|---|
| α-Pinene, β-Pinene, Limonene | [PMC11408196](https://pmc.ncbi.nlm.nih.gov/articles/PMC11408196/) — *Monoterpenes: Promising agents* |
| Linalool | [PMC9864992](https://pmc.ncbi.nlm.nih.gov/articles/PMC9864992/) — *Biological activities of linalool* |
| Menthol, Menthone | [PMC4171855](https://pmc.ncbi.nlm.nih.gov/articles/PMC4171855/), [PMC9572119](https://pmc.ncbi.nlm.nih.gov/articles/PMC9572119/) |
| Camphor, Borneol | [PMC7404215](https://pmc.ncbi.nlm.nih.gov/articles/PMC7404215/) |
| β-Caryophyllene | [Taylor & Francis](https://www.tandfonline.com/doi/full/10.1080/14756366.2019.1596088) — *Caryophyllene review* |
| Myrcene | [PMC5402865](https://pmc.ncbi.nlm.nih.gov/articles/PMC5402865/) — *Myrcene review* |
| 1,8-Cineole / Eucalyptol | [Voicemed UC](https://www.voicemeduc.com/) |
| Limonene | [Chem Biol Interact 2018](https://pubmed.ncbi.nlm.nih.gov/29454610/) |

### Autres bases consultées

- **[AromaDb](https://cb.imsc.res.in/aromadb/)** — 166 plantes commerciales, 1 321 structures chimiques
- **[Cleveland Clinic](https://my.clevelandclinic.org/health/treatments/essential-oils)** — Essentiels cliniques documentés
- **[PubChem](https://pubchem.ncbi.nlm.nih.gov/)** — Structures et propriétés des composés

---

## 🛠️ Stack technique

- **Frontend** : HTML5, CSS3 (variables CSS, grid, flexbox), JavaScript vanilla (ES2020+)
- **Graphiques** : SVG natif (camemberts, barres, matrices)
- **Données** : JSON
- **Hébergement** : GitHub Pages
- **Design** : Inspiré du [Système de Design de l'État](https://www.systeme-de-design.gouv.fr/) (Marianne)

Aucune dépendance externe, aucun framework — l'ensemble tient dans un seul fichier `index.html`.

---

## ⚠️ Avertissement médical

> **Ces informations sont strictement documentaires et issues de la littérature scientifique.**
> Elles **ne constituent en aucun cas un avis médical**.
> L'usage thérapeutique d'huiles essentielles doit être encadré par un professionnel de santé qualifié (pharmacien, médecin, aromathérapeute diplômé).
> Certaines huiles essentielles sont **déconseillées** voire **interdites** chez l'enfant, la femme enceinte ou allaitante, et en cas de pathologies particulières.

---

## 📜 Licence

Ce projet est distribué sous licence **MIT**. Voir [LICENSE](LICENSE).

Les **données brutes** restent la propriété de leurs sources respectives (sCentInDB, publications scientifiques citées).

---

## 🙏 Crédits

- **Développement** : [@gunout](https://github.com/gunout)
- **Données** : Institute of Mathematical Sciences (IMSc), Chennai, Inde
- **Design** : Système de Design de l'État français

---

<div align="center">

**🇫🇷 Liberté · Égalité · Fraternité**

*Fait avec ❤️ pour la recherche ouverte*

</div>

---

<div align="center">

### 🇫🇷 Gunout · 2026

![Made in France](https://img.shields.io/badge/Made_in-France-002395?style=flat-square&labelColor=FFFFFF&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA5MDAgNjAwIj48cmVjdCB3aWR0aD0iOTAwIiBoZWlnaHQ9IjYwMCIgZmlsbD0iIzAwMjM5NSIvPjxyZWN0IHdpZHRoPSI5MDAiIGhlaWdodD0iNDAwIiB5PSIxMDAiIGZpbGw9IiNmZmYiLz48cmVjdCB3aWR0aD0iOTAwIiBoZWlnaHQ9IjIwMCIgeT0iNDAwIiBmaWxsPSIjZWQyOTM5Ii8+PC9zdmc+)
![GitHub](https://img.shields.io/badge/GitHub-gunout-181717?style=flat-square&logo=github&logoColor=white)
![Year](https://img.shields.io/badge/2026-ED2939?style=flat-square&labelColor=FFFFFF)

<sub>© 2026 <strong>Gunout</strong> — Tous droits réservés.</sub>

</div>
