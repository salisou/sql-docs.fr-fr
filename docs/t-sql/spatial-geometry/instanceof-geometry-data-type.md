---
title: InstanceOf (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- InstanceOf
- InstanceOf_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- InstanceOf (geometry Data Type)
ms.assetid: fdea1248-29a4-4bab-a60d-a1b359b5e109
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 7eee6c8aa847a199f7b1547f61bbcd523039644f
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68101241"
---
# <a name="instanceof-geometry-data-type"></a>InstanceOf (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Méthode qui teste si l’instance **geometry** est du même type que l’instance spécifiée. Retourne 1 si le type de l’instance **geometry** est identique au type spécifié. Cette méthode retourne également 1 si le type spécifié est un ancêtre du type d’instance. Sinon, elle retourne 0.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.InstanceOf (geometry_type )  
```  
  
## <a name="arguments"></a>Arguments  
*geometry_type*  
Chaîne **nvarchar(4000)** spécifiant l’un des 15 types exposés dans la hiérarchie de type **geometry**.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **bit**  
  
 Type de retour CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Notes  
 L’entrée de la méthode doit être l’un des types suivants : **Geometry**, **Point**, **Curve**, **LineString**, **CircularString**, **CompoundCurve**, **Surface**, **Polygon**, **CurvePolygon**, **GeometryCollection**, **MultiSurface**, **MultiPolygon**, **MultiCurve**, **MultiLineString** ou **MultiPoint**. Cette méthode lève **ArgumentException** si d’autres chaînes sont utilisées en entrée.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `MultiPoint` et utilise `InstanceOf()` pour voir si l'instance est un `GeometryCollection`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT(0 0, 13.5 2, 7 19)', 0);  
SELECT @g.InstanceOf('GEOMETRYCOLLECTION');  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur des instances geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

