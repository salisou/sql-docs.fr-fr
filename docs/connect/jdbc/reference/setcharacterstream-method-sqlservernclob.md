---
title: setCharacterStream Method (SQLServerNClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 09042ee9-dfb1-4d0b-82bd-d1224b0aea80
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a84aac6a02e3fabac2774a41ab8dfc8e99af8b25
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927192"
---
# <a name="setcharacterstream-method-sqlservernclob"></a>Méthode setCharacterStream (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère un flux servant à écrire un flux de caractères Unicode dans la valeur **NCLOB** représentée par cet objet **java.sql.NClob**, en commençant à la position spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.io.Writer setCharacterStream(long pos)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pos*  
  
 Position à laquelle commencera l’écriture dans la valeur **NCLOB** ; la première position est 1.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet Writer représentant le flux sur lequel peuvent être écrits les caractères encodés Unicode.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setCharacterStream est spécifiée par la méthode setCharacterStream de l’interface java.sql.NClob.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerNClob, méthodes](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob, membres](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob, classe](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
