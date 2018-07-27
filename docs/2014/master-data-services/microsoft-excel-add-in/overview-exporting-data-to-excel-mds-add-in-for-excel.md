---
title: Le chargement des données (complément MDS pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b628548b-982b-4e45-abf4-c8e83e3ab1c2
caps.latest.revision: 8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: ad7d9de63907fb8156631880bb1af8a336412fd0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37290885"
---
# <a name="loading-data-mds-add-in-for-excel"></a>Chargement de données (Complément MDS pour Excel)
  Dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], vous devez charger des données à partir du référentiel MDS dans une feuille de calcul Excel active avant de pouvoir travailler avec lui. Lorsque vous avez terminé de manipuler les données, publiez-les dans le référentiel MDS afin que d'autres utilisateurs puissent les utiliser.  
  
 Les données que vous pouvez charger sont celles auxquelles vous avez l'autorisation d'accéder. Les autorisations d'accès aux données sont définies dans l'application Web de [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] ou par programme.  
  
 Lorsque vous chargez un grand nombre de données, vous pouvez définir des avertissements qui s'affichent lorsque le chargement risque d'être très long. Pour cela, dans le groupe **Options** , cliquez sur **Paramètres**. Sous l’onglet **Données** , sélectionnez **Afficher l’avertissement de filtrage pour les jeux de données volumineux**.  
  
> [!WARNING]  
>  Un classeur compatible DM doit être ouvert et mis à jour uniquement dans Excel avec le complément MDS pour Excel. L'ouverture d'un classeur compatible DM dans Excel sur un ordinateur sur lequel le complément MDS Excel n'est pas installé n'est pas prise en charge et peut endommager le fichier du classeur. Si vous souhaitez partager des données avec une autre personne, envoyez-lui un fichier de requête de raccourci par courrier électronique au lieu d'enregistrer la feuille de calcul et de la lui envoyer par courrier électronique. Pour plus d’informations sur la requête, consultez [Envoyer par e-mail un fichier de requête de raccourci &#40;Complément MDS pour Excel&#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md).  
  
## <a name="filtering-data"></a>Filtrage des données  
 Vous pouvez filtrer les données avant le chargement afin de limiter le volume de données que vous allez télécharger. Par exemple, vous pouvez choisir les attributs (colonnes) que vous souhaitez charger, l'ordre d'affichage des attributs et les membres (lignes de données) que vous souhaitez utiliser. Pour plus d’informations, consultez [filtrer les données avant le chargement &#40;complément MDS pour Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md).  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a>Connexion automatique et chargement de données fréquemment utilisées  
 Si vous souhaitez vous connecter toujours au même serveur et charger le même jeu de données, vous pouvez créer des fichiers de requête de raccourci contenant les informations de connexion et de filtre. Pour plus d’informations sur les fichiers de requête, consultez [Fichiers de requête de raccourci &#40;Complément MDS pour Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md).  
  
## <a name="refreshing-data"></a>Actualisation des données  
 Les données du référentiel MDS peuvent être mises à jour par d'autres utilisateurs après que vous les ayez téléchargées. Vous pouvez extraire ces données sans perdre les modifications apportées aux données non managées MDS. Pour plus d’informations, consultez [Actualisation des données &#40;Complément MDS pour Excel&#41;](refreshing-data-mds-add-in-for-excel.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Filtrez les données MDS avant de les charger dans Excel.|[Filtrer les données avant le chargement &#40;complément MDS pour Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md)|  
|Chargez des données MDS dans Excel.|[Charger des données MDS dans Excel](export-data-to-excel-from-master-data-services.md)|  
|Modifiez l'ordre des colonnes avant de télécharger les données.|[Réorganiser les colonnes &#40;complément MDS pour Excel&#41;](reorder-columns-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Connexions &#40;Complément MDS pour Excel#41;](connections-mds-add-in-for-excel.md)  
  
-   [Fichiers de requête de raccourci &#40;Complément MDS pour Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Complément Master Data Services pour Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [Sécurité &#40;Master Data Services&#41;](../security-master-data-services.md)  
  
  