# Projet de Master : Scan et Falsification de Messages Vocaux en Direct

## **1. Introduction**

Les messages vocaux envoyés sur des plateformes comme WhatsApp, Discord et Telegram sont de plus en plus utilisés pour la communication. Cependant, ces messages peuvent être interceptés, modifiés et réinjectés dans une conversation à l'insu des participants.

### **Problématique**

- Les plateformes de messagerie ne vérifient pas l’authenticité des messages vocaux envoyés.
- Avec l’essor des deepfakes vocaux, il devient possible d’usurper une identité et de manipuler des conversations.

📌 **Objectif du projet** :

1. **Scanner un réseau local pour intercepter des messages vocaux en transit**.
2. **Utiliser une IA pour cloner et modifier un message vocal en direct**.
3. **Réinjecter le message deepfake sans que l’expéditeur ou le destinataire ne le détecte**.

## **2. Technologies et Outils Utilisés**

### **Infrastructure & Capture des Données**

✅ **Docker** : Isolation de l’environnement pour exécuter Metasploit et mitmproxy.
✅ **Metasploit (Ruby)** : Interception des paquets réseau contenant des fichiers audio.
✅ **Wireshark / TShark** : Analyse du trafic pour identifier et extraire les fichiers vocaux.
✅ **Mitmproxy** : Attaque Man-in-the-Middle pour détourner et modifier les fichiers audio.

### **Modification et Injection des Messages Vocaux**

✅ **ElevenLabs API / Vall-E / RVC** : Clonage vocal et transformation de voix en deepfake.
✅ **FFmpeg + OpenCV Audio** : Modification de la fréquence et du pitch des fichiers audio.
✅ **Python (Scapy)** : Analyse des paquets réseau et extraction automatique des fichiers audio.

## **3. Comparaison des Cibles Possibles**

| **Application** | **Version Web** | **Facilité d’Interception** | **Protection** | **Difficulté** |
| --- | --- | --- | --- | --- |
| **WhatsApp Web** | ✅ Oui | 📥 Facile (fichiers audio transférés en HTTPs/TLS) | 🔒 Moyen (chiffrement de bout en bout, mais stocké localement) | ⚡ **Facile** |
| **Telegram Web** | ✅ Oui | 📥 Facile (fichiers accessibles sur le client Web) | 🔒 Fort (stocké en local mais accessible) | ⚡ **Moyen** |
| **Discord** | ✅ Oui | 📥 Facile (messages vocaux en fichiers envoyés) | 🔒 Faible (pas de chiffrement E2E) | ⚡ **Très Facile** |
| **Signal** | ❌ Non | ❌ Très difficile | 🔒🔒🔒 Fort (chiffrement strict) | 🚫 Impossible |
| **Messenger** | ✅ Oui | 📥 Facile (messages audio téléchargeables) | 🔒 Moyen | ⚡ **Facile** |

✅ **🎯 Meilleur choix : Discord ou WhatsApp Web (Faciles à intercepter et falsifier).**

## **4. Déroulement du Projet**

### **1️⃣ Scan et Capture des Messages Vocaux**

🔎 **Objectif** : Identifier et extraire les fichiers vocaux envoyés via WhatsApp Web ou Discord.
📌 **Mise en œuvre** :

- Déploiement d’un container Docker contenant Metasploit et mitmproxy.
- Capture des paquets réseau contenant des fichiers **.ogg, .mp3, .wav**.
- Extraction et stockage des fichiers interceptés.

### **2️⃣ Modification et Génération du Deepfake Vocal**

🕵️ **Objectif** : Transformer un message vocal en deepfake et modifier son contenu.
📌 **Mise en œuvre** :

- Extraction de la voix originale pour entraîner un modèle de clonage.
- Modification du contenu du message avec une phrase différente.
- Génération d’un fichier vocal deepfake réaliste.

### **3️⃣ Réinjection et Manipulation du Message Vocal**

🎯 **Objectif** : Renvoyer le message falsifié sans éveiller les soupçons.
📌 **Mise en œuvre** :

- Détournement du fichier original via mitmproxy.
- Injection du fichier modifié dans la conversation cible.
- Vérification que le destinataire reçoit bien le message deepfake.

## **5. Démonstration Immersive**

🎤 **Scénario de démonstration** :
1️⃣ **Scan en direct d’un message vocal envoyé sur WhatsApp Web ou Discord**.
2️⃣ **Interception et modification du fichier vocal capturé**.
3️⃣ **Réinjection du message deepfake dans la conversation en direct**.
4️⃣ **Le destinataire entend un faux message vocal, sans se douter qu’il a été altéré**.

📌 **Matériel requis** :
✅ PC avec Docker, Metasploit et Wireshark.
✅ Téléphone avec WhatsApp Web ou Discord connecté au même Wi-Fi.
✅ Enceinte Bluetooth pour diffuser le message modifié devant le jury.

## **6. Impact et Sécurité**

✅ **Démonstration impressionnante et réaliste** : L’attaque montre comment les deepfakes vocaux peuvent manipuler des conversations en ligne.
✅ **Reproductible dans un environnement de test** : Tout est faisable avec un PC et une connexion réseau.
✅ **Application réelle en cybersécurité** : Permet de comprendre les failles des communications vocales et les risques liés aux deepfakes.

[**Cahier des Charges Technique – DeepFake Voice Hijack**](https://www.notion.so/Cahier-des-Charges-Technique-DeepFake-Voice-Hijack-19b155b12bcc80939fc2f15b8e5a1555?pvs=21)