---
title: MSSQLSERVER_14420 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 14420 (Database Engine error)
ms.assetid: 4a1d72b1-ab1b-4119-a11b-a8a05c6fdb45
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5c2818c322749672c514cd9d392b61b580d40e88
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62869901"
---
# <a name="mssqlserver_14420"></a>MSSQLSERVER_14420
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|14420|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum14420|  
|Texte du message|La base de données primaire d'envoi de journaux %s.%s a un seuil de sauvegarde de %d minutes et n'a pas effectué de journalisation des sauvegardes depuis %d minutes. Vérifiez les informations du journal de l'agent et du moniteur de copie des journaux de transaction.|  
  
## <a name="explanation"></a>Explication  
 La copie des journaux de transaction n'est plus synchronisée en cas de dépassement du seuil de sauvegarde. Le seuil de sauvegarde correspond au nombre de minutes qui peuvent s'écouler entre les travaux de sauvegarde de la copie des journaux de transaction avant qu'une alerte soit générée. Ce message n'indique pas nécessairement un problème avec la copie des journaux de transaction. Il peut, en fait, indiquer l'un des problèmes suivants :  
  
-   Le travail de sauvegarde n'est pas en cours d'exécution. Les causes possibles sont les suivantes : le service Agent SQL Server sur l'instance du serveur principal n'est pas en cours d'exécution, le travail est désactivé ou la planification du travail a été modifiée.  
  
-   Le travail de sauvegarde est en échec. Les causes possibles sont les suivantes : le chemin d'accès du dossier de sauvegarde n'est pas valide, le disque est plein ou toute autre raison pouvant entraîner l'échec de l'instruction BACKUP.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre le problème qui est à l'origine de ce message :  
  
-   Assurez-vous que le service Agent SQL Server est en cours d'exécution pour l'instance du serveur principal et que le travail de sauvegarde pour cette base de données primaire est activé et est planifié pour s'exécuter à la fréquence appropriée.  
  
-   Il est possible que le travail de sauvegarde sur le serveur principal soit en échec. Dans ce cas, consultez l'historique des travaux de sauvegarde pour déterminer la cause de l'échec.  
  
-   Il se peut que le travail de sauvegarde de la copie des journaux de transaction, qui s’exécute sur l’instance du serveur principal, ne puisse pas se connecter à l’instance du serveur moniteur pour mettre à jour la table **log_shipping_monitor_primary**. Ceci peut être dû à un problème d'authentification entre l'instance du serveur moniteur et l'instance du serveur principal.  
  
-   La valeur du seuil d'alerte de sauvegarde est peut-être incorrecte. Dans l'idéal, cette valeur doit être au moins trois fois supérieure à la fréquence du travail de sauvegarde. Si vous modifiez la fréquence du travail de sauvegarde une fois que la copie des journaux de transaction est configurée et fonctionnelle, la valeur du seuil d'alerte de sauvegarde doit être mise à jour en conséquence.  
  
-   Lorsque l’instance du serveur moniteur est mise hors connexion et qu’elle revient ensuite en ligne, la table **log_shipping_monitor_primary** n’est pas mise à jour avec les valeurs actuelles avant l’exécution du travail de message d’alerte. Pour mettre à jour les tables du serveur moniteur afin qu’elles contiennent les données les plus récentes pour la base de données primaire, exécutez **sp_refresh_log_shipping_monitor** sur l’instance du serveur principal.  
  
-   La date ou l'heure est incorrecte sur l'instance du serveur principal ou du serveur moniteur. Ceci peut également générer des messages d'alerte. Il est possible que la date ou l'heure système ait été modifiée sur l'une des deux instances.  
  
    > [!NOTE]  
    >  Une différence de fuseaux horaires entre les deux instances de serveurs ne pose généralement aucun problème.  
  
## <a name="see-also"></a>Voir aussi  
 [log_shipping_monitor_primary &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql)   
 [À propos de la copie des journaux de &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_help_log_shipping_monitor_primary &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql)   
 [sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql)   
 [À propos de la copie des journaux de transaction &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
