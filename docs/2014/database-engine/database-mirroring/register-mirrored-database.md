---
title: Inscrire la base de données mise en miroir | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.registermirroreddb.f1
ms.assetid: 6acd02b9-2311-49b0-a5f8-3852beecb4b0
caps.latest.revision: 28
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e84e0d6598c8657e48dbfbd3fb6570f0f8ad7c72
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289475"
---
# <a name="register-mirrored-database"></a>Inscrire la base de données mise en miroir
  Utilisez cette boîte de dialogue pour inscrire une ou plusieurs bases de données mises en miroir sur une instance de serveur donnée en ajoutant la ou les bases de données au moniteur de mise en miroir de bases de données. Lorsqu'une base de données est ajoutée, le moniteur de mise en miroir de bases de données met en cache localement des informations sur la base de données, ses partenaires et la connexion aux partenaires.  
  
> [!IMPORTANT]  
>  Si vous êtes membre du rôle de serveur fixe **sysadmin** sur l’instance de serveur principal, mais pas sur l’instance de serveur miroir, vous pouvez uniquement afficher l’état sur l’instance de serveur principal.  
  
 **Pour utiliser SQL Server Management Studio pour contrôler la mise en miroir de base de données**  
  
-   [Démarrer le moniteur de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a>Options  
 **Instance de serveur**  
 Sélectionnez une instance de serveur dans la liste d’instances de serveurs sur lesquelles le moniteur de mise en miroir de bases de données a déjà stocké une connexion, ou cliquez sur **Se connecter**. Pour spécifier de nouvelles informations d’identification pour une instance de serveur répertoriée, cliquez sur **Se connecter** et connectez-vous en utilisant ces nouvelles informations.  
  
> [!NOTE]  
>  Pour inscrire des bases de données sur plusieurs instances de serveurs, une fois que vous avez sélectionné les bases de données souhaitées pour une instance de serveur, cliquez sur **Appliquer**et sélectionnez une autre instance de serveur.  
  
 **Se connecter**  
 Pour spécifier de nouvelles informations d’identification pour l’instance de serveur, cliquez sur **Se connecter** et connectez-vous en utilisant ces nouvelles informations. Lors de la connexion à une instance de serveur, le moniteur de mise en miroir de bases de données affiche le message **Attente de données**.  
  
 **Bases de données mises en miroir**  
 La grille **Bases de données mises en miroir** affiche les bases de données mises en miroir sur l’instance de serveur.  
  
 Cette grille comporte les colonnes suivantes :  
  
|Nom de colonne|Description|  
|-----------------|-----------------|  
|**Inscrire**|Sélectionnez chaque base de données à inscrire. Si une base de données est actuellement surveillée, la case à cocher correspondante est sélectionnée et inactive.<br /><br /> Remarque : pour annuler l’inscription d’une base de données, fermez la boîte de dialogue **Inscrire la base de données mise en miroir** , sélectionnez la base de données dans l’arborescence de navigation, puis choisissez **Annuler l’inscription** dans le menu **Action** .|  
|**Sauvegarde de la base de données**|Nom d'une base de données mise en miroir sur l'instance de serveur sélectionnée.|  
|**Rôle actuel**|Rôle actuel de mise en miroir de la base de données (Principal ou Miroir) sur l'instance de serveur sélectionnée.|  
|**Partenaire (Se connecter en tant que)**|Nom du partenaire de basculement pour la base de données. **Authentification Windows de l’utilisateur de la console** ou **Authentification SQL Server de '***\<nom_compte_de_connexion>***'** s’affiche entre parenthèses. Il s'agit des informations d'authentification actuellement utilisées si l'instance a été ajoutée auparavant ou qui seront utilisées si l'instance n'a pas encore été ajoutée au moniteur.|  
  
 **Afficher la boîte de dialogue Gérer les connexions serveur lorsque je clique sur OK.**  
 Par défaut, le moniteur de mise en miroir de bases de données utilise les informations d'authentification Windows pour les instances de serveurs partenaires pour lesquelles aucune information d'identification n'a été précédemment fournie. Activez cette option si vous souhaitez modifier les informations d'identification sur une ou plusieurs instances de serveurs, une fois que vous avez inscrit des bases de données.  
  
 Si cette option est activée, lorsque vous cliquez sur **OK**, la boîte de dialogue **Gérer les connexions serveur** s’ouvre. Vous pouvez alors choisir une instance de serveur pour laquelle vous souhaitez spécifier des informations d'identification qui seront utilisées par le moniteur lors de la connexion à un partenaire de basculement donné.  
  
 Pour modifier les informations d’identification pour un partenaire, recherchez l’entrée correspondante dans la grille **Instances de serveur** et cliquez sur **Modifier** dans cette ligne. La boîte de dialogue **Se connecter au serveur** s’ouvre pour ce nom d’instance de serveur, avec les contrôles d’informations d’identification initialisés sur la valeur actuelle mise en cache. Modifiez les informations d’identification comme souhaité et cliquez sur **Se connecter**. Si les informations d’identification disposent des privilèges suffisants, la colonne **Se connecter avec** est mise à jour avec les nouvelles informations d’identification.  
  
 **Appliquer**  
 Cliquez sur ce bouton pour inscrire les bases de données sélectionnées (et enregistrer les informations d'identification pour les instances de serveurs partenaires) tout en laissant la boîte de dialogue ouverte.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le moniteur de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Surveillance de la mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Démarrer l’Assistant Configuration de la sécurité de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
  