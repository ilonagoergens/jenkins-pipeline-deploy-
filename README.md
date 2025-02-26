# Jenkins Pipeline für EC2 Deployment

Dieses Repository enthält eine Jenkins-Pipeline für den Build und das Deployment einer React-Anwendung auf einen EC2-Server. Die Pipeline umfasst das Klonen des Repositories, das Installieren der notwendigen Node.js-Abhängigkeiten, das Erstellen der Anwendung und das Deployment auf einen EC2-Server.

## Voraussetzungen

- **Jenkins**: Du benötigst einen funktionierenden Jenkins-Server, um diese Pipeline auszuführen.
- **EC2-Instanz**: Eine EC2-Instanz, die mit `nginx` konfiguriert ist und über SSH zugänglich ist.
- **GitHub-Repository**: Dein Code muss auf GitHub gehostet werden.
- **SSH-Schlüssel**: Der Jenkins-Server benötigt Zugriff auf die EC2-Instanz über SSH. Stelle sicher, dass du den richtigen SSH-Schlüssel hast und dass er in Jenkins als `jenkins-ec2-key` hinterlegt ist.

## Einrichtung

### 1. Jenkins installieren

Stelle sicher, dass Jenkins auf deinem Server installiert ist. Weitere Informationen findest du in der [Jenkins Dokumentation](https://www.jenkins.io/doc/).

### 2. GitHub-Repository verbinden

- Erstelle ein GitHub-Repository und lade dein Projekt hoch.
- Füge das Repository zu Jenkins hinzu, sodass es bei jedem Commit oder auf Abruf gebaut werden kann.

### 3. SSH-Schlüssel konfigurieren

- Stelle sicher, dass Jenkins auf deiner EC2-Instanz per SSH zugreifen kann. Du kannst den öffentlichen SSH-Schlüssel von Jenkins zu deiner EC2-Instanz hinzufügen.

### 4. Jenkins Pipeline

Das Jenkinsfile, das sich im Root-Verzeichnis dieses Repositories befindet, definiert die Schritte für den Build und das Deployment der Anwendung. Es führt die folgenden Aufgaben aus:

- Klonen des Git-Repositories
- Installieren von Node.js
- Installieren der Abhängigkeiten mit `npm install`
- Erstellen der Anwendung mit `npm run build`
- Deployment der Anwendung auf die EC2-Instanz
- Neustart des `nginx`-Servers auf der EC2-Instanz

## Deployment auf EC2

- **EC2_HOST**: Die IP-Adresse deiner EC2-Instanz.
- **EC2_USER**: Der Benutzername auf der EC2-Instanz (meistens `ubuntu`).
- **DEPLOY_PATH**: Der Pfad auf der EC2-Instanz, in dem die Anwendung gespeichert wird (z. B. `/home/ubuntu/app2`).

### Nginx

Die Pipeline sorgt dafür, dass `nginx` auf der EC2-Instanz installiert wird und die Anwendung nach dem Deployment mit einem Neustart von `nginx` verfügbar ist.

## Fazit

Diese Jenkins-Pipeline automatisiert den gesamten Prozess, um eine React-Anwendung auf einer EC2-Instanz zu bauen und bereitzustellen. Sie spart Zeit und reduziert Fehler, die bei manuellen Deployments auftreten können.

