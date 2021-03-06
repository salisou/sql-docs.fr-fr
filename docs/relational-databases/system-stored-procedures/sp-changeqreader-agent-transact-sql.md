---
title: sp_changeqreader_agent (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changeqreader_agent_TSQL
- sp_changeqreader_agent
helpviewer_keywords:
- sp_changeqreader_agent
ms.assetid: d3fe79c5-31ef-4565-bf38-b476b5fb16f7
author: stevestein
ms.author: sstein
ms.openlocfilehash: b636eb929d74aec7b0f3555ce511372f6592c5b0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68099140"
---
# <a name="sp_changeqreader_agent-transact-sql"></a>sp_changeqreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les propriétés de sécurité d'un Agent de lecture de la file d'attente. Cette procédure stockée est exécutée sur la base de données de distribution du serveur de distribution ou sur la base de publication du serveur de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_changeqreader_agent [ [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @frompublisher = ] frompublisher   
```  
  
## <a name="arguments"></a>Arguments  
`[ @job_login = ] 'job_login'`Nom de connexion du compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l’agent s’exécute. *job_login* est de type **nvarchar (257)**, avec NULL comme valeur par défaut.  
  
`[ @job_password = ] 'job_password'`Mot de passe du compte Windows sous lequel l’agent s’exécute. *job_password* est de **type sysname**, avec NULL comme valeur par défaut.  
  
`[ @frompublisher = ] frompublisher`Indique si la procédure est exécutée sur le serveur de publication. *frompublisher* est de bits, avec **0**comme valeur par défaut. La valeur **1** signifie que la procédure est exécutée à partir du serveur de publication sur la base de données de publication.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_changeqreader_agent** est utilisé dans la réplication transactionnelle.  
  
 **sp_changeqreader_agent** est utilisé pour modifier le compte Windows sous lequel un agent de lecture de la file d’attente s’exécute. Vous pouvez changer le mot de passe d'une connexion Windows existante ou fournir une nouvelle connexion et un nouveau mot de passe Windows.  
  
 Après avoir modifié le nom de connexion ou le mot de passe d'un Agent, vous devez arrêter et redémarrer celui-ci avant que la modification prenne effet.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_changeqreader_agent**.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les paramètres de sécurité de la réplication](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_addqreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md)  
  
  
