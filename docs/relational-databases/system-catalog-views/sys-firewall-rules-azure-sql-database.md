---
title: sys. firewall_rules (Azure SQL Database) | Microsoft Docs
ms.date: 03/26/2019
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.firewall_rules
- firewall_rules
- sys.firewall_rules_TSQL
- firewall_rules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- firewall_rules
- sys.firewall_rules
ms.assetid: 140d2cd8-9aa1-4cc5-870d-e1dbc873b3fe
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 91c3a4101f19afe4a986514fea8dab207c6d9b48
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "70155550"
---
# <a name="sysfirewall_rules-azure-sql-database"></a>sys_firewall_rules (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur les paramètres de pare-feu au niveau [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]du serveur associés à votre.  
  
 La vue `sys.firewall_rules` contient les colonnes suivantes :  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|id|**TIERS**|Identificateur du paramètre de pare-feu au niveau serveur.|  
|name|**NVARCHAR (128)**|Le nom que vous avez choisi pour décrire et distinguer le paramètre de pare-feu au niveau serveur.|  
|start_ip_address|**VARCHAR (45)**|Adresse IP la plus basse dans la plage de paramètres de pare-feu au niveau serveur. Les adresses IP supérieures ou égales à celle-ci peuvent essayer de se connecter au serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. L"adresse IP la plus basse possible est `0.0.0.0`.|  
|end_ip_address|**VARCHAR (45)**|Adresse IP la plus élevée dans la plage de paramètres de pare-feu au niveau serveur. Les adresses IP inférieures ou égales à celle-ci peuvent essayer de se connecter au serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. L"adresse IP la plus élevée possible est `255.255.255.255`.<br /><br /> Remarque : les tentatives de connexion Azure sont autorisées lorsque ce champ et le champ **start_ip_address** est `0.0.0.0`égal à.|  
|create_date|**Date/heure**|Date et heure UTC auxquelles le paramètre de pare-feu au niveau serveur a été créé.<br /><br /> Remarque : l’heure UTC est un acronyme de temps universel coordonné.|  
|modify_date|**Date/heure**|Date et heure UTC auxquelles le paramètre de pare-feu au niveau serveur a été modifié la dernière fois.|  
  
## <a name="remarks"></a>Notes

 Pour renvoyer des informations sur les paramètres de pare-feu au niveau de la base de données associés à votre Microsoft Azure SQL Database, utilisez [sys. database_firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md).  
  
## <a name="permissions"></a>Autorisations

 L’accès en lecture seule à cette vue est disponible pour tous les utilisateurs autorisés à se connecter à la base de données **Master** .  
  
## <a name="see-also"></a>Voir aussi

[sp_set_firewall_rule &#40;Base de données Azure SQL&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)  
[sp_delete_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-firewall-rule-azure-sql-database.md)   
[sp_set_database_firewall_rule &#40;Base de données Azure SQL&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)  
[sp_delete_database_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)  
[sys. database_firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
[Configurer un pare-feu Windows pour l’accès Moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)     
[Configurer un pare-feu pour l’accès FILESTREAM](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)  
[Configurer un pare-feu pour accéder au serveur de rapports](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md) 
