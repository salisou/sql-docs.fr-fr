---
title: sys. dm_exec_query_profiles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/25/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_profiles_TSQL
- sys.dm_exec_query_profiles_TSQL
- dm_exec_query_profiles
- sys.dm_exec_query_profiles
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_profiles dynamic management view
ms.assetid: 54efc6cb-eea8-4f6d-a4d0-aa05eeb54081
author: stevestein
ms.author: sstein
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cd30a6c07bccde04bb38189fab00f688dd763356
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "74165505"
---
# <a name="sysdm_exec_query_profiles-transact-sql"></a>sys.dm_exec_query_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

Contrôle la progression en temps réel lorsqu'une requête est en cours d'exécution. Par exemple, utilisez cette vue de gestion dynamique pour déterminer la partie de la requête qui est lente. Joignez cette vue de gestion dynamique à d'autres vues de gestion dynamique système identifiées dans le champ de description. Ou bien, joignez cette vue de gestion dynamique à d'autres compteurs de performances (tels que l'analyseur de performances, xperf) à l'aide de colonnes timestamp.  
  
## <a name="table-returned"></a>Table retournée  
Les compteurs retournés sont par opérateur par thread. Les résultats sont dynamiques et ne correspondent pas aux résultats des options existantes, telles `SET STATISTICS XML ON` que la création d’une sortie uniquement lorsque la requête est terminée.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|Identifie la session dans laquelle cette requête s'exécute. Référence dm_exec_sessions.session_id.|  
|request_id|**int**|Identifie la demande cible. Référence dm_exec_sessions.request_id.|  
|sql_handle|**varbinary(64)**|Jeton qui identifie de façon unique le lot ou la procédure stockée dont fait partie la requête. Référence dm_exec_query_stats.sql_handle.|  
|plan_handle|**varbinary(64)**|Jeton qui identifie de façon unique un plan d’exécution de requête pour un lot exécuté et dont le plan réside dans le cache du plan, ou qui est en cours d’exécution. Référence dm_exec_query_stats. plan_handle.|  
|physical_operator_name|**nvarchar(256)**|Nom de l'opérateur physique.|  
|node_id|**int**|Identifie un nœud d'opérateur dans l'arborescence de requête.|  
|thread_id|**int**|Fait la distinction entre les threads (pour une requête parallèle) qui appartiennent au même nœud d'opérateur de requête.|  
|task_address|**varbinary (8)**|Identifie la tâche SQLOS utilisée par ce thread. Référence dm_os_tasks.task_address.|  
|row_count|**bigint**|Nombre de lignes retournées par l'opérateur jusqu'à présent.|  
|rewind_count|**bigint**|Nombre de rembobinages jusqu'à présent.|  
|rebind_count|**bigint**|Nombre de reliaisons jusqu'à présent.|  
|end_of_scan_count|**bigint**|Nombre de fins d'analyses jusqu'à présent.|  
|estimate_row_count|**bigint**|Nombre de lignes estimé. Il peut être utile pour comparer estimated_row_count à actual row_count réel.|  
|first_active_time|**bigint**|Heure du premier appel de l'opérateur en millisecondes.|  
|last_active_time|**bigint**|Heure du dernier appel de l'opérateur en millisecondes.|  
|open_time|**bigint**|Horodatage lors de l'ouverture (en millisecondes).|  
|first_row_time|**bigint**|Horodatage lors de l'ouverture de la première ligne (en millisecondes).|  
|last_row_time|**bigint**|Horodatage lors de l'ouverture de la dernière ligne (en millisecondes).|  
|close_time|**bigint**|Horodatage lors de la fermeture (en millisecondes).|  
|elapsed_time_ms|**bigint**|Temps total écoulé (en millisecondes) utilisé par les opérations du nœud cible jusqu’à présent.|  
|cpu_time_ms|**bigint**|Temps processeur total (en millisecondes) utilisé par les opérations du nœud cible jusqu’à présent.|  
|database_id|**smallint**|ID de la base de données qui contient l'objet sur lequel les opérations de lecture et d'écriture sont effectuées.|  
|object_id|**int**|Identificateur de l'objet sur lequel les opérations de lecture et écriture sont effectuées. Fait référence à sys.objects.object_id.|  
|index_id|**int**|Index (le cas échéant) dans lequel l'ensemble de lignes est ouvert.|  
|scan_count|**bigint**|Nombre d'analyses de tables ou d'index jusqu'à présent.|  
|logical_read_count|**bigint**|Nombre de lectures logiques jusqu'à présent.|  
|physical_read_count|**bigint**|Nombre de lectures physiques jusqu'à présent.|  
|read_ahead_count|**bigint**|Nombre de lectures anticipées jusqu'à présent.|  
|write_page_count|**bigint**|Nombre d'écritures de page jusqu'à présent en raison de débordement.|  
|lob_logical_read_count|**bigint**|Nombre de lectures logiques LOB jusqu'à présent.|  
|lob_physical_read_count|**bigint**|Nombre de lectures physiques LOB jusqu'à présent.|  
|lob_read_ahead_count|**bigint**|Nombre de lectures anticipées LOB jusqu'à présent.|  
|segment_read_count|**int**|Nombre de lectures anticipées de segment jusqu'à présent.|  
|segment_skip_count|**int**|Nombre de segments ignorés jusqu'à présent.| 
|actual_read_row_count|**bigint**|Nombre de lignes lues par un opérateur avant l’application du prédicat résiduel.| 
|estimated_read_row_count|**bigint**|**S’applique à :** À partir [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] de SP1. <br/>Nombre de lignes dont la lecture est estimée par un opérateur avant l’application du prédicat résiduel.|  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Si le nœud de plan de requête n’a pas d’e/s, tous les compteurs d’e/s sont définis sur NULL.  
  
 Les compteurs d’e/s rapportés par cette DMV sont plus granulaires que ceux signalés par `SET STATISTICS IO` les deux méthodes suivantes :  
  
-   `SET STATISTICS IO`regroupe les compteurs pour l’ensemble des e/s d’une table donnée. Avec cette vue de gestion dynamique, vous obtiendrez des compteurs distincts pour chaque nœud du plan de requête qui effectue des e/s vers la table.  
  
-   En cas d'analyse parallèle, cette vue de gestion dynamique indique des compteurs pour chaque threads parallèles de l'analyse.
 
À compter [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] de SP1, l' *infrastructure de profilage des statistiques d’exécution de requête standard* existe côte à côte avec une *infrastructure de profilage des statistiques d’exécution de requête légère*. `SET STATISTICS XML ON`et `SET STATISTICS PROFILE ON` utilisent toujours l' *infrastructure de profilage des statistiques d’exécution de requête standard*. Pour `sys.dm_exec_query_profiles` que soit rempli, l’une des infrastructures de profilage de requête doit être activée. Pour plus d’informations, consultez [interroger l’infrastructure de profilage](../../relational-databases/performance/query-profiling-infrastructure.md).    

>[!NOTE]
> La requête en cours d’investigation doit démarrer **après** l’activation de l’infrastructure de profilage de la requête. l’activation de la requête après `sys.dm_exec_query_profiles`le démarrage de la requête ne produira pas de résultats dans. Pour plus d’informations sur la façon d’activer les infrastructures de profilage de requête, consultez [interroger l’infrastructure de profilage](../../relational-databases/performance/query-profiling-infrastructure.md).

## <a name="permissions"></a>Autorisations  
Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] Managed instance `VIEW DATABASE STATE` , requiert l’autorisation et `db_owner` l’appartenance du rôle de base de données.   
Sur [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] les niveaux Premium, requiert l' `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] les niveaux standard et de base, nécessite l' **administrateur du serveur** ou un compte d' **administrateur Azure Active Directory** .   
   
## <a name="examples"></a>Exemples  
 Étape 1 : Connectez-vous à une session dans laquelle vous envisagez d’exécuter la requête `sys.dm_exec_query_profiles`que vous allez analyser avec. Pour configurer la requête pour le profilage `SET STATISTICS PROFILE ON`, utilisez. Exécutez votre requête dans la même session.  
  
```sql  
--Configure query for profiling with sys.dm_exec_query_profiles  
SET STATISTICS PROFILE ON;  
GO  

--Or enable query profiling globally under SQL Server 2016 SP1 or above (not needed in SQL Server 2019)  
DBCC TRACEON (7412, -1);  
GO 
  
--Next, run your query in this session, or in any other session if query profiling has been enabled globally 
```  
  
 Étape 2 : Connectez-vous à une deuxième session qui est différente de la session dans laquelle votre requête s’exécute.  
  
 L'instruction suivante résume l'avancement de la requête en cours d'exécution dans la session 54. Pour ce faire, elle calcule le nombre total de lignes de sortie de tous les threads pour chaque nœud, et compare ce nombre au nombre estimé de lignes de sortie pour ce nœud.  
  
```sql  
--Run this in a different session than the session in which your query is running. 
--Note that you may need to change session id 54 below with the session id you want to monitor.
SELECT node_id,physical_operator_name, SUM(row_count) row_count, 
  SUM(estimate_row_count) AS estimate_row_count, 
  CAST(SUM(row_count)*100 AS float)/SUM(estimate_row_count)  
FROM sys.dm_exec_query_profiles   
WHERE session_id=54
GROUP BY node_id,physical_operator_name  
ORDER BY node_id;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Vues et fonctions de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Fonctions et vues de gestion dynamique relatives aux exécutions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
 
