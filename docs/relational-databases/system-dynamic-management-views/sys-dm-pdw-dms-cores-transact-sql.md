---
title: sys. dm_pdw_dms_cores (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b3f09b15-0863-4418-9347-a4f5fd2ab7c7
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 76a154639a71b22bfe3f119233f3abbcd329f7c3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67899528"
---
# <a name="sysdm_pdw_dms_cores-transact-sql"></a>sys. dm_pdw_dms_cores (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations sur tous les services DMS s’exécutant sur les nœuds de calcul de l’appliance. Elle répertorie une ligne par instance de service, qui est actuellement une ligne par nœud.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|dms_core_id|**int**|ID numérique unique associé à ce noyau DMS.<br /><br /> Clé pour cette vue.|Défini sur le pdw_node_id du nœud sur lequel ce noyau DMS s’exécute.|  
|pdw_node_id|**int**|ID du nœud sur lequel ce service DMS s’exécute.|Consultez node_id dans [sys. dm_pdw_nodes &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar(32)**|État actuel du service DMS.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
 Pour plus d’informations sur le nombre maximal de lignes conservées par cette vue, consultez la section métadonnées dans la rubrique [limites de capacité](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) .  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de gestion dynamique Data Warehouse parallèles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
