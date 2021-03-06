---
title: Types de données d’intégration du classement et du CLR | Microsoft Docs
description: Dans SQL Server l’intégration du CLR, les API de chaîne .NET Framework utilisent la propriété CompareInfo de CultureInfo du thread actuel pour effectuer des comparaisons de chaînes.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
author: rothja
ms.author: jroth
ms.openlocfilehash: 46e4d450db90e4bfc93187a48ca8adae472036c6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488486"
---
# <a name="collation-and-clr-integration-data-types"></a>Classement et types de données de l'intégration du CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Dans [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], l’objet **CompareInfo** gère les classements. Les [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] interfaces de programmation d’application (API) de chaîne utilisent la propriété **CompareInfo** associée à l’objet **CultureInfo** du thread actuel pour effectuer des comparaisons de chaînes. Le paramètre par défaut de l’objet **CultureInfo** est basé sur [!INCLUDE[msCoName](../../includes/msconame-md.md)] les paramètres régionaux Windows de l’ordinateur sur lequel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécute. Cela détermine la sémantique de comparaison par défaut, si aucun **CultureInfo** explicite n’est spécifié, pour les comparaisons de valeurs **System. String** . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ne change pas explicitement la propriété **CompareInfo** en classement de base de données ou de serveur. Si nécessaire, les utilisateurs doivent définir la propriété **CompareInfo** appropriée dans leurs routines.  
  
## <a name="parameter-collation"></a>Paramètre Collation  
 Lorsque vous créez une routine de Common Language Runtime (CLR) et qu’un paramètre d’une méthode CLR liée à la routine est de **SQLString**type SqlString [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , crée une instance du paramètre avec le classement par défaut de la base de données qui contient la routine d’appel. Si un paramètre n’est pas un **SQLType** (par exemple, **String** plutôt que **SqlString**), les informations de classement de la base de données ne sont pas associées au paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans le .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
