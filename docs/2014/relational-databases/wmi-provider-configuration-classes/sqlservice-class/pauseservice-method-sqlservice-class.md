---
title: Méthode PauseService (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- PauseService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PauseService method
ms.assetid: 5c3a8feb-58b8-4385-b4c8-bf33cf4d276d
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: f4b9667f9d0018920885d4fdf7e5fce3b5a47311
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63061837"
---
# <a name="pauseservice-method-sqlservice-class"></a>Méthode PauseService (classe SqlService)
  Tente de placer le service dans l'état de pause.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.PauseService()  
  
```  
  
## <a name="parts"></a>Éléments  
 *objet*  
 Objet de [classe SqlService](sqlservice-class.md) qui représente le service.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur uint32 égale à 0 si le service a été correctement arrêté, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
