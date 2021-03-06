---
title: Vérifications de cohérence système des tables temporelles | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: ec081d42-57e4-43c7-9e1c-317ba8f23437
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d0957ffb1aa78ee0cbaf3c7c3e5acdb973aa8fb7
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "74165718"
---
# <a name="temporal-table-system-consistency-checks"></a>Vérifications de cohérence système des tables temporelles

[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Lorsque vous utilisez des tables temporelles, le système exécute un nombre de vérifications de cohérence pour s’assurer que le schéma est conforme aux exigences pour Temporal et que les données sont cohérentes et restent cohérentes. En outre, les vérifications temporelles ont été ajoutées à l’instruction **DBCC CHECKCONSTRAINTS** .

## <a name="system-consistency-checks"></a>Vérifications de cohérence système

Avant que **SYSTEM_VERSIONING** soit défini sur **ON**, un ensemble de vérifications sont effectuées sur la table de l’historique et sur la table en cours. Ces vérifications sont regroupées en contrôles de schémas et contrôles de données (si la table de l’historique n’est pas vide). En outre, le système effectue également une vérification de cohérence du runtime.

### <a name="schema-check"></a>Contrôle du schéma

Lorsque vous créez ou modifiez une table en table temporelle, le système vérifie que les conditions sont remplies :

1. Les noms et le nombre de colonnes est le même dans la table en cours et dans la table de l’historique.
2. Les types de données correspondent pour chaque colonne entre la table en cours et la table de l’historique.
3. Les colonnes de période sont définies sur **NOT NULL**.
4. La table en cours comporte une contrainte de clé primaire, ce qui n’est pas le cas de la table de l’historique.
5. Aucune colonne **IDENTITY** n’est définie dans la table de l’historique.
6. Aucun déclencheur n’est défini dans la table de l’historique.
7. Aucune clé primaire n’est définie dans la table de l’historique.
8. Aucune contrainte de table ou de colonne n’est définie sur la table de l’historique. Toutefois, les valeurs de colonne par défaut sur la table de l’historique sont autorisées.
9. La table de l’historique n’est pas placée dans un groupe de fichiers en lecture seule.
10. La table de l’historique n’est pas configurée pour le suivi des modifications ou la capture des modifications de données.

### <a name="data-consistency-check"></a>Vérification de la cohérence des données

Avant que **SYSTEM_VERSIONING** soit défini sur **ON** et dans le cadre d’une opération DML, le système effectue la vérification suivante : **SysEndTime** ≥**SysStartTime**

Lorsque vous créez un lien vers une table de l’historique existante, vous pouvez choisir d’effectuer une vérification de cohérence des données. Cette vérification de cohérence des données garantit que les enregistrements existants ne se chevauchent pas et que les spécifications temporelles sont satisfaites pour chaque enregistrement individuel. La vérification de cohérence des données est effectuée par défaut. En général, l’exécution de la vérification de cohérence des données est recommandée chaque fois que les données des tables en cours et des tables de l’historique risquent d’être désynchronisées, comme lorsque vous incorporez une table de l’historique existante remplie avec des données d’historique.

> [!WARNING]
> Les changements manuels de l’horloge système provoquent l’échec inattendu du système car les vérifications de cohérence des données du runtime mises en place pour éviter les conditions de chevauchement (c’est-à-dire que l’heure de fin d’un enregistrement ne doit pas être antérieure à l’heure de début) échouent.

## <a name="dbcc-checkconstraints"></a>DBCC CHECKCONSTRAINTS

La commande **DBCC CHECKCONSTRAINTS** inclut des vérifications de cohérence des données temporelles. Pour plus d’informations, consultez [DBCC CHECKCONSTRAINTS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkconstraints-transact-sql.md).

## <a name="next-steps"></a>Étapes suivantes

- [Tables temporelles](../../relational-databases/tables/temporal-tables.md)
- [Prise en main des tables temporelles avec versions gérées par le système](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)
- [Partitionnement des tables temporelles](../../relational-databases/tables/partitioning-with-temporal-tables.md)
- [Considérations et limitations liées aux tables temporelles](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)
- [Sécurité de la table temporelle](../../relational-databases/tables/temporal-table-security.md)
- [Gérer la rétention des données d’historique dans les tables temporelles avec contrôle de version par le système](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)
- [Tables temporelles avec version gérée par le système avec tables à mémoire optimisée](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)
- [Vues et fonctions de métadonnées de table temporelle](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
