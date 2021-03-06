---
title: INFORMATION_SCHEMA. SCHEMATA retourne des noms de schéma dans une base de données, et non des bases de données dans une instance | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0e3683ee043785ec6adc349ac52301280c7bc2b8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66094727"
---
# <a name="information_schemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a>INFORMATION_SCHEMA.SCHEMATA retourne les noms de schémas dans une base de données, pas les bases de données dans une instance
  Le Conseiller de mise à niveau a détecté des instructions faisant référence à la vue INFORMATION_SCHEMA.SCHEMATA. Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cette vue retourne toutes les bases de données d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure, la vue retourne tous les schémas d'une base de données.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la vue INFORMATION_SCHEMA.SCHEMATA retourne toutes les bases de données d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La vue retourne tous les schémas d'une base de données, conformément à la norme SQL.  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez votre application pour qu’elle fasse référence à l’affichage catalogue **sys. databases** afin de retourner toutes les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]bases de données d’une instance de.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
