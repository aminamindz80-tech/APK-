# ERP Atelier — application Android autonome (hors ligne)

L'application contient **tout l'ERP** : le serveur Python (`server.py`) tourne dans le téléphone et la base SQLite est stockée dans l'application.
Aucun PC, aucun Wi-Fi, aucune connexion Internet n'est nécessaire. Elle n'est pas reliée à la version PC : les données du téléphone restent sur le téléphone.

## Fonctions propres au téléphone
- **📷 Scanner une photo** (menu) : photographiez un BL, un BC ou une liste d'articles → le texte est lu sur le téléphone (ML Kit, modèle inclus dans l'APK) → vous vérifiez/corrigez le tableau → enregistrement dans la base de l'application :
  - BL / BC : créés en **brouillon** (jamais validés automatiquement), avec N°, date, client/fournisseur et lignes. Les articles sont retrouvés par référence ou désignation ; sinon ils sont créés.
  - Articles : création des fiches (stock initial enregistré dans le journal de stock). Les articles déjà existants ne sont pas modifiés.
- Photos d'articles avec l'appareil photo, ouverture des PDF, téléchargements Excel/PDF (dossier Téléchargements), impression.
- Connexion initiale : **admin / admin123** — à changer au premier lancement.

## Limites de la lecture de photo
Texte imprimé en alphabet latin uniquement (français) ; pas d'écriture manuscrite ni d'arabe. Photo à plat, bien éclairée, un seul tableau. Vérifiez toujours les quantités avant d'enregistrer.

## Générer l'APK
Le dossier `android/` seul ne suffit pas : l'application reprend `server.py` et `static/` du dossier parent (copiés automatiquement avant chaque compilation).

**Sans Android Studio (GitHub)** : déposez tout le contenu du dossier parent dans un dépôt GitHub → onglet *Actions* → « Compiler l'APK Android » → *Run workflow*. L'APK est dans *Artifacts* (`ERP_Atelier_apk`) après quelques minutes.

**Avec Android Studio** : `File > Open` → dossier `android` (laissez le dossier parent à sa place), Internet requis pour la synchronisation Gradle, puis `Build > Build APK(s)`. Fichier : `app/build/outputs/apk/debug/app-debug.apk`.

## Installer
Copiez `app-debug.apk` sur le téléphone, ouvrez-le, autorisez « Sources inconnues » si demandé.

## Données et sauvegardes
La base est dans le stockage privé de l'application (désinstaller l'application efface les données). Des sauvegardes automatiques sont créées toutes les 6 h dans l'application ; utilisez le menu **Sauvegarde / Restauration** pour en créer une avant toute mise à jour importante.
