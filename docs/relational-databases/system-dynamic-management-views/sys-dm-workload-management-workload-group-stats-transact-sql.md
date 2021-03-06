---
title: sys. dm_workload_management_workload_groups_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/02/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: = azure-sqldw-latest||= sqlallproducts-allversions
ms.openlocfilehash: 6e77239d019cb51e66a34a3a5b909e01c28a7faa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "73633433"
---
# <a name="sysdm_workload_management_workload_groups_stats-transact-sql"></a>sys. dm_workload_management_workload_groups_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Retourne les statistiques des groupes de charges de travail et les valeurs effectives du groupe de charge de travail dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|group_id|**int**|ID unique du groupe de charges de travail.||
|name|**sysname**|Nom du groupe de charges de travail.||
|statistics_start_time|**datetime**|Heure de début de la collecte de statistiques pour le groupe de charge de travail.  La valeur est lorsque le groupe de charge de travail a été créé ou lorsque l’instance est suspendue ou mise à l’échelle.||
|total_request_count|**bigint**|Nombre cumulatif de demandes traitées dans le groupe de charges de travail.||
|total_shared_resource_reqeusts|**bigint**|Nombre cumulatif de demandes terminées dans le groupe de charge de travail qui utilisaient des ressources du pool partagé.||
|total_queued_request_count|**bigint**|Nombre cumulatif de demandes en attente une fois la limite d’max_concurrency atteinte.||
|total_request_execution_timeouts|**bigint**|Nombre cumulatif de demandes dans le groupe de charge de travail qui ont dépassé le délai d’exécution en fonction du paramètre de query_execution_timeout_sec.||
|effective_min_percentage_resource|**tinyint**|Le paramètre de min_percentage_resource effectif est autorisé à prendre en compte le niveau de service et les paramètres de groupe de charge de travail. Le min_percentage_resource effectif peut être ajusté plus haut sur des niveaux de service inférieurs.  Par exemple, sur DW100c, la min_percentage_resource la plus faible autorisée est de 25%.  Le min_percentage_resource est ajusté à 0% si la valeur ne peut pas être accordée au niveau du service.  Par exemple, min_percentage_resource défini sur 10% sur DW6000c, aurait une effective_min_percentage_resource de 0% en cas de mise à l’échelle de DW100c.||
|effective_cap_percentage_resource|**tinyint**|Cap_percentage_resource effective pour le groupe de charge de travail.  S’il existe d’autres groupes de charges de travail avec min_percentage_resource > 0, le effective_cap_percentage_resource est abaissé proportionnellement.||
|effective_request_min_resource_grant_percent|**décimal (5, 2)**|Valeur d’exécution effective pour request_min_resource_grant_percent du groupe de charge de travail. La valeur effective compte tenu du niveau de service et de la façon dont le groupe de charge de travail est configuré.  Si min_percentage_resource est ajusté en raison du niveau de service, effective_request_min_resource_grant_percent sera ajusté en conséquence.||
|effective_request_max_resource_grant_percent|**décimal (5, 2)**|La valeur d’exécution effective pour request_max_resource_grant_percent du groupe de charge de travail en tenant compte de la configuration de tous les groupes de charges de travail.||
|||||

## <a name="see-also"></a>Voir aussi

 [SQL Data Warehouse et les vues de gestion dynamique Data Warehouse parallèles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
