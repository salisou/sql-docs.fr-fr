---
title: Instruction CLEAR CALCULations (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1b0766cb002960a96d702184ac9719abe7610afd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67938022"
---
# <a name="mdx-data-manipulation---clear-calculations"></a>Manipulation de données MDX - CLEAR CALCULATIONS


  Supprime tous les calculs du cube et retourne le cube au test de calcul 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CLEAR CALCULATIONS [FROMCube_Expression]  
```  
  
## <a name="arguments"></a>Arguments  
 *Cube_Expression*  
 Expression de cube MDX (Multidimensional Expressions) valide.  
  
## <a name="remarks"></a>Notes  
 La clause **from** peut être omise lorsque le contexte du cube est connu, par exemple dans un script MDX.  
  
> [!NOTE]  
>  Cette instruction peut uniquement être exécutée par l'administrateur d'un serveur ou d'une base de données, ou bien par le membre d'un rôle ayant accès aux données source du cube (soit ReadSourceData=true)  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de manipulation de données MDX &#40;&#41;MDX](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
