# Prompt 2 — Rendre RetraiteIA fonctionnel

Ce prompt transforme la maquette en un outil qui analyse de VRAIS documents de retraite avec l'IA.

---

```
Je veux transformer cette maquette RetraiteIA en un outil fonctionnel qui analyse de VRAIS documents de retraite.

Voici ce que je veux :

### Architecture cible
- Projet Next.js (App Router) déployé sur Vercel
- Le fichier index.html actuel sert de référence design — reproduire le même rendu exact
- 1 API route `/api/analyze` qui reçoit les textes des PDF et appelle Claude

### Fonctionnement souhaité

**Étape 1 — Extraction PDF (côté client)**
- Intégrer pdf.js (Mozilla) via CDN pour extraire le texte des PDF uploadés directement dans le navigateur
- Quand l'utilisateur drop ses fichiers, extraire le texte de chaque PDF
- Afficher la progression d'extraction par document

**Étape 2 — Analyse IA (API route)**
- Envoyer tous les textes extraits à l'API route `/api/analyze`
- L'API route appelle Claude (claude-sonnet-4-5-20250929) avec un prompt structuré
- Le prompt demande à Claude de retourner un JSON avec exactement cette structure :

```json
{
  "beneficiaire": { "nom": "", "date_naissance": "", "num_ss": "" },
  "carriere": [
    { "employeur": "", "poste": "", "debut": "", "fin": "", "salaire_annuel": 0, "regime": "", "trimestres": 0 }
  ],
  "anomalies": [
    { "severite": "critique|important|mineur", "titre": "", "description": "", "impact_mensuel": 0, "action_recommandee": "" }
  ],
  "estimation": {
    "cnav": { "trimestres": 0, "pension_mensuelle": 0 },
    "agirc_arrco": { "points": 0, "pension_mensuelle": 0 },
    "rsi": { "trimestres": 0, "pension_mensuelle": 0 },
    "total_mensuel": 0,
    "age_taux_plein": "",
    "pension_62_ans": 0,
    "pension_taux_plein": 0,
    "pension_67_ans": 0
  },
  "fiabilite": 0,
  "recommandations": [
    { "titre": "", "description": "", "gain_mensuel": 0 }
  ]
}
```

**Étape 3 — Pipeline visuel en temps réel**
- Utiliser le streaming de Claude (SSE) pour simuler le pipeline multi-agents
- Pendant que Claude analyse, les 4 agents s'activent séquentiellement
- Les logs affichent des messages de progression basés sur les données réelles

**Étape 4 — Rendu dynamique**
- Quand le JSON revient, peupler dynamiquement :
  - La timeline carrière (couleurs automatiques par employeur)
  - Les cartes d'anomalies
  - Le tableau d'estimation et le graphique Chart.js
  - Les exports PPTX et Word avec les vraies données

### Variables d'environnement Vercel
```
ANTHROPIC_API_KEY=sk-ant-xxx
```

### Contraintes
- Le design final doit être IDENTIQUE à la maquette actuelle
- L'extraction PDF est 100% côté client (pas d'upload serveur)
- Seul le texte extrait est envoyé à l'API (pas les fichiers)
- Gérer les erreurs : PDF illisible, timeout Claude, documents non pertinents
- Ajouter un message si les documents uploadés ne sont pas des documents de retraite
- Le prompt Claude doit inclure les règles de calcul retraite française 2024 (CNAV, AGIRC-ARRCO, RSI/SSI, décote/surcote, SAM 25 meilleures années, valeur du point)
```
