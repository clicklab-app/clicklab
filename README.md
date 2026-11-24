# ClickLab

Plateforme de labs de TP à la demande. L'étudiant clique sur « Démarrer » et reçoit en moins d'une minute un lab Linux isolé, directement dans son navigateur. Le lab se supprime tout seul à la fin du créneau.

Projet du Cycle d'Innovation Digitale, EPSI Montpellier (M1 2026-27, puis M2).

## Organisation du dépôt

| Dossier | Contenu | Responsable |
| --- | --- | --- |
| `infra/terraform` | Création du cluster Oracle Cloud (et AWS ponctuellement) | M1 plateforme et infrastructure |
| `infra/ansible` | Configuration des serveurs | M1 plateforme et infrastructure |
| `platform` | Déploiement sur Kubernetes : Helm, ArgoCD, Traefik, cert-manager | M1 plateforme et infrastructure |
| `backend` | API FastAPI, PostgreSQL, comptes, et le moteur des labs (`backend/moteur`) | M1 backend (moteur : M1 plateforme) |
| `labs` | Images Docker des labs (ARM et x86, utilisateur non root) | M1 labs et cahier des charges |
| `frontend` | Portail Vue.js et Tailwind | B1 |
| `docs` | Contrat du moteur, schémas, notes techniques | Toute l'équipe |

## Règles de travail

- On ne pousse jamais directement sur `main` : chaque changement passe par une branche, puis une pull request relue par au moins une autre personne.
- Nom des branches : `type/sujet-court`, par exemple `feat/moteur-creer-lab` ou `fix/ingress-chemin`.
- Messages de commit : `type: ce qui change`, avec `feat`, `fix`, `docs`, `chore`, `infra` ou `test`.
- Aucun secret dans Git : mots de passe, clés et fichiers `.env` restent sur vos machines. Le `.gitignore` bloque les cas les plus courants, mais vérifiez avant chaque commit.
- Chaque pull request est reliée à sa carte Trello.

## Démarrer en local

Le guide d'installation (k3s, premier lab) arrive dans `docs/`.
