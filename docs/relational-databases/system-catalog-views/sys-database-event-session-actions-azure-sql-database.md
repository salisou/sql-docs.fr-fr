---
title: sys. database_event_session_actions (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: 32494df1-7ab7-4b88-a858-6b1021d67433
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 16aa77224f45a07540f7c5e688f9e3b6bc9bb6ea
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67915146"
---
# <a name="sysdatabase_event_session_actions-azure-sql-database"></a>sys.database_event_session_actions (Azure SQL Database)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque action d'un événement d'une session d'événements.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 et à toutes les versions ultérieures.|  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|ID de la session d'événements. N'accepte pas la valeur NULL.|  
|event_id|**int**|ID de l'événement. Cet ID est unique dans l'objet de la session d'événements. N'accepte pas la valeur NULL.|  
|name|**sysname**|Nom de l’action. Autorise la valeur NULL.|  
|package|**sysname**|Nom du package d'événement qui contient l'événement. Autorise la valeur NULL.|  
|module|**sysname**|Nom du module qui contient l'événement. Autorise la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation VIEW DATABASE STATE sur le serveur.  
  
## <a name="remarks"></a>Notes  
 Cette vue a les cardinalités de relation suivantes.  
  
||||  
|-|-|-|  
|À partir|À|Relation|  
|sys. database_event_session_actions. event_session_id|sys. sys. database_event_sessions. event_session_id|Plusieurs-à-un|  
|sys. database_event_session_actions. event_id<br /><br /> sys. database_event_session_actions. event_session_id|sys. database_event_session_events. event_session_id<br /><br /> sys. database_event_session_events. event_id|Plusieurs-à-un|  
  
  
