---
title: sys. dm_exec_external_work (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_EXTERNAL_WORK
- DM_EXEC_EXTERNAL_WORK_TSQL
- SYS.DM_EXEC_EXTERNAL_WORK_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_external_work management view
- dm_exec_external_work management view
- PolyBase,views
- PolyBase
ms.assetid: 7597d97b-1fde-4135-ac35-4af12968f300
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b0ba7eecc8e117e429f6992622d0c7bb2073f86a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "74834333"
---
# <a name="sysdm_exec_external_work-transact-sql"></a>sys. dm_exec_external_work (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Retourne des informations sur la charge de travail par travail, sur chaque nœud de calcul.  
  
 Interrogez sys. dm_exec_external_work pour identifier le travail qui doit communiquer avec la source de données externe (par exemple, Hadoop ou SQL Server externe).  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|`nvarchar(32)`|Identificateur unique de la requête Polybase associée.|Consultez *request_ID* dans [sys. Dm_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|step_index|`int`|Requête exécutée par ce processus de travail.|Consultez *step_index* dans [sys. Dm_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|dms_step_index|`int`|Étape du plan DMS que ce processus de travail exécute.|Consultez [sys. dm_exec_dms_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md).|  
|compute_node_id|`int`|Nœud sur lequel le processus de travail s’exécute.|Consultez [sys. dm_exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|type|`nvarchar(60)`|Type de travail externe.|'Fichier fractionné'|  
|work_id|`int`|ID du fractionnement réel.|Supérieur ou égal à 0.|  
|input_name|`nvarchar(4000)`|Nom de l’entrée à lire|Nom de fichier lors de l’utilisation de Hadoop.|  
|read_location|`bigint`|Emplacement de décalage ou de lecture.|Décalage du fichier à lire.|  
|bytes_processed|`bigint`|Nombre total d’octets alloués pour le traitement des données par ce Worker. Cela ne représente peut-être pas nécessairement le nombre total de données retournées par la requête. |Supérieur ou égal à 0.|  
|length|`bigint`|Longueur du bloc Split ou HDFS dans le cas de Hadoop|Définissable par l’utilisateur. La valeur par défaut est 64M|  
|status|`nvarchar(32)`|État du Worker|En attente, traitement, terminé, échec, abandonné|  
|start_time|`datetime`|Début du travail||  
|end_time|`datetime`|Fin du travail||  
|total_elapsed_time|`int`|Durée totale en millisecondes||
|compute_pool_id|`int`|Identificateur unique du pool.|

## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes de Polybase avec les vues de gestion dynamique](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Vues et fonctions de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues de gestion dynamique liées à la base de données &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
