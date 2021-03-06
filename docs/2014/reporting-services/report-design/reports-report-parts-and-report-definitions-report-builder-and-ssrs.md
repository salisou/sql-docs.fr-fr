---
title: Rapports, parties de rapports et définitions de rapports (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report definitions
- reports
ms.assetid: 2d746550-f8cc-4e97-8a06-d0f03cffc18d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d22c8c22170ecef301eacd553f15c16091c9a6e7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66105044"
---
# <a name="reports-report-parts-and-report-definitions-report-builder-and-ssrs"></a>Rapports, parties de rapports et définitions de rapports (Générateur de rapports et SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]utilise un certain nombre de termes pour décrire un rapport dans différents États, notamment la définition initiale, le rapport publié et le rapport affiché tel qu’il apparaît à l’utilisateur.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-definition-rdl-files"></a>Fichiers de définition de rapport (.rdl)  
 Une définition de rapport est un fichier que vous créez dans le Générateur de rapports ou le Concepteur de rapports. Il fournit une description complète des connexions aux sources de données, des requêtes destinées à récupérer des données et des expressions, paramètres, images, zones de texte et tableaux, ainsi que de tous les autres éléments que vous pouvez inclure dans le rapport lors de sa conception. Bien qu'une définition de rapport puisse être complexe, dans sa plus simple expression elle spécifie une requête, ainsi que le contenu, les propriétés et la mise en page du rapport.  
  
 Au moment de l'exécution, les définitions de rapport sont rendues en tant que rapport traité. Les données sont ainsi extraites de la source de données et mises en forme conformément aux instructions contenues dans la définition du rapport. Une définition de rapport peut être exécutée directement à partir de votre ordinateur et enregistrée localement, comme elle peut être publiée sur un serveur de rapports pour être exécutée également par d'autres utilisateurs.  
  
 Les définitions de rapport sont écrites en langage XML conforme à une grammaire XML nommée RDL (Report Definition Language). Le langage RDL décrit les éléments XML en couvrant toutes les variations possibles d'un rapport.  
  
## <a name="client-report-definition-rdlc-files"></a>Fichiers de définition de rapport client (.rdlc)  
 Le Concepteur de rapports Visual Studio produit des fichiers de définition de rapport client (.rdlc) à utiliser avec le contrôle ReportViewer. Les fichiers .rdlc peuvent être convertis en fichiers .rdl pour une utilisation avec le Concepteur de rapports Reporting Services.  
  
## <a name="report-part-rsc-files"></a>Fichiers de parties de rapports (.rsc)  
 Une définition de partie de rapport est un fragment XML d'un fichier de définition de rapport. Vous créez des parties de rapports en créant une définition de rapport, puis en sélectionnant séparément des éléments de rapport dans le rapport à publier sous forme de parties de rapports. Les parties de rapports incluent des régions de données, des rectangles et les éléments qu'ils contiennent, ainsi que des images. Vous pouvez enregistrer une partie de rapport avec ses références aux sources de données partagées et ses datasets dépendants, afin de pouvoir le réutiliser dans d'autres rapports.  
  
 [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
## <a name="published-reports"></a>Rapports publiés  
 Après avoir créé un fichier .rdl, vous pouvez l'enregistrer localement ou dans un dossier personnel (tel que le dossier Mes rapports) sur le serveur de rapports. Lorsque le rapport est prêt, vous pouvez le publier en l'enregistrant à partir du Générateur de rapports dans un dossier public sur le serveur de rapports, en le téléchargeant via le Gestionnaire de rapports, ou en déployant une solution de projet de rapport à partir du Concepteur de rapports. Un rapport publié est un élément qui est stocké dans une base de données du serveur de rapports et géré sur un serveur de rapports ou un site SharePoint.  
  
 La sécurité d'un rapport publié est assurée au moyen des attributions de rôles utilisant le modèle de sécurité basée sur les rôles de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Les rapports publiés sont accessibles par le biais d'URL, de composants WebPart SharePoint ou du Gestionnaire de rapports. Vous pouvez également naviguer jusqu'aux rapports et les ouvrir dans le Générateur de rapports.  
  
### <a name="report-snapshots"></a>Instantanés de rapport  
 Un rapport peut également être publié sous la forme d'un instantané qui contient à la fois les informations de mise en page et les données qui étaient en vigueur au moment où le rapport a été exécuté pour la première fois. Les instantanés de rapport ne sont pas enregistrés dans un format de rendu particulier. Ils sont générés dans un format d'affichage final (par exemple, au format HTML) uniquement à la demande d'un utilisateur ou d'une application. Pour plus d’informations, consultez [Recherche et affichage de rapports dans le Gestionnaire de rapports &#40;Générateur de rapports et SSRS&#41;](../report-builder/finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md).  
  
## <a name="rendered-reports"></a>Rapports rendus  
 Un rapport rendu est un rapport dont le traitement est complet et qui contient à la fois des informations de mise en page et des données dans un format d'affichage approprié (par exemple au format HTML). Il est impossible de lire un rapport tant que son rendu n'est pas effectué dans un format de sortie. Vous pouvez effectuer le rendu d'un rapport en procédant de l'une des façons suivantes :  
  
-   Créez ou ouvrez un rapport dans le Générateur de rapports ou le Concepteur de rapports, puis exécutez-le.  
  
-   Recherchez et exécutez un rapport dans le Gestionnaire de rapports.  
  
-   Recherchez et exécutez un rapport sur un site SharePoint intégré à un serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   Abonnez-vous à un rapport dont la remise est effectuée, au format de sortie que vous indiquez, dans une boîte de réception de messagerie électronique ou dans un partage de fichiers.  
  
 Abonnez-vous à un rapport, dont la remise est effectuée, au format de sortie que vous indiquez, dans une boîte de réception de messagerie électronique ou dans un partage de fichiers. Le format de rendu par défaut est HTML 4.0 pour les rapports du Générateur de rapports. Outre le format HTML, les rapports peuvent être générés dans divers formats de sortie, notamment Excel, Word, XML, PDF, TIFF et CSV. Tout comme les rapports publiés, les rapports rendus ne peuvent être ni modifiés ni réenregistrés sur un serveur de rapports. Pour plus d’informations, consultez [exportation de rapports &#40;générateur de rapports et&#41;SSRS ](../report-builder/export-reports-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de création de rapports &#40;Générateur de rapports et SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md)   
 [Générateur de rapports SQL Server 2014](../report-builder/report-builder-in-sql-server-2016.md)   
 [Installer, désinstaller et Générateur de rapports la prise en charge](../install-uninstall-and-report-builder-support.md)   
 [Recherche, affichage et gestion de rapports &#40;Générateur de rapports et SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Exportation de rapports &#40;Générateur de rapports et SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
