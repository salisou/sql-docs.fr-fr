---
title: InternetTimeout, propriété (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- InternetTimeout property [ADO]
ms.assetid: 4d1c8892-4bbc-4e71-bf4b-ba52c0ea9549
author: MightyPen
ms.author: genemi
ms.openlocfilehash: eaaa72c302c9218810ce653ea59fe5ff29a54ef0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67963876"
---
# <a name="internettimeout-property-rds"></a>InternetTimeout, propriété (RDS)
Indique le nombre de millisecondes à attendre avant l’expiration d’une demande.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **type long** qui représente le nombre de millisecondes avant l’expiration d’une demande.  
  
## <a name="remarks"></a>Notes  
 Cette propriété s’applique uniquement aux requêtes envoyées avec les protocoles HTTP ou HTTPs.  
  
 L’exécution des requêtes dans un environnement à trois niveaux peut prendre plusieurs minutes. Utilisez cette propriété pour spécifier une durée supplémentaire pour les requêtes de longue durée.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[DataSpace, objet (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [InternetTimeout, exemple de propriété (VB)](../../../ado/reference/rds-api/internettimeout-property-example-vb.md)   
 [InternetTimeout, exemple de propriété (VC++)](../../../ado/reference/rds-api/internettimeout-property-example-vc.md)   
 

