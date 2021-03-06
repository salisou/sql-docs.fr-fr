---
title: Détermination des éléments pris en charge | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- editing data [ADO], Supports method
- Supports method [ADO]
ms.assetid: 65090cba-6d46-4775-8d61-f6838e7752a6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dc42e9128ccc1ccb43996f554ffe280916884307
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925520"
---
# <a name="determining-what-is-supported"></a>Détermination de ce qui est pris en charge
La méthode **prend en charge** l’utilisation de la méthode pour déterminer si un objet **Recordset** spécifié prend en charge un type particulier de fonctionnalité. Sa syntaxe est la suivante :  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="remarks"></a>Notes  
 La méthode **supports** retourne une valeur booléenne qui indique si le fournisseur prend en charge toutes les fonctionnalités identifiées par l’argument CursorOptions. Vous pouvez utiliser la méthode **supports** pour déterminer les types de fonctionnalités qu’un objet **Recordset** prend en charge. Si l’objet **Recordset** prend en charge les fonctionnalités dont les constantes correspondantes se trouvent dans *CursorOptions*, la méthode **supports** retourne la **valeur true**. Sinon, elle retourne **false**.  
  
 À l’aide de la méthode **supports** , vous pouvez vérifier la capacité de l’objet **Recordset** à ajouter de nouveaux enregistrements, utiliser des signets, utiliser la méthode **Find** , utiliser le défilement, utiliser la propriété **index** et effectuer des mises à jour par lots. Pour obtenir la liste complète des constantes et leurs significations, consultez [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md).  
  
 Bien que la méthode **supports** puisse retourner la **valeur true** pour une fonctionnalité donnée, elle ne garantit pas que le fournisseur peut rendre la fonctionnalité disponible dans toutes les circonstances. La méthode **supports** retourne simplement une valeur indiquant si le fournisseur peut prendre en charge les fonctionnalités spécifiées, en supposant que certaines conditions sont remplies. Par exemple, la méthode **supports** peut indiquer qu’un objet **Recordset** prend en charge les mises à jour, même si le curseur est basé sur une jointure de plusieurs tables, dont certaines colonnes ne peuvent pas être mises à jour.
