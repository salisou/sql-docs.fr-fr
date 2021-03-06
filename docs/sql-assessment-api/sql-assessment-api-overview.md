---
title: API SQL Server Assessment
description: Fournit une description de l’API SQL Server Assessment.
ms.prod: sql
ms.technology: tools-other
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 11/04/2019
ms.openlocfilehash: 76a6e99d06061ae581b753ce0edd96a5a82d0f95
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "78946718"
---
# <a name="sql-assessment-api"></a>API d’évaluation SQL

L’API SQL Assessment fournit un mécanisme permettant de déterminer si votre configuration de SQL Server est conforme aux bonnes pratiques. L’API est fournie avec un ensemble de règles contenant les règles de bonnes pratiques suggérées par l’équipe de SQL Server. Bien que nous améliorions cet ensemble de règles à chaque publication d’une nouvelle version, l’API est en même temps conçue comme une solution hautement personnalisable et extensible. Les utilisateurs peuvent donc paramétrer les règles par défaut et créer leurs propres règles.

L’API SQL Assessment est utile pour vérifier si votre configuration de SQL Server est conforme aux bonnes pratiques recommandées. Après une évaluation initiale, vous pouvez suivre la stabilité de la configuration au moyen d’évaluations planifiées à intervalles réguliers.

Vous pouvez utiliser l’API pour évaluer Azure SQL Database Managed Instance et SQL Server versions 2012 et ultérieures. SQL sur Linux est pris en charge.

## <a name="rules"></a>Règles

Les règles, parfois appelées « vérifications », sont définies dans des fichiers au format JSON. Ce format nécessite la spécification du nom et de la version d’un ensemble de règles. Ainsi, quand vous utilisez des ensembles de règles personnalisés, vous pouvez facilement savoir quelles recommandations proviennent de quel ensemble de règles. 

L’ensemble de règles fourni par Microsoft est disponible sur GitHub. Pour plus d’informations, consultez le [dépôt d’exemples](https://aka.ms/sql-assessment-api).

## <a name="sql-assessment-cmdlets-and-smo-extension"></a>Applets de commande SQL Assessment et extension SMO

L’API SQL Assessment fait partie de [SQL Server Management Objects (SMO)](../relational-databases/server-management-objects-smo/installing-smo.md) et du [module SQL Server PowerShell](../powershell/download-sql-server-ps-module.md), versions datées de juillet 2019 et ultérieures.

* [Installer SMO](../relational-databases/server-management-objects-smo/installing-smo.md)

* [Installer le module SQL Server PowerShell](../powershell/download-sql-server-ps-module.md)

Le module SqlServer obtient deux nouvelles applets de commande pour utiliser l’API SQL Assessment :

* **Get-SqlAssessmentItem** : fournit la liste des contrôles d’évaluation disponibles pour un objet SQL Server

* **Invoke-SqlAssessment** : fournit les résultats d’une évaluation

SMO Framework est complété par l’extension d’API SQL Assessment qui fournit les méthodes suivantes :

* **GetAssessmentItems**  : retourne les vérifications disponibles pour un objet SQL spécifique (IEnumerable<…>)

* **GetAssessmentResults**  : évalue de manière synchrone l’évaluation et retourne les résultats et les erreurs éventuelles (IEnumerable<…>)

* **GetAssessmentResultsList**  : évalue de manière synchrone l’évaluation et retourne les résultats et les erreurs éventuelles (Task<…>)

## <a name="get-started-using-sql-assessment-cmdlets"></a>Commencer à utiliser les applets de commande SQL Assessment

Une évaluation est effectuée sur un objet SQL Server choisi. Dans l’ensemble de règles par défaut, seuls deux genres d’objets sont vérifiés : Server et Database (en plus de ceux-ci, l’API prend en charge les genres FileGroup et AvailabilityGroup). Si vous souhaitez évaluer une instance SQL et toutes ses bases de données, vous devez exécuter les applets de commande SQL Assessment pour chaque objet séparément. Vous pouvez également passer des objets à évaluer aux applets de commande SQL Assessment dans une variable ou le pipeline.

Les objets SqlServer et RegisteredServer sont interchangeables, ce qui vous permet de passer l’un ou l’autre aux applets de commande SQL Assessment.

Passez en revue les exemples ci-dessous pour commencer.

1. Obtenez la liste des vérifications disponibles pour une instance par défaut locale afin de vous familiariser avec les vérifications. Dans cet exemple, nous utilisons le pipe pour transmettre la sortie de l’applet de commande Get-SqlInstance à l’applet de commande SqlAssessmentItem afin de lui transmettre l’objet d’instance.

    ```powershell
    Get-SqlInstance -ServerInstance 'localhost' | Get-SqlAssessmentItem
    ```

2. Obtenez la liste des vérifications disponibles pour toutes les bases de données de l’instance. Ici, nous utilisons l’applet de commande Get-Item et un chemin implémenté avec le fournisseur Windows PowerShell SQL Server pour obtenir la liste des bases de données, que nous transmettons ensuite à l’applet de commande SqlDatabase.

    ```powershell
    Get-Item SQLSERVER:\SQL\localhost\default | Get-SqlAssessmentItem
    ```

    Vous pouvez également utiliser l’applet de commande Get-SqlDatabase pour obtenir le même résultat.

    ```powershell
    Get-SqlDatabase -ServerInstance 'localhost' | Get-SqlAssessmentItem
    ```

3. Obtenez la liste des vérifications disponibles pour toutes les bases de données de l’instance. Ici, nous utilisons l’applet de commande Get-Item et un chemin implémenté avec le fournisseur Windows PowerShell SQL Server pour obtenir la liste des bases de données, que nous transmettons ensuite à l’applet de commande SqlDatabase.

    ```powershell
    Get-Item SQLSERVER:\SQL\localhost\default | Get-SqlAssessmentItem
    ```

    Vous pouvez également utiliser l’applet de commande Get-SqlDatabase pour obtenir le même résultat.

    ```powershell
    Get-SqlDatabase -ServerInstance 'localhost' | Get-SqlAssessmentItem
    ```

4. Appelez l’évaluation pour l’instance et enregistrez les résultats dans une table SQL. Dans cet exemple, nous utilisons le pipe pour transmettre la sortie de l’applet de commande Get-SqlInstance à l’applet de commande Invoke-SqlAssessment, dont les résultats sont transmis à l’aide du pipe à l’applet de commande Write-SqlTableData. L’applet de commande Invoke-Assessment est exécutée avec le paramètre `-FlattenOutput` dans cet exemple. Ce paramètre adapte la sortie à l’applet de commande Write-SqlTableData. Cette dernière génère une erreur si vous omettez le paramètre.

    ```powershell
    Get-SqlInstance -ServerInstance 'localhost' |
    Invoke-SqlAssessment -FlattenOutput |
    Write-SqlTableData -ServerInstance 'localhost' -DatabaseName SQLAssessmentDemo -SchemaName Assessment -TableName Results -Force
    ```

    Appelons à présent une évaluation pour toutes les bases de données de l’instance et ajoutons les résultats à la même table.

    ```powershell
    Get-SqlDatabase -ServerInstance 'localhost' |
    Invoke-SqlAssessment -FlattenOutput |
    Write-SqlTableData -ServerInstance 'localhost' -DatabaseName SQLAssessmentDemo -SchemaName Assessment -TableName Results -Force
    ```

5. Suivez les descriptions et les liens dans la table pour mieux comprendre les recommandations.

6. Personnalisez les règles en fonction de votre environnement et des exigences de votre organisation (voir ci-dessous).

7. Planifiez une tâche ou un travail pour exécuter l’évaluation à intervalles réguliers ou à la demande afin de mesurer la progression.

## <a name="customizing-rules"></a>Personnalisation des règles

Les règles sont conçues pour être personnalisables et extensibles. L’ensemble de règles de Microsoft est conçu pour fonctionner dans la plupart des environnements. Toutefois, il est impossible d’avoir un ensemble de règles qui fonctionne pour tous les environnements. Les utilisateurs peuvent écrire leurs propres fichiers JSON et personnaliser des règles existantes ou en ajouter d’autres. Vous trouverez des exemples de personnalisation et l’ensemble de règles complet publié par Microsoft dans le [dépôt d’exemples](https://aka.ms/sql-assessment-api). Pour plus d’informations sur l’exécution des applets de commande SQL Assessment avec des fichiers JSON personnalisés, utilisez l’applet de commande Get-Help.

### <a name="options-available-with-rule-customization-feature"></a>Options disponibles avec la fonctionnalité de personnalisation de règle

#### <a name="enablingdisabling-certain-rules-or-groups-of-rules-using-tags"></a>Activation/désactivation de règles ou de groupes de règles spécifiques (à l’aide de balises)

Vous pouvez désactiver des règles spécifiques quand elles ne sont pas appliquées à votre environnement ou jusqu’à ce qu’un travail planifié soit effectué pour corriger le problème.

#### <a name="changing-threshold-parameters"></a>Modification des paramètres de seuil

Des règles spécifiques ont des seuils qui sont comparés à la valeur actuelle d’une métrique pour identifier un problème. Si les seuils par défaut ne sont pas adaptés, vous pouvez les modifier.

#### <a name="adding-more-rules-written-by-you-or-third-parties"></a>Ajout de règles écrites par vous ou des tiers

Vous pouvez chaîner des ensembles de règles en ajoutant un ou plusieurs fichiers JSON comme paramètres à votre appel d’API SQL Assessment. Votre organisation peut écrire ces fichiers ou les obtenir auprès d’un tiers. Par exemple, vous pouvez avoir votre fichier JSON qui désactive des règles spécifiques de l’ensemble de règles Microsoft, un autre fichier JSON écrit par un expert du secteur qui inclut des règles que vous trouvez utiles pour votre environnement, puis un autre fichier JSON qui modifie certaines valeurs de seuil dans ce fichier JSON.

> [!IMPORTANT]  
> Nous vous recommandons vivement de passer attentivement en revue les ensembles de règles provenant de sources non approuvées avant de les utiliser afin de vérifier qu’ils ne présentent aucun risque.

## <a name="next-steps"></a>Étapes suivantes

Examinez [SQL Server Management Objects (SMO)](../relational-databases/server-management-objects-smo/overview-smo.md) et [PowerShell](../powershell/download-sql-server-ps-module.md).
