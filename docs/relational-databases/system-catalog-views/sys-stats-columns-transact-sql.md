---
title: sys. stats_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- stats_columns_TSQL
- stats_columns
- sys.stats_columns
- sys.stats_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.stats_columns catalog view
ms.assetid: 93414d07-97e9-4501-8577-f35b8d68fbe9
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6abf636a371047f344861f09affaa1dd9f7d82de
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68108976"
---
# <a name="sysstats_columns-transact-sql"></a>sys.stats_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contient une ligne pour chaque colonne qui fait partie des statistiques **sys. stats** .  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID de l'objet dont cette colonne fait partie.|  
|**stats_id**|**int**|ID des statistiques auxquelles cette colonne prend part.<br /><br />Si les statistiques correspondent à un index, la valeur *stats_id* est identique à la valeur *index_id* de l’affichage catalogue [sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) .|  
|**stats_column_id**|**int**|Ordinal à partir de 1 dans l'ensemble des colonnes de statistiques.|  
|**column_id**|**int**|ID de la colonne de **sys. Columns**.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Questions fréquentes sur l'interrogation des catalogues système de SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
 [Portent](../../relational-databases/statistics/statistics.md)    
 [sys. dm_db_stats_properties &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)   
 [sys. dm_db_stats_histogram &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)  
  
  
