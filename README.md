# Jarvis Personal Assistant — mini-site de présentation OAuth

**Brouillon à examiner avant publication**, créé le 22 octobre 2026. Site statique, aucun framework ni logiciel payant nécessaire.

## Fichiers
- `index.html` : page d'accueil de l'application
- `confidentialite.html` : projet de politique de confidentialité à adapter et valider
- `styles.css` : mise en page responsive

## À valider impérativement avant publication
1. Remplacer `[AJOUTER UNE ADRESSE DE CONTACT AVANT PUBLICATION]` par une adresse de contact dédiée ou choisie. Publier l'adresse la rend publique.
2. Vérifier les traitements de données réellement effectués par Jarvis, les durées de conservation des journaux, les fournisseurs d'IA distants et toute transmission vers d'autres services. Ne pas publier des promesses inexactes.
3. Confirmer le périmètre OAuth : Calendar, gmail.modify, gmail.send et scopes d'identité ; pas de Drive sur cette autorisation d'après le diagnostic Codex.
4. Les pages publiques ne doivent JAMAIS contenir jetons, secrets, client secret, fichiers .env, captures d'écran privées ou liens vers le dashboard local.

## Hébergement gratuit
- Créer un dépôt public GitHub ne contenant **que ces trois fichiers web**.
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
