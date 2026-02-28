# Yoris

**Un assistant de bureau intelligent qui *comprend* vos fichiers.**

[Fonctionnalités](#fonctionnalités) • [Démo](#démo) • [Installation](#installation) • [Utilisation](#utilisation) • [Architecture](#architecture) • [Roadmap](#roadmap)

---

## Le problème

On a tous des centaines (voire des milliers) de fichiers éparpillés entre le Bureau, les Téléchargements et les Documents. Les retrouver, c'est une galère : on ne se souvient jamais du nom exact, et la recherche classique par nom de fichier ne suffit pas.

**Yoris résout ça.** Au lieu de chercher par nom, vous décrivez ce que vous cherchez en langage naturel, et l'IA retrouve les bons fichiers en analysant leur contenu.

## Fonctionnalités

**Recherche sémantique** — Dites "trouve mes cours de géopolitique" et Yoris retrouve `Les États-Unis et le monde.pdf`, même si le nom ne contient pas le mot "géopolitique". Il lit le contenu des PDF, Word et fichiers texte pour comprendre de quoi il s'agit.

**Organisation automatique** — Un dossier Téléchargements avec 2000 fichiers en vrac ? Yoris les trie en catégories (Documents, Images, Vidéos...) ou par thème, en une seule commande.

**Tri en entonnoir** — Pour les gros dossiers, Yoris utilise un pipeline en 3 étapes pour être rapide sans gaspiller de tokens IA :
1. **Extension** — tri instantané par type de fichier
2. **Nom** — analyse IA légère sur les noms
3. **Contenu** — analyse IA profonde uniquement sur les fichiers restants

**Détection de doublons** — Identifie les fichiers identiques par hash et les images similaires par comparaison perceptuelle (imagehash).

**Déplacement en masse** — "Déplace tous les résultats dans Documents/Cours" en une commande. Avec historique d'annulation.

**Compression / extraction** — Gère les archives ZIP, RAR, etc.

## Démo

| Vous dites | Yoris comprend |
|---|---|
| "Trouve mes cours de géopolitique" | `Les États-Unis et le monde.pdf`, `Relations internationales.docx` |
| "Organise mes téléchargements" | Trie 2000 fichiers en dossiers Documents, Images, Vidéos... |
| "Cherche mes factures de 2024" | Retrouve les PDFs de factures même si elles s'appellent `scan_001.pdf` |
| "Trouve les doublons dans Images" | Détecte les fichiers identiques et les images visuellement similaires |

## Installation

### Télécharger l'app (recommandé)

1. Allez dans [Releases](https://github.com/gabinson45/Yoris/releases)
2. Téléchargez `Yoris.app` (Mac) 
3. Lancez l'application
4. Configurez votre clé API Gemini (voir ci-dessous)

### Depuis les sources
```bash
git clone https://github.com/gabinson45/Yoris.git
cd Yoris

python -m venv venv
source venv/bin/activate  # Mac/Linux
# venv\Scripts\activate   # Windows

pip install -r requirements.txt
python run_app.py
```

### Clé API Gemini (gratuite)

Yoris utilise l'API Gemini de Google. Pour obtenir une clé :

1. Rendez-vous sur [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Créez une clé API
3. Collez-la dans le fichier `config.txt` :
