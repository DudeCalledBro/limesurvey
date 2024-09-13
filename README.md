# Limesurvey (Docker)

[![CI](https://github.com/DudeCalledBro/limesurvey/actions/workflows/ci.yml/badge.svg)](https://github.com/DudeCalledBro/limesurvey/actions/workflows/ci.yml)

Im Rahmen einer Projektarbeit war es notwendig eine Umfrage zu erstellen. Ich habe mich aus verschiedenen Gründen gegen eine Lösung in der Cloud entschieden. Ich möchte die vollständige Kontrolle über meine Daten und die Daten meiner Umfrageteilnehmer haben (z.B. Weitergabe von Anmeldedaten oder Ergebnissen). Deshalb habe ich mich für [Limesurvey](https://github.com/LimeSurvey/LimeSurvey) entschieden - einer OpenSource Umfrageplattform. Das Deployment der Software wird mithilfe von Ansible und Docker Compose realisiert.

## Voraussetzungen

- Für dieses Deployment muss Ansible auf dem Controller installiert sein (e.g. `pip3 install ansible`)
- Für dieses Deployment muss Docker (+DockerCompose Plugin V2) auf dem Zielsystem installiert werden. Die Installation habe ich bereits in meiner [Docker-Rolle]((https://github.com/DudeCalledBro/ansible-role-docker)) automatisiert.

## Installation

1. Zuerst muss das Inventory und die Variablen angepasst werden. Dazu sind folgende Schritte notwendig:

    - Ansible Inventory erstellen: `cp example.inventory.yml inventory.yml`
    - Ansible Variablen erstellen: `cp example.config.yml config.yml`

> **Wichtig!** Bitte erstelle ein TLS Zertifikat und hinterlege dies in den Variablen `httpd_docker_key` und  `httpd_docker_crt`.

2. Danach kann das Playbook zum Rollout der Software gestartet werden:

    ```bash
    ansible-playbook play-survey.yml
    ```

## Lizenz

Copyright © 2024 Niclas Spreng

Licensed under the [MIT license](LICENSE).
