---
title: Extensions
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: f7a64289bd3f1e1bd8fce71d21e5e1604e5bf4b4
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "68262887"
---
# <a name="extensions-for-sql-server-reporting-services-ssrs"></a>Extensions pour SQL Server Reporting Services (SSRS)

  Le serveur de rapports dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] utilise des extensions pour moduler les types d’entrées ou de sorties qu’il accepte pour l’authentification, le traitement des données, le rendu et la remise de rapports. Cela facilite l'utilisation de nouveau standards logiciels, tels qu'un nouveau schéma d'authentification ou un type de source de données personnalisé, par les installations de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] existantes. Le serveur de rapports prend en charge les extensions d'authentification personnalisées, les extensions pour le traitement des données, les extensions pour le traitement des rapports, les extensions de rendu et les extensions de remise. De plus, les extensions qui sont à la disposition des utilisateurs sont configurables dans le fichier de configuration RSReportServer.config. Par exemple, vous pouvez limiter les formats d'exportation que la visionneuse de rapport est autorisée à utiliser. Un serveur de rapports nécessite au moins une extension d'authentification, une extension pour le traitement des données et une extension de rendu. Les extensions de remise et de traitement des rapports sont facultatives, mais nécessaires si vous voulez prendre en charge la diffusion des rapports ou les contrôles personnalisés.  
  
 Cette rubrique décrit les extensions qui sont rapidement disponibles dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
## <a name="security-extensions"></a>Extensions de sécurité

 Les extensions de sécurité servent à authentifier et à autoriser des utilisateurs et des groupes sur un serveur de rapports. L'extension de sécurité par défaut repose sur l'authentification Windows. Vous pouvez également créer une extension de sécurité personnalisée pour remplacer la sécurité par défaut si votre modèle de déploiement nécessite une approche d'authentification différente (par exemple, si vous avez besoin d'une authentification à partir de formulaires pour le déploiement Internet ou extranet). Vous ne pouvez utiliser qu’une seule extension de sécurité dans une installation [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Vous pouvez remplacer l'extension de sécurité pour l'authentification Windows utilisée par défaut, mais vous ne pouvez pas l'utiliser conjointement avec une extension de sécurité personnalisée.  
  
## <a name="data-processing-extensions"></a>Extensions pour le traitement des données

 Les extensions pour le traitement des données sont utilisées pour demander une source de données et retourner un ensemble de lignes aplati. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] utilise différentes extensions pour interagir avec des types de sources de données différents. Vous pouvez utiliser les extensions incluses dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]ou bien développer vos propres extensions. Des extensions de traitement de données pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], Oracle, [!INCLUDE[SAP_DPE_BW_1](../includes/sap-dpe-bw-1-md.md)], Hyperion Essbase, Teradata, OLE DB et ODBC sont fournies. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] peut également utiliser n’importe quel fournisseur de données [!INCLUDE[vstecado](../includes/vstecado-md.md)] . Ces extensions traitent les demandes de requêtes émises par le composant processeur de rapports en effectuant les tâches ci-dessous :  
  
- Ouvrir une connexion à une source de données.  
  
- Analyser une requête et renvoyer une liste de noms de champs.  
  
- Exécuter une requête avec une source de données et renvoyer un ensemble de lignes.  
  
- Passer des paramètres à une requête, le cas échéant.  
  
- Effectuer une itération dans l'ensemble de lignes et récupérer des données.  
  
Certaines extensions peuvent également effectuer les tâches suivantes :  
  
- Analyser une requête et retourner la liste des noms de paramètres utilisés dans la requête.  
  
- Analyser une requête et retourner la liste des champs de regroupement.  
  
- Analyser une requête et retourner la liste des champs de tri.  
  
- Fournir un nom d'utilisateur et un mot de passe pour la connexion à la source de données.  
  
- Passer des paramètres avec plusieurs valeurs à une requête.  
  
- Effectuer une itération dans l'ensemble des lignes et récupérer des métadonnées auxiliaires.  
  
## <a name="rendering-extensions"></a>Extensions de rendu

 Les extensions de rendu transforment les données et les informations de mise en page du processeur de rapport en un format spécifique au périphérique. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] inclut sept extensions de rendu : HTML, Excel, CSV, XML, Image, PDF et [!INCLUDE[msCoName](../includes/msconame-md.md)] Word.  
  
- **Extension de rendu HTML** Quand vous demandez un rapport auprès du serveur de rapports par le biais d’un navigateur web, le serveur de rapports utilise l’extension de rendu HTML pour le rendu du rapport. L'extension de rendu HTML génère l'ensemble du HTML selon la norme d'encodage UTF-8. Pour plus d’informations, consultez [Rendu au format HTML &#40;Générateur de rapports et SSRS&#41;](../reporting-services/report-builder/rendering-to-html-report-builder-and-ssrs.md) et [Prise en charge des navigateurs pour Reporting Services et Power View](../reporting-services/browser-support-for-reporting-services-and-power-view.md).  
  
- **Extension de rendu Excel** L’extension de rendu Excel effectue un rendu de rapport qu’il est possible d’afficher et de modifier dans [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 97 ou version ultérieure. Cette extension de rendu crée des fichiers au format BIFF (Binary Interchange File Format), soit le format de fichier natif des données Excel. Les rapports générés dans [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] prennent en charge toutes les fonctionnalités disponibles pour n'importe quelle feuille de calcul. Pour plus d’informations, consultez [Exportation vers Microsoft Excel &#40;Générateur de rapports et SSRS&#41;](../reporting-services/report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).  
  
- **Extension de rendu CSV** L’extension de rendu CSV effectue le rendu des rapports dans des fichiers texte bruts aux valeurs délimitées par des virgules, sans aucune mise en forme. Les utilisateurs peuvent alors ouvrir ces fichiers avec un tableur (par exemple [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]) ou avec tout autre programme capable de lire des fichiers texte. Pour plus d’informations, consultez [Exportation vers un fichier CSV &#40;Générateur de rapports et SSRS&#41;](../reporting-services/report-builder/exporting-to-a-csv-file-report-builder-and-ssrs.md).  
  
- **Extension de rendu XML** L’extension de rendu XML restitue les rapports dans des fichiers XML. Ces fichiers XML peuvent ensuite être stockés ou lus par d'autres programmes. Vous pouvez également utiliser une transformation XSLT pour convertir le rapport dans un autre schéma XML utilisable par une autre application. Le langage XML généré par l'extension de rendu XML respecte la norme d'encodage UTF-8. Pour plus d’informations, consultez [Exportation vers XML &#40;Générateur de rapports et SSRS&#41;](../reporting-services/report-builder/exporting-to-xml-report-builder-and-ssrs.md).  
  
- **Extension de rendu d’image** L’extension de rendu d’image effectue le rendu des rapports dans des fichiers Bitmap ou des métafichiers. Les rapports sont rendus dans les formats suivants : BMP, EMF, GIF, JPEG, PNG, TIFF et WMF. Par défaut, l'image est rendue au format TIFF, lequel est pris en charge par la visionneuse d'images par défaut de votre système d'exploitation (par exemple Aperçu des images et des télécopies Windows). Vous pouvez imprimer l'image à partir du programme ayant servi à l'afficher. L'utilisation de l'extension de rendu de type image permet de s'assurer que le rendu de rapport a une présentation identique sur tous les clients. (Lorsqu'un utilisateur affiche un rapport au format HTML, l'apparence de ce rapport peut varier en fonction de la version du navigateur utilisé, des paramètres du navigateur et des polices disponibles). L'extension de rendu de type image effectue le rendu du rapport sur le serveur ; par conséquent, tous les utilisateurs voient la même image. Dans la mesure où le rapport est rendu sur le serveur, toutes les polices utilisées dans le rapport doivent être installées sur le serveur. Pour plus d’informations, consultez [Exportation vers un fichier image &#40;Générateur de rapports et SSRS&#41;](../reporting-services/report-builder/exporting-to-an-image-file-report-builder-and-ssrs.md).  
  
- **Extension de rendu PDF** L’extension de rendu PDF effectue le rendu des rapports dans des fichiers PDF qu’il est possible d’ouvrir et d’afficher avec Adobe Acrobat 6.0 ou version ultérieure. Pour plus d’informations, consultez [Exportation vers un fichier PDF &#40;Générateur de rapports et SSRS&#41;](../reporting-services/report-builder/exporting-to-a-pdf-file-report-builder-and-ssrs.md).  
  
- **Extension de rendu Word** L’extension de rendu [!INCLUDE[msCoName](../includes/msconame-md.md)] Word permet de générer un rapport sous forme de document Word compatible avec [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Word 2000 ou version ultérieure. Pour plus d’informations, consultez [Exportation vers Microsoft Word &#40;Générateur de rapports et SSRS&#41;](../reporting-services/report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md).  
  
## <a name="report-processing-extensions"></a>Extensions pour le traitement des rapports

 Des extensions pour le traitement des rapports peuvent être ajoutées afin d'assurer un traitement des rapports personnalisés contenant des éléments de rapport qui ne sont pas fournis avec [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Par défaut, un serveur de rapports peut traiter tables, graphiques, matrices, listes, zones de texte, images et tout autre élément de rapport. Si vous voulez ajouter des fonctionnalités particulières à un rapport nécessitant un traitement personnalisé au cours de son exécution (par exemple, l’incorporation d’une carte [!INCLUDE[msCoName](../includes/msconame-md.md)] MapPoint), vous pouvez créer une extension pour le traitement de ce rapport.  
  
## <a name="delivery-extensions"></a>Extensions de remise
 L'application de traitement en arrière-plan utilise des extensions de remise pour remettre des rapports à différents emplacements. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] propose une extension de remise par e-mail et une extension de remise par partage de fichiers. L'extension de remise par courrier électronique envoie, via le protocole SMTP (Simple Mail Transport Protocol), un message électronique qui englobe soit le rapport proprement dit, soit une URL pointant vers le rapport. Il est également possible d'envoyer de brefs messages de notification, sans URL ni rapport, vers des récepteurs de radiomessagerie, des téléphones ou d'autres périphériques. L'extension de remise dans un partage de fichiers enregistre les rapports dans un dossier partagé sur votre réseau. Vous pouvez spécifier un emplacement, un format de rendu, un nom de fichier ainsi que des options de remplacement pour le fichier créé. Utilisez la remise dans un partage de fichiers pour archiver des rapports présentés, mais aussi pour assurer une stratégie d'utilisation de rapports volumineux. Les extensions de remise fonctionnent avec les abonnements. Lorsqu'un utilisateur crée un abonnement, il peut choisir l'une des extensions de remise disponibles pour déterminer le mode de remise du rapport.