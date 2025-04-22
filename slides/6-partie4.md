## Documentation

---

## Documentation
1. Page internet statique
2. Petite application 
3. prototype de SaaS

---

### I-A) Documentation Netlify

Étapes de déploiement:
- Création du compte sur netlify.com
- Import du projet depuis GitHub
- Configuration du build
- Paramétrage du domaine et SSL

---

### I-B) Documentation Vercel

Processus de déploiement:
- Compte sur vercel.com et connexion GitHub
- Import et détection automatique d'Astro
- Configuration du build
- Gestion du domaine personnalisé

---

### II-A) Documentation Heroku

Déploiement:
- Installation CLI: `curl https://cli-assets.heroku.com/install.sh | sh`
- Création app: `heroku create mcqgen-app`
- Configuration API: `heroku config:set OPENAI_API_KEY=your_key`
- Déploiement: `git push heroku main`

---

### II-A) Documentation Heroku (suite)

Maintenance:
- Logs: `heroku logs --tail`
- Restart: `heroku restart`
- SSL automatique et CDN inclus
- Pipeline d'intégration continue

---

### II-B) Documentation AWS EC2

Configuration serveur:
- Instance t2.large avec Ubuntu
- SSH: `ssh -i key.pem ubuntu@ip`
- Installation dépendances
- Configuration réseau et sécurité

---

### III) Prototype SaaS

Documentation en attente de déploiement complet.