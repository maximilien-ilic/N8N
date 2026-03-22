# 🤖 N8N AI Automation

Projet d'automatisation locale utilisant **n8n**, **Ollama**, et l'**API Claude** 
pour gérer des outils via un agent IA — boîte mail, Pull Requests GitHub, et plus.

## 🏗️ Architecture

Le projet contient deux workflows principaux :

### 1. 📧 Récapitulatif d'emails quotidien
Analyse automatiquement tes emails du jour à 18h et envoie un résumé 
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
docker run -d \
  --name n8n \
  -p 5678:5678 \
  -v n8n_data:/home/node/.n8n \
  n8nio/n8n:latest
```

### 2. Lancer Ollama
```bash
# Définir OLLAMA_HOST pour Docker
$env:OLLAMA_HOST = "0.0.0.0"  # Windows PowerShell

# Télécharger un modèle
ollama pull mistral
```

### 3. Accéder à n8n
Ouvre [http://localhost:5678](http://localhost:5678)

## 🔑 Configuration des credentials

Dans n8n : **Settings → Credentials → Add Credential**

| Service | Champs requis |
|---------|--------------|
| **Ollama** | Base URL : `http://host.docker.internal:11434` |
| **Gmail OAuth2** | Client ID + Client Secret (Google Cloud Console) |
| **Discord Bot** | Bot Token (Discord Developer Portal) |
| **DeepL** | API Key  |
| **Claude API** | API Key (console.anthropic.com) |
| **GitHub** | Access Token + Webhook Secret |

## 📋 Workflows

### 📧 Email Daily Recap
- Se déclenche automatiquement à **16h30** chaque jour
- Récupère tous les emails du jour depuis Gmail
- Traduit le contenu en français via DeepL
- Génère un résumé avec priorités via Ollama
- Envoie le récap en **DM Discord**

### 🔐 PR Security Audit  
- Se déclenche à chaque **Pull Request** GitHub
- Analyse les diffs de code
- Détecte les vulnérabilités (XSS, injection, secrets exposés...)
- Génère un rapport JSON via Claude API
- Poste un commentaire directement sur la PR

## 🛠️ Stack technique

- **[n8n](https://n8n.io/)** — Orchestration des workflows
- **[Ollama](https://ollama.com/)** — LLM local (Mistral, LLaMA...)
- **[Claude API](https://anthropic.com)** — Analyse de sécurité avancée
- **[DeepL API](https://deepl.com)** — Traduction automatique
- **Docker** — Containerisation

## ⚠️ Notes importantes

- n8n doit être **actif** à 18h pour le déclenchement automatique
- Ollama doit tourner avec `OLLAMA_HOST=0.0.0.0` pour être accessible depuis Docker

