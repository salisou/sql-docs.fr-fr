---
title: sys. dm_external_script_requests | Microsoft Docs
ms.custom: ''
ms.date: 10/28/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_external_script_requests
- sys.dm_external_script_requests_TSQL
- dm_external_script_requests
- dm_external_script_requests_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_external_script_requests dynamic management view
ms.assetid: e7e7c50f-b8b2-403c-b8c8-1955da5636c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 70f1024f73ff955facaa2b6a2af2b9f5f4ccf247
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488198"
---
# <a name="sysdm_external_script_requests"></a>Sys.dm_external_script_requests
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Renvoie une ligne pour chaque compte de travail actif qui exécute un script externe.
  
> [!NOTE] 
>  
> Cette vue de gestion dynamique (DMV) est disponible uniquement si vous avez installé et activé la fonctionnalité qui prend en charge l’exécution de scripts externes. Pour plus d’informations, consultez [R services dans SQL Server 2016](../../machine-learning/r/sql-server-r-services.md) et [machine learning services (r, Python) dans SQL Server 2017 et versions ultérieures](../../machine-learning/sql-server-machine-learning-services.md).  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|external_script_request_id|**Identificateur unique**|ID du processus qui a envoyé la demande de script externe. Cela correspond à l’ID de processus tel qu’il a été reçu par[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]|  
|langage|**nvarchar**|Mot clé qui représente un langage de script pris en charge. |  
|degree_of_parallelism|**int**|Nombre indiquant le nombre de traitements parallèles qui ont été créés. Cette valeur peut être différente du nombre de traitements parallèles qui ont été demandés.|  
|external_user_name|**nvarchar**|Le compte de travail Windows sous lequel le script a été exécuté.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation VIEW SERVER STATE sur le serveur.  
  
> [!NOTE]
>   
>  Les utilisateurs qui exécutent des scripts externes doivent avoir l’autorisation supplémentaire EXECUTE ANY EXTERNAL SCRIPT, toutefois, cette vue de gestion dynamique peut être utilisée par les administrateurs sans cette autorisation. 
  
## <a name="remarks"></a>Notes  

Cette vue peut être filtrée à l’aide de l’identificateur de langage de script.

La vue renvoie également le compte de travail sous lequel le script est en cours d’exécution. Pour plus d’informations sur les comptes de travail utilisés par les scripts externes, voir la section identités utilisées en traitement (SQLRUserGroup) dans [vue d’ensemble de la sécurité de l’infrastructure d’extensibilité dans SQL Server machine learning services](../../machine-learning/concepts/security.md#sqlrusergroup).

Le GUID renvoyé dans le champ **external_script_request_id** représente également le nom de fichier du répertoire sécurisé où sont stockés les fichiers temporaires. Chaque compte de travail, tel que MSSQLSERVER01 représente une connexion SQL unique ou un utilisateur Windows et peut être utilisé pour exécuter plusieurs demandes de script. Par défaut, ces fichiers temporaires sont nettoyés après l’achèvement du script demandé.
 
Cette vue de gestion dynamique surveille uniquement les processus actifs et ne peut pas générer de rapports sur des scripts déjà effectués. Si vous avez besoin de suivre la durée des scripts, nous vous recommandons d’ajouter des informations de durée à votre script et de les capturer dans le cadre de l’exécution du script.

## <a name="examples"></a>Exemples  
  
### <a name="viewing-the-currently-active-r-scripts-for-a-particular-process"></a>Afficher les scripts R actuellement actifs pour un processus particulier 
 L’exemple suivant affiche le nombre d’exécutions de scripts externes en cours d’exécution sur l’instance actuelle.  
  
```  
SELECT external_script_request_id 
  , [language]
  , degree_of_parallelism
  , external_user_name
FROM sys.dm_external_script_requests; 
```  

Résultats  


external_script_request_id  |langage  |degree_of_parallelism  |external_user_name  
---------|---------|---------|---------
183EE6FC-7399-4318-AA2E-7A6C68E435A8     |     R    |      1   |  MSSQLSERVER01       


  
## <a name="see-also"></a>Voir aussi  
 [Vues et fonctions de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Fonctions et vues de gestion dynamique relatives aux exécutions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[sys. dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  

