---
title: Utilisation des fonctions tuple | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9a329c8786ce580469e4601709509ca8a2de73f6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68037981"
---
# <a name="using-tuple-functions"></a>Utilisation de fonctions de tuple


  Une fonction de tuple récupère un tuple à partir d'un jeu ou en résolvant la représentation sous forme de chaîne d'un tuple.  
  
 Les fonctions de tuple, comme les fonctions de membre et les fonctions de définition, sont essentielles à la négociation des structures multidimensionnelles présentes dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Il existe trois fonctions de tuple dans MDX, [en cours &#40;mdx&#41;](../mdx/current-mdx.md), [Item &#40;tuple&#41; &#40;MDX&#41;](../mdx/item-tuple-mdx.md) et [StrToTuple &#40;MDX ](../mdx/strtotuple-mdx.md)&#41;. L'exemple de requête suivant montre comment les utiliser :  
  
 `WITH`  
  
 `//Creates a set of tuples consisting of Years and Countries`  
  
 `SET MyTuples AS  [Date].[Calendar Year].[Calendar Year].MEMBERS * [Customer].[Country].[Country].MEMBERS`  
  
 `//Returns a string representation of that set using the Current and Generate functions`  
  
 `MEMBER MEASURES.CURRENTDEMO AS GENERATE(MyTuples, TUPLETOSTR(MyTuples.CURRENT), ", ")`  
  
 `//Retrieves the fourth tuple from that set and displays it as a string`  
  
 `MEMBER MEASURES.ITEMDEMO AS TUPLETOSTR(MyTuples.ITEM(3))`  
  
 `//Creates a tuple consisting of the measure Internet Sales Amount and the country Australia from a string`  
  
 `MEMBER MEASURES.STRTOTUPLEDEMO AS STRTOTUPLE("([Measures].[Internet Sales Amount]" + ", [Customer].[Country].&[Australia])")`  
  
 `SELECT{MEASURES.CURRENTDEMO,MEASURES.ITEMDEMO,MEASURES.STRTOTUPLEDEMO} ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;syntaxe MDX&#41;](../mdx/functions-mdx-syntax.md)   
 [Utilisation des fonctions membres](../mdx/using-member-functions.md)   
 [Utilisation de fonctions de jeu](../mdx/using-set-functions.md)  
  
  
