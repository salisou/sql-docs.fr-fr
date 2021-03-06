---
title: Prise en charge internationale (pilote ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- double-byte character sets [ODBC]
- FoxPro ODBC driver [ODBC], international support
- DBCS [ODBC]
- international support [ODBC]
- sort order [ODBC]
- collating sequences [ODBC]
- Visual FoxPro ODBC driver [ODBC], international support
ms.assetid: cd3fab32-13f1-4a86-abc4-5e18667669fc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b4b0c758bb478ea6a468e6756c3d6f0f52c766f5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299969"
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>Prise en charge internationale (pilote ODBC Visual FoxPro)
Le pilote ODBC Microsoft Visual FoxPro prend en charge les éléments suivants :  
  
-   Jeux de caractères codés sur deux octets (DBCS)  
  
-   Plusieurs séquences de classement  
  
 Une séquence de classement définit l' *ordre de tri* des données stockées dans une table ou une base de données Visual FoxPro. Par défaut, le pilote est configuré pour utiliser les séquences de classement qui prennent en charge la version linguistique de votre système d’exploitation.  
  
 Pour obtenir la liste des séquences de classement prises en charge, consultez [Set COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
## <a name="locale"></a>locale  
 Ensemble d’informations qui correspond à une langue et à un pays ou une région donnés. Les paramètres régionaux indiquent des paramètres spécifiques tels que les séparateurs décimaux, les formats de date et d’heure et l’ordre de tri des caractères.  
  
## <a name="sort-order"></a>ordre de tri  
 Les ordres de tri incorporent les règles de tri des différents *paramètres régionaux*, ce qui vous permet de trier correctement les données dans ces langues. Dans Visual FoxPro, l’ordre de tri actuel détermine les résultats des comparaisons d’expressions de caractères et l’ordre dans lequel les enregistrements s’affichent dans les tables indexées ou triées.
