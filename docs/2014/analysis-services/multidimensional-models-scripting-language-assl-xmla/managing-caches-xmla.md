---
title: Gestion des caches (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 72e36e7d8f0efc9880d0dd164a253030712ee120
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62727585"
---
# <a name="managing-caches-xmla"></a>Gestion des caches (XMLA)
  Vous pouvez utiliser la commande [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) dans XML for Analysis (XMLA) pour effacer le cache d’une dimension ou d’une partition spécifiée. L’effacement du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cache force à reconstruire le cache pour cet objet.  
  
## <a name="specifying-objects"></a>Spécification d'objets  
 La propriété [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) de la `ClearCache` commande peut contenir une référence d’objet uniquement pour l’un des objets suivants. Si une référence d'objet désigne un objet différent de ceux mentionnés ci-dessous, une erreur se produit :  
  
 Base de données  
 Efface le cache pour l'ensemble des dimensions et des partitions contenues dans la base de données.  
  
 Dimension  
 Efface le cache pour la dimension spécifiée.  
  
 Cube  
 Efface le cache pour l'ensemble des partitions contenues dans les groupes de mesures du cube.  
  
 Groupe de mesures  
 Efface le cache pour l'ensemble des partitions contenues dans le groupe de mesures.  
  
 Partition  
 Efface le cache pour la partition spécifiée.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
