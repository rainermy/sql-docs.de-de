---
title: CLR-Integrationssicherheit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- authorization [CLR integration]
- common language runtime [SQL Server], security
- database objects [CLR integration], security
ms.assetid: 05d7a471-c5d5-4730-b903-e4edc8157bb4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 48f9935f26ac4ae17b15f4008dcdb0d8a0e69e5c
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51677719"
---
# <a name="clr-integration-security"></a>Sicherheit der CLR-Integration
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Das Sicherheitsmodell der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Integration in die [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-CLR (Common Language Runtime) dient zur Verwaltung und zum Schutz des Zugriffs auf verschiedene Typen von CLR-Objekten und anderen Objekten, die in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt werden. Diese Objekte werden möglicherweise durch eine [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung oder ein anderes CLR-Objekt, das im Server ausgeführt wird, aufgerufen. Die Aufrufe zwischen Objekten werden als Links bezeichnet. Die Typen von Sicherheitsüberprüfungen, die für diese Objekte ausgeführt werden, hängen von den betroffenen Linktypen ab.  
  
 Das Sicherheitsmodell der CLR Integration dient folgenden Zielen:  
  
-   Standardmäßig sollte durch die Ausführung von verwaltetem Benutzercode in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die Integrität und Stabilität von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nicht beeinträchtigt werden. Die Durchführung von Vorgängen, die die Stabilität von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] potenziell beeinträchtigen, sollte durch entsprechende Berechtigungen auf höherer Ebene geschützt werden.  
  
-   Verwalteter Benutzercode sollte keinen unbefugten Zugriff auf Benutzerdaten oder anderen in der Datenbank enthaltenen Benutzercode erhalten. Benutzerdefinierter Code sollte in dem Sicherheitskontext der Benutzersitzung, in der er aufgerufen wurde, und mit den richtigen Berechtigungen für diesen Sicherheitskontext ausgeführt werden.  
  
-   Der Benutzercode sollte durch geeignete Maßnahmen daran gehindert werden, auf Ressourcen außerhalb des Servers zuzugreifen, sodass er ausschließlich für den Zugriff auf lokale Daten und Berechnungen genutzt wird.  
  
-   Benutzerdefinierter Code sollte nicht in der Lage sein, nur deshalb unbefugten Zugriff auf Systemressourcen zu erlangen, weil er im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Prozess ausgeführt wird.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] kombiniert jetzt das benutzerbasierte Sicherheitsmodell von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit dem auf dem Codezugriff basierenden Sicherheitsmodell der CLR. Einige Vorteile dieses kombinierten Sicherheitsansatzes werden in diesem Abschnitt erläutert.  
  
 In der folgenden Tabelle sind die Themen dieses Abschnitts aufgeführt.  
  
 [CLR-Integration und Codezugriffssicherheit](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)  
 Erläutert das Codezugriffssicherheitsmodell für verwalteten Code.  
  
 [Hostschutzattribute und Programmierung der CLR-Integration](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)  
 Stellt Informationen zu den Hostschutzattributwerten bereit, die in SAFE-Assemblys und EXTERNAL_ACCESS-Assemblys nicht zulässig sind.  
  
 [Links in der Sicherheit der CLR-Integration](https://msdn.microsoft.com/library/168efd01-d12e-4bdf-a1b3-0b5c76474eaf)  
 Beschreibt, wie Teile von Benutzercode in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] einander aufrufen können.  
  
 [Identitätswechsel und Sicherheit der CLR-Integration](https://msdn.microsoft.com/library/1495a7af-2248-4cee-afdb-9269fb3a7774)  
 Erläutert, wie verwalteter Code mithilfe des Identitätswechsels auf externe Ressourcen zugreift.  
  
 [Zulassen von teilweise vertrauenswürdigen Aufrufern](https://msdn.microsoft.com/library/20b0248f-36da-4fc3-97d2-3789fcf6e084)  
 Erläutert Probleme, die auftreten, wenn eine verwaltete Methode eine Methode in einer Klasse aufruft, die in einer anderen Assembly enthalten ist.  
  
 [Anwendungsdomänen und Sicherheit der CLR-Integration](https://msdn.microsoft.com/library/54ee904e-e21a-4ee7-b4ad-a6f6f71bd473)  
 Beschreibt, wie Assemblys in Anwendungsdomänen geladen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von CLR-Integrationsassemblys](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)  
  
  
