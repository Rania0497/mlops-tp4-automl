# Comparatif des approches

| Approche | F1 test | Temps humain | Temps machine | Coût estimé (source, date) | Explicabilité | Export / réversibilité |
|---|---|---|---|---|---|---|
| Logistique (réf.) | 0.7407 | Faible | Faible | 0 (poste local) | Maximale | Total |
| Manuel (TP2) | 0.8669 | Élevé | Moyen | 0 (poste local) | Moyenne/Bonne | Total |
| FLAML 60 s | 0.8409 | Faible | 60 s | 0 (poste local) | Moyenne/Basse | Total |
| Vertex AI AutoML | non mesuré | Moyen | Facturé au nœud-heure | 21,252 $/heure de nœud (Google Cloud, consulté le 22/10/2026) | Bonne (explications, notebooks) | Export possible mais réversibilité partielle |
| SageMaker Autopilot | non mesuré | Moyen | Facturé à l'usage (calcul + stockage) | Facturation à la seconde des instances utilisées (AWS, consulté le 22/10/2026) | Bonne (rapports, feature importance) | Export possible mais couplage fort à SageMaker |
| Azure Automated ML | non mesuré | Moyen | Facturé à l'heure de calcul | Facturation à l'usage des instances de calcul (Azure, consulté le 22/10/2026) | Bonne via Responsible AI dashboard | Export possible mais format propriétaire |

## Commentaire (5 lignes)

1. **Logistique** : à privilégier comme baseline rapide, interprétable et gratuite, surtout si le contexte exige une transparence totale et un modèle auditable sans dépendance externe.
2. **Manuel (TP2)** : pertinent quand on a le temps et l'expertise pour itérer, ou quand le volume de données est trop petit pour que l'AutoML ait de quoi explorer efficacement.
3. **FLAML local** : idéal pour prototyper vite à coût nul, garder le contrôle des données et éviter tout verrouillage fournisseur, même si le gain sur un petit jeu de données peut être modeste (ici, légèrement en dessous du manuel).
4. **Vertex AI / SageMaker / Azure** : préférables si l'équipe veut déléguer l'infrastructure, si les données sont déjà dans le cloud correspondant, ou si l'on a besoin d'un registre de modèles et d'endpoints managés pour la production.
5. **Managé vs local** : le managé coûte cher à l'heure et verrouille, mais réduit la charge d'exploitation ; le local est gratuit et réversible, mais exige de gérer soi-même l'environnement, les logs et la mise en production.