---
title: Types de données d’intégration du classement et du CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 40c4abad803424ac9b274045f699785b85689644
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62874844"
---
# <a name="collation-and-clr-integration-data-types"></a>Classement et types de données de l'intégration du CLR
  Dans le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], l'objet `CompareInfo` gère les classements. Les interfaces de programmation d'applications (API) de chaîne du [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] utilisent la propriété `CompareInfo` associée à l'objet `CultureInfo` du thread courant pour effectuer les comparaisons de chaînes. Le paramètre par défaut de `CultureInfo` l’objet est basé sur [!INCLUDE[msCoName](../../includes/msconame-md.md)] les paramètres régionaux Windows de l’ordinateur sur lequel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécute. Cela détermine la sémantique de comparaison par défaut, si aucune propriété `CultureInfo` explicite n'est spécifiée, pour les comparaisons de valeurs `System.String`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne change pas explicitement la propriété `CompareInfo` en classement de la base de données ou du serveur. Si besoin est, les utilisateurs doivent définir la propriété `CompareInfo` appropriée dans leurs routines.  
  
## <a name="parameter-collation"></a>Paramètre Collation  
 Lorsque vous créez une routine CLR et qu'un paramètre d'une méthode CLR liée à la routine est de type `SQLString`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée une instance du paramètre avec le classement par défaut de la base de données qui contient la routine d'appel. Si un paramètre n'est pas un `SqlType` (par exemple, `String` au lieu de `SQLString`), les informations de classement de la base de données ne sont pas associées au paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans le .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  
