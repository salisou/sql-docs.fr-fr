---
title: Composants génériques et validation de contenu | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- wildcard components [XML]
- content validation [XML]
ms.assetid: ffa7d974-3645-446c-8425-f0b22b6b060a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b824b240c6801317b16ac84820e0fc82054875b0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63193003"
---
# <a name="wildcard-components-and-content-validation"></a>Composants génériques et validation de contenu
  Les composants génériques sont utilisés pour accroître la flexibilité en termes d'éléments pouvant apparaître dans un modèle de contenu. Ils sont pris en charge comme suit dans le langage XSD :  
  
-   Composants génériques éléments. Ils sont représentés par l’élément **\<xsd:any>** .  
  
-   Composants génériques attributs. Ils sont représentés par l’élément **\<xsd:anyAttribute>** .  
  
 Ces deux éléments de caractère générique, **\<xsd:any>** et **\<xsd:anyAttribute>** , prennent en charge l’utilisation d’un attribut **processContents**. Grâce à lui, vous pouvez préciser une valeur indiquant comment les applications XML vont gérer la validation du contenu des documents associé à ces éléments de caractères génériques. Les valeurs possibles et leurs effets sont décrits ci-dessous :  
  
-   La valeur **strict** indique que le contenu est entièrement validé.  
  
-   La valeur **skip** indique que le contenu n'est pas validé.  
  
-   La valeur **lax** indique que sont validés uniquement les éléments et les attributs pour lesquels des définitions de schéma sont disponibles.  
  
## <a name="lax-validation-and-xsanytype-elements"></a>Validation de type lax et éléments xs:anyType  
 La spécification de schéma XML utilise la validation de type **lax** pour les éléments du type **anyType** . Étant donné que [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ne prenait pas en charge la validation de type lax, la validation de type strict était appliquée aux éléments de type **anyType**. À compter de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], la validation de type lax est prise en charge. Le contenu des éléments de type **anyType** sera validé à l'aide de la validation de type lax.  
  
 L'exemple suivant illustre la validation de type lax. L'élément de schéma `e` est de type **anyType** . L'exemple crée des variables **xml** typées et illustre la validation de type lax de l'élément de type **anyType** .  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"   
        targetNamespace="http://ns">  
   <element name="e" type="anyType"/>  
   <element name="a" type="byte"/>  
   <element name="b" type="string"/>  
 </schema>'  
GO  
```  
  
 L'exemple ci-dessous aboutit, car la validation de `<e>` réussit.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>1</a><b>data</b></e>'  
GO  
```  
  
 L'exemple ci-dessous aboutit. L'instance est acceptée, bien qu'aucun élément `<c>` ne soit défini dans le schéma :  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>1</a><c>Wrong</c><b>data</b></e>'  
GO  
```  
  
 L'instance XML dans l'exemple suivant est rejetée car la définition de l'élément `<a>` n'autorise pas de valeur de chaîne.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>Wrong</a><b>data</b></e>'  
SELECT @var  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifications et limitations relatives aux collections de schémas XML sur le serveur](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
