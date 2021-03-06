---
title: LoadFromFile, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_LoadFromFile
helpviewer_keywords:
- LoadFromFile method [ADO]
ms.assetid: b18d8d38-7354-4a94-b637-6ac035faa433
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ce90b13a677246fb64462fbe691eb9e3efaa3c7f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67918273"
---
# <a name="loadfromfile-method-ado"></a>LoadFromFile, méthode (ADO)
Charge le contenu d’un fichier existant dans un [flux](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.LoadFromFileFileName  
```  
  
#### <a name="parameters"></a>Paramètres  
 *FileName*  
 Valeur de **chaîne** qui contient le nom d’un fichier à charger dans le **flux**. *Filename* peut contenir n’importe quel chemin d’accès et nom valide au format UNC. Si le fichier spécifié n’existe pas, une erreur d’exécution se produit.  
  
## <a name="remarks"></a>Notes  
 Cette méthode peut être utilisée pour charger le contenu d’un fichier local dans un objet de **flux** . Cela peut être utilisé pour charger le contenu d’un fichier local sur un serveur.  
  
 L’objet de **flux** doit être déjà ouvert avant d’appeler **LoadFromFile**. Cette méthode ne modifie pas la liaison de l’objet de **flux** ; elle est toujours liée à l’objet spécifié par l’URL ou l' **enregistrement** avec lequel le **flux** a été ouvert à l’origine.  
  
 **LoadFromFile** remplace le contenu actuel de l’objet de **flux** par les données lues à partir du fichier. Tout octet existant dans le **flux** de fichiers est remplacé par le contenu du fichier. Les octets précédemment existants et restants qui suivent le [EOS](../../../ado/reference/ado-api/eos-property.md) créé par **LoadFromFile**sont tronqués.  
  
 Après un appel à **LoadFromFile**, la position actuelle est définie au début du **flux** (la[position](../../../ado/reference/ado-api/position-property-ado.md) est 0).  
  
 Étant donné que 2 octets peuvent être ajoutés au début du flux pour l’encodage, la taille du flux peut ne pas correspondre exactement à la taille du fichier à partir duquel il a été chargé.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
