---
title: MSdynamicsnapshotjobs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdynamicsnapshotjobs_TSQL
- MSdynamicsnapshotjobs
dev_langs:
- TSQL
helpviewer_keywords:
- MSdynamicsnapshotjobs system table
ms.assetid: 4f36a325-0e3c-46c4-aeeb-416346cce0bc
author: stevestein
ms.author: sstein
ms.openlocfilehash: f8822b0e7c56fe109a251365050f5aed9cdef178
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67907368"
---
# <a name="msdynamicsnapshotjobs-transact-sql"></a>MSdynamicsnapshotjobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table **MSdynamicsnapshotjobs** effectue le suivi des informations sur les filtres de lignes paramétrables appliquées pour générer un instantané de données filtrées. Cette table est stockée dans les bases de données de publication et d’abonnement.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID de la tâche d'instantané des données filtrées.|  
|**name**|**sysname**|Nom de la tâche d'instantané des données filtrées.|  
|**pubid**|**uniqueidentifier**|Numéro d'identification unique de cette publication.|  
|**job_id**|**uniqueidentifier**|ID de la tâche de l'Agent SQL Server sur le serveur de distribution.|  
|**agent_id**|**int**|ID de l'Agent SQL Server.|  
|**dynamic_filter_login**|**sysname**|Valeur utilisée pour évaluer la fonction [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) dans les filtres de lignes paramétrables définis pour la publication.|  
|**dynamic_filter_hostname**|**sysname**|Valeur utilisée pour évaluer la fonction [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) dans les filtres de lignes paramétrables définis pour la publication.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Chemin d'accès au dossier à partir duquel les fichiers d'instantané sont lus en cas d'utilisation d'un instantané de données filtrées.|  
|**partition_id**|**int**|ID de la partition de données à laquelle la tâche appartient.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
