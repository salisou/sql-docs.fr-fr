---
title: Modification de la dimension Product | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8e3ffecd-7f40-41a8-8735-bc9858a310cb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ff912ed43048e00f0ed77989a46b3b7d0b111cff
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66078842"
---
# <a name="modifying-the-product-dimension"></a>Modification de la dimension Product
  Au cours des tâches de cette rubrique, vous allez utiliser un calcul nommé pour fournir des noms plus descriptifs pour les lignes de produits, définir une hiérarchie dans la dimension Product et spécifier le nom de membre (All) pour la hiérarchie. Vous regroupez également les attributs dans des dossiers d'affichage.  
  
## <a name="adding-a-named-calculation"></a>Ajout d'un calcul nommé  
 Vous pouvez ajouter un calcul nommé à une table dans une vue de source de données. Dans la tâche suivante, vous créez un calcul nommé qui affiche le nom de la ligne du produit complet.  
  
#### <a name="to-add-a-named-calculation"></a>Pour ajouter un calcul nommé  
  
1.  Pour ouvrir la vue de source de données **Adventure Works DW 2012** , double-cliquez sur **Adventure Works DW 2012** dans le dossier **Vues des sources de données** de l’Explorateur de solutions.  
  
2.  En bas du volet Schéma, cliquez avec le bouton droit sur l’en-tête de la table **Product** , puis cliquez sur **Nouveau calcul nommé**.  
  
3.  Dans la boîte de dialogue **créer un calcul nommé** , tapez `ProductLineName` dans la zone nom de la **colonne** .  
  
4.  Dans la zone **Expression** , tapez ou copiez l’instruction **CASE** suivante :  
  
    ```  
    CASE ProductLine  
       WHEN 'M' THEN 'Mountain'  
       WHEN 'R' THEN 'Road'  
       WHEN 'S' THEN 'Accessory'  
       WHEN 'T' THEN 'Touring'  
       ELSE 'Components'  
    END  
    ```  
  
     Cette instruction **CASE** crée des noms conviviaux pour chaque ligne de produits dans le cube.  
  
5.  Cliquez sur **OK** pour créer `ProductLineName` le calcul nommé. Cela peut prendre un certain temps.  
  
6.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="modifying-the-namecolumn-property-of-an-attribute"></a>Modification de la propriété NameColumn d'un attribut  
  
#### <a name="to-modify-the-namecolumn-property-value-of-an-attribute"></a>Pour modifier la valeur de la propriété NameColumn d'un attribut  
  
1.  Affichez le Concepteur de dimensions pour la dimension Product. Pour cela, double-cliquez sur la dimension **Product** du nœud **Dimensions** de l’Explorateur de solutions.  
  
2.  Dans le volet **Attributs** de l’onglet **Structure de dimension** , sélectionnez **Product Line**.  
  
3.  Dans le Fenêtre Propriétés sur le côté droit de l’écran, cliquez sur le champ de propriété **NameColumn** en bas de la fenêtre, puis cliquez sur le bouton de navigation (**...**) pour ouvrir la boîte de dialogue **colonne de nom** . (Il peut être nécessaire de cliquer sur l’onglet **Propriétés** à droite de l’écran pour ouvrir la fenêtre Propriétés.)  
  
4.  Sélectionnez `ProductLineName` au bas de la liste **colonne source** , puis cliquez sur **OK**.  
  
     Le champ NameColumn contient maintenant le texte, **Product.ProductLineName (WChar)**. Les membres de la hiérarchie d’attributs **Product Line** affichent maintenant le nom complet de la ligne de produits et non plus le nom abrégé.  
  
5.  Dans le volet **Attributs** de l’onglet **Structure de dimension** , sélectionnez **Product Key**.  
  
6.  Dans la Fenêtre Propriétés, cliquez sur le champ de propriété **NameColumn** , puis cliquez sur le bouton de navigation (**...**) pour ouvrir la boîte de dialogue **colonne de nom** .  
  
7.  Sélectionnez **EnglishProductName** dans la liste **Colonne source** , puis cliquez sur **OK**.  
  
     Le champ NameColumn contient maintenant le texte **Product.EnglishProductName (WChar)**.  
  
8.  Dans le Fenêtre Propriétés, faites défiler la **Name** liste vers le haut, cliquez sur `Product Name`le champ de propriété Name, puis tapez.  
  
## <a name="creating-a-hierarchy"></a>Création d'une hiérarchie  
  
#### <a name="to-create-a-hierarchy"></a>Pour créer une hiérarchie  
  
1.  Faites glisser l’attribut **Product Line** du volet **Attributs** vers le volet **Hiérarchies** .  
  
2.  Faites glisser l’attribut **Model Name** du volet **attributs** vers le ** \<nouveau niveau>** cellule dans le volet **hiérarchies** , sous le niveau **Product Line** .  
  
3.  Faites glisser `Product Name` l’attribut du volet **attributs** vers le ** \<nouveau niveau>** cellule dans le volet **hiérarchies** , sous le niveau **nom du modèle** . (Vous avez renommé Product Key en Product Name dans la section précédente.)  
  
4.  Dans le volet **hiérarchies** de l’onglet **structure de dimension** , cliquez avec le bouton droit sur la barre de titre de la hiérarchie **hiérarchie** , cliquez sur **Renommer**, puis tapez `Product Model Lines`.  
  
     Le nom de la hiérarchie est maintenant `Product Model Lines`.  
  
5.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="specifying-folder-names-and-all-member-names"></a>Spécification de noms de dossiers et de noms de membres pour le niveau All  
  
#### <a name="to-specify-the-folder-and-member-names"></a>Pour spécifier les noms de dossiers et de membres  
  
1.  Dans le volet **Attributs** , sélectionnez les attributs suivants en maintenant la touche Ctrl enfoncée pendant que vous cliquez sur chacun d’eux :  
  
    -   **Classe**  
  
    -   **Couleur**  
  
    -   **Jours de fabrication**  
  
    -   **Reorder Point**  
  
    -   **Safety Stock Level**  
  
    -   **Taille**  
  
    -   **Size Range**  
  
    -   **Style**  
  
    -   **Poids**  
  
2.  Dans le champ de propriété **AttributeHierarchyDisplayFolder** de l’fenêtre Propriétés, `Stocking`tapez.  
  
     Vous avez maintenant groupé ces attributs dans un seul dossier d'affichage.  
  
3.  Dans le volet **Attributs** , sélectionnez les attributs suivants :  
  
    -   **Dealer Price**  
  
    -   **List Price**  
  
    -   **Standard Cost**  
  
4.  Dans la cellule de propriété **AttributeHierarchyDisplayFolder** de la fenêtre Propriétés, `Financial`tapez.  
  
     Vous avez maintenant groupé ces attributs dans un deuxième dossier d'affichage.  
  
5.  Dans le volet **Attributs** , sélectionnez les attributs suivants :  
  
    -   **Date de fin**  
  
    -   **Date de début**  
  
    -   **État**  
  
6.  Dans la cellule de propriété **AttributeHierarchyDisplayFolder** de la fenêtre Propriétés, `History`tapez.  
  
     Vous avez maintenant groupé ces attributs dans un troisième dossier d'affichage.  
  
7.  Sélectionnez la `Product Model Lines` hiérarchie dans le volet **hiérarchies** , puis remplacez la valeur de la propriété **AllMemberName** dans `All Products`la fenêtre Propriétés par.  
  
8.  Cliquez sur une zone ouverte du volet **hiérarchies** , puis modifiez la propriété **AttributeAllMemberName** en haut de la fenêtre Propriétés en `All Products`.  
  
     Ceci vous permet de modifier les propriétés de la dimension Product. Vous pouvez aussi cliquer sur **Product** en haut de la liste des attributs dans le volet **Attributs** .  
  
9. Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="defining-attribute-relationships"></a>Définition des relations d'attributs  
 Si les données sous-jacentes le prennent en charge, il est également conseillé de définir des relations d'attributs entre les attributs. La définition de relations d'attributs accélère le traitement des dimensions, des partitions et des requêtes. Pour plus d’informations, consultez [Définir des relations d’attributs](multidimensional-models/attribute-relationships-define.md) et [Relations d’attributs](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
#### <a name="to-define-attribute-relationships"></a>Pour définir les relations d'attributs  
  
1.  Dans le **Concepteur de dimensions** pour la dimension Product, cliquez sur l’onglet **Relations d’attributs** .  
  
2.  Dans le diagramme, cliquez avec le bouton droit sur l’attribut **Model Name** puis sélectionnez **Nouvelle relation d’attribut**.  
  
3.  Dans la boîte de dialogue **Créer une relation d’attribut** , **l’Attribut source** est **Model Name**. Définissez **l’Attribut associé** sur **Product Line**.  
  
     Dans la liste **Type de relation** , laissez le type de relation défini sur **Flexible** car les relations entre les membres peuvent changer au fil du temps. Par exemple, un modèle de produit peut se retrouver déplacé vers une autre ligne de produits.  
  
4.  Cliquez sur **OK**.  
  
5.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="reviewing-product-dimension-changes"></a>Vérification des modifications apportées à la dimension Product  
  
#### <a name="to-review-the-product-dimension-changes"></a>Pour vérifier les modifications apportées à la dimension Product  
  
1.  Dans le menu **Générer** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], cliquez sur **Déployer Analysis Services Tutorial**.  
  
2.  Après avoir reçu le message **Le déploiement est terminé** , cliquez sur l’onglet **Navigateur** du **Concepteur de dimensions** pour la dimension **Product** , puis cliquez sur le bouton Reconnecter de la barre d’outils du Concepteur.  
  
3.  Vérifiez que `Product Model Lines` est sélectionné dans la liste **hiérarchie** , puis développez `All Products`.  
  
     Notez que le nom du membre **All** apparaît sous la `All Products`forme. Cela est dû au fait que **AllMemberName** vous avez modifié la propriété AllMemberName `All Products` de la hiérarchie en plus tôt dans la leçon. De même, les membres du niveau **Product Line** ont maintenant des noms conviviaux, au lieu d’abréviations d’une seule lettre.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Modification de la dimension Date](lesson-3-4-modifying-the-date-dimension.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Définir des calculs nommés dans une vue de source de données &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)   
 [Créer des hiérarchies définies par l’utilisateur](multidimensional-models/user-defined-hierarchies-create.md)   
 [Configurer le niveau &#40;Tous&#41; des hiérarchies d’attributs](multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
