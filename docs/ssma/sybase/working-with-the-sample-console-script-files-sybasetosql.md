---
title: Utilisation des exemples de fichiers de script de console (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sybase Console,Sample Console Script Files
ms.assetid: ef221118-b442-4ca6-9409-6ee1d9f8d948
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: fe9e05f0078f0d1a9d3ab5ea6e2763ac28207085
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68091789"
---
# <a name="working-with-the-sample-console-script-files-sybasetosql"></a>Utilisation des exemples de fichiers de script de console (SybaseToSQL)
Quelques exemples de fichiers ont été fournis avec le produit pour la référence et l’utilisation de l’utilisateur. Cette section décrit la façon de personnaliser facilement ces scripts en fonction des besoins de l’utilisateur final.  
  
## <a name="sample-console-script-files"></a>Exemples de fichiers de script de console  
Les exemples de fichiers de script de console suivants couvrant différents scénarios ont été fournis pour la référence utilisateur :  
  
-   ServersConnectionFileSample. Xml  
  
-   VariableValueFileSample. Xml  
  
-   AssessmentReportGenerationSample. Xml  
  
-   SqlStatementConversionSample. Xml  
  
-   ConversionAndDataMigrationSample. Xml  
  
-   **ServersConnectionFileSample. xml :**  
  
    -   Cet exemple fournit les différents modes de connexion disponibles pour la base de données source et cible, et l’utilisateur peut sélectionner n’importe quel mode conformément à la spécification. Cet exemple contient les définitions de serveur.  
  
    -   L’utilisateur peut se connecter à la base de données requise en remplaçant simplement les valeurs par les définitions des serveurs source et cible requis. Dans l’exemple fourni, toutes les valeurs ont été fournies en tant que valeurs de variable disponibles dans **VariableValueFileSample. xml**.  Tous les autres paramètres de connexion peuvent être supprimés du fichier de connexion du serveur de travail de l’utilisateur.  
  
    -   Pour plus d’informations sur la connexion aux serveurs source et cible, consultez [création de fichiers de connexion au serveur &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md).  
  
-   **VariableValueFileSample. xml :**  
    Toutes les variables qui ont été utilisées dans les exemples de fichiers de `ServersConnectionFileSample.xml` script de console et qui ont été assemblées dans ce fichier. Pour exécuter les exemples de scripts de la console, l’utilisateur doit simplement remplacer les exemples de valeurs de variables par des scripts définis par l’utilisateur et passer ce fichier comme argument de ligne de commande supplémentaire avec le fichier de script.  
  
    Pour plus d’informations sur le fichier de valeurs de variable, consultez [création de fichiers de valeurs de variables &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-variable-value-files-sybasetosql.md).  
  
-   **AssessmentReportGenerationSample. xml :**  
    Cet exemple permet à l’utilisateur de générer un rapport d’évaluation XML qui peut être utilisé par l’utilisateur pour l’analyse avant de commencer à convertir et à migrer des données.  
  
    Dans la `generate-assessment-report` commande, l’utilisateur doit mandatorily remplacer la valeur de la variable (refer **VariableValueFileSample. xml**) `object-name` dans l’attribut par le nom de la base de données en cours d’utilisation par l’utilisateur. Selon le type d’objet spécifié, la `object-type` valeur doit également être modifiée.  
  
    Si l’utilisateur doit évaluer plusieurs objets/bases de données, il peut spécifier `metabase-object` plusieurs nœuds, comme `generate-assessment-report` illustré dans l’exemple 4 de la commande de l’exemple de fichier de script de console.  
  
    Pour plus d’informations sur la génération de rapports, consultez [génération de rapports &#40;&#41;SybaseToSQL ](../../ssma/sybase/generating-reports-sybasetosql.md).  
  
    > [!NOTE]  
    > -   Assurez-vous que l’argument de ligne de commande du fichier de valeur de variable est passé à l’application console et que VariableValueFileSample. xml est mis à jour avec les valeurs spécifiées par l’utilisateur.  
    > -   Vérifiez que l’argument de ligne de commande du fichier de connexion du serveur est passé à l’application console et que ServersConnectionFileSample. xml est mis à jour avec des valeurs de paramètre de serveur correctes.  
  
-   **SqlStatementConversionSample. xml :**  
    Cet exemple permet à l’utilisateur de générer le `t-sql` script correspondant pour la commande `sql` de base de données source fournie en entrée.  
  
    Dans la `convert-sql-statement` commande, l’utilisateur doit mandatorily remplacer la valeur de la variable (reportez-vous `context` à **VariableValueFileSample. xml**) dans l’attribut par le nom de la base de données en cours d’utilisation par l’utilisateur. L’utilisateur devra également changer la valeur de l' `sql` attribut en la commande de base `sql` de données source dont il a besoin pour être converti.  
  
    L’utilisateur peut également fournir des fichiers SQL à convertir. Cela a été illustré dans l' `convert-sql-statement` exemple 4 de la commande de l’exemple de fichier de script de console.  
  
    > [!NOTE]  
    > Assurez-vous que l’argument de ligne de commande du fichier de valeur de variable est passé à l’application console et que VariableValueFileSample. xml est mis à jour avec les valeurs spécifiées par l’utilisateur.  
  
-   **ConversionAndDataMigrationSample. xml :**  
     Cet exemple permet à l’utilisateur d’effectuer une migration de bout en bout, de la conversion à la migration des données. La liste des valeurs d’attribut obligatoires qu’ils devront modifier est indiquée ci-dessous :  
  
    **Nom de la commande**  
  
    `map-schema`  
  
    Mappage de schéma de la base de données source vers le schéma cible.  
  
    **Attribut**  
  
    -   `source-schema:`Spécifie la base de données source qui nécessite d’être convertie.  
  
    -   `sql-server-schema`: Spécifie la base de données cible à migrer vers  
  
    **Nom de la commande**  
  
    `convert-schema`  
  
    -   Effectue une conversion de schéma de la source vers le schéma cible.  
  
    -   Si l’utilisateur doit évaluer plusieurs objets/bases de données, il peut spécifier `metabase-object` plusieurs nœuds, comme `convert-schema` illustré dans l’exemple 4 de la commande de l’exemple de fichier de script de console.  
  
    **Attribut**  
  
    `object-name`: Spécifiez le nom de la base de données ou de l’objet source qui doit être converti. Assurez-vous `object-type` que le correspondant est modifié en fonction du type d’objet spécifié dans le`object-name`  
  
    **Nom de la commande**  
  
    `synchronize-target`  
  
    -   Synchronise les objets cibles avec la base de données cible.  
  
    -   Si l’utilisateur doit évaluer plusieurs objets/bases de données, il peut spécifier `metabase-object` plusieurs nœuds, comme `synchronize-target` illustré dans l’exemple 3 de la commande de l’exemple de fichier de script de console.  
  
    **Attribut**  
  
    `object-name:`Spécifiez le nom de la base de données ou de l’objet SQL Server qui doit être créé. Assurez-vous `object-type` que le correspondant est modifié en fonction du type d’objet spécifié dans le`object-name`  
  
    **Nom de la commande**  
  
    `migrate-data`  
  
    -   Migre les données sources vers la cible.  
  
    -   Si l’utilisateur doit évaluer plusieurs objets/bases de données, il peut spécifier `metabase-object` plusieurs nœuds, comme `migrate-data` illustré dans l’exemple 2 de la commande de l’exemple de fichier de script de console.  
  
    **Attribut**  
  
    `object-name:`Spécifie le nom de la base de données/des tables source dont la migration doit être effectuée. Assurez-vous `object-type` que le correspondant est modifié en fonction du type d’objet spécifié dans le`object-name`  
  
## <a name="see-also"></a>Voir aussi  
[Création de fichiers de valeurs de variables &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-variable-value-files-sybasetosql.md)  
[Création des fichiers de connexion au serveur &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
[Génération de rapports &#40;&#41;SybaseToSQL](../../ssma/sybase/generating-reports-sybasetosql.md)  
  
