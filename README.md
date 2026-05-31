# Koyai Ski — Déploiement Vercel

## Structure du projet

```
koyai-ski-shop/
├── index.html        ← site complet
├── api/
│   └── chat.js       ← proxy API Anthropic (Edge Function)
└── vercel.json       ← config Vercel
```

## Étapes de déploiement

### 1. Créer un compte Vercel
https://vercel.com — gratuit, connecte ton compte GitHub.

### 2. Pousser le projet sur GitHub
```bash
cd koyai-ski-shop
git init
git add .
git commit -m "init"
git branch -M main
git remote add origin https://github.com/TON-USER/koyai-ski.git
git push -u origin main
```

### 3. Importer sur Vercel
- Aller sur https://vercel.com/new
- Choisir le repo GitHub
- Cliquer "Deploy" (pas besoin de configurer le build)

### 4. Ajouter la clé API Anthropic (CRITIQUE)
Dans Vercel → ton projet → Settings → Environment Variables :

| Name | Value |
|------|-------|
| `ANTHROPIC_API_KEY` | `sk-ant-api03-...` (ta clé Anthropic) |

Récupère ta clé sur : https://console.anthropic.com/settings/keys

Puis **redéployer** : Vercel → Deployments → "Redeploy".

### 5. Ajouter tes liens de paiement
Dans `index.html`, cherche ces deux lignes et remplace par tes vraies URLs :
```js
document.getElementById('mp-link').href = 'https://mpago.la/tu-link-aqui';
document.getElementById('tb-link').href = 'https://webpay.cl/tu-link-aqui';
```

---

## Coût API Anthropic

- Modèle utilisé : claude-sonnet-4-20250514
- Coût estimé par conversation agent : ~$0.002–0.005 USD
- Pour 100 conversations/mois : ~$0.20–0.50 USD

Crée ton compte et génère une clé sur :
https://console.anthropic.com

---

## Domaine personnalisé (optionnel)
Vercel → ton projet → Settings → Domains → ajouter `koyaiskishop.cl`
Puis configurer les DNS chez ton registrar.
