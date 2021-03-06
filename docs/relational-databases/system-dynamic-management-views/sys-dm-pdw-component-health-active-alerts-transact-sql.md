---
title: sys. dm_pdw_component_health_active_alerts (Transact-SQL
ms.custom: seo-dt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: c53e4a36-b841-424a-b8e2-255b1878deb6
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 90531889d3e510d342ff39abdf069f75f3c371aa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401713"
---
# <a name="sysdm_pdw_component_health_active_alerts-transact-sql"></a>sys. dm_pdw_component_health_active_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Stocke les alertes [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] actives sur les composants.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Identificateur unique d’un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] nœud.<br /><br /> pdw_node_id, component_id, component_instance_id, alert_id et alert_instance_id constituent la clé de cette vue.|NOT NULL|  
|component_id|**int**|ID du composant. Consultez [sys. pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id, component_id, component_instance_id, alert_id et alert_instance_id constituent la clé de cette vue.|NOT NULL|  
|component_instance_id|**nvarchar(255)**|pdw_node_id, component_id, component_instance_id, alert_id et alert_instance_id constituent la clé de cette vue.|NOT NULL|  
|alert_id|**int**|ID du type d’alerte. Consultez [sys. pdw_health_alerts &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md).<br /><br /> pdw_node_id, component_id, component_instance_id, alert_id et alert_instance_id constituent la clé de cette vue.|NOT NULL|  
|alert_instance_id|**nvarchar (36)**|Identifie une instance d’une alerte donnée.<br /><br /> pdw_node_id, component_id, component_instance_id, alert_id et alert_instance_id constituent la clé de cette vue.|NOT NULL|  
|current_value|**nvarchar(255)**|Utilisé lorsque l’alerte est de type StatusChange. Il s’agit de l’état actuel du composant. La valeur est NULL pour les alertes de type Threshold. Pour obtenir la liste des types d’alerte, consultez [sys. pdw_health_alerts &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) .|NULL|  
|previous_value|**nvarchar(255)**|Utilisé lorsque l’alerte est de type StatusChange. Il s’agit de l’état du composant précédent. La valeur est NULL pour les alertes de type Threshold. Pour obtenir la liste des types d’alerte, consultez [sys. pdw_health_alerts &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) .|NULL|  
|create_time|**datetime**|Heure et date de génération de l’alerte.|NOT NULL|  
  
 Pour plus d’informations sur le nombre maximal de lignes conservées par cette vue, consultez « valeurs minimales [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]et maximales » dans le.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de gestion dynamique Data Warehouse parallèles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
