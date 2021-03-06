---
title: Utilisation des types de données (JDBC) | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d05200ff0c634ea327e58e5288ff8e99c0ec9418
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922557"
---
# <a name="working-with-data-types-jdbc"></a>Utilisation des types de données (JDBC)

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

La fonction principale du [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] est de permettre aux développeurs Java d’accéder aux données contenues dans les bases de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour ce faire, le pilote JDBC sert d’interface pour la conversion entre les types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et les types et objets en langage Java.  
  
> [!NOTE]  
> Pour obtenir une présentation détaillée des types de données de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et du pilote JDBC, notamment leurs différences et leur conversion en types de données en langage Java, consultez [Présentation des types de données du pilote JDBC](../../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
Afin de travailler avec les types de données SQL Server, le pilote JDBC fournit les méthodes get\<Type> et set\<Type> pour les classes [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) et [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md). Il fournit également les méthodes get\<Type> et update\<Type> pour la classe [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md). La méthode que vous utilisez dépend du type de données avec lequel vous travaillez et si vous utilisez des jeux de résultats ou des requêtes.  
  
Les rubriques de cette section décrivent comment utiliser les types de données du pilote JDBC pour accéder aux données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans vos applications Java.  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
| Rubrique                                                                         | Description                                                                                                                                                                                                                                                  |
| ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Exemple de types de données de base](../../../connect/jdbc/code-samples/basic-data-types-sample.md)   | Décrit l’utilisation des méthodes getter du jeu de résultats pour récupérer les valeurs des types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de base, ainsi que l’utilisation des méthodes update du jeu de résultats pour mettre à jour ces valeurs.                                             |
| [Exemple de type de données SQLXML](../../../connect/jdbc/code-samples/sqlxml-data-type-sample.md)   | Explique comment stocker des données XML dans une base de données relationnelle, comment récupérer des données XML à partir d’une base de données et comment analyser des données XML à l’aide du type de données Java **SQLXML**.                                                                                   |
| [Exemple de types de données spatiales](../../../connect/jdbc/code-samples/spatial-data-types-sample.md) | Décrit comment stocker des types de données spatiales dans SQL Server et comment récupérer ces types à partir de SQL Server. Explique également comment utiliser les classes nouvellement définies **Geometry** et **Geography** à partir du pilote pour gérer la référence Java de ces types de données. |
  
## <a name="see-also"></a>Voir aussi

[Exemples d'applications du pilote JDBC](../../../connect/jdbc/code-samples/sample-jdbc-driver-applications.md)  
