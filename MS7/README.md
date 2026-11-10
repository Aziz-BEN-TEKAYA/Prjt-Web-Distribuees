# MS7 — WellNest AI Engine (module commun)

Moteur intelligent transversal, developpe collectivement par les 6 membres.
**Technologie : Python (FastAPI) ou Node.js — a decider par l'equipe.**
Ce module n'est pas un projet Spring Boot.

## Role
- Consommer les donnees exportees par les 6 modules metier (endpoint `/export/ai` de chaque MS)
- Personal Behavior Analysis, Anomaly Detection (ex: Isolation Forest), Clustering (ex: K-Means),
  Predictive Analytics, Recommendation Engine, Intelligent Daily Report
- Ne fait **pas** le CRUD des autres modules ; n'accede jamais directement a leurs bases

## Format d'echange commun (contrat avec les 6 MS)

| Champ       | Type              | Exemple            |
|-------------|-------------------|--------------------|
| `userId`    | long              | 12                 |
| `timestamp` | ISO-8601          | 2026-11-10T00:00Z  |
| `metric`    | string            | `daily_steps`      |
| `value`     | number            | 4210               |
| `unit`      | string            | `steps`            |
| `source`    | enum              | `SYNTHETIC`        |
| `quality`   | enum              | `COMPLETE`         |

## Limites (cf. document de repartition)
- Une absence de donnees n'est pas une absence d'activite ni une urgence
- Aucun resultat n'est un diagnostic medical
