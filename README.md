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
![Architecture Chatbox]([<img width="578" height="397" alt="chatbox" src="https://github.com/user-attachments/assets/6248e589-678c-49ea-82dc-508f027b666d" />](https://private-user-images.githubusercontent.com/159456382/567433188-cab2fe65-64f1-4a02-9d63-b785e6d386ea.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzQyMDAzOTMsIm5iZiI6MTc3NDIwMDA5MywicGF0aCI6Ii8xNTk0NTYzODIvNTY3NDMzMTg4LWNhYjJmZTY1LTY0ZjEtNGEwMi05ZDYzLWI3ODVlNmQzODZlYS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwMzIyJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDMyMlQxNzIxMzNaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1mMjQ0YTMyYTIyNjBkM2FlNjY0N2JlYTAyZDA0M2JmYmE2MGNkNmY2OGIyY2U1MDRhYWE3N2MzYjViNDc1MmY4JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.eUaNeN_FpVyQcqL9fXJRKNO84QeLzx6cvo1RjfBrrgg))

![Architecture PR \ Email]([lien_image_2](https://private-user-images.githubusercontent.com/159456382/567433191-d0aa9fe7-ea2a-439c-9622-3afdc11748e7.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzQyMDAzOTMsIm5iZiI6MTc3NDIwMDA5MywicGF0aCI6Ii8xNTk0NTYzODIvNTY3NDMzMTkxLWQwYWE5ZmU3LWVhMmEtNDM5Yy05NjIyLTNhZmRjMTE3NDhlNy5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwMzIyJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDMyMlQxNzIxMzNaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0zMzc3ZDRiOTA1NmFlZjQ4Mzc1NTk3MTdkZjFlMDYwNDIyNTQyNGZiYTQ0MWVlYmFiNzM5NTBiYTdmMzVkZThjJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.94hsGSBlLEbxBq7mwdUMRrbXaYxcQ03vNVCGFXXIh7g))

### Résultats
![Résultat PR Audit]([lien_image_3]([https://github.com/maximilien-ilic/N8N/issues/1)](https://private-user-images.githubusercontent.com/159456382/567433189-bb6d29b8-00de-4665-9150-fffeb1083a0d.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzQyMDAzOTMsIm5iZiI6MTc3NDIwMDA5MywicGF0aCI6Ii8xNTk0NTYzODIvNTY3NDMzMTg5LWJiNmQyOWI4LTAwZGUtNDY2NS05MTUwLWZmZmViMTA4M2EwZC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwMzIyJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDMyMlQxNzIxMzNaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0zMTYwMWQ4YjNjYTdiZThkMTRlYzNkMzIzZDIxOTcyMzllMDQ2NDUxNmFlNjU2NTY1Y2UzYWZiODQ4Yzk2MjM0JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.ga18CmEZPHtT_cd0KX_LNYNw75yeiK2fx0FTULZvh9k))
![Résultat Discord DM]([lien_image_4](https://private-user-images.githubusercontent.com/159456382/567433189-bb6d29b8-00de-4665-9150-fffeb1083a0d.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzQyMDAzOTMsIm5iZiI6MTc3NDIwMDA5MywicGF0aCI6Ii8xNTk0NTYzODIvNTY3NDMzMTg5LWJiNmQyOWI4LTAwZGUtNDY2NS05MTUwLWZmZmViMTA4M2EwZC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwMzIyJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDMyMlQxNzIxMzNaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0zMTYwMWQ4YjNjYTdiZThkMTRlYzNkMzIzZDIxOTcyMzllMDQ2NDUxNmFlNjU2NTY1Y2UzYWZiODQ4Yzk2MjM0JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.ga18CmEZPHtT_cd0KX_LNYNw75yeiK2fx0FTULZvh9k))

## 🚀 Installation

### Prérequis
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Ollama](https://ollama.com/) installé en local
- Un compte [Discord Developer](https://discord.com/developers)
- Un compte [Google Cloud](https://console.cloud.google.com) (Gmail API)
- Un compte [DeepL API](https://www.deepl.com/fr/pro-api) (gratuit)

### 1. Lancer n8n avec Docker
```bash
