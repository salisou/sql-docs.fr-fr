---
title: Membres de SQLServerClob | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apitype: Assembly
ms.assetid: 7db785ca-edd5-4833-8053-17fdbf87279a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d69a32f3822a82d2395d51a375fedf0867b3f3e5
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80909589"
---
# <a name="sqlserverclob-members"></a>Membres de SQLServerClob
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Les tableaux suivants présentent les membres exposés par la classe [SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md).  
  
## <a name="constructors"></a>Constructeurs  
  
|Name|Description|  
|----------|-----------------|  
|[SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-constructor-sqlserverconnection-java-lang-string.md)|Initialise une nouvelle instance de la classe SQLServerClob.|  
  
## <a name="fields"></a>Champs  
 Aucun.  
  
## <a name="inherited-fields"></a>Champs hérités  
 Aucun.  
  
## <a name="methods"></a>Méthodes  
  
|Name|Description|  
|----------|-----------------|  
|[free](../../../connect/jdbc/reference/free-method-sqlserverclob.md)|Cette méthode libère l'objet CLOB, ainsi que les ressources qu'il détient.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverclob.md)|Matérialise le Clob en tant que flux ASCII.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverclob.md)|Retourne les données Clob en tant qu'objet java.io.Reader ou que flux de caractères.|  
|[getSubString](../../../connect/jdbc/reference/getsubstring-method-sqlserverclob.md)|Retourne une copie de la sous-chaîne spécifiée dans le Clob, en fonction de la position de départ spécifiée et du nombre de caractères à copier.|  
|[length](../../../connect/jdbc/reference/length-method-sqlserverclob.md)|Retourne le nombre de caractères dans le Clob.|  
|[position](../../../connect/jdbc/reference/position-method-sqlserverclob.md)|Retourne la position de caractère de l'objet Clob spécifié ou d'une sous-chaîne dans le Clob, en fonction de la position de départ spécifiée.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlserverclob.md)|Retourne un flux à utiliser pour écrire des caractères ASCII dans le Clob, en démarrant à la position spécifiée.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverclob.md)|Retourne un flux à utiliser pour écrire un flux de caractères Unicode dans le Clob, en démarrant à la position spécifiée.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)|Écrit la chaîne spécifiée dans le Clob, en démarrant à la position spécifiée.|  
|[truncate](../../../connect/jdbc/reference/truncate-method-sqlserverclob.md)|Tronque le Clob en fonction de la longueur spécifiée.|  
  
## <a name="inherited-methods"></a>Méthodes héritées  
  
|Classe héritée de|Méthodes|  
|--------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerClob, classe](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
