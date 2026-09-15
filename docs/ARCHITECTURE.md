# Architecture Technique - Projet Bot IA Tinder

## 1. Stack Technique
- **Langage :** Python (ou Node.js) - *À définir selon la préférence du développeur*.
- **Automatisation Web :** Playwright (interaction avec le DOM via sélecteurs CSS/XPath).
- **IA :** API LLM (ex: OpenAI GPT-4o-mini ou Anthropic Claude 3 Haiku).
- **Configuration :** Variables d'environnement (`.env`) pour les clés API et le contexte utilisateur.

## 2. Stratégie de Connexion Navigateur
Au lieu de lancer un nouveau navigateur, le script utilisera la méthode `connect_over_cdp` (Chrome DevTools Protocol) de Playwright.
- **Prérequis :** Lancer Chrome avec le flag `--remote-debugging-port=9222`.
- **Avantage :** Partage des cookies, pas de déconnexion, contournement des protections de login.

## 3. Structure du Projet (Pattern Modulaire)


/tinder-bot-ia
│
├── /src
│   ├── /scraper         # Fonctions Playwright (get_conversations, read_messages, send_message)
│   ├── /ai              # Appels à l'API LLM et gestion des prompts
│   ├── /utils           # Fonctions anti-ban (sleep aléatoire, simulate_typing)
│   ├── /config          # Définition des Personas et chargement des configs
│   └── main.py          # Orchestrateur : point d'entrée du script
│
├── .env                 # Clé API LLM, Port du navigateur (ex: 9222)
├── system_prompt.txt    # Contexte perso (Ma bio, mes passions)
├── audit.md             # Doc fonctionnelle
├── architecture.md      # Doc technique
└── requirements.txt     # Dépendances (playwright, openai, python-dotenv...)