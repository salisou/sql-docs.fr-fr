---
title: sys. dm_pdw_exec_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 4f4ebcbf84da7d899b4d4cbd861cfb2ae3f75863
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82087559"
---
# <a name="sysdm_pdw_exec_requests-transact-sql"></a>sys. dm_pdw_exec_requests (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations sur toutes les demandes actuellement ou récemment [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]actives dans. Elle répertorie une ligne par requête/requête.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Clé pour cette vue. ID numérique unique associé à la demande.|Unique pour toutes les demandes dans le système.|  
|session_id|**nvarchar(32)**|ID numérique unique associé à la session dans laquelle cette requête a été exécutée. Consultez [sys. dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|status|**nvarchar(32)**|État actuel de la demande.|« Running », « Suspended », « Completed », « Canceled », « failed ».|  
|submit_time|**datetime**|Heure à laquelle la demande a été soumise pour exécution.|**DateTime** valide, plus petit ou égal à l’heure actuelle et à la start_time.|  
|start_time|**datetime**|Heure à laquelle l’exécution de la requête a été démarrée.|NULL pour les demandes mises en file d’attente ; dans le cas contraire, la valeur **DateTime** valide est inférieure ou égale à l’heure actuelle.|  
|end_compile_time|**datetime**|Heure à laquelle le moteur a terminé la compilation de la requête.|NULL pour les requêtes qui n’ont pas encore été compilées ; Sinon, une valeur **DateTime** valide inférieure à start_time et inférieure ou égale à l’heure actuelle.|
|end_time|**datetime**|Heure à laquelle l’exécution de la requête s’est terminée, a échoué ou a été annulée.|NULL pour les demandes en file d’attente ou actives ; dans le cas contraire, un **DateTime** valide est plus petit ou égal à l’heure actuelle.|  
|total_elapsed_time|**int**|Temps écoulé durant l’exécution depuis le début de la demande, en millisecondes.|Entre 0 et la différence entre start_time et end_time.</br></br> Si total_elapsed_time dépasse la valeur maximale d’un entier, total_elapsed_time sera toujours la valeur maximale. Cette condition génère l’avertissement « la valeur maximale a été dépassée ».</br></br> La valeur maximale en millisecondes est identique à 24,8 jours.|  
|label|**nvarchar(255)**|Chaîne d’étiquette facultative associée à certaines instructions de requête SELECT.|Toute chaîne contenant « a-z », « A-Z », « 0-9 », « _ ».|  
|error_id|**nvarchar (36)**|ID unique de l’erreur associée à la demande, le cas échéant.|Consultez [sys. dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); Affectez la valeur NULL si aucune erreur ne s’est produite.|  
|database_id|**int**|Identificateur de la base de données utilisée par le contexte explicite (par exemple, utilisez DB_X).|Consultez ID dans [sys. databases &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|command|**nvarchar(4000)**|Contient le texte complet de la demande, tel qu’il est soumis par l’utilisateur.|Tout texte de requête ou de requête valide. Les requêtes dont la taille est supérieure à 4000 octets sont tronquées.|  
|resource_class|**nvarchar(20**|Groupe de charge de travail utilisé pour cette demande. |Classes de ressources statiques</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80</br>            </br>Classes de ressources dynamiques</br>SmallRC</br>MediumRC</br>LargeRC</br>XLargeRC|
|importance|**nvarchar(128)**|Importance du paramètre de requête exécutée sur.  Il s’agit de l’importance relative d’une demande dans ce groupe de charges de travail et entre les groupes de charge de travail pour les ressources partagées.  L’importance spécifiée dans le classifieur remplace le paramètre d’importance du groupe de charge de travail.</br>S’applique à : Azure SQL Data Warehouse|NULL</br>low</br>below_normal</br>normal (par défaut)</br>above_normal</br>high|
|group_name|**sysname** |Pour les demandes qui utilisent des ressources, group_name est le nom du groupe de charge de travail sous lequel la requête s’exécute.  Si la demande n’utilise pas de ressources, group_name a la valeur null.</br>S’applique à : Azure SQL Data Warehouse|
|classifier_name|**sysname**|Pour les demandes qui utilisent des ressources, nom du classifieur utilisé pour assigner des ressources et leur importance.||
|resource_allocation_percentage|**décimal (5, 2)**|Pourcentage de ressources allouées à la demande.</br>S’applique à : Azure SQL Data Warehouse|
|result_cache_hit|**nombres**|Indique si une requête terminée a utilisé le cache du jeu de résultats.  </br>S’applique à : Azure SQL Data Warehouse| 1 = accès au cache de l’ensemble de résultats </br> 0 = absence dans le cache du jeu de résultats </br> Valeurs négatives = raisons pour lesquelles la mise en cache du jeu de résultats n’a pas été utilisée.  Pour plus d’informations, consultez la section Notes.|
||||
  
## <a name="remarks"></a>Notes 
 Pour plus d’informations sur le nombre maximal de lignes conservées par cette vue, consultez la section métadonnées dans la rubrique [limites de capacité](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) .

 Le result_cache_hit est un masque de masque de l’utilisation d’une requête du cache de jeu de résultats.  Cette colonne peut être [| (Opérateur or au niveau du bit)](../../t-sql/language-elements/bitwise-or-transact-sql.md) produit d’une ou plusieurs des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|**1**|Accès au cache du jeu de résultats|  
|-**0x00**|Absence dans le cache du jeu de résultats|  
|-**0x01**|La mise en cache du jeu de résultats est désactivée sur la base de données.|  
|-**0x02**|La mise en cache du jeu de résultats est désactivée sur la session. | 
|-**0x04**|La mise en cache du jeu de résultats est désactivée en raison de l’absence de sources de données pour la requête.|  
|-**0x08**|La mise en cache du jeu de résultats est désactivée en raison des prédicats de sécurité au niveau des lignes.|  
|-**0x10**|La mise en cache du jeu de résultats est désactivée en raison de l’utilisation d’une table système, d’une table temporaire ou d’une table externe dans la requête.|  
|-**0x20**|La mise en cache du jeu de résultats est désactivée, car la requête contient des constantes d’exécution, des fonctions définies par l’utilisateur ou des fonctions non déterministes.|  
|-**0x40**|La mise en cache du jeu de résultats est désactivée, car la taille estimée du jeu de résultats est >10 Go.|  
|-**0x80**|La mise en cache du jeu de résultats est désactivée, car le jeu de résultats contient des lignes de grande taille (>64 Ko).|  
  
## <a name="permissions"></a>Autorisations

 Requiert l'autorisation VIEW SERVER STATE.  
  
## <a name="security"></a>Sécurité

 sys. dm_pdw_exec_requests ne filtre pas les résultats de la requête en fonction des autorisations spécifiques à la base de données. Les connexions avec l’autorisation VIEW SERVER STATE peuvent obtenir des résultats de requête de résultats pour toutes les bases de données  
  
>[!WARNING]  
>Une personne malveillante peut utiliser sys. dm_pdw_exec_requests pour récupérer des informations sur des objets de base de données spécifiques en ayant simplement l’autorisation VIEW SERVER STATE et en n’ayant pas d’autorisation propre à la base de données.  
  
## <a name="see-also"></a>Voir aussi

 [SQL Data Warehouse et les vues de gestion dynamique Data Warehouse parallèles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)
