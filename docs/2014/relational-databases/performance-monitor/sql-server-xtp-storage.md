---
title: Stockage XTP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 50e62a9232690deb368096723f428118e9de7aa2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63151153"
---
# <a name="xtp-storage"></a>Storage XTP
  L'objet de performance XTP Storage contient des compteurs associés au stockage XTP dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Ce tableau décrit les compteurs **XTP Storage**.  
  
|Compteur|Description|  
|-------------|-----------------|  
|**Points de contrôle fermés**|Nombre de points de contrôle fermés effectués par l'agent en ligne.|  
|**Points de contrôle terminés**|Nombre de points de contrôle traités par le thread de point de contrôle hors connexion.|  
|**Fusions principales terminées**|Nombre de fusions principale exécutées par le thread de travail de fusion. Ces fusions ne sont pas encore installées.|  
|**Évaluations de la stratégie de fusion**|Nombre d'évaluations de la stratégie de fusion depuis le démarrage du serveur.|  
|**Demandes de fusion en attente**|Nombre de demandes de fusion en attente depuis le démarrage du serveur.|  
|**Fusions abandonnées**|Nombre de fusions abandonnées en raison d'un échec.|  
|**Fusions installées**|Nombre de fusions correctement installées.|  
|**Fichiers totaux fusionnés**|Nombre total de fichiers sources fusionnés. Ce nombre peut être utilisé pour rechercher le nombre moyen de fichiers sources dans la fusion.|  
  
## <a name="see-also"></a>Voir aussi  
 [Les compteurs de performances de l’OLTP en mémoire &#40;de XTP&#41;](../../integration-services/performance/performance-counters.md)  
  
  
