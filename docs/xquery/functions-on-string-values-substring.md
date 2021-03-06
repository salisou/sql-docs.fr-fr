---
title: Fonction SUBSTRING (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- substring function [XQuery]
- fn:substring function
ms.assetid: 2b3b8651-de51-46dc-af82-c86c45eac871
author: rothja
ms.author: jroth
ms.openlocfilehash: 2188cff20411fe90d4858763f65cff7f6fe9c9d1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68004641"
---
# <a name="functions-on-string-values---substring"></a>Fonctions sur les valeurs de chaîne : substring
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne une partie de la valeur de *$sourceString*, en commençant à la position indiquée par la valeur de *$startingLoc* et continue pour le nombre de caractères indiqué par la valeur de *$Length*.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
fn:substring($sourceString as xs:string?,  
                          $startingLoc as xs:decimal?) as xs:string?  
  
fn:substring($sourceString as xs:string?,  
                          $startingLoc as xs:decimal?,  
                          $length as xs:decimal?) as xs:string?  
```  
  
## <a name="arguments"></a>Arguments  
 *$sourceString*  
 Chaîne source.  
  
 *$startingLoc*  
 Point de départ dans la chaîne source à partir duquel la sous-chaîne commence. Si cette valeur est inférieure ou égale à 0, seuls les caractères dans des positions supérieures à zéro sont retournés. Si la valeur est supérieure à la longueur de la *$sourceString*, la chaîne de longueur nulle est retournée.  
  
 *$length*  
 [facultatif] Nombre de caractères à extraire. S’il n’est pas spécifié, elle retourne tous les caractères de l’emplacement spécifié dans *$startingLoc* jusqu’à la fin de la chaîne.  
  
## <a name="remarks"></a>Notes  
 La version à trois arguments de la fonction retourne les caractères de `$sourceString` dont la position `$p` obéit à :  
  
 `fn:round($startingLoc) <= $p < fn:round($startingLoc) + fn:round($length)`  
  
 La valeur de *$Length* peut être supérieure au nombre de caractères de la valeur de *$sourceString* après la position de début. Dans ce cas, la sous-chaîne retourne les caractères jusqu’à la fin de *$sourceString*.  
  
 Le premier caractère d'une chaîne se trouve à la position 1.  
  
 Si la valeur de *$sourceString* est la séquence vide, elle est gérée comme une chaîne de longueur nulle. Dans le cas contraire, si *$startingLoc* ou *$Length* est une séquence vide, la séquence vide est retournée.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caractères supplémentaires (paires de substitution)  
 Le comportement de la paire de substitution dans des fonctions XQuery dépend du niveau de compatibilité de la base de données et, dans certains cas, de l'URI de l'espace de noms par défaut des fonctions. Pour plus d’informations, consultez la section « les fonctions XQuery prennent en charge les substitutions » dans la rubrique [modifications avec rupture des fonctionnalités de moteur de base de données dans SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md). Consultez également [niveau de compatibilité ALTER database &#40;&#41;Transact-SQL](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) et la [prise en charge d’Unicode et du classement](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="implementation-limitations"></a>Limites de mise en œuvre  
 SQL Server nécessite que les paramètres *$startingLoc* et *$Length* soient de type xs : decimal au lieu de XS : double.  
  
 SQL Server permet à *$startingLoc* et *$Length* d’être la séquence vide, car la séquence vide est une valeur possible suite au mappage des erreurs dynamiques à ().  
  
## <a name="examples"></a>Exemples  
 Cette rubrique fournit des exemples de XQuery relatifs à des instances **xml** XML stockées dans différentes colonnes [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] de type XML dans la base de données.  
  
### <a name="a-using-the-substring-xquery-function-to-retrieve-partial-summary-product-model-descriptions"></a>A. Utilisation de la fonction XQuery substring() pour extraire une synthèse partielle des descriptions de modèles de produits.  
 La requête récupère les 50 premiers caractères du texte qui décrivent le modèle de produit, le <`Summary`> élément dans le document.  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
    <Prod>{ substring(string((/pd:ProductDescription/pd:Summary)[1]), 1, 50) }</Prod>  
 ') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('/pd:ProductDescription')  = 1;  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   La fonction **String ()** retourne la valeur de chaîne de l' `Summary` élément<>. Cette fonction est utilisée, parce que l' `Summary` élément <> contient à la fois le texte et les sous-éléments (éléments de mise en forme html) et que vous ignorez ces éléments et récupérez tout le texte.  
  
-   La fonction **Substring ()** récupère les 50 premiers caractères de la valeur de chaîne récupérée par la **chaîne ()**.  
  
 Voici un extrait du résultat :  
  
```  
ProductModelID Result  
-------------- ----------------------------------------------------  
19      <Prod>Our top-of-the-line competition mountain bike.</Prod>   
23      <Prod>Suitable for any type of riding, on or off-roa</Prod>  
...  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions XQuery impliquant le type de données xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
