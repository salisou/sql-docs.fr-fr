---
title: SET EXCLUSIVE, commande | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET EXCLUSIVE command [ODBC]
ms.assetid: d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d140c4be3ab850547ac82f9b954e7313b008dbf0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300859"
---
# <a name="set-exclusive-command"></a>SET EXCLUSIVE, commande
Spécifie si les fichiers de table sont ouverts pour une utilisation exclusive ou partagée sur un réseau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET EXCLUSIVE ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ACTIVÉ  
 Limite l’accessibilité d’une table ouverte sur un réseau à l’utilisateur qui l’a ouverte. La table n’est pas accessible aux autres utilisateurs sur le réseau. La clause EXCLUSIVE ON empêche également tous les autres utilisateurs d’avoir un accès en lecture seule.  
  
 OFF  
 (Valeur par défaut pour le pilote ; les valeurs par défaut pour Visual FoxPro sont ACTIVÉes pour la session de données globale et désactivées pour une session de données privée.) Autorise le partage et la modification d’une table ouverte sur un réseau par n’importe quel utilisateur sur le réseau.  
  
## <a name="remarks"></a>Notes  
 La modification de la valeur de SET EXCLUSIVE ne modifie pas l’état des tables précédemment ouvertes. Par exemple, si une table est ouverte avec SET EXCLUSIVE défini sur ON et que l’option SET EXCLUSIVE est remplacée par la valeur OFF, la table conserve son état d’utilisation exclusive.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration d’ODBC pour Visual FoxPro, boîte de dialogue](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
