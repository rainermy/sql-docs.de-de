---
title: Anzeigen der Facets der richtlinienbasierten Verwaltung für ein SQL Server-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facets
ms.assetid: 5f423b9f-a6c4-41a7-9d8d-8f4926ce1fb4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: cb2a08d874dd022fdad3646ea263d34dd65b9739
ms.sourcegitcommit: 78e32562f9c1fbf2e50d3be645941d4aa457e31f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54100825"
---
# <a name="view-the-policy-based-management-facets-on-a-sql-server-object"></a>Anzeigen der Facets der richtlinienbasierten Verwaltung für ein SQL Server-Objekt
  In diesem Thema wird beschrieben, wie Sie alle Facets der richtlinienbasierten Verwaltung, die auf ein bestimmtes SQL Server-Objekt in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] angewendet wurden, mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]anzeigen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **Anzeigen aller Facets in einem Objekt mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-view-all-of-the-facets-in-an-object"></a>So zeigen Sie alle Facets in einem Objekt an  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ein Instanzobjekt, eine Datenbank oder ein Datenbankobjekt, und klicken Sie dann auf **Facets**.  
  
2.  In der **Facets anzeigen –**_Object_name_ Dialogfeld die **Facet** wählen Sie ein Facet aus, dessen Eigenschaften Sie anzeigen. Weitere Informationen zu den Optionen in diesem Dialogfeld finden Sie unter [View Facets Dialog Box](view-facets-dialog-box.md).  
  
3.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
  
