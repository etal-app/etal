# Étal — feuille de route

Ce fichier sert à ne rien perdre entre deux sessions de travail sur le code.
Mis à jour à chaque envoi.

## ✅ Fait (dans la version envoyée)

- Vraie base de données persistante (Supabase)
- Hébergement réel en ligne (GitHub + Vercel) — https://etal-tau.vercel.app
- Logo monogramme "É" (sans l'accent toit)
- Comptes de démo auto-créés si base vide
- Face ID / Touch ID (connexion rapide, propre à chaque appareil)
- Photo de profil utilisateur (remplace la lettre-avatar si ajoutée)
- Nouvelle grille tarifaire :
  - Gratuit : réponse aux avis incluse, 1 alerte/semaine
  - Pro (12€/mois) : alertes illimitées, galerie photo, fidélité, stats complètes
  - Premium (29€/mois) : tout Pro + placement prioritaire local (rayon 50 km),
    alertes ciblées clients fidèles (annoncé, pas encore codé), multi-commerces
    (annoncé, pas encore codé)
- Placement prioritaire Premium réellement codé dans le tri de la liste (rayon 50 km,
  jamais national)
- Bouton "Scanner un QR" remonté en haut de la fiche commerce (plus besoin d'aller
  dans l'onglet Fidélité)
- Scan QR réparé pour Safari/iPhone (ajout d'un décodeur de secours jsQR, en plus de
  l'API native utilisée sur Chrome/Android)
- Suppression du menu de filtre catégorie redondant sur l'écran découverte

## 🔜 À faire (pas urgent, dans l'ordre discuté)

- 🎯 Alertes ciblées aux clients fidèles (Premium) — vraie fonctionnalité à coder
  (UI + logique), pour l'instant juste listée dans la fiche tarifs
- 🏬 Plusieurs commerces sur un seul compte (Premium) — vraie fonctionnalité à coder,
  pour l'instant juste listée dans la fiche tarifs
- 📄 Pages légales (CGU / CGV / politique de confidentialité) + case à cocher
  "Je certifie avoir pris connaissance" + bouton "J'accepte" obligatoire à
  l'inscription
- 🔄 Migration de la persistance depuis le blob JSON unique (`app_state`) vers les
  vraies tables relationnelles déjà créées dans Supabase (`accounts`, `shops`,
  `posts`, etc. — voir `schema.sql`)
- 💳 Carte de fidélité dans Apple Wallet / Google Wallet — écarté pour l'instant
  (nécessite un compte Apple Developer à 99$/an + un petit service de signature ;
  à reconsidérer une fois que l'appli a de vrais utilisateurs actifs)

## Notes techniques utiles

- Le code source de travail est `etal.jsx`. Le fichier réellement déployé est
  `index.html` (React + Babel chargés depuis cdnjs, `etal.jsx` collé dedans).
- Persistance : Supabase, table `app_state` (une seule ligne JSON pour l'instant).
- Le dépôt GitHub (`github.com/etal-app/etal`) contient `index.html` à la racine ;
  Vercel redéploie automatiquement à chaque mise à jour de ce fichier.
