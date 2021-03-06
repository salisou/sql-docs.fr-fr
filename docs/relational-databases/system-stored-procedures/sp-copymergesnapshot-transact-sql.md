---
title: sp_copymergesnapshot (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_copymergesnapshot
- sp_copymergesnapshot_TSQL
helpviewer_keywords:
- sp_copymergesnapshot
ms.assetid: eaecd6e0-8486-4e5d-ace7-8ae75768c0a8
author: stevestein
ms.author: sstein
ms.openlocfilehash: d51f29399487ee156210e96fe598c38288755913
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "72381713"
---
# <a name="sp_copymergesnapshot-transact-sql"></a>sp_copymergesnapshot (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Copie le dossier d’instantané de la publication spécifiée dans le dossier indiqué dans le ** \@destination_folder**. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_copymergesnapshot [ @publication = ] 'publication', [ @destination_folder = ] 'destination_folder'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication dont le contenu de l’instantané doit être copié. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @destination_folder = ] 'destination_folder'`Nom du dossier dans lequel le contenu de l’instantané de publication doit être copié. *destination_folder*est de type **nvarchar (255)**, sans valeur par défaut. La *destination_folder* peut être un autre emplacement, par exemple sur un autre serveur, sur un lecteur réseau ou sur un support amovible (tel qu’un CD-ROM ou un disque amovible).  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_copymergesnapshot** est utilisé dans la réplication de fusion. Les abonnés [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui exécutent la version 7,0 et les versions antérieures ne peuvent pas utiliser l’autre emplacement d’instantané.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_copymergesnapshot**.  
  
## <a name="see-also"></a>Voir aussi  
 [Autres emplacements de dossier d’instantanés](../../relational-databases/replication/snapshot-options.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
