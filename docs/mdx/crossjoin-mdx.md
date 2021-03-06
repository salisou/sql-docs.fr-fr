---
title: Crossjoin (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 63de71ae82e60b8ec7d8a39e18f89e6bd2393f2d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68892947"
---
# <a name="crossjoin-mdx"></a>Crossjoin (MDX)


  Retourne le produit croisé d'un ou plusieurs jeux.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Standard syntax  
Crossjoin(Set_Expression1 ,Set_Expression2 [,...n] )  
  
Alternate syntax  
Set_Expression1 * Set_Expression2 [* ...n]  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Set_Expression2*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
## <a name="remarks"></a>Notes  
 La fonction **CrossJoin** retourne le produit croisé de deux ou plusieurs jeux spécifiés. L'ordre des tuples dans le jeu résultant dépend de l'ordre des jeux à joindre et de l'ordre de leurs membres. Par exemple, lorsque le premier jeu est composé de {x1, x2,..., x*n*} et que le deuxième jeu est {Y1, Y2,..., y*n*}, le produit croisé de ces jeux est le suivant :  
  
 {(x1, Y1), (x1, Y2),..., (x1, y*n*), (x2, Y1), (x2, y2),...,  
  
 (x2, y*n*),..., (x*n*, Y1), (x*n*, Y2),..., (xn, y*n*)}  
  
> [!IMPORTANT]  
>  Si les jeux dans la jointure croisée se composent de tuples issus de différentes hiérarchies d'attribut au sein de la même dimension, cette fonction retourne uniquement les tuples réellement existants. Pour plus d’informations, consultez [concepts clés dans MDX &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services).  
  
## <a name="examples"></a>Exemples  
 La requête suivante affiche des exemples simples de l'utilisation de la fonction Crossjoin sur les axes de colonnes et de lignes d'une requête :  
  
 `SELECT`  
  
 `[Customer].[Country].Members *`  
  
 `[Customer].[State-Province].Members`  
  
 `ON 0,`  
  
 `Crossjoin(`  
  
 `[Date].[Calendar Year].Members,`  
  
 `[Product].[Category].[Category].Members)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE Measures.[Internet Sales Amount]`  
  
 L'exemple suivant affiche le filtrage automatique qui a lieu lorsque les hiérarchies différentes de la même dimension sont des jointures croisées :  
  
 `SELECT`  
  
 `Measures.[Internet Sales Amount]`  
  
 `ON 0,`  
  
 `//Only the dates in Calendar Years 2003 and 2004 will be returned here`  
  
 `Crossjoin(`  
  
 `{[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]},`  
  
 `[Date].[Date].[Date].Members)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 Les trois exemples ci-après retournent les mêmes résultats, soit la mesure Internet Sales Amount (volume de vente Internet) par état pour les états des États-Unis. Les deux premiers utilisent les deux syntaxes de jointure croisée ; le troisième démontre l'utilisation de la clause WHERE pour le retour des mêmes informations.  
  
### <a name="example-1"></a>Exemple 1  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
       [Customer].[State-Province].Members  
   ) ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
### <a name="example-2"></a>Exemple 2  
  
```  
SELECT   
   [Customer].[Country].[United States] *   
      [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
### <a name="example-3"></a>Exemple 3  
  
```  
SELECT   
   [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE (Measures.[Internet Sales Amount],  
   [Customer].[Country].[United States])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
