---
title: sys. partitions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- partitions
- partitions_TSQL
- sys.partitions_TSQL
- sys.partitions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.partitions catalog view
ms.assetid: 1c19e1b1-c925-4dad-a652-581692f4ab5e
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2531dde9237734d3c6eb4b3ea96ed2ac18e9d399
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "73982801"
---
# <a name="syspartitions-transact-sql"></a>sys.partitions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contient une ligne pour chaque partition de toutes les tables et la plupart des types d'index de la base de données. Les types d'index spéciaux comme Texte intégral, Spatial et XML ne sont pas inclus dans cette vue. Tous les index et tables de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contiennent au moins une partition, qu'ils soient ou non explicitement partitionnés.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|partition_id|**bigint**|Indique l'ID de partition. Unique dans une base de données.|  
|object_id|**int**|Indique l’ID de l’objet auquel cette partition appartient. Chaque table ou vue comporte au moins une partition.|  
|index_id|**int**|Indique l'ID de l'index de l'objet auquel cette partition appartient.<br /><br /> 0 = segment de mémoire<br />1 = index cluster<br />2 ou plus = index non-cluster|  
|partition_number|**int**|Numéro de partition en base 1 dans l'index ou le segment de mémoire propriétaire. Pour les tables et les index non partitionnés, la valeur de cette colonne est 1.|  
|hobt_id|**bigint**|Indique l’ID de la segment de mémoire ou arbre B (B-tree) de données (HoBT) qui contient les lignes de cette partition.|  
|rows|**bigint**|Indique le nombre approximatif de lignes dans cette partition.|  
|filestream_filegroup_id|**smallint**|**S’applique à** : [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures.<br /><br /> Indique l'ID du groupe de fichiers FILESTREAM stocké sur cette partition.|  
|data_compression|**tinyint**|Indique l'état de compression pour chaque partition :<br /><br /> 0 = AUCUN <br />1 = LIGNE <br />2 = PAGE <br />3 = COLUMNSTORE : **s’applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures<br />4 = COLUMNSTORE_ARCHIVE : **s’applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et versions ultérieures<br /><br /> **Remarque :** Les index de recherche en texte intégral sont compressés [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dans n’importe quelle édition de.|  
|data_compression_desc|**nvarchar(60)**|Indique l'état de compression pour chaque partition. Les valeurs possibles pour les tables rowstore sont AUCUN, LIGNE et PAGE. Les valeurs possibles pour les tables columnstore sont COLUMNSTORE et COLUMNSTORE_ARCHIVE.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Questions fréquentes sur l'interrogation des catalogues système de SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
