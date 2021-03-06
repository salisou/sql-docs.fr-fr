---
title: MSSQLSERVER_17300 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17300 (Database Engine error)
ms.assetid: c1d6bfb6-28af-4df6-8087-25807602d282
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1d6b4f7cdabc8688fda5ad21cc40e6c5f11fa39e
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68131658"
---
# <a name="mssqlserver_17300"></a>MSSQLSERVER_17300
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|17300|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PROC_OUT_OF_SYSTASK_SESSIONS|  
|Texte du message|SQL Server n'a pas pu exécuter une nouvelle tâche système, soit parce que la mémoire est insuffisante, soit parce que le nombre de sessions configurées dépasse le nombre maximal autorisé sur le serveur. Vérifiez que le serveur dispose de la mémoire adéquate. Utilisez sp_configure avec l'option « User connections » pour spécifier le nombre maximal de connexions utilisateur autorisées. Utilisez sys.dm_exec_sessions pour vérifier le nombre actuel de sessions, y compris les processus utilisateur.|  
  
## <a name="explanation"></a>Explication  
Une tentative d'exécution d'une nouvelle tâche système a échoué à cause d'une insuffisance de mémoire ou d'un dépassement du nombre de sessions configurées sur le serveur.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Vérifiez que le serveur dispose de suffisamment de mémoire. Vérifiez le nombre actuel de tâches système en utilisant sys.dm_exec_sessions et vérifiez la valeur configurée du maximum de connexions utilisateur en utilisant sp_configure.  
  
Effectuez les tâches suivantes comme il convient :  
  
-   Ajoutez de la mémoire au serveur.  
  
-   Mettez fin à une ou plusieurs sessions.  
  
-   Augmentez le nombre maximal de connexions utilisateur autorisées sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
[sp_configure &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
[Options de configuration de serveur &#40;SQL Server&#41;](~/database-engine/configure-windows/server-configuration-options-sql-server.md)  
[sys.dm_exec_sessions &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
[Configurer l’option de configuration du serveur user connections](~/database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md)  
[KILL &#40;Transact-SQL&#41;](~/t-sql/language-elements/kill-transact-sql.md)  
  
