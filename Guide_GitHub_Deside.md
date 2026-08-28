# 🗂️ GUIDE COMPLET — GitHub pour Deside (A → Z)

**But :** mettre le code de ton site sur GitHub (un coffre-fort en ligne),
puis le connecter à Cloudflare pour que ton site **se mette à jour tout seul**.
Résultat : **plus aucune dépendance à ton ordinateur.**

> Compte à utiliser partout : **ayitideside@gmail.com** (ton compte-racine Deside).
> Coupe ton VPN pendant les inscriptions (évite les blocages).

---

## 🧭 CE QU'ON VA FAIRE (vue d'ensemble)

1. Créer un compte **GitHub** (gratuit).
2. Créer un **dépôt** (repository) = le dossier en ligne de ton code.
3. **Déposer** tes fichiers (index.html, dashboard) dedans.
4. **Connecter** GitHub à Cloudflare → déploiement automatique.
5. (Plus tard) Brancher ton domaine **deside509.com** dessus.
6. Comprendre comment **mettre à jour** le site désormais.

---

# PARTIE 1 — Créer le compte GitHub

1. Va sur **https://github.com**
2. Clique **« Sign up »** (S'inscrire), en haut à droite.
3. **Email** : tape `ayitideside@gmail.com` → Continue.
4. **Password** : choisis un mot de passe fort (garde-le avec tes autres). → Continue.
5. **Username** : choisis `deside509` (sinon `deside-509`, `deside-ayiti`).
   - C'est ton identifiant GitHub. → Continue.
6. GitHub demande une **petite vérification** (un puzzle « prouvez que vous êtes humain »). Résous-le.
7. GitHub envoie un **code par email** à `ayitideside@gmail.com`.
   - Va chercher le code dans ta boîte mail, tape-le.
8. Quand il propose un plan : choisis **« Free »** (gratuit). ✅
9. (S'il pose des questions « combien de personnes », « intérêts »… → réponds vite ou clique « Skip ».)

➡️ **Ton compte GitHub est créé.** Tu arrives sur ton tableau de bord.

---

# PARTIE 2 — Créer le dépôt (le dossier de Deside)

1. En haut à droite, clique le **« + »** → **« New repository »**.
2. **Repository name** : `deside509-site`
3. **Description** (optionnel) : `Site public Deside`
4. Coche **« Public »** (ou Private si tu préfères — Public est plus simple pour Cloudflare).
5. Coche **« Add a README file »** (ça initialise le dépôt).
6. Clique **« Create repository »** (bouton vert).

➡️ **Ton dépôt est créé.** Tu vois une page avec un fichier `README.md`.

---

# PARTIE 3 — Déposer tes fichiers du site

> Le fichier principal DOIT s'appeler **`index.html`** (page d'accueil).

1. Dans ton dépôt, clique **« Add file »** → **« Upload files »**.
2. **Glisse** ton fichier `index.html` dans la zone (ou clique « choose your files »).
   - Ajoute aussi `deside_dashboard.html` si tu veux le dashboard dessus.
3. En bas, dans **« Commit changes »**, écris un petit message : `Ajout du site Deside`.
4. Clique **« Commit changes »** (bouton vert).

➡️ **Ton code est maintenant en sécurité sur GitHub, en ligne.**
Même sans ton ordinateur, il est là, pour toujours.

---

# PARTIE 4 — Connecter GitHub à Cloudflare (déploiement automatique)

> Ici, le but : quand tu modifies le code sur GitHub, Cloudflare **met à jour le site tout seul**.
> On utilise **Cloudflare Pages** (la façon la plus simple pour un site connecté à GitHub).

1. Va sur **https://dash.cloudflare.com** (connecté avec `ayitideside@gmail.com`).
2. Menu de gauche → **« Workers & Pages »**.
3. Clique **« Create »** → onglet **« Pages »** → **« Connect to Git »**.
4. Clique **« Connect GitHub »** → une fenêtre GitHub s'ouvre → **autorise Cloudflare**
   (clique « Authorize Cloudflare »). Choisis ton dépôt `deside509-site`.
5. **Build settings** (réglages) — TRÈS IMPORTANT, mets exactement ça :
   - **Framework preset** : `None` (aucun)
   - **Build command** : (laisse **vide**)
   - **Build output directory** : `/` (juste une barre oblique)
6. Clique **« Save and Deploy »**.
7. Cloudflare construit le site (1-2 min) et te donne une adresse du type :
   **`deside509-site.pages.dev`**
8. Ouvre cette adresse → **ton site s'affiche.** 🎉

➡️ **À partir de maintenant :** dès que tu modifies un fichier sur GitHub,
Cloudflare **redéploie automatiquement**. Plus besoin d'uploader depuis ton ordi !

---

# PARTIE 5 — Brancher ton domaine deside509.com (à faire quand tu es prêt)

> ⚠️ Étape un peu délicate : ton domaine `deside509.com` est actuellement branché
> sur ton ancien Worker. On va le déplacer vers le nouveau projet Pages.
> **Fais-le seulement quand le site pages.dev marche bien.**

**A. Autoriser le nouveau domaine dans Firebase (sinon la connexion Google casse) :**
- Firebase → Authentication → Paramètres → Domaines autorisés → ajoute :
  `deside509-site.pages.dev` (le temps du test).

**B. Déplacer le domaine :**
1. Cloudflare → Workers & Pages → ton **ancien Worker `deside`** → onglet **Domains**.
2. Retire (Remove) le domaine `deside509.com` de l'ancien Worker.
3. Va sur ton **nouveau projet Pages** (`deside509-site`) → onglet **« Custom domains »**.
4. Clique **« Set up a custom domain »** → tape `deside509.com` → confirme.
   - Comme le domaine est déjà chez Cloudflare, ça se configure tout seul (quelques minutes).
5. Ajoute aussi `www.deside509.com` de la même façon.

**C. Vérifier Firebase :**
- Confirme que `deside509.com` et `www.deside509.com` sont bien dans les
  Domaines autorisés Firebase.

➡️ **Ton domaine pointe maintenant vers le site déployé depuis GitHub.**

> 💡 Si cette étape te stresse, garde l'ancien Worker actif et teste tranquillement
> sur `pages.dev` d'abord. Rien ne presse — le site actuel continue de marcher.

---

# PARTIE 6 — Comment tu mets à jour le site MAINTENANT

Désormais, tu n'uploades plus rien depuis ton ordi. Deux façons de modifier :

**Façon simple (directement sur GitHub, depuis n'importe quel appareil) :**
1. Va sur ton dépôt GitHub → clique sur `index.html`.
2. Clique l'icône **crayon ✏️** (Edit).
3. Modifie le code.
4. En bas → **« Commit changes »**.
5. Cloudflare redéploie tout seul en 1-2 min. ✅

**Façon avec fichier (si quelqu'un te donne un nouveau fichier) :**
1. GitHub → **« Add file »** → **« Upload files »**.
2. Glisse le nouveau `index.html` (il remplace l'ancien).
3. **Commit changes** → déploiement auto.

---

# 🗺️ ARCHITECTURE FINALE (où vit chaque chose)

| Élément | Où c'est stocké | Coût |
|---|---|---|
| **Code du site** | GitHub | Gratuit |
| **Déploiement / hébergement** | Cloudflare Pages | Gratuit |
| **Base de données** (votes, sondages, articles, leaders) | Firebase Firestore | Gratuit (Spark) |
| **Vidéos longues / documentaires** | YouTube (chaîne Deside) | Gratuit |
| **Photos / flyers** | Hébergeur d'images gratuit (ImgBB, etc.) | Gratuit |
| **Domaine** | deside509.com (Cloudflare) | ~10 $/an |

➡️ **RIEN ne dépend de ton ordinateur.** Tu travailles depuis partout.

---

# ✅ CHECKLIST RAPIDE

- [ ] Compte GitHub créé (ayitideside@gmail.com)
- [ ] Dépôt `deside509-site` créé
- [ ] `index.html` déposé dessus
- [ ] Cloudflare Pages connecté à GitHub
- [ ] Site visible sur `...pages.dev`
- [ ] (Plus tard) domaine `deside509.com` déplacé vers Pages
- [ ] (Plus tard) domaines autorisés Firebase à jour

---

# ⚠️ RÈGLES DE SÉCURITÉ

- **Active la validation en 2 étapes (2FA)** sur GitHub ET sur ton Gmail-racine.
  (GitHub → Settings → Password and authentication → Two-factor authentication)
- Garde tes mots de passe en lieu sûr.
- Ne partage jamais tes mots de passe. Pour donner accès au DG/staff,
  on utilisera des **rôles**, pas le partage de mot de passe.

---

*Guide préparé pour Deside509 — média neutre 100% Ayiti.*
*Réalisé avec AYITIPRO. À garder comme référence permanente.*
