---
title: Plan Guide Successful, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Plan Guide Successful event class
ms.assetid: fecfbb6c-56c9-4db4-84d3-00d6e338355a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 56157ce2c29a95d35198ab44835b50e45d7831a4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62827202"
---
# <a name="plan-guide-successful-event-class"></a>Plan Guide Successful, classe d'événements
  La classe d'événements Plan Guide Successful indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a produit correctement un plan d'exécution pour une requête ou un lot qui contenait un repère de plan. L'événement est déclenché lorsque les conditions suivantes sont remplies :  
  
-   Le module ou le lot dans la définition de repère de plan correspond au module ou lot exécuté.  
  
-   La requête dans la définition de repère de plan correspond à la requête exécutée.  
  
-   Les indicateurs dans la définition de repère de plan, y compris l'indicateur USE PLAN, n'ont pas été appliqués correctement à la requête. Autrement dit, le plan de requête compilé honore les indicateurs spécifiés.  
  
## <a name="plan-guide-successful-event-class-data-columns"></a>Colonnes de données de la classe d'événements Plan Guide Successful  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie par des valeurs transmises par l'application et non pas du nom affiché du programme.|10|Oui|  
|ClientProcessID|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. La colonne de données est remplie si le client fournit l'ID du processus client.|9|Oui|  
|DatabaseID|`int`|ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance indiquée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données ServerName est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|nom_base_de_données|`nvarchar`|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|EventClass|`int`|Type d'événement = 214.|27|Non|  
|EventSequence|`int`|Séquence d'un événement spécifique dans la demande.|51|Non|  
|HostName|`nvarchar`|Nom de l'ordinateur sur lequel le client est exécuté. La colonne de données est remplie si le client fournit le nom de l'hôte. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|IsSystem|`int`|Indique si l'événement s'est produit dans un processus système ou un processus utilisateur : 1 = système, 0 = utilisateur.|60|Oui|  
|LoginName|`nvarchar`|Nom de la connexion de l’utilisateur (soit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la connexion de sécurité [!INCLUDE[msCoName](../../includes/msconame-md.md)] , soit les informations d’identification de connexion Windows\\sous la forme domaine*nom*d’utilisateur).|11|Oui|  
|LoginSid|`image`|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Ces informations se trouvent dans les vues de catalogue [sys.server_principals](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql) ou [sys.sql_logins](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql) . Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|NTDomainName|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|NTUserName|`nvarchar`|Nom d'utilisateur Windows.|6|Oui|  
|ObjectID|`int`|ID d'objet du module compilé lorsque le repère de plan a été appliqué. Si le repère de plan n'a pas été appliqué à un module, cette colonne a la valeur NULL.|22|Oui|  
|RequestID|`int`|ID de la demande qui contient l'instruction.|49|Oui|  
|ServerName|`nvarchar`|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|Non|  
|SessionLoginName|`nvarchar`|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant le nom Connexion1 et que vous exécutez une instruction en tant que Connexion2, SessionLoginName affiche Connexion1 et LoginName, Connexion2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|SPID|`int`|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|StartTime|`datetime`|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|TextData|`ntext`|Nom du repère de plan.|1|Oui|  
|TransactionID|`bigint`|ID affecté par le système à la transaction.|4|Oui|  
|XactSequence|`bigint`|Jeton qui décrit la transaction en cours.|50|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Plan Guide Unsuccessful (classe d’événements)](plan-guide-unsuccessful-event-class.md)   
 [Événements étendus](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
