---
title: Programmation à l'aide de SQLXML | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4d2cc57c-7293-4d92-b8b1-525e2b35f591
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6571c9592514bb0f29c796ae5a671363f3214ca7
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920638"
---
# <a name="programming-with-sqlxml"></a>Programmation à l'aide de SQLXML
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Cette section explique comment utiliser les méthodes de l’API [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] pour stocker et récupérer un document XML dans une base de données relationnelle avec des objets **SQLXML**.  
  
 Cette section contient également des informations sur les types d'objets SQLXML ; par ailleurs, elle dresse une liste des recommandations et limitations importantes relatives à l'utilisation des objets SQLXML.  
  
## <a name="reading-and-writing-xml-data-with-sqlxml-objects"></a>Lecture et écriture de données XML à l'aide d'objets SQLXML  
 La liste suivante explique comment utiliser les méthodes de l’API [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] pour lire et écrire des données XML avec des objets SQLXML :  
  
-   Pour créer un objet SQLXML, utilisez la méthode [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Notez que cette méthode crée un objet SQLXML sans aucune donnée. Pour ajouter des données **xml** à l’objet SQLXML, appelez l’une des méthodes suivantes spécifiées dans l’interface SQLXML : setResult, setCharacterStream, setBinaryStream ou setString.  
  
-   Pour récupérer l’objet SQLXML proprement dit, utilisez les méthodes getSQLXML de la classe [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) ou de la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md).  
  
-   Pour récupérer les données **xml** à partir d’un objet SQLXML, utilisez l’une des méthodes suivantes spécifiées dans l’interface SQLXML : getSource, getCharacterStream, getBinaryStream ou getString.  
  
-   Pour mettre à jour les données **xml** dans un objet SQLXML, utilisez la méthode [updateSQLXML](../../connect/jdbc/reference/updatesqlxml-method-sqlserverresultset.md) de la classe [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
-   Pour stocker un objet SQLXML dans une colonne de table de base de données de type **xml**, utilisez les méthodes setSQLXML de la classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) ou de la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md).  
  
 L'exemple de code de [Exemple de type de données SQLXML](../../connect/jdbc/sqlxml-data-type-sample.md) montre comment effectuer ces tâches d'API courantes.  
  
## <a name="readable-and-writable-sqlxml-objects"></a>Objets SQLXML accessibles en lecture et en écriture  
 Le tableau suivant répertorie les types d'objets SQLXML pris en charge par les méthodes setter, getter et updater fournies par l'API JDBC. Les colonnes du tableau font référence aux éléments suivants :  
  
-   La colonne **Nom de la méthode** liste les méthodes getter, setter et updater prises en charge dans l’API JDBC.  
  
-   La colonne **Objet SQLXML getter** représente un objet SQLXML créé par la méthode [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md) de la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) ou par la méthode [getSQLXML](../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md) de la classe [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
-   La colonne **Objet SQLXML setter** représente un objet SQLXML créé par la méthode [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Notez que les méthodes setter ci-dessous acceptent seulement un objet SQLXML créé par la méthode [createSQLXML](../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md).  
  
|Nom de la méthode|Objet SQLXML getter<br /><br /> (Accessible en lecture)|Objet SQLXML setter<br /><br /> (Accessible en écriture)|  
|-----------------|-------------------------------------------|-------------------------------------------|  
|CallableStatement.setSQLXML()|Non pris en charge|Prise en charge|  
|CallableStatement.setObject()|Non pris en charge|Prise en charge|  
|PreparedStatement.setSQLXML()|Non pris en charge|Prise en charge|  
|PreparedStatement.setObject()|Non pris en charge|Prise en charge|  
|ResultSet.updateSQLXML()|Non pris en charge|Prise en charge|  
|ResultSet.updateObject()|Non pris en charge|Prise en charge|  
|ResultSet.getSQLXML()|Prise en charge|Non pris en charge|  
|CallableStatement.getSQLXML()|Prise en charge|Non pris en charge|  
  
 Comme indiqué dans le tableau ci-dessus, les méthodes SQLXML setter ne fonctionnent pas avec les objets SQLXML accessibles en lecture ; de même, les méthodes getter ne fonctionnent pas avec les objets SQLXML accessibles en écriture.  
  
 Si l’application appelle la méthode setObject en spécifiant un paramètre d’échelle ou de longueur avec un objet SQLXML, ce paramètre d’échelle ou de longueur est ignoré.  
  
## <a name="guidelines-and-limitations-when-using-sqlxml-objects"></a>Recommandations et limitations relatives à l'utilisation des objets SQLXML  
 Les applications peuvent utiliser des objets SQLXML pour lire et écrire les données XML dans la base de données. La liste suivante fournit des informations sur les limitations et recommandations spécifiques à l'utilisation d'objets SQLXML :  
  
-   Un objet SQLXML ne peut être valide que pendant la durée de la transaction au cours de laquelle il a été créé.  
  
-   Un objet SQLXML reçu à partir d'une méthode getter ne peut être utilisé que pour lire des données.  
  
-   Un objet SQLXML créé par l'objet de connexion ne peut être utilisé que pour écrire des données.  
  
-   L'application ne peut appeler qu'une seule méthode getter sur un objet SQLXML accessible en lecture pour lire des données. Une fois la méthode getter appelée, toutes les autres méthodes getter ou setter sur le même objet SQLXML échouent.  
  
-   L’application ne peut appeler que la méthode free sur l’objet SQLXML, une fois qu’un accès en lecture ou en écriture a eu lieu sur ce dernier. Toutefois, il est toujours possible de traiter la source ou le flux retourné tant que la colonne ou le paramètre sous-jacent est actif. Si la colonne ou le paramètre sous-jacent devient inactif, la source ou le flux associé à l'objet SQLXML est fermé. Si la colonne ou le paramètre sous-jacent n'est plus valide, les données sous-jacentes ne sont pas disponibles pour les méthodes getter du flux, de SAX (Simple API for XML) et de StAX (Streaming API for XML).  
  
-   L'application ne peut appeler qu'une seule méthode setter sur un objet SQLXML accessible en écriture. Une fois la méthode setter appelée, toutes les autres méthodes setter ou getter sur le même objet SQLXML échouent.  
  
-   Pour définir des données sur l'objet SQLXML, l'application doit utiliser la méthode setter appropriée ainsi que les fonctions correspondantes dans l'objet retourné.  
  
-   Les méthodes getSQLXML de la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) et de la classe [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) retournent des données **Null** si la colonne sous-jacente est **Null**.  
  
-   Les objets setter peuvent être valides via la connexion dans laquelle ils ont été créés.  
  
-   Les applications ne sont pas autorisées à définir une valeur **Null** à l’aide des méthodes setter fournies par l’interface SQLXML. Les applications peuvent définir une chaîne vide ("") à l'aide des méthodes setter fournies dans l'interface SQLXML. Pour définir une valeur **Null**, les applications doivent appeler au choix :  
  
    -   les méthodes setNull de la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) et de la classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) ;  
  
    -   les méthodes setObject de la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) et de la classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) ;  
  
    -   les méthodes setSQLXML de la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) et de la classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) avec une valeur de paramètre **Null**.  
  
-   Lors de l'utilisation de documents XML, il est recommandé de privilégier les analyseurs SAX (Simple API for XML) et StAX (Streaming API for XML) aux analyseurs DOM (Document Object Model) pour des raisons de performances.  
  
 Les analyseurs XML ne peuvent pas gérer les valeurs vides. Toutefois, SQL Server permet aux applications de récupérer et de stocker des valeurs vides dans les colonnes de base de données de type de données XML. En d'autres termes, lors de l'analyse des données XML, si la valeur sous-jacente est vide, une exception est levée par l'analyseur. Pour les sorties DOM, le pilote JDBC intercepte cette exception et génère une erreur. Pour les sorties SAX et Stax, l'erreur provient directement de l'analyseur.  
  
## <a name="adaptive-buffering-and-sqlxml-support"></a>Prise en charge de la mise en mémoire tampon adaptative et de SQLXML  
 Les flux de données aux formats binaire et caractère retournés par l'objet SQLXML obéissent aux modes de mise en mémoire tampon adaptative ou de mise en mémoire tampon complète. Par ailleurs, si les analyseurs XML ne sont pas des flux, ils n'obéissent pas aux paramètres de mise en mémoire tampon adaptative ou de mise en mémoire tampon complète. Pour plus d’informations sur la mise en mémoire tampon adaptative, consultez [Utiliser la mise en mémoire tampon adaptative](../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des données XML](../../connect/jdbc/supporting-xml-data.md)  
  
  
