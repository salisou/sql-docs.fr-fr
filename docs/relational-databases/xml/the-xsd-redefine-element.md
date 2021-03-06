---
title: '&lt;xsd:redefine&gt;, élément | Microsoft Docs'
description: Apprenez-en davantage sur la prise en charge de l’élément W3C XSD redefine et sur la mise à jour d’un schéma XML ou de ses composants.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xsd:redefine element
ms.assetid: 5f3e9b65-f10e-4db2-a62c-b270ac11d04e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8b222cf1105fbe8121e9c9738a79257c59fc3abf
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388149"
---
# <a name="the-ltxsdredefinegt-element"></a>Élément &lt;xsd:redefine&gt;
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  L’élément W3C XSD **redefine** assure la prise en charge de la redéfinition des composants de schéma. Toutefois, la prise en charge de cette directive est potentiellement dommageable en termes de performances et exige en outre que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] revalide toutes les instances du type de données **xml** associées au schéma redéfini. Par conséquent, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge cet élément. Les schémas XML qui incluent l’élément **\<xsd:redefine>** sont rejetés par le serveur.  
  
 Au lieu d'utiliser cet élément, vous pouvez mettre à jour un schéma ou ses composants en procédant comme suit :  
  
1.  Créez une nouvelle collection de schémas XML en y incluant les composants de schéma modifiés.  
  
2.  Retapez tous les types de données **xml** (XML DT) qui utilisent la collection de schémas XML à redéfinir de façon à utiliser à la place la nouvelle collection de schémas XML. Pour cela, utilisez l'option ALTER COLUMN de la commande ALTER TABLE pour retaper les colonnes ou modifiez les contraintes de collection de schémas XML sur les variables ou les paramètres.  
  
3.  Supprimez l'ancienne version de la collection de schémas XML.  

## <a name="see-also"></a>Voir aussi  
 [Spécifications et limitations relatives aux collections de schémas XML sur le serveur](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
