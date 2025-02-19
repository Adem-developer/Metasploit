# Cahier des Charges Technique – DeepFake Voice Hijack


## **1. Introduction**

Ce document définit le cahier des charges technique pour le développement du projet "DeepFake Voice Hijack", qui consiste à intercepter, modifier et réinjecter des messages vocaux sur des plateformes comme **WhatsApp Web ou Discord**. Le projet sera réalisé par une équipe de **trois développeurs** et sera basé sur **Metasploit (Ruby), Docker et des outils d’IA vocale**.

---

## **2. Objectifs Techniques**

✅ Intercepter des fichiers audio en transit sur un réseau local.
✅ Modifier le message capturé en utilisant une IA deepfake.
✅ Réinjecter le message modifié dans la conversation.
✅ Automatiser le processus via un module Metasploit en Ruby.
✅ Conteneuriser l’environnement de travail avec Docker.

---

## **3. Répartition des Rôles et Responsabilités**

| **Développeur** | **Responsabilités** |
| --- | --- |
| **Dev 1 - Capture & Interception** | Développer le module Metasploit en Ruby pour capturer les fichiers audio sur WhatsApp Web/Discord. Mettre en place **Wireshark/TShark** pour analyser les paquets. Intégrer **Mitmproxy** pour intercepter et détourner les fichiers. |
| **Dev 2 - Deepfake & Transformation Audio** | Mettre en place **l’API ElevenLabs / Vall-E / RVC** pour générer un deepfake vocal. Utiliser **FFmpeg + OpenCV Audio** pour modifier les fréquences et pitch des fichiers capturés. Gérer l’entraînement et l’optimisation du modèle vocal. |
| **Dev 3 - Réinjection & Automatisation** | Développer le script Ruby pour **réinjecter le fichier modifié** dans la conversation via Mitmproxy. Conteneuriser l’ensemble du projet avec **Docker**. Intégrer un **workflow d’attaque automatisé** avec Metasploit. |

---

## **4. Architecture Technique**

### **🖥️ Environnement de Développement**

- **Docker** : Conteneurisation de l’environnement Metasploit + Mitmproxy.
- **Metasploit Framework (Ruby)** : Développement du module d’attaque.
- **Python (Scapy + mitmproxy API)** : Analyse et modification des paquets réseau.
- **Wireshark / TShark** : Interception et capture des fichiers vocaux.
- **FFmpeg + OpenCV Audio** : Modification et encodage des fichiers audio.
- **API ElevenLabs / Vall-E / RVC** : Clonage et transformation des voix en deepfake.

### **🛠️ Dépendances et Librairies**

- **Docker Compose** : Gestion des services (Mitmproxy, Metasploit, IA vocale).
- **Ruby Gems : Metasploit, Rex, Net/HTTP** pour la communication réseau.
- **Python Packages : Scapy, mitmproxy, OpenCV, FFmpeg-python**.

### **📝 Flux d’Exécution**

1️⃣ **Capture du message vocal**

- Metasploit scanne et intercepte les fichiers vocaux.
- Wireshark/TShark extrait les fichiers audio.

2️⃣ **Modification du message**

- IA transforme la voix et modifie le contenu.
- FFmpeg applique des ajustements de tonalité et d’encodage.

3️⃣ **Réinjection et Attaque**

- Mitmproxy remplace le fichier original par la version modifiée.
- L’utilisateur reçoit un faux message vocal sans s’en rendre compte.

---

## **5. Plan de Développement et Délais**

| **Phase** | **Tâche** | **Responsable** | **Durée Estimée** |
| --- | --- | --- | --- |
| 📌 **Phase 1** | Mise en place de l’environnement Docker | Dev 3 | 1 semaine |
| 📌 **Phase 2** | Développement du module Metasploit pour l’interception | Dev 1 | 2 semaines |
| 📌 **Phase 3** | Implémentation du deepfake vocal et transformation audio | Dev 2 | 3 semaines |
| 📌 **Phase 4** | Automatisation et réinjection des fichiers modifiés | Dev 3 | 2 semaines |
| 📌 **Phase 5** | Tests et démonstration finale | Tous | 1 semaine |

⏳ **Durée totale estimée :** 9 semaines.

---

## **6. Critères de Réussite**

✅ Capture réussie des messages vocaux sur WhatsApp Web/Discord.
✅ Modification réaliste des voix et du contenu des messages.
✅ Réinjection transparente du message falsifié dans la conversation.
✅ Fonctionnement complet sous Docker avec automatisation via Metasploit.
✅ Démonstration en live avec une attaque convaincante en soutenance.

---

## **7. Risques et Solutions**

| **Risque** | **Solution** |
| --- | --- |
| 📉 **Chiffrement des messages vocaux** | Exploitation des fichiers stockés en cache sur le navigateur |
| ⏳ **Temps de latence du deepfake** | Optimisation du modèle IA et pré-génération de certaines voix |
| 🔒 **Détection de l’attaque par la plateforme** | Rotation des proxies et randomisation des injections |
| 🖥️ **Problème de compatibilité OS** | Conteneurisation avec Docker pour uniformiser l’environnement |

---

## **8. Déploiement et Tests**

✅ **Test en local** : Intercepter des messages vocaux dans un environnement de test (machine virtuelle, réseau fermé).
✅ **Test en conditions réelles** : Simulation sur WhatsApp Web / Discord pour vérifier l’efficacité.
✅ **Démonstration live en soutenance** : Transformer la voix d’un camarade en celle du professeur en direct.

---

## **9. Prochaine Étape**

📌 **Début du développement technique** : Installation de l’environnement Docker et des dépendances.
📌 **Répartition des tâches entre les développeurs** et mise en place d’un dépôt Git pour le suivi du projet.
📌 **Planification des tests et démonstration finale**.
