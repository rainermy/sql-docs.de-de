---
title: Verwalten von Oracle-Tabellenbereichen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], managing tablespaces
- tablespaces [SQL Server replication]
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 437cab6e91e7fe607eea88370c654ad9848824b4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47777998"
---
# <a name="manage-oracle-tablespaces"></a>Verwalten von Oracle-Tabellenbereichen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Ein Tabellenbereich ist eine Einheit des Datenbankspeicherplatzes, die in etwa einer Dateigruppe in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]entspricht. Tabellenbereiche ermöglichen das Speichern und Verwalten von Datenbankobjekten innerhalb einzelner Gruppen. Weitere Informationen finden Sie in der Oracle-Dokumentation.  
  
 Wenn Sie eine Tabelle als Teil einer Oracle-Veröffentlichung konfigurieren, können Sie optional einen vorhandenen Oracle-Tabellenbereich angeben, der beim Speichern der Replikations-Protokollinformationen verwendet wird. Wird kein spezifischer Tabellenbereich angegeben, wird für die Replikationsobjekte der Standardtabellenbereich verwendet, der mit dem Schema für den administrativen Replikationsbenutzer verknüpft ist, das beim Konfigurieren des Verlegers konfiguriert wurde.  
  
 **So geben Sie einen Tabellenbereich für eine Artikelprotokolltabelle an**:  
  
-   Geben Sie im Dialogfeld **Artikeleigenschaften** einen Tabellenbereich an. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
-   Verwenden Sie [sp_changearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md). Soll **sp_changearticle**verwendet werden, geben Sie Folgendes an:  
  
    -   Den Namen des Oracle-Verlegers für den Parameter **@publisher**entspricht.  
  
    -   Den Namen der Oracle-Veröffentlichung für den Parameter **@publication**entspricht.  
  
    -   Den Namen des Artikels für den Parameter **@article**entspricht.  
  
    -   Wert 'tablespace' für den Parameter **@property**entspricht.  
  
    -   Name des Tabellenbereichs für den Parameter **@value**entspricht.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Konfigurieren eines Oracle-Verlegers](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Objects Created on the Oracle Publisher](../../../relational-databases/replication/non-sql/objects-created-on-the-oracle-publisher.md)  
  
  
