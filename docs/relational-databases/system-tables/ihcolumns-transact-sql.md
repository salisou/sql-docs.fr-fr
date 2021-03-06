---
title: IHcolumns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHcolumns_TSQL
- IHcolumns
dev_langs:
- TSQL
helpviewer_keywords:
- IHcolumns system table
ms.assetid: 5bb027e5-5279-487b-9c33-5f402987253c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9985b0587316641955219eb5179ffd6ed07916d3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67990387"
---
# <a name="ihcolumns-transact-sql"></a>IHcolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table système **IHcolumns** contient une ligne pour chaque colonne publiée. Cette table permet de définir la manière dont les types de données colonne issus d'un serveur de publication non-SQL Server seront représentées lors de leur publication. Les types de données sont alors mappés entre le système de gestion de base de données non-SQL Server et SQL Server. Cette table est stockée dans la base de données de distribution.  
  
## <a name="definition"></a>Définition  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**column_id**|**int**|Identifie une colonne publiée.|  
|**publishercolumn_id**|**int**|Associe une colonne publiée à des métadonnées de colonne stockées dans la table système [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) .|  
|**name**|**sysname**|Spécifie le nom de la colonne.|  
|**article_id**|**int**|Identifie l'article auquel appartient la colonne.|  
|**column_ordinal**|**int**|Identifie la colonne par ordre.|  
|**mapped_type**|**tinyint**|Type de données colonne de la colonne de destination chez l'abonné.|  
|**mapped_length**|**bigint**|Longueur de la colonne chez l'abonné.|  
|**mapped_prec**|**int**|Précision de la colonne chez l'abonné.|  
|**mapped_scale**|**int**|Échelle de la colonne chez l'abonné.|  
|**mapped_nullable**|**bit**|Indique si la colonne sur l’abonné accepte les valeurs NULL, où **1** signifie que les valeurs NULL sont acceptées.|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de bases de données hétérogènes](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sysarticlecolumns &#40;vue système&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)   
 [sysarticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
