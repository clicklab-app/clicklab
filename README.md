# ClickLab

Plateforme de labs de TP à la demande. L'étudiant clique sur « Démarrer » et reçoit en moins d'une minute un lab Linux isolé, directement dans son navigateur. Le lab se supprime tout seul à la fin du créneau.

Projet du Cycle d'Innovation Digitale, EPSI Montpellier (M1 2026-27, puis M2).

## L'équipe

| Qui | Rôle |
| --- | --- |
| Casimir | Porteur du projet, plateforme et infrastructure : Terraform, Kubernetes, moteur des labs, CI/CD, ArgoCD |
| Ali | Sécurité et supervision : règles réseau, quotas, Pod Security, Kyverno, Prometheus, Grafana |
| Helvira | Labs et cahier des charges : images Docker des labs, suivi du CDC |
| Wassila | Backend : API FastAPI, PostgreSQL, comptes |
| Emilien | Maquettes Figma et portail Vue.js |

## Organisation du dépôt

| Dossier | Contenu | Responsable |
| --- | --- | --- |
| `infra/terraform` | Création du cluster Oracle Cloud (et AWS ponctuellement) | Casimir |
| `infra/ansible` | Configuration des serveurs | Casimir |
| `platform` | Déploiement sur Kubernetes : Helm, ArgoCD, Traefik, cert-manager, et les règles de sécurité et de supervision | Casimir et Ali |
| `backend` | API FastAPI, PostgreSQL, comptes | Wassila |
| `backend/moteur` | Le moteur qui crée et supprime les labs | Casimir |
| `labs` | Images Docker des labs (ARM et x86, utilisateur non root) | Helvira |
| `frontend` | Portail Vue.js et Tailwind | Emilien |
| `docs` | Contrat du moteur, schémas, notes techniques | Toute l'équipe |

## Règles de travail

- On ne pousse jamais directement sur `main` : chaque changement passe par une branche, puis une pull request relue par au moins une autre personne.
- Nom des branches : `type/sujet-court`, par exemple `feat/moteur-creer-lab` ou `fix/ingress-chemin`.
- Messages de commit : `type: ce qui change`, avec `feat`, `fix`, `docs`, `chore`, `infra` ou `test`.
- Aucun secret dans Git : mots de passe, clés et fichiers `.env` restent sur vos machines. Le `.gitignore` bloque les cas les plus courants, mais vérifiez avant chaque commit.
- Chaque pull request est reliée à sa carte Trello.

## Démarrer en local

Le guide d'installation (k3s, premier lab) arrive dans `docs/`.
