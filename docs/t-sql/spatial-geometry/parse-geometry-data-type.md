---
title: Parse (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Parse (geometry Data Type)
ms.assetid: 6e080919-4b64-46cd-8dd2-254a9c232e53
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 91bcf58df4f8dd9651f077c200d69eea2c1f7660
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68101053"
---
# <a name="parse-geometry-data-type"></a>Parse (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne une instance **geometry** à partir d’une représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text). `Parse()` équivaut à [STGeomFromText()](../../t-sql/spatial-geometry/parse-geometry-data-type.md). Toutefois, cela suppose un SRID (ID de référence spatiale) ayant la valeur 0 en tant que paramètre. L'entrée peut contenir des valeurs Z (élévation) et M (mesure) facultatives.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Parse ( 'geometry_tagged_text' )  
```  
  
## <a name="arguments"></a>Arguments  
 *geometry_tagged_text*  
 Représentation WKT de l’instance **geometry** à retourner. *geometry_tagged_text* est une expression **nvarchar**.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
## <a name="remarks"></a>Notes  
 Le type OGC de l’instance **geometry** retournée par `Parse()` a comme valeur l’entrée WKT correspondante.  
  
 La chaîne « Null » est interprétée en tant qu’instance **geometry** ayant une valeur Null.  
  
 Cette méthode lève **FormatException** si l’entrée n’est pas au format approprié.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise la méthode `Parse()` pour créer une instance `geometry`.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::Parse('LINESTRING (100 100, 20 180, 180 180)');  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [STGeomFromText](../../t-sql/spatial-geometry/parse-geometry-data-type.md)   
 [Méthodes geometry statiques étendues](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

