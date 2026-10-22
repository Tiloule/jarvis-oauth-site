# Jarvis Personal Assistant — mini-site de présentation OAuth

**Site de présentation statique**, actualisé le 22 octobre 2026. Site statique, aucun framework ni logiciel payant nécessaire.

## Fichiers
- `index.html` : page d'accueil de l'application
- `confidentialite.html` : politique de confidentialité avec contact public via GitHub Issues
- `styles.css` : mise en page responsive

## Transparence et vérifications
1. Contact public : [GitHub Issues](https://github.com/Tiloule/jarvis-oauth-site/issues/new). Ces demandes sont publiques : ne jamais y transmettre de données personnelles, jetons ou secrets.
2. Maintenir la politique de confidentialité à jour si les fournisseurs d'IA, la conservation des journaux ou les flux de données évoluent.
3. Périmètre OAuth observé : Calendar, gmail.modify, gmail.send et scopes d'identité ; pas de Drive sur cette autorisation d'après le diagnostic Codex.
4. Ne JAMAIS publier jetons, secrets, client secret, fichiers .env, captures d'écran privées ou liens vers le dashboard local.

## Hébergement gratuit
- Créer un dépôt public GitHub ne contenant **que les fichiers publics du mini-site**.
- Activer GitHub Pages dans Settings → Pages → Deploy from a branch → main / (root).
- Le site sera à une adresse de type `https://UTILISATEUR.github.io/DEPOT/`.
- Pour les exigences d'identité OAuth Google, prévoir un domaine/sous-domaine dont on peut vérifier la propriété via un enregistrement TXT DNS : une URL github.io **seule** n'est pas une garantie d'acceptation de Google lors de la vérification d'un domaine.
- Possibilités gratuites sous réserve d'acceptation : `EU.org` (délégation DNS et validation manuelle), ou `is-a.dev` (sous-domaine via GitHub et TXT, vérification d'acceptation par Google à faire).
- L'URL d'accueil et l'URL de confidentialité doivent utiliser le même domaine ; l'accueil doit lier vers la politique.

## Passage en production de Google OAuth
- Vérifier la propriété du domaine choisi dans Search Console avec un compte propriétaire/éditeur du projet Google Cloud.
- Enregistrer les URLs dans Google Auth Platform → Branding (accueil et confidentialité), puis le domaine autorisé.
- Dans Audience, utiliser « Publier l'application » si les contrôles Google sont satisfaits.
- Pour un usage personnel, la vérification complète des scopes peut bénéficier d'une exception, mais Google peut afficher un avertissement « application non vérifiée », limiter le nombre d'utilisateurs et demander d'autres pièces. Un site ne garantit pas à lui seul la validation d'une app ni l'absence de futurs refus de jeton.
- Une fois l'état In production établi, renouveler **une fois** le consentement gog avec les scopes existants sauvegardés. Les anciens refresh tokens peuvent rester invalides ; la publication n'en crée pas automatiquement de nouveaux.
