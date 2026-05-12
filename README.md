Agent de répartition des factures fournisseurs — CFGT
Application web interne pour le Centre Francophone du Grand Toronto permettant la répartition des factures fournisseurs entre les ~50 programmes / bailleurs de fonds.
Fonctionnalités
Référentiels importables par CSV : programmes (avec indicateur Santé/Standard), employés (multi-programmes par pourcentage), surfaces (sqft par localisation)
5 clés de répartition : par nombre d'employés, par budget, parts égales, par surface (avec filtre de localisation), nominale (employés nommés)
Décomposition TVH automatique : régime 13 % Ontario, TPS 5 % seulement, ou sans taxe
4 comptes de récupération CRA appliqués automatiquement :
Programmes standard : compte 1101 (50 % de la TPS) et 1106 (82 % de la TVP)
Programmes santé : compte 1102 (83 % de la TPS) et 1107 (87 % de la TVP)
Parser télécom intelligent : extraction des noms depuis le texte brut d'une facture avec correspondance floue (Levenshtein)
Exports : CSV Sage 300 (3 lignes par programme), PDF de traçabilité via impression
Historique avec statistique de remboursement TVH mensuel cumulé
Sauvegarde / restauration en JSON
Stockage des données
Toutes les données (référentiels et historique) sont stockées localement dans le navigateur de chaque utilisateur (localStorage). Aucune donnée n'est envoyée à un serveur. Pour partager les référentiels entre collègues : utiliser le bouton « 💾 Sauvegarde » puis « ↻ Restaurer » sur le poste suivant.
Modèles CSV d'import
Trois modèles sont fournis dans le dépôt :

modele-programmes.csv — colonnes : code, nom, bailleur, employes, budget, sante
modele-employes.csv — colonnes : prenom, nom, programme, pourcentage
modele-surfaces.csv — colonnes : localisation, programme, sqft
Déploiement
Ce projet est conçu pour être déployé sur Vercel ou tout hébergement statique :

Pousser le dépôt sur GitHub
Importer dans Vercel
Déployer (aucune configuration de build nécessaire — c'est un fichier HTML statique)
Calculs vérifiés
Exemple : facture 1 000 $ HT, TVH 13 %, répartie 70 % programme santé / 30 % programme standard :

TPS = 50 $, TVP = 80 $, TTC = 1 130 $
P001 (santé, 70 %) : récup TPS = 35 × 83 % = 29,05 $ (compte 1102) — récup TVP = 56 × 87 % = 48,72 $ (compte 1107)
P002 (standard, 30 %) : récup TPS = 15 × 50 % = 7,50 $ (compte 1101) — récup TVP = 24 × 82 % = 19,68 $ (compte 1106)
Total remboursement CRA estimé = 104,95 $
Licence et confidentialité
Outil interne CFGT — Direction des finances. Ne contient aucune donnée du centre dans le code source. Les données saisies par les utilisateurs restent sur leur poste.

