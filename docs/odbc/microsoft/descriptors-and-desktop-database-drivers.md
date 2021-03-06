---
title: Descripteurs et pilotes de base de données de bureau | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- desktop database drivers [ODBC], descriptors
- Jet-based ODBC drivers [ODBC], descriptors
- descriptors [ODBC], Jet-supported descriptor fields
- ODBC desktop database drivers [ODBC], descriptors
ms.assetid: 9ae2d9b5-365f-4f0a-9116-defe9498b401
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ef79855f71d23e5a884822371f1894eb83442a9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303510"
---
# <a name="descriptors-and-desktop-database-drivers"></a>Descripteurs et pilotes pour les bases de données de poste de travail
Un descripteur est une structure de données qui contient des informations sur les données de colonne ou les paramètres dynamiques. **SQLGetDescField** peut être utilisé pour récupérer les descripteurs pris en charge ci-dessous. Les descripteurs de paramètre d’implémentation (IPD) ne sont pas remplis automatiquement, car **SQLDescribeParam** n’est pas pris en charge. Les champs de descripteur qui ne sont pas disponibles via Jet (tels que SQL_DESC_BASE_TABLE_NAME) ne sont pas non plus pris en charge.  
  
 Pour plus d’informations sur les champs de descripteur pris en charge par jet, consultez le *Guide du programmeur Microsoft jet moteur de base de données*.  
  
 Pour plus d’informations sur les descripteurs, consultez les rubriques sous « descripteurs » dans le *Guide de référence du programmeur ODBC*.  
  
|Champs de descripteur|Niveau de support|  
|-----------------------|-------------------|  
|SQL_DESC_ALLOC_TYPE|Pris en charge|  
|SQL_DESC_ARRAY_SIZE|Pris en charge uniquement pour ARD|  
|SQL_DESC_ARRAY_STATUS_PTR|Pris en charge|  
|SQL_DESC_BIND_OFFSET_PTR|Pris en charge|  
|SQL_DESC_BIND_TYPE|Pris en charge|  
|SQL_DESC_COUNT|Pris en charge|  
|SQL_DESC_ROWS_PROCESSED_PTR|Pris en charge uniquement pour ARD|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Pris en charge|  
|SQL_DESC_BASE_COLUMN_NAME|Pris en charge (nouveau)|  
|SQL_DESC_BASE_TABLE_NAME|Pris en charge (nouveau)|  
|SQL_DESC_CASE_SENSITIVE|Toujours FALSe|  
|SQL_DESC_CATALOG_NAME|Non prise en charge|  
|SQL_DESC_CONCISE_TYPE|Pris en charge|  
|SQL_DESC_DATA_PTR|Pris en charge|  
|SQL_DESC_DATETIME_INTERVAL_CODE|Pris en charge|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|Pris en charge pour les types d’intervalle C|  
|SQL_DESC_DISPLAY_SIZE|Pris en charge|  
|SQL_DESC_FIXED_PREC_SCALE|Pris en charge (vrai pour Money)|  
|SQL_DESC_INDICATOR_PTR|Pris en charge|  
|SQL_DESC_LABEL|Pris en charge|  
|SQL_DESC_LENGTH|Pris en charge|  
|SQL_DESC_LITERAL_PREFIX|Pris en charge|  
|SQL_DESC_LITERAL_SUFFIX|Pris en charge|  
|SQL_DESC_LOCAL_TYPE_NAME|Non pris en charge (retourne une chaîne vide)|  
|SQL_DESC_NAME|Pris en charge|  
|SQL_DESC_NULLABLE|Pris en charge<br /><br /> **Remarque** Non pris en charge dans les versions précédentes de Jet 4,0|  
|SQL_DESC_NUM_PREC_RADIX|Pris en charge|  
|SQL_DESC_OCTET_LENGTH|Pris en charge|  
|SQL_DESC_OCTET_LENGTH_PTR|Pris en charge|  
|SQL_DESC_PARAMETER_TYPE|Uniquement les paramètres d’entrée|  
|SQL_DESC_PRECISION|Pris en charge|  
|SQL_DESC_SCALE|Pris en charge|  
|SQL_DESC_SCHEMA_NAME|Non prise en charge|  
|SQL_DESC_SEARCHABLE|Pris en charge|  
|SQL_DESC_TABLE_NAME|Non prise en charge|  
|SQL_DESC_TYPE|Pris en charge|  
|SQL_DESC_TYPE_NAME|Pris en charge|  
|SQL_DESC_UNNAMED|Pris en charge|  
|SQL_DESC_UNSIGNED|Pris en charge|  
|SQL_DESC_UPDATABLE|Pris en charge|
