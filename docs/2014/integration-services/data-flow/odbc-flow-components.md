---
title: Composants de flux ODBC | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cf751f1e-2348-4a77-904c-bd92c0d7d0ae
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e42099ede229ef7d0b10cf8d88b4ac92c60d3370
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62901429"
---
# <a name="odbc-flow-components"></a>Composants de flux ODBC
  Cette rubrique décrit les concepts nécessaires pour créer un flux de données ODBC à l'aide de [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]  
  
 Le connecteur pour Open Database Connectivity (ODBC) d'Attunity pour [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] aide les développeurs SSIS à créer facilement des packages qui chargent et déchargent des données des bases de données compatibles ODBC.  
  
 Le connecteur ODBC est conçu pour obtenir des performances optimales lors du chargement ou du déchargement de données dans une base de données ODBC dans le contexte de [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
## <a name="benefits"></a>Avantages  
 La source ODBC et la destination ODBC pour [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] procurent un avantage concurrentiel à SSIS dans les projets impliquant le chargement de données dans des bases de données compatibles ODBC ou de déchargement de données depuis ces dernières.  
  
 La source ODBC et la destination ODBC permettent d'intégrer des données hautes performances dans les bases de données compatibles ODBC. Ces deux composants peuvent être configurés de manière à utiliser des liaisons de table de paramètres selon les lignes pour les fournisseurs ODBC hautement sollicités qui prennent en charge ce mode de liaison, ainsi que des liaisons de paramètre de ligne unique pour les fournisseurs ODBC peu sollicités.  
  
## <a name="getting-started-with-the-odbc-source-and-destination"></a>Prise en main de la source et de la destination ODBC  
 Avant de pouvoir configurer des packages qui utilisent [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], vous devez vous assurer de la disponibilité des éléments suivants.  
  
-   [Source ODBC](odbc-source.md)  
  
-   [Destination ODBC](odbc-destination.md)  
  
 La source ODBC et la destination ODBC permettent de décharger et de charger facilement des données et de les transférer d'une base de données source compatible ODBC vers une base de données de destination compatible ODBC.  
  
 Pour utiliser la source ou la destination afin de charger ou de décharger des données, ouvrez un nouveau projet [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Faites glisser la source ou la destination sur l'aire de conception de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
-   Le composant source ODBC lit les données dans la base de données source compatible ODBC.  
  
 Vous pouvez connecter la source ODBC à n'importe quelle destination ou transformer le composant pris en charge par SSIS.  
  
 **Voir aussi :**  
  
 Source ODBC  
  
 Éditeur de source ODBC (page Gestionnaire de connexions)  
  
 Éditeur de source ODBC (page Sortie d'erreur)  
  
-   La destination ODBC charge les données dans une base de données compatible ODBC. Vous connectez la destination à n'importe quelle source ou transformez le composant pris en charge par SSIS.  
  
 **Voir aussi :**  
  
 Destination ODBC  
  
 Éditeur de destination ODBC (page Gestionnaire de connexions)  
  
 Éditeur de destination ODBC (page Sortie d'erreur)  
  
## <a name="operating-scenarios"></a>Scénarios d'utilisation  
 Cette section décrit quelques-unes des principales utilisations des composants sources et de destination ODBC.  
  
### <a name="bulk-copy-data-from-sql-server-tables-to-any-odbc-supported-database-table"></a>Copie en bloc de données de tables SQL Server vers n'importe quelle table de base de données compatible ODBC  
 Vous pouvez utiliser les composants pour copier en bloc les données d’une ou de plusieurs tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers une même table de base de données compatible ODBC.  
  
 L'exemple suivant montre comment créer une tâche de flux de données SSIS qui extrait des données d'une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les charge dans une table DB2.  
  
-   Créez un projet [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
-   Créez un gestionnaire de connexions OLE DB qui se connecte à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenant les données à copier.  
  
-   Créez un gestionnaire de connexions ODBC qui utilise un pilote ODBC DB2 installé en local avec un DSN pointant vers une base de données DB2 locale ou distante. Cette base de données est l'emplacement auquel les données de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont chargées.  
  
-   Faites glisser une source OLE DB sur l'aire de conception, puis configurez la source pour obtenir les données de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et la table avec les données que vous allez extraire. Utilisez le gestionnaire de connexions OLE DB précédemment créé.  
  
-   Faites glisser une destination ODBC sur l'aire de conception, connectez la sortie de la source à la destination ODBC, puis configurez la destination de manière à charger les données dans la table DB2 avec les données que vous extrayez de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Utilisez le gestionnaire de connexions ODBC précédemment créé.  
  
### <a name="bulk-copy-data-from-odbc-supported-database-tables-to-any-sql-server-table"></a>Copie en bloc de données de tables de base de données compatibles ODBC vers n'importe quelle table SQL Server  
 Vous pouvez utiliser les composants pour copier en bloc les données d'une ou de plusieurs tables de base de données compatibles ODBC vers une table de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unique.  
  
 L'exemple suivant montre comment créer une tâche de flux de données SSIS qui extrait des données d'une table de base de données Sybase et les charge dans une table de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Créez un projet [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]  
  
-   Créez un gestionnaire de connexions ODBC qui utilise un pilote ODBC Sybase installé en local avec un DSN pointant vers une base de données Sybase locale ou distante. Cette base de données est l'emplacement auquel les données sont extraites.  
  
-   Créez un gestionnaire de connexions OLE DB qui se connecte à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans laquelle vous voulez charger les données.  
  
-   Faites glisser une source ODBC dans l'aire de conception, puis configurez la source de manière à obtenir les données de la base de données Sybase avec la table que vous allez copier. Utilisez le gestionnaire de connexions ODBC précédemment créé.  
  
-   Faites glisser une destination OLE DB sur l'aire de conception, connectez la sortie de la source à la destination OLE DB, puis configurez la destination de manière à charger les données dans la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec les données que vous extrayez de la base de données Sybase. Utilisez le gestionnaire de connexions OLE DB précédemment créé.  
  
## <a name="supported-data-types"></a>Types de données pris en charge  
 Les composants SSIS ODBC en bloc prennent en charge tous les types de données ODBC intégrés, notamment les objets volumineux (objets CLOB et BLOB).  
  
Il n’existe aucune prise en charge des types de données pour les types C extensibles tels que décrits dans les spécifications ODBC 3.8. Le tableau suivant décrit les types de données SSIS utilisés pour chaque type SQL ODBC. Un développeur SSIS peut remplacer le mappage par défaut et spécifier un autre type de données SSIS pour les colonnes d'entrée/sortie sans nuire aux performances des conversions de données requises.  
  
|Type SQL ODBC|Type de données SSIS|Commentaires|  
|-----------------|------------------|------------|  
|SQL_BIT|DT_BOOL||  
|SQL_TINYINT|DT_I1<br /><br />DT_UI1|Les types de données SQL sont mappés aux types non signés SSIS (DT_UI1, DT_UI2, DT_UI4, DT_UI8) lorsque le pilote ODBC attribue à UNSIGNED_ATTRIBUTE la valeur SQL_TRUE pour ce type de données SQL.|  
|SQL_SMALLINT|DT_I2<br /><br />DT_UI2|Les types de données SQL sont mappés aux types non signés SSIS (DT_UI1, DT_UI2, DT_UI4, DT_UI8) lorsque le pilote ODBC attribue à UNSIGNED_ATTRIBUTE la valeur SQL_TRUE pour ce type de données SQL.|  
|SQL_INTEGER|DT_I4<br /><br />DTUI4|Les types de données SQL sont mappés aux types non signés SSIS (DT_UI1, DT_UI2, DT_UI4, DT_UI8) lorsque le pilote ODBC attribue à UNSIGNED_ATTRIBUTE la valeur SQL_TRUE pour ce type de données SQL.|  
|SQL_BIGINT|DT_I8<br /><br />DT_UI8|Les types de données SQL sont mappés aux types non signés SSIS (DT_UI1, DT_UI2, DT_UI4, DT_UI8) lorsque le pilote ODBC attribue à UNSIGNED_ATTRIBUTE la valeur SQL_TRUE pour ce type de données SQL.|  
|SQL_DOUBLE|DT_R8|  
|SQL_FLOAT|DT_R8|  
|SQL_REAL|DT_R4|  
|SQL_NUMERIC (p,s)|DT_NUMERIC (p,s)<br /><br />DT_R8<br /><br />DT_CY|Le type de données numeric est mappé à DT_NUMERIC lorsque P est supérieur ou égal à 38 et que S est supérieur ou égal à 0 et que S est inférieur ou égal à P. Le type de données numeric est mappé à DT_R8 lorsqu’au moins l’une des conditions suivantes est vraie :<br /><br />La précision est supérieure à 38<br /><br />L'échelle est inférieure à zéro<br /><br />L'échelle est supérieure à 38<br /><br />L'échelle est supérieure à la précision<br /><br /><br /><br />Notez que le type de données numeric est mappé à DT_CY lorsqu’il est déclaré en tant que type de données Money.|  
|SQL_DECIMAL (p,s)|DT_NUMERIC (p,s)<br /><br />DT_R8<br /><br />DT_CY|Le type de données decimal est mappé à DT_NUMERIC lorsque P est supérieur ou égal à 38 et que S est supérieur ou égal à 0 et que S est inférieur ou égal à P. Le type de données decimal est mappé à DT_R8 lorsqu’au moins l’une des conditions suivantes est vraie :<br /><br />La précision est supérieure à 38<br /><br />L'échelle est inférieure à zéro<br /><br />L'échelle est supérieure à 38<br /><br />L'échelle est supérieure à la précision<br /><br />Notez que le type de données decimal est mappé à DT_CY lorsqu’il est déclaré en tant que type de données Money.|  
|SQL_DATE<br /><br />SQL_TYPE_DATE|DT_DBDATE|  
|SQL_TIME<br /><br />SQL_TYPE_TIME|DT_DBTIME|  
|SQL_TIMESTAMP<br /><br />SQL_TYPE_TIMESTAMP|DT_DBTIMESTAMP<br /><br />DT_DBTIMESTAMP2|Les types de données SQL_TIMESTAMP sont mappés à DT_DBTIMESTAMP2 si l'échelle est supérieure à 3. Dans tous les autres cas, ils sont mappés à DT_DBTIMESTAMP.|  
|SQL_CHAR<br /><br />SQLVARCHAR|DT_STR<br /><br />DT_WSTR<br /><br />DT_TEXT<br /><br />DT_NTEXT|DT_STR est utilisé si la longueur de colonne est inférieure ou égale à 8 000 et si la propriété **ExposeStringsAsUnicode** a la valeur false.<br /><br />DT_WSTR est utilisé si la longueur de colonne est inférieure ou égale à 8 000 et si la propriété **ExposeStringsAsUnicode** a la valeur true.<br /><br />DT_TEXT est utilisé si la longueur de colonne est supérieure à 8 000 et si la propriété **ExposeStringsAsUnicode** a la valeur false.<br /><br />DT_NTEXT est utilisé si la longueur de colonne est supérieure à 8 000 et si la propriété **ExposeStringsAsUnicode** a la valeur true.|  
|SQL_LONGVARCHAR|DT_TEXT<br /><br />DT_NTEXT|DT_NTEXT est utilisé si la propriété **ExposeStringsAsUnicode** a la valeur true.|  
|SQL_WCHAR<br /><br />SQL_WVARCHAR|DT_WSTR<br /><br />DT_NTEXT|DT_WSTR est utilisé si la longueur de colonne est inférieure ou égale à 4000.<br /><br />DT_NTEXT est utilisé si la longueur de colonne est supérieure à 4000.|  
|SQL_WLONGVARCHAR|DT_NTEXT|  
|SQL_BINARY|DT_BYTE<br /><br />DT_IMAGE|DT_BYTES est utilisé si la longueur de colonne est inférieure ou égale à 8000.<br /><br />DT_IMAGE si la longueur de colonne est supérieure à 8000.|  
|SQL_LONGVARBINARY|DT_IMAGE|  
|SQL_GUID|DT_GUID|  
|SQL_INTERVAL_YEAR<br /><br />SQL_INTERVAL_MONTH<br /><br />SQL_INTERVAL_DAY<br /><br />SQL_INTERVAL_HOUR<br /><br />SQL_INTERVAL_MINUTE<br /><br />SQL_INTERVAL_SECOND<br /><br />SQL_INTERVAL_YEAR_TO_MONTH<br /><br />SQL_INTERVAL_DAY_TO_HOUR<br /><br />SQL_INTERVAL_DAY_TO_MINUTE<br /><br />SQL_INTERVAL_DAY_TO_SECOND<br /><br />SQL_INTERVAL_HOUR_TO_MINUTE<br /><br />SQL_INTERVAL_HOUR_TO_SECOND<br /><br />SQL_INTERVAL_MINUTE_TO_SECOND|DT_WSTR|  
|Types de données spécifiques au fournisseur|DT_BYTES<br /><br />DT_IMAGE|DT_BYTES est utilisé si la longueur de colonne est inférieure ou égale à 8000.<br /><br />DT_IMAGE est utilisé si la longueur de colonne est zéro ou supérieure à 8000.|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Source ODBC](odbc-source.md)  
  
-   [Destination ODBC](odbc-destination.md)  
  
 
