---
title: MSmerge_contents (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_contents
- MSmerge_contents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_contents system table
ms.assetid: 8d68a61a-683f-4b20-92f9-c0a8d9ba0ad1
author: stevestein
ms.author: sstein
ms.openlocfilehash: a4be6cffcc7e4f13b88d8037b53d438d604b9650
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68089946"
---
# <a name="msmerge_contents-transact-sql"></a>MSmerge_contents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table **MSmerge_contents** contient une ligne pour chaque ligne modifiée dans la base de données active depuis sa publication. Cette table est utilisée par le processus de fusion afin de déterminer les lignes qui ont été modifiées. Cette table est stockée dans les bases de données de publication et d’abonnement.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Surnom de la table publiée.|  
|**rowguid**|**uniqueidentifier**|Identificateur de ligne pour la ligne concernée.|  
|**toute**|**bigint**|Génération de la ligne identifiée par **tablenick** et **rowguid**.|  
|**partchangegen**|**bigint**|Génération associée à la dernière modification de données pouvant avoir changé si la ligne appartient à une publication filtrée|  
|**lignage**|**varbinary (501)**|Surnom de l'abonné et numéro de version utilisés pour mettre à jour l'historique des modifications apportées à cette ligne|  
|**colvl**|**varbinary (7489)**|Informations relatives à la version de colonne|  
|**repère**|**uniqueidentifier**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|Identifie la ligne parente de niveau supérieur dans **MSmerge_contents** (par **rowguid**) pour chaque ligne enfant correspondante dans un enregistrement logique.|  
|**logical_record_lineage**|**varbinary (501)**|Paires surnom de l'abonné/numéro de version permettant de gérer un historique des modifications apportées à la ligne parente de niveau supérieur dans un enregistrement logique. Pour toutes les lignes enfants d'un enregistrement logique, cette valeur est NULL.|  
|**logical_relation_change_gen**|**bigint**|Valeur de génération associée à la dernière modification ayant provoqué un réalignement de l'enregistrement logique, correspondant à la perte ou au gain par celui-ci d'une ligne existante.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
