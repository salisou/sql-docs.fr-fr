---
title: Utiliser les widgets d’insight pour superviser les serveurs et les bases de données
titleSuffix: Azure Data Studio
description: En savoir plus sur les widgets d’insight dans Azure Data Studio
ms.custom: seodec18, sqlfreshmay19, seo-lt-2019
ms.date: 05/14/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4edf4003d40da35dcd54b3938e0f318ef8b9440a
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "74957053"
---
# <a name="manage-servers-and-databases-with-insight-widgets-in-name-sos"></a>Gérer les serveurs et les bases de données avec les widgets d’insight dans [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Les widgets d’insight prennent les requêtes Transact-SQL (T-SQL) que vous utilisez pour analyser les serveurs et les bases de données et les transformer en visualisations informatives.

Les insights sont des graphiques personnalisables que vous ajoutez aux tableaux de bord de surveillance des serveurs et des bases de données. Affichez un aperçu de vos serveurs et bases de données, puis explorez les détails et lancez les actions de gestion que vous définissez.

Vous pouvez créer des tableaux de bord de gestion des serveurs et des bases de données, comme dans l’exemple suivant :

![Tableau de bord de base de données](media/insight-widgets/database-dashboard.png)

Pour vous lancer et commencer à créer différents types d’aperçus, consultez les didacticiels suivants :

- [Créer un widget insight personnalisé](tutorial-build-custom-insight-sql-server.md)
- *Activer les widgets d’insight intégrés*
  - [Activer l’analyse des performances](tutorial-qds-sql-server.md)
  - [Activer l’analyse de l’utilisation de l’espace de table](tutorial-table-space-sql-server.md)

## <a name="sql-queries"></a>Requêtes SQL

[!INCLUDE[name-sos](../includes/name-sos-short.md)] tente d’éviter d’introduire un autre langage ou une interface utilisateur lourde et tente donc d’utiliser le langage T-SQL le plus possible avec une configuration JSON minimale. La configuration des widgets d’insight avec T-SQL s’appuie sur les nombreuses sources existantes de requêtes T-SQL utiles qui peuvent être transformées en widgets d’insight.

Les widgets d’insight sont composés d’une ou deux requêtes T-SQL :
* *La requête du widget d’insight* est obligatoire et est la requête qui retourne les données qui s’affichent dans le widget.
* *La requête de détails d’insight* est requise uniquement si vous créez une page de détails d’insight.

Une requête de widget d’insight définit un jeu de données qui restitue un nombre ou un graphique. La requête de détails d’insight est utilisée pour répertorier les informations d’insight détaillées pertinentes dans un format tabulaire dans le panneau de détails de l’insight. 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] exécute des requêtes de widget d’insight et mappe le jeu de résultats de la requête au jeu de données d’un graphique, puis le restitue. Quand les utilisateurs ouvrent les détails d’un aperçu, il exécute la requête de détails d’insight et affiche le résultat dans une vue de grille dans la boîte de dialogue.

L’idée de base est d’écrire une requête T-SQL de manière à ce qu’elle puisse être utilisée en tant que jeu de données d’un widget de nombres ou de graphiques. 

## <a name="summary"></a>Résumé

La requête T-SQL et son jeu de résultats déterminent le comportement du widget d’insight. L’écriture d’une requête pour un type de graphique ou le mappage d’un type de graphique approprié pour une requête existante est le point essentiel pour créer un widget d’insight efficace.



## <a name="additional-resources"></a>Ressources supplémentaires
- [Éditeur de requête](tutorial-sql-editor.md)

