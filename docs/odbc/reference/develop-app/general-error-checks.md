---
title: Vérifications générales des erreurs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- general error checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 0c9a3425-0a7c-48de-9ff6-73601c26283e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 35dc509e0bda51c8d219b76f48b44b2b03dba8cc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305560"
---
# <a name="general-error-checks"></a>Vérifications des erreurs générales
Le gestionnaire de pilotes vérifie une erreur générale. Elle retourne toujours SQL_ERROR lorsqu’elle rencontre l’erreur suivante : la fonction doit être prise en charge par le pilote.
