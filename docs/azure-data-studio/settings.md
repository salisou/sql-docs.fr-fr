---
title: Paramètres de l’utilisateur et de l’espace de travail
titleSuffix: Azure Data Studio
description: Comment personnaliser Azure Data Studio en modifiant les paramètres de l’utilisateur et de l’espace de travail.
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: a874aaf9ec136ff9ea27cbeaa92011a07f3718c7
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "79287063"
---
# <a name="modify-user-and-workspace-settings"></a>Modifier les paramètres de l’utilisateur et de l’espace de travail

Il est facile de configurer [!INCLUDE[name-sos](../includes/name-sos-short.md)] à votre convenance par le biais de paramètres. Presque toutes les parties de l’éditeur de [!INCLUDE[name-sos](../includes/name-sos-short.md)], de l’interface utilisateur et du comportement fonctionnel disposent d’options que vous pouvez modifier.

[!INCLUDE[name-sos](../includes/name-sos-short.md)] fournit deux étendues différentes pour les paramètres :

* **Utilisateur** Ces paramètres s’appliquent globalement à toute instance de [!INCLUDE[name-sos](../includes/name-sos-short.md)] que vous ouvrez.
* **Espace de travail** Les paramètres de l’espace de travail sont des paramètres spécifiques à un dossier sur votre ordinateur et sont disponibles uniquement lorsque le dossier est ouvert dans la barre latérale de l’Explorateur. Les paramètres définis sur cette étendue remplacent l’étendue Utilisateur.

## <a name="creating-user-and-workspace-settings"></a>Création des paramètres de l’utilisateur et de l’espace de travail

La commande de menu **Fichier** > **Préférences** > **Paramètres** (**Code** > **Préférences** > **Paramètres** sur Mac) fournit le point d’entrée pour configurer les paramètres de l’utilisateur et de l’espace de travail. Une liste de paramètres par défaut vous est fournie. Copiez les paramètres que vous souhaitez modifier dans le fichier `settings.json` approprié. Les onglets à droite vous permettent de basculer rapidement entre les fichiers de paramètres de l’utilisateur et de l’espace de travail.

Vous pouvez également ouvrir les paramètres de l’utilisateur et de l’espace de travail à partir de la **palette de commandes** (**Ctrl+Maj+P**) avec **Préférences : Ouvrir les paramètres utilisateur** et **Préférences : Ouvrir les paramètres d’espace de travail** ou utiliser le raccourci clavier (**Ctrl +,** ).

L’exemple suivant désactive les numéros de ligne dans l’éditeur et configure les lignes de code pour qu’elles soient indentées automatiquement.

![Exemples de paramètres](media/settings/sample-settings.png)

Les modifications apportées aux paramètres sont rechargées par [!INCLUDE[name-sos](../includes/name-sos-short.md)] après l’enregistrement du fichier `settings.json` modifié.

>**Remarque :** Les paramètres d’espace de travail sont utiles pour partager des paramètres spécifiques au projet dans une équipe.

## <a name="settings-file-locations"></a>Emplacements des fichiers de paramètres

En fonction de votre plateforme, le fichier de paramètres utilisateur se trouve ici :

* **Windows** `%APPDATA%\azuredatastudio\User\settings.json`
* **Mac** `$HOME/Library/Application Support/azuredatastudio/User/settings.json`
* **Linux** `$HOME/.config/azuredatastudio/User/settings.json`

Le fichier de paramètres de l’espace de travail se trouve sous le dossier `.[!INCLUDE[name-sos](../includes/name-sos-short.md)]` dans votre projet.

## <a name="hot-exit"></a>Sortie à chaud

Azure Data Studio mémorise les modifications non enregistrées apportées aux fichiers lorsque vous quittez par défaut. Il s’agit de la même fonctionnalité de sortie à chaud que dans Visual Studio Code.

Par défaut, la sortie à chaud est désactivée. Activez la sortie à chaud en modifiant le paramètre `files.hotExit`. Pour plus d’informations, consultez [Sortie à chaud (dans la documentation de Visual Studio code)](https://code.visualstudio.com/docs/editor/codebasics#_hot-exit).


## <a name="tab-color"></a>Couleur de l’onglet

Pour simplifier l’identification des connexions que vous utilisez, ouvrez des onglets dans l’éditeur. Leurs couleurs peuvent être définies pour correspondre à la couleur du groupe de serveurs auquel la connexion appartient. Par défaut, les couleurs d’onglet sont désactivées. Activez les couleurs d’onglet en modifiant le paramètre `sql.tabColorMode`.

## <a name="additional-resources"></a>Ressources supplémentaires

Étant donné que [!INCLUDE[name-sos](../includes/name-sos-short.md)] hérite de la fonctionnalité des paramètres de l’utilisateur et de l’espace de travail de Visual Studio Code, des informations détaillées sur les paramètres se trouvent dans l’article [Paramètres de Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings).
