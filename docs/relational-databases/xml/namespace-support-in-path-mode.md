---
title: Prise en charge d’espace de noms en mode PATH | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f75729d1e31989bde851d1fde3a05ab932b6f460
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665031"
---
# <a name="namespace-support-in-path-mode"></a>Prise en charge d'espace de noms en mode PATH
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  La prise en charge des espaces de noms en mode PATH est fournie à l'aide de WITH NAMESPACES. Par exemple, la requête suivante démontre l'utilisation de la syntaxe WITH NAMESPACES pour déclarer un espace de noms ("a:") qui peut ensuite être utilisé dans l'instruction SELECT ultérieure :  
  
```  
WITH XMLNAMESPACES('a' as a)  
SELECT 1 as 'a:b'  
FOR XML PATH  
```  
  
## <a name="examples"></a>Exemples  
 Ces exemples montrent comment utiliser le mode PATH pour générer un document XML à partir d'une requête SELECT. Nombre de ces requêtes sont spécifiées par rapport aux documents XML des instructions de fabrication de bicyclettes stockés dans la colonne Instructions de la table ProductModel.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode PATH avec FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
