---
title: sys. FileGroups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.filegroups_TSQL
- filegroups
- sys.filegroups
- filegroups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filegroups catalog view
ms.assetid: 9e851f72-1f8e-4515-a25d-152ebc12ed56
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 313c0b80a1bf1d2a094760198053e26426e99c36
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68005174"
---
# <a name="sysfilegroups-transact-sql"></a>sys.filegroups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contient une ligne pour chaque espace de données représentant un groupe de fichiers.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**\<colonnes héritées>**|--|Pour obtenir la liste des colonnes héritées par cette vue, consultez [sys. data_spaces &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md).|  
|**filegroup_guid**|**uniqueidentifier**|GUID du groupe de fichiers.<br /><br /> NULL = groupe de fichiers PRIMARY|  
|**log_filegroup_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la valeur est NULL.|  
|**is_read_only**|**bit**|1 = Le groupe de fichiers est en lecture seule.<br /><br /> 1 = le groupe de fichiers est accessible en lecture/écriture.|  
|**is_autogrow_all_files**|**bit**|**S’applique à** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (jusqu’à la [version actuelle](https://go.microsoft.com/fwlink/p/?LinkId=299658)).<br /><br /> 1 = lorsqu’un fichier du groupe de fichiers atteint le seuil de croissance automatique, tous les fichiers du groupe de fichiers augmentent.<br /><br /> 0 = lorsqu’un fichier du groupe de fichiers atteint le seuil de croissance automatique, seul ce fichier augmente. Il s’agit de la valeur par défaut.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Les espaces de données &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)  
  
  
