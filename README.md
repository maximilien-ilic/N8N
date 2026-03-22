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
![Architecture Email](<img width="578" height="397" alt="chatbox" src="https://github.com/user-attachments/assets/6248e589-678c-49ea-82dc-508f027b666d" />)

![Architecture PR](lien_image_2)

### Résultats
![Résultat PR Audit](lien_image_3)
![Résultat Discord DM](lien_image_4)

## 🚀 Installation

### Prérequis
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Ollama](https://ollama.com/) installé en local
- Un compte [Discord Developer](https://discord.com/developers)
- Un compte [Google Cloud](https://console.cloud.google.com) (Gmail API)
- Un compte [DeepL API](https://www.deepl.com/fr/pro-api) (gratuit)

### 1. Lancer n8n avec Docker
```bash
