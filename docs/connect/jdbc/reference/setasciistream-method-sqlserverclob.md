---
title: Méthode setAsciiStream (SQLServerClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.setAsciiStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6e1779df-3b2a-41d1-8dca-99692cc9da14
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 665696770d4a683bc67aa469ff0e1b27a8378615
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921954"
---
# <a name="setasciistream-method-sqlserverclob"></a>Méthode setAsciiStream (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne un flux à utiliser pour écrire des caractères ASCII dans l'objet CLOB, en démarrant à la position spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.io.OutputStream setAsciiStream(long pos)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pos*  
  
 Position à laquelle démarrer l'écriture dans l'objet CLOB.  
  
## <a name="return-value"></a>Valeur de retour  
 Flux sur lequel les caractères encodés ASCII peuvent être écrits.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode setAsciiStream est spécifiée par la méthode setAsciiStream dans l’interface java.sql.Clob.  
  
 Les données de caractères dans l'objet CLOB sont remplacées par le flux de sortie en commençant à la position donnée et elles peuvent dépasser la longueur initiale de l'objet CLOB. La spécification d'une valeur position+1 permet d'ajouter des caractères ASCII. La spécification d'une valeur position+2 ou supérieure (ou de zéro ou d'une valeur inférieure) génère une erreur de position.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerClob, méthodes](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob, membres](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob, classe](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
