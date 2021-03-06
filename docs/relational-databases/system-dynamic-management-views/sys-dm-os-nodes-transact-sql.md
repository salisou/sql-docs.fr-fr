---
title: sys. dm_os_nodes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/13/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_nodes
- dm_os_nodes_TSQL
- dm_os_nodes
- sys.dm_os_nodes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_nodes dynamic management view
ms.assetid: c768b67c-82a4-47f5-850b-0ea282358d50
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b2b6f88e857ab7fc6300698174914126fb0881f6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68265728"
---
# <a name="sysdm_os_nodes-transact-sql"></a>sys.dm_os_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Un composant interne nommé SQLOS crée des structures de nœuds qui simulent la localité du processeur du matériel. Ces structures peuvent être modifiées à l’aide de [soft-NUMA](../../database-engine/configure-windows/soft-numa-sql-server.md) pour créer des dispositions de nœud personnalisées.  

> [!NOTE]
> À compter [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]de, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] le utilise automatiquement le NUMA soft pour certaines configurations matérielles. Pour plus d’informations, consultez [Automatic soft-NUMA](../../database-engine/configure-windows/soft-numa-sql-server.md#automatic-soft-numa).
  
Le tableau suivant fournit des informations sur ces nœuds.  
  
> [!NOTE]
> Pour appeler cette DMV à [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] partir [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]de ou, utilisez le nom **sys. dm_pdw_nodes_os_nodes**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|node_id|**smallint**|Identificateur du nœud.|  
|node_state_desc|**nvarchar(256)**|Description de l'état du nœud. Les valeurs sont affichées avec, en premier, les valeurs qui s'excluent mutuellement, suivies par les valeurs pouvant être associées. Par exemple :<br /> En ligne, Ressources de thread réduites, Préemptif différé<br /><br />Il existe quatre valeurs node_state_desc mutuellement exclusives. Elles sont répertoriées ci-dessous avec leurs descriptions.<br /><ul><li>EN ligne : le nœud est en ligne<li>HORS connexion : le nœud est hors connexion<li>Inactif : le nœud n’a aucune demande de travail en attente et est passé à l’état inactif.<li>IDLE_READY : le nœud n’a aucune demande de travail en attente et est prêt à entrer dans un état d’inactivité.</li></ul><br />Il existe trois valeurs node_state_desc pouvant être combinées, répertoriées ci-dessous avec leurs descriptions.<br /><ul><li>DAC : ce nœud est réservé pour la [connexion d’administration dédiée](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).<li>THREAD_RESOURCES_LOW : aucun nouveau thread ne peut être créé sur ce nœud en raison d’une condition de mémoire insuffisante.<li>AJOUT à chaud : indique que les nœuds ont été ajoutés en réponse à un événement d’ajout de processeur à chaud.</li></ul>|  
|memory_object_address|**varbinary (8)**|Adresse de l'objet mémoire associé à ce nœud. Relation un-à-un à [sys. dm_os_memory_objects](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md). memory_object_address.|  
|memory_clerk_address|**varbinary (8)**|Adresse du régisseur de mémoire associé à ce nœud. Relation un-à-un à [sys. dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md). memory_clerk_address.|  
|io_completion_worker_address|**varbinary (8)**|Adresse du thread de travail assigné à l'achèvement d'E/S pour ce nœud. Relation un-à-un à [sys. dm_os_workers](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md). worker_address.|  
|memory_node_id|**smallint**|ID du nœud de mémoire auquel ce nœud appartient. Relation plusieurs-à-un à [sys. dm_os_memory_nodes](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-nodes-transact-sql.md). memory_node_id.|  
|cpu_affinity_mask|**bigint**|Bitmap qui identifie les unités centrales auxquelles ce nœud est associé.|  
|online_scheduler_count|**smallint**|Nombre de planificateurs en ligne qui sont gérés par ce nœud.|  
|idle_scheduler_count|**smallint**|Nombre de planificateurs en ligne qui n'ont aucun thread de travail actif.|  
|active_worker_count|**int**|Nombre de threads de travail qui sont actifs sur tous les planificateurs gérés par ce nœud.|  
|avg_load_balance|**int**|Nombre moyen de tâches par planificateur sur ce nœud.|  
|timer_task_affinity_mask|**bigint**|Bitmap qui identifie les planificateurs auxquels des tâches de minuterie peuvent être assignées.|  
|permanent_task_affinity_mask|**bigint**|Bitmap qui identifie les planificateurs auxquels des tâches permanentes peuvent être assignées.|  
|resource_monitor_state|**bit**|Un moniteur de ressource est assigné à chaque nœud. Le moniteur de ressource peut être en cours d'exécution ou inactif. La valeur 1 indique qu'il est en cours d'exécution et la valeur 0 indique qu'il est inactif.|  
|online_scheduler_mask|**bigint**|Identifie le masque d'affinité de processus pour ce nœud.|  
|processor_group|**smallint**|Identifie le groupe de processeurs pour ce nœud.|  
|cpu_count |**int** |Nombre de processeurs disponibles pour ce nœud. |
|pdw_node_id|**int**|Identificateur du nœud sur lequel cette distribution se trouve.<br /><br /> **S’applique à**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
## <a name="permissions"></a>Autorisations

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiert `VIEW SERVER STATE` l’autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux Premium, requiert l' `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] les niveaux standard et de base, nécessite l' **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .   

## <a name="see-also"></a>Voir aussi    
 [SQL Server vues de gestion dynamique liées au système d’exploitation &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [Soft-NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
