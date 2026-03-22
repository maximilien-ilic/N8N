# 🤖 N8N AI Automation

Projet d'automatisation locale utilisant **n8n**, **Ollama**, et l'**API Claude** 
pour gérer des outils via un agent IA — boîte mail, Pull Requests GitHub, et plus.

## 🏗️ Architecture

Le projet contient deux workflows principaux :

### 1. 📧 Récapitulatif d'emails quotidien
Analyse automatiquement tes emails du jour à 16h30 et envoie un résumé 
structuré en DM Discord.

**Workflow :**
`Schedule Trigger (18h)` → `Gmail` → `DeepL` → `AI Agent (Ollama)` → `Discord DM`

### 2. 🔐 Audit de sécurité de Pull Requests
Analyse automatiquement les diffs de Pull Requests GitHub et génère 
un rapport de sécurité complet.

**Workflow :**
`GitHub Webhook` → `Filtre fichiers` → `AI Agent (Claude)` → `Commentaire PR`

## 📸 Aperçu

### Workflows n8n
![Architecture Chatbox](https://github.com/user-attachments/assets/6248e589-678c-49ea-82dc-508f027b666d)
![Architecture PR / Email](https://github.com/user-attachments/assets/d0aa9fe7-ea2a-439c-9622-3afdc11748e7)

### Résultats
![Résultat PR Audit](https://github.com/user-attachments/assets/f12a419c-0a59-4bc3-b821-9a5e6d0c9483)
![Résultat Discord DM](https://github.com/user-attachments/assets/bb6d29b8-00de-4665-9150-fffeb1083a0d)
## 🚀 Installation

### Prérequis
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Ollama](https://ollama.com/) installé en local
- Un compte [Discord Developer](https://discord.com/developers)
- Un compte [Google Cloud](https://console.cloud.google.com) (Gmail API)
- Un compte [DeepL API](https://www.deepl.com/fr/pro-api) (gratuit)

### 1. Lancer n8n avec Docker
```bash
