# Prompt 1 — Reproduire la maquette RetraiteIA

Copiez-collez ce prompt dans Claude Code pour recréer l'application depuis zéro.

---

```
Tu es un expert en développement web et en retraite française. Crée une application web complète en UN SEUL fichier HTML (pas de framework, pas de backend) qui simule un outil de bilan retraite assisté par intelligence artificielle.

L'application s'appelle "RetraiteIA" et doit avoir 6 onglets :

1. **Documents** — Zone de drag & drop pour importer des PDF. Bouton "Jeu de test" qui ajoute 5 documents fictifs avec animation. Chaque document affiche nom, taille, type, statut (Analysé/En attente). Bouton de suppression sur chaque carte.

2. **Pipeline IA** — 4 agents IA visuels en ligne horizontale (Lecteur RIS → Analyseur Bulletins → Expert Régimes → Calculateur), reliés par des flèches animées. Bouton "Lancer l'analyse" qui active séquentiellement chaque agent avec : spinner, changement de couleur (bleu=actif, vert=terminé), et un panneau de logs style terminal en bas (fond noir, texte vert) qui affiche les messages en temps réel.

3. **Carrière** — Timeline horizontale colorée montrant le parcours professionnel fictif (6 employeurs sur 39 ans, de 1985 à 2024). Au survol de chaque bloc : tooltip riche avec employeur, poste, salaire, régime, trimestres. En dessous : 4 cartes de stats (durée, trimestres, employeurs, régimes).

4. **Anomalies** — 5 anomalies détectées avec 3 niveaux de sévérité (critique=rouge, important=orange, mineur=jaune). Chaque anomalie a un impact financier en €/mois. Bannière "impact total" en haut. Section "Recommandations IA" avec des actions concrètes et le gain potentiel. Boutons Corriger/Signaler/Ignorer fonctionnels.

5. **Estimation** — Tableau de pension par régime (CNAV, AGIRC-ARRCO, RSI). Graphique Chart.js (barres) montrant la pension à 62, 64 ans 6 mois et 67 ans. Tableau comparatif mensuel. Callouts informatifs (taux plein, comparaison moyenne nationale DREES).

6. **Export** — Aperçu visuel de 4 slides PowerPoint miniatures (cliquables pour zoom). Aperçu du rapport Word. Bouton "Exporter PowerPoint" qui génère un VRAI fichier .pptx (utiliser PptxGenJS en CDN). Bouton "Exporter Word" qui génère un fichier HTML formaté.

Design : palette bleu marine institutionnel (#1e3a5f, #2563eb), typographie Inter + Source Serif 4 (Google Fonts), icônes Font Awesome 6. Header sticky avec logo, badge "Multi-agents", barre de progression circulaire SVG. Bannière de bienvenue avec infos du dossier (nom, date naissance, n° SS, âge taux plein). Animations CSS subtiles (fadeIn, slideIn, pulse). Responsive mobile. Styles d'impression.

Données fictives réalistes pour Martin Dupont, né le 15/03/1963, 156 trimestres validés, pension estimée 2 611 €/mois à taux plein.

Libraries CDN autorisées : Chart.js 4.4, PptxGenJS 3.12, Font Awesome 6.5, Google Fonts.
```
