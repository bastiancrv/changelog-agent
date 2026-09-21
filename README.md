# Changelog Agent

Agent IA qui lit l'historique git d'un dépôt **local** et génère un `CHANGELOG.md` propre avec Gemini.

## Prérequis
- Python 3.10+ (ou Docker)
- git
- Une clé API Gemini gratuite : https://aistudio.google.com/apikey

## Installation avec Odin
```bash
odin install changelog-agent
odin keys set GEMINI_API_KEY
```

## Utilisation
```bash
# Depuis le dossier d'un dépôt git
odin run changelog-agent --task "Changelog en anglais"
odin run changelog-agent --dry-run
```

## Utilisation sans Odin
```bash
pip install -r requirements.txt
export GEMINI_API_KEY=ta_cle
python agent.py --dry-run
python agent.py --commits 10 --task "Changelog en anglais"
```

## Options
| Option | Défaut | Rôle |
|---|---|---|
| `--task` | "Génère un changelog" | Consigne donnée au LLM |
| `--commits` | 30 | Nombre de commits lus |
| `--output` | CHANGELOG.md | Fichier généré |
| `--dry-run` | - | Affiche le plan sans rien exécuter |

## Permissions demandées
- `internet` : appel à l'API Gemini
- `read_files` : lecture du dépôt git
- `write_files` : écriture du CHANGELOG.md
- `execute_code` : exécution de `git log`

## Exemples de tâches
- "Changelog en anglais"
- "Résume uniquement les corrections de bugs"
- "Ton formel, pour une release note client"
