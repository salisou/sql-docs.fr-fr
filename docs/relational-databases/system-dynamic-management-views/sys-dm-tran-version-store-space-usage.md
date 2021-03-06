---
title: sys. dm_tran_version_store_space_usage (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_version_store_space_usage_TSQL
- sys.dm_tran_version_store_space_usage
- dm_tran_version_store_space_usage
- dm_tran_version_store_space_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_version_store_space_usage dynamic management view
ms.assetid: 7ab44517-0351-4f91-bdd9-7cf940f03c51
author: savjani
ms.author: pariks
manager: ajayj
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2a4fac732f784a401206f37fb2af9d3d8e0688ba
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68262661"
---
# <a name="sysdm_tran_version_store_space_usage-transact-sql"></a>sys. dm_tran_version_store_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-2016sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2016sp2-asdb-xxxx-xxx-md.md)]

Retourne une table qui affiche l’espace total dans tempdb utilisé par les enregistrements de la Banque des versions pour chaque base de données. **sys. dm_tran_version_store_space_usage** est efficace et n’est pas coûteux à exécuter, car il ne parcourt pas les enregistrements individuels de la Banque des versions et retourne l’espace de la Banque des versions agrégé utilisé dans tempdb par base de données.
  
Chaque enregistrement avec version est stocké sous forme de données binaires, avec des informations de suivi ou d’État. À l'instar des enregistrements des tables de la base de données, ceux de la banque des versions sont stockés dans des pages de 8 192 octets. Si un enregistrement excède ces 8 192 octets, il est réparti sur deux enregistrements.  
  
Comme l'enregistrement avec contrôle de version est stocké sous forme binaire, cela ne pose pas de problème avec les différents classements des différentes bases de données. Utilisez **sys. dm_tran_version_store_space_usage** pour surveiller et planifier la taille de tempdb en fonction de l’utilisation de l’espace de la Banque des versions des bases de données dans une instance SQL Server.
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ID de base de données de la base de données.|  
|**reserved_page_count**|**bigint**|Nombre total de pages réservées dans tempdb pour les enregistrements de la Banque des versions de la base de données.|  
|**reserved_space_kb**|**bigint**|Espace total utilisé en kilo-octets dans tempdb pour les enregistrements de la base de données de la Banque des versions.|  
  
## <a name="permissions"></a>Autorisations  
Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requiert `VIEW SERVER STATE` l’autorisation.   

## <a name="examples"></a>Exemples  
La requête suivante peut être utilisée pour déterminer l’espace consommé dans tempdb, par la Banque des versions de chaque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données dans une instance. 
  
```sql  
SELECT 
  DB_NAME(database_id) as 'Database Name',
  reserved_page_count,
  reserved_space_kb 
FROM sys.dm_tran_version_store_space_usage;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Database Name            reserved_page_count reserved_space_kb  
------------------------ -------------------- -----------  
msdb                      0                    0             
AdventureWorks2016        10                   80             
AdventureWorks2016DW      0                    0             
WideWorldImporters        20                   160             
```
 
## <a name="see-also"></a>Voir aussi  
 [Vues et fonctions de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Fonctions et vues de gestion dynamique relatives aux transactions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
