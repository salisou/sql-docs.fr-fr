---
title: sys. syscharsets (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.syscharsets
- syscharsets
- sys.syscharsets_TSQL
- syscharsets_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syscharsets system table
- sys.syscharsets compatibility view
ms.assetid: f16d987c-bd19-4668-9ef7-785b8fb9ff5b
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4332159765791addfdfcc32a9d19d29836f2460c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68053543"
---
# <a name="syssyscharsets-transact-sql"></a>sys.syscharsets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contient une ligne pour chaque jeu de caractères et ordre de tri défini pour être utilisé par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. L’un des ordres de tri est marqué dans **sysconfigures** comme l’ordre de tri par défaut. Il s'agit du seul ordre de tri effectivement utilisé.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**type**|**smallint**|Type de l'entité décrite par cette ligne :<br /><br /> 1001 = jeu de caractères.<br /><br /> 2001 = ordre de tri.|  
|**id**|**tinyint**|Numéro d'identification unique du jeu de caractères ou de l'ordre de tri. Notez que les ordres de tri et les jeux de caractères ne peuvent pas avoir le même numéro d'identification. Les identificateurs compris entre 1 et 240 sont réservés à l'utilisation par le [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|**csid**|**tinyint**|Si la ligne représente un jeu de caractères, ce champ n'est pas utilisé. Si elle représente un ordre de tri, ce champ contient le numéro d'identification du jeu de caractères sur lequel cet ordre de tri est construit. Il est supposé dans ce cas qu'une ligne de jeu de caractères contenant ce numéro d'identification figure dans la table.|  
|**statut**|**smallint**|Bits d'information d'état à usage interne.|  
|**name**|**sysname**|Nom unique du jeu de caractères ou de l'ordre de tri. Ce champ peut contenir uniquement des lettres (A-Z ou a-z), des chiffres (0 - 9) et des traits de soulignement (_) ; il doit commencer par une lettre.|  
|**descriptive**|**nvarchar(255)**|Description facultative des caractéristiques du jeu de caractères ou de l'ordre de tri.|  
|**binarydefinition**|**varbinary(6000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**définition**|**image**|Définition interne du jeu de caractères ou de l'ordre de tri. La structure des données de ce champ dépend du type.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage de tables système à des vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
