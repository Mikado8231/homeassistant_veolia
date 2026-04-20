<a href=""><img src="https://raw.githubusercontent.com/Jezza34000/homeassistant_veolia/main/images/veolialogo.png"></a>

[![GitHub Release][releases-shield]][releases]
[![HACS Default](https://img.shields.io/badge/HACS-Default-blue.svg?style=for-the-badge)](https://hacs.xyz/docs/faq/custom_repositories)

> [!IMPORTANT]
>
> ## Message important concernant l’avenir de cette intégration :
>
> Ayant récemment déménagé dans une zone non couverte par Veolia, je n’ai désormais plus accès à un compte Veolia actif.
>
> Cela rend difficile le maintien, les tests et l’évolution du projet dans de bonnes conditions.
> Je continuerai autant que possible à assurer le support, les corrections de bugs et la maintenance générale.
>
> Toutefois, pour garantir la pérennité de l’intégration et permettre son évolution, je recherche un ou plusieurs développeurs motivés pouvant m’aider à la faire avancer, tester les nouveautés et contribuer aux futures améliorations.
>
> Si vous êtes intéressé(e) pour rejoindre le développement ou simplement donner un coup de main sur certaines fonctionnalités, n’hésitez pas à ouvrir une issue ou à me contacter. Toute contribution, même modeste, est la bienvenue.
>
> Merci d’avance pour votre aide et votre engagement ! 💙

> ### UNIQUEMENT compatible avec le nouveau site de Veolia : https://www.eau.veolia.fr/
>
> ### N'est PAS compatible avec les sous domaines suivant : https://service.eau.veolia.fr & https://espace-client.vedif.eau.veolia.fr

---

<p align="center">
  <a href="https://www.buymeacoffee.com/jezza" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-yellow.png" alt="Buy Me A Coffee" height="80" width="320"></a>
</p>

## Informations disponibles

**Cette intégration configurera les plateformes suivantes.**

| Plateforme      | Description                                         |
| --------------- | --------------------------------------------------- |
| `sensor`        | Affiche les informations de l'API Veolia            |
| `switch`        | Switch d'activation/désactivation des alertes conso |
| `text`          | Saisie des valeurs de réglages des alertes          |
| `binary_sensor` | Affiche l'états des alertes conso                   |

### Données disponibles

- Consommation d'eau (journalière, mensuelle)
- Index de consommation d'eau
- Seuils d'alertes de consommation d'eau
- Etat des alertes de consommation d'eau
- Date de la dernière relève de consommation d'eau

> #### **Note :** Les données de l'intégration sont mises à jour toutes les 12h.

### Capteurs :

<a href=""><img src="https://raw.githubusercontent.com/Jezza34000/homeassistant_veolia/main/images/capteurs.png"></a>

### Contrôles :

<a href=""><img src="https://raw.githubusercontent.com/Jezza34000/homeassistant_veolia/main/images/controles.png"></a>

### Configuration des alertes

L'intégration Veolia permet de configurer des alertes de consommation d'eau pour surveiller votre utilisation
quotidienne et mensuelle, et même pour détecter une fuite si vous n'êtes pas chez vous.

Les alertes sont activées ou désactivées, en renseignant les champs seuils d'alertes (0 = désactivé, >0 = activé)

Il existe 3 types d'alertes :

- Alerte journalière
  - L'alerte journalière est une alerte qui se déclenche si votre consommation d'eau quotidienne dépasse un certain seuil **cette valeur est en litre, le minimum est de 100 litres.**
- Alerte mensuelle
  - L'alerte mensuelle est une alerte qui se déclenche si votre consommation d'eau mensuelle dépasse un certain seuil **cette valeur est en metre cubes, le minimum est de 1m3**.
- Alerte logement "vide"
  - L'alerte logement vide est une alerte qui se déclenche si une consommation d'eau est détectée alors que vous n'êtes pas chez vous.

Informations supplémentaires :

> Les notifications d'alerte sont envoyées par Veolia directement par email et par SMS (aux coordonnées de contact renseigné dans votre compte Veolia).

> Il n'est pas possible de désactiver les notifications d'alerte par email, mais vous pouvez choisir d'activer ou pas les notifications par SMS, uniquement si un seuil est renseigné.

### Visualisation des données de consommation

L'intégration Veolia permet de visualiser les données de consommation d'eau en natif dans Home Assistant. Elle re-télécharge l'historique du mois en cours depuis Véolia et met à jour la base de données Home Assistant.

#### 1. Ajout au dashboard energie de Home Assistant

<a href=""><img src="https://raw.githubusercontent.com/Jezza34000/homeassistant_veolia/main/images/dashboard_eau.png"></a>

Pour ajouter la consommation d'eau au dashboard energie de Home Assistant, allez `Energie` -> 3 petits points en haut à droite -> `Configuration de l'energie` -> `Ajouter une source d'eau` -> Dans le champ `Consommation d'eau` choissisez `sensor.veolia_index_compteur`

<a href=""><img src="https://raw.githubusercontent.com/Jezza34000/homeassistant_veolia/main/images/consommation.png"></a>

#### 2. Ajout d'une carte de consommation d'eau journalière

<a href=""><img src="https://raw.githubusercontent.com/Jezza34000/homeassistant_veolia/main/images/historique.png"></a>

Pour ajouter la carte de consommation d'eau journalière, sur votre dashboard, cliquez sur `Ajouter une carte` puis selectionner `Graphique des statistiques` et choissisez l'entité `sensor.veolia_consommation_journaliere`, configurer la carte comme l'exemple ci-dessous :

<a href=""><img src="https://raw.githubusercontent.com/Jezza34000/homeassistant_veolia/main/images/config_carte.png"></a>

> #### **Note :** La carte Graphique des statistiques ne fonctionnera qu'avec le sensor `sensor.veolia_consommation_journaliere`

## Installation

### Via [HACS](https://hacs.xyz/) (recommandé)

**Cliquez ici:**

[![Open your Home Assistant instance and open the repository inside the Home Assistant Community Store.](https://my.home-assistant.io/badges/hacs_repository.svg?style=flat-square)](https://my.home-assistant.io/redirect/hacs_repository/?owner=Jezza34000&repository=homeassistant_veolia&category=integration)

**ou suivez ces étapes:**

1. Ouvrez HACS (Home Assistant Community Store)
2. Cliquez sur les trois points en haut à droite
3. Cliquez sur `Dépôts personnalisées`
4. Dans le champ `Dépôt` entrez https://github.com/Jezza34000/homeassistant_veolia/
5. Dans le champ `Type` sélectionnez `Intégration`
6. Cliquez sur `Ajouter`
7. Recherchez `Veolia` dans la liste des intégrations
8. Installez l'intégration
9. Redémarrez Home Assistant
10. Ouvrez paramètres -> intégrations -> ajouter une intégration -> recherchez `Veolia`
11. Suivez les instructions pour configurer l'intégration

### Manuellement

1. Copiez le dossier `custom_components/veolia` dans le dossier `custom_components` de votre configuration Home Assistant.
2. Redémarrez Home Assistant
3. Ouvrez paramètres -> intégrations -> ajouter une intégration -> recherchez `Veolia`
4. Suivez les instructions pour configurer l'intégration

## Bug et demande de fonctionnalités

- [Cliquez-ici](https://github.com/Jezza34000/homeassistant_veolia/issues)

## API Veolia

Cette intégration utilise mon client API Veolia disponible ici : [veolia-api](https://github.com/Jezza34000/veolia-api).

## Credits

Le modèle de code de cette intégration à principalement été tiré du blueprint de @Ludeeus. Merci à lui pour son travail.

[![GitHub Activity][commits-shield]][commits]
[![License][license-shield]](LICENSE)
![Project Maintenance][maintenance-shield]

---

<!---->

[hacsbadge]: https://img.shields.io/badge/HACS-Custom-orange.svg?style=for-the-badge
[hacs]: https://hacs.xyz
[releases-shield]: https://img.shields.io/github/v/release/Jezza34000/homeassistant_veolia.svg?style=for-the-badge
[releases]: https://github.com/Jezza34000/homeassistant_veolia/releases
[commits-shield]: https://img.shields.io/github/commit-activity/y/ludeeus/integration_blueprint.svg?style=for-the-badge
[commits]: https://github.com/Jezza34000/homeassistant_veolia/commits/main
[license-shield]: https://img.shields.io/github/license/ludeeus/integration_blueprint.svg?style=for-the-badge
[maintenance-shield]: https://img.shields.io/badge/maintainer-%20%40Jezza34000-blue.svg?style=for-the-badge
[sensorsimg]: images/entities.png
