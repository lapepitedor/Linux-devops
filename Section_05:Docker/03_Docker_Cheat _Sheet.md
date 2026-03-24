#  Docker Cheat Sheet (Grundlegende Befehle)

## 📦 Image erstellen

```bash
docker build -t my-image .
```
Erstellt ein Docker-Image aus einem Dockerfile.


## ▶️ Container starten

```bash
docker run -d -p 8080:80 nginx
```
Startet einen Container im Hintergrund und mapped Port 8080 (Host) auf Port 80 (Container).

## ⛔ Container stoppen

```bash
docker stop <container_id>
```
Stoppt einen laufenden Container.


## 📋 Laufende Container anzeigen

```bash
docker ps
```
Zeigt alle aktiven Container.


## 📦 Alle Images anzeigen

```bash
docker images
```
Listet alle lokal verfügbaren Images auf.


## 🔐 Bei Docker Hub anmelden

```bash
docker login
```
Authentifizierung bei Docker Hub.

## 🏷️ Image taggen

```bash
docker tag my-image username/my-image:latest
```
Bereitet ein Image für den Upload vor.


## ☁️ Image hochladen
```bash
docker push username/my-image
```
Lädt ein Image zu Docker Hub hoch.


## 🧩 Mehrere Container starten (Docker Compose)

```bash
docker compose up -d
```
Startet alle Services aus der docker-compose.yml.

## 🧹 Alles stoppen & entfernen

```bash
docker compose down
```
Stoppt und entfernt alle Container, Netzwerke und Ressourcen.


## 💡 Hinweis
Ersetze <container_id> durch die tatsächliche ID oder den Namen des Containers.

## 🧠 Zusammenfassung
Images = Vorlage
Container = laufende Instanz
Docker Compose = mehrere Container orchestrieren
