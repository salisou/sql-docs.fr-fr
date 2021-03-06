---
title: sysopentapes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysopentapes
- sysopentapes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup media [SQL Server], sysopentapes system table
- sysopentapes system table
ms.assetid: c066ca9b-9cfd-46b1-90a3-5c8dc9e7b6ae
author: stevestein
ms.author: sstein
ms.openlocfilehash: 813592ffa5b67a4926dff611c2ba0e0faf36d273
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68029797"
---
# <a name="sysopentapes-transact-sql"></a>sysopentapes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque unité de bande actuellement ouverte. Cette vue est stockée dans la base de données **Master** .  
  
> [!IMPORTANT]  
>  Cette table système est incluse en tant que vue pour la compatibilité descendante. Utilisez plutôt la vue de gestion dynamique [sys. dm_io_backup_tapes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md) .  
  
> [!NOTE]  
>  Vous ne pouvez pas supprimer la vue **sysopentapes** .  

  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**openTape**|**nvarchar (64)**|Nom de fichier physique de l'unité de bande ouverte. Pour plus d’informations sur l’ouverture et la libération de périphériques à bandes, consultez [BACKUP &#40;Transact-sql&#41;](../../t-sql/statements/backup-transact-sql.md) et [Restore &#40;transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md).|  
  
## <a name="permissions"></a>Autorisations  
 L’utilisateur doit disposer de l’autorisation VIEW SERVER STATE sur le serveur.  
  
  
