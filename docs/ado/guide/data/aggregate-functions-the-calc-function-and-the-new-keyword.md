---
title: Fonctions d’agrégation, fonction CALC et mot clé NEW | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data shaping [ADO], functions
- CALC function [ADO]
- NEW keyword [ADO]
- aggregate functions [ADO]
ms.assetid: 0590b466-2a36-49a2-868e-028ef5e49394
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5a7ed836b9b57ddd690dd85dd94cc12cb967c472
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926007"
---
# <a name="aggregate-functions-the-calc-function-and-the-new-keyword"></a>Fonctions d’agrégation, fonction CALC et mot clé NEW
La mise en forme des données prend en charge les fonctions suivantes. Le nom affecté au chapitre contenant la colonne à utiliser est l' *alias du chapitre*.  
  
 Un alias-Chapter peut être complet, constitué de chaque nom de colonne de chapitre menant au chapitre contenant le *nom de colonne,* tous séparés par des points. Par exemple, si le chapitre parent, chap1, contient un chapitre enfant, Chap2, qui a une colonne Amount, AMT, le nom qualifié est chap1. Chap2. AMT.  
  
|Fonctions d’agrégation|Description|  
|-------------------------|-----------------|  
|SOMME (*alias-Chapter*.* nom de colonne*)|Calcule la somme de toutes les valeurs dans la colonne spécifiée.|  
|AVG (*alias-Chapter*.* nom de colonne*)|Calcule la moyenne de toutes les valeurs dans la colonne spécifiée.|  
|MAX (*alias-Chapter*.* nom de colonne*)|Calcule la valeur maximale dans la colonne spécifiée.|  
|MIN (*Chapter-alias*.* nom de colonne*)|Calcule la valeur minimale dans la colonne spécifiée.|  
|COUNT (*alias-Chapter*[.* Column-Name*])|Compte le nombre de lignes dans l’alias spécifié. Si une colonne est spécifiée, seules les lignes pour lesquelles cette colonne est non NULL sont incluses dans le nombre.|  
|ECARTYPE (*alias-Chapter*.* nom de colonne*)|Calcule l’écart type de la colonne spécifiée.|  
|ANY (*alias-chapitre)*.* nom de colonne*)|Valeur de la colonne spécifiée. ANY a une valeur prévisible uniquement lorsque la valeur de la colonne est la même pour toutes les lignes du chapitre.<br /><br /> **Remarque** Si la colonne ne contient pas la même valeur pour toutes les lignes du chapitre, la commande SHAPE retourne arbitrairement l’une des valeurs pour être la valeur de la fonction ANY.|  
  
|Expression calculée|Description|  
|---------------------------|-----------------|  
|CALC (*expression*)|Calcule une expression arbitraire, mais uniquement sur la ligne de l’ensemble d' **enregistrements** contenant la fonction Calc. Toute expression utilisant ces [fonctions Visual Basic pour applications (VBA)](../../../ado/guide/data/visual-basic-for-applications-functions.md) est autorisée.|  
  
|Mot clé NEW|Description|  
|-----------------|-----------------|  
|NEW *Field-type* [(*largeur* &#124; *échelle* &#124; *précision* &#124; *erreur* [, mise à l' *échelle* &#124; *erreur*])]|Ajoute une colonne vide du type spécifié à l’ensemble d' **enregistrements**.|  
  
 Le *type de champ* passé avec le mot clé New peut être l’un des types de données suivants.  
  
|Types de données OLE DB|Équivalent (s) de type de données ADO|  
|-----------------------|-----------------------------------|  
|DBTYPE_BSTR|adBSTR|  
|DBTYPE_BOOL|adBoolean|  
|DBTYPE_DECIMAL|adDecimal|  
|DBTYPE_UI1|adUnsignedTinyInt|  
|DBTYPE_I1|adTinyInt|  
|DBTYPE_UI2|adUnsignedSmallInt|  
|DBTYPE_UI4|adUnsignedInt|  
|DBTYPE_I8|adBigInt|  
|DBTYPE_UI8|adUnsignedBigInt|  
|DBTYPE_GUID|adGuid|  
|DBTYPE_BYTES|adBinary, AdVarBinary, adLongVarBinary|  
|DBTYPE_STR|adChar, adVarChar, adLongVarChar|  
|DBTYPE_WSTR|adWChar, adVarWChar, adLongVarWChar|  
|DBTYPE_NUMERIC|adNumeric|  
|DBTYPE_DBDATE|adDBDate|  
|DBTYPE_DBTIME|adDBTime|  
|DBTYPE_DBTIMESTAMP|adDBTimeStamp|  
|DBTYPE_VARNUMERIC|adVarNumeric|  
|DBTYPE_FILETIME|adFileTime|  
|DBTYPE_ERROR|adError|  
  
 Lorsque le nouveau champ est de type Decimal (dans OLE DB, DBTYPE_DECIMAL ou dans ADO, adDecimal), vous devez spécifier les valeurs de précision et d’échelle.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de mise en forme des données](../../../ado/guide/data/data-shaping-example.md)   
 [Grammaire de forme formelle](../../../ado/guide/data/formal-shape-grammar.md)   
 [Généralités sur les commandes SHAPE](../../../ado/guide/data/shape-commands-in-general.md)
