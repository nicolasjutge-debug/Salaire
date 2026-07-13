# Suivi Salaire, RTT & Congés

Application personnelle de suivi de salaire, primes, RTT et congés payés — Nicolas, Sarah, Simon, Nelly.

## Icône

`favicon.ico` + `icons/icon-*.png` + `manifest.json` sont référencés dans `index.html` (favicon, apple-touch-icon, PWA). Dépose ces fichiers à la racine du repo, à côté d'`index.html`, en conservant la structure `icons/`.

## Onglet Estimation

Rapport complet d'estimation salariale annuelle pour Nicolas : résumé exécutif, tableau récapitulatif, détail mensuel des calculs (dépliable), hypothèses retenues, formules utilisées, et gestion des archives par année (les paramètres utilisés sont figés dans chaque archive, même si tu les modifies ensuite).

Paramètres pris en compte : taux de prime d'expérience (1,5 % par défaut, appliqué au salaire mensuel), valorisation de la base conventionnelle (+9 % par défaut à partir d'août 2025, appliquée aux mois estimés uniquement), et titres-restaurant recalculés sur les jours réellement travaillés (jours ouvrés − RTT pris − CP pris).

## Fonctionnalités RTT/CP

- **Période complète** : dans « Jours pris », renseigne une date de fin pour poser plusieurs jours d'un coup (week-ends exclus automatiquement). Les alertes (période bloquée, RTT consécutifs) s'appliquent à toute la période.
- **Modification** : chaque jour pris ou période bloquée peut être édité (icône crayon), pas seulement supprimé.
- **Envoi par mail** : le bouton « Envoyer par mail » dans « Périodes sans RTT/CP possible » ouvre ton client mail avec la liste pré-remplie.

## Déploiement sur GitHub

1. Crée un repo GitHub et mets `index.html` à sa racine.
2. Va dans **Settings → Pages → Deploy from branch**, choisis `main` et `/ (root)`.
3. L'appli est accessible à l'URL fournie par GitHub Pages (ou ouvre simplement `index.html` en local, ça fonctionne aussi sans hébergement).

Aucune étape de build n'est nécessaire : React, Babel et le style sont chargés/inclus directement dans la page (React/Babel depuis cdnjs.cloudflare.com).

## Stockage des données

Par défaut, les données sont enregistrées dans le stockage local du navigateur (`localStorage`) — rien à configurer, ça marche immédiatement.

Quand tu es prêt à synchroniser entre plusieurs appareils, clique sur **« synchroniser »** en haut de l'appli :

1. Crée un compte gratuit sur [jsonbin.io](https://jsonbin.io) et copie ta **X-Master-Key** depuis ton tableau de bord.
2. Colle-la dans le panneau et choisis **« Créer un bin »** (première fois) ou **« J'ai déjà un bin »** (si tu as déjà connecté un autre appareil — renseigne alors aussi le Bin ID).
3. Une fois connecté, chaque modification est enregistrée à la fois localement et sur JSONBin. Le bouton devient **« sync ✓ »** (ou **« sync ⚠ »** en cas d'échec réseau — tes données restent alors sauvegardées localement en attendant).
4. **« Déconnecter »** dans le panneau revient au stockage local uniquement.

⚠️ Ta clé API et l'ID du bin restent dans le stockage local de ton navigateur — jamais commités sur GitHub, jamais envoyés ailleurs qu'à l'API JSONBin.

Le bouton **« réinitialiser »** efface les données (locales, et sur JSONBin si connecté) — double-tap pour confirmer.

## Aperçu dans Claude

Le fichier fonctionne aussi directement dans l'aperçu de Claude (React/Babel sont chargés depuis cdnjs.cloudflare.com, et le style est autonome — plus de dépendance à unpkg.com ou cdn.tailwindcss.com, non accessibles depuis cet aperçu).

