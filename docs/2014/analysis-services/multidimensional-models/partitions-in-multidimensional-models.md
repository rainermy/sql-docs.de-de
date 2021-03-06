---
title: Partitionen in mehrdimensionalen Modellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 26e01dc7-fa49-4b1f-99eb-7799d1b4dcd2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8caec3620a5f7c0df1e3a5d0558272b1a2fb7bfa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164190"
---
# <a name="partitions-in-multidimensional-models"></a>Partitionen in mehrdimensionalen Modellen
  In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]stellt eine *Partition* den physischen Speicher der in eine Measuregruppe geladenen Faktendaten dar. Für jede Measuregruppe wird automatisch eine einzelne Partition erstellt. Es ist jedoch üblich, zusätzliche Partitionen zur weiteren Segmentierung der Daten zu erstellen, um eine effizientere Verarbeitung und eine schnellere Abfrageleistung zu erzielen.  
  
 Die Verarbeitung ist effizienter, da Partitionen unabhängig von einander parallel auf einem oder mehreren Servern verarbeitet werden können. Abfragen werden schneller ausgeführt, weil für jede Partition Speichermodi und Aggregationsoptimierungen konfiguriert werden können, die zu kürzeren Antwortzeiten führen. Wenn Sie den MOLAP-Speicher beispielsweise für Partitionen auswählen, die neuere Daten enthalten, erzielen Sie im Normalfall eine höhere Leistung als bei ROLAP. Bei einer Partitionierung nach Datum weisen Partitionen, die neuere Daten enthalten, ebenso mehr Optimierungen auf als Partitionen, die ältere, seltener abgefragte Daten enthalten. Wenn Speicher- und Aggregationsverfahren nach Partition variieren, wirkt sich das negativ auf zukünftige Zusammenführungsvorgänge aus. Überprüfen Sie, ob das Zusammenführen ein wesentlicher Bestandteil Ihrer Partitionsverwaltungsstrategie ist, bevor Sie einzelne Partitionen optimieren.  
  
> [!NOTE]  
>  Die Business Intelligence und Enterprise Edition bieten Unterstützung für mehrere Partitionen. In der Standard Edition werden mehrere Partitionen nicht unterstützt. Weitere Informationen finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="important-considerations-when-designing-a-partitioning-strategy"></a>Wichtige Überlegungen zum Entwickeln einer Partitionierungsstrategie  
 Die Integrität der Cubedaten basiert darauf, dass die Daten über die Partitionen des Cubes verteilt werden, ohne dass Daten doppelt auf den Partitionen vorhanden sind. Wenn Daten von den Partitionen zusammengefasst werden, werden alle Datenelemente, die in mehr als einer Partition vorkommen, so zusammengefasst, als wären sie unterschiedliche Datenelemente. Dies kann dazu führen, dass der Endbenutzer falsche Zusammenfassungen und fehlerhafte Daten erhält. Wenn eine Verkaufstransaktion für Produkt X beispielsweise in den Faktentabellen für zwei Partitionen dupliziert wird, könnte die duplizierte Transaktion doppelt berücksichtigt werden, wenn die Verkäufe von Produkt X zusammengefasst werden.  
  
 Es besteht die Möglichkeit, Partitionen zusammenzuführen – ein Aspekt, der Ihre Gesamtstrategie für Speichernutzung und Datenupdates beeinflussen könnte. Partitionen können nur zusammengeführt werden, wenn sie den gleichen Speichermodus und den gleichen Aggregationsentwurf aufweisen. Wenn Sie Partitionen erstellen, die später zusammengeführt werden sollen, können Sie beim Erstellen von Partitionen den Aggregationsentwurf einer anderen Partition kopieren. Partitionen lassen sich nach der Erstellung auch bearbeiten, indem der Aggregationsentwurf einer anderen Partition kopiert wird. Das Zusammenführen von Partitionen sollte mit besonderer Sorgfalt ausgeführt werden, um doppelte Daten in der resultierenden Partition zu vermeiden, was zu Ungenauigkeiten in den Cubedaten führen könnte.  
  
## <a name="local-partitions"></a>Lokale Partitionen  
 Bei lokalen Partitionen handelt es sich um Partitionen, die auf einem einzelnen Server definiert, verarbeitet und gespeichert werden. Wenn sich große Measuregruppen in einem Cube befinden, ist es möglicherweise empfehlenswert, sie auf andere Partitionen auszulagern, damit die Verarbeitung parallel über mehrere Partitionen verteilt stattfindet. Parallele Verarbeitung bietet den Vorteil, dass die Ausführung beschleunigt wird. Weil der Verarbeitungsauftrag für eine Partition nicht beendet sein muss, bevor ein anderer gestartet werden kann, können die Prozesse parallel ausgeführt werden. Weitere Informationen finden Sie unter [Create and Manage a Local Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md).  
  
## <a name="remote-partitions"></a>Remotepartitionen  
 Bei Remotepartitionen handelt es sich um Partitionen, die auf einem Server definiert, aber auf einem anderen verarbeitet und gespeichert werden. Verwenden Sie Remotepartitionen, wenn Sie die Speicherung Ihrer Daten und Metadaten über mehrere Server verteilen möchten. Wenn Sie von der Entwicklung zur Produktion wechseln, wächst die Größe der zu analysierenden Daten normalerweise um ein Vielfaches. Bei so großen Datensegmenten besteht eine mögliche Alternative aus der Verteilung der Daten über mehrere Computer. Das liegt nicht nur daran, dass ein Computer nicht alle Daten fassen kann, sondern dass es sinnvoll ist, die Daten parallel auf mehr als einem Computer zu verarbeiten. Weitere Informationen finden Sie unter [Create and Manage a Remote Partition &#40;Analysis Services&#41;](create-and-manage-a-remote-partition-analysis-services.md).  
  
## <a name="aggregations"></a>Aggregations  
 Aggregationen sind vorausberechnete Zusammenfassungen von Cubedaten, die die Abfrageantwortzeiten in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] beschleunigen. Sie können die Anzahl der für eine Measuregruppe erstellten Aggregationen steuern, indem Sie Grenzwerte für den Speicher und Leistungsgewinne festlegen oder den Prozess zur Erstellung von Aggregationen nach einer Weile willkürlich beenden. Mehr Aggregationen bringen nicht unbedingt Vorteile. Jede neue Aggregation verursacht Kosten sowohl beim Festplattenspeicher als auch bei der Verarbeitungszeit. Es wird empfohlen, Aggregationen für einen Leistungsgewinn von 30 % zu erstellen und die Anzahl von Aggregationen nur zu erhöhen, wenn Tests oder der laufende Betrieb dies erforderlich machen. Weitere Informationen finden Sie unter [Entwerfen von Aggregationen &#40;Analysis Services – Mehrdimensional&#41;](designing-aggregations-analysis-services-multidimensional.md).  
  
## <a name="partition-merging-and-editing"></a>Zusammenführen und Bearbeiten von Partitionen  
 Wenn zwei Partitionen denselben Aggregationsentwurf verwenden, können Sie diese beiden Partitionen zu einer Partition zusammenführen. Wenn z. B. eine Inventardimension nach Monaten partitioniert ist, können Sie am Ende des Kalendermonats die Partition für diesen Monat mit der für das laufende Jahr zusammenführen. Auf diese Weise kann die Partition für den laufenden Monat schnell verarbeitet und analysiert werden, während die anderen Monate des laufenden Jahres nur bei der Zusammenführung erneut verarbeitet werden müssen. Diese Neuverarbeitung nimmt mehr Verarbeitungszeit in Anspruch und kann weniger häufig ausgeführt werden. Weitere Informationen zum Verwalten der Zusammenführung von Partitionen finden Sie unter [Merge Partitions in Analysis Services &#40;SSAS - Multidimensional&#41;](merge-partitions-in-analysis-services-ssas-multidimensional.md). So bearbeiten Sie Cubepartitionen mithilfe der **Partitionen** Registerkarte im Cube-Designer, finden Sie unter [bearbeiten oder Löschen von Partitionen &#40;Analysis Services – mehrdimensional&#41;](edit-or-delete-partitions-analyisis-services-multidimensional.md).  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Thema|Description|  
|-----------|-----------------|  
|[Erstellen und verwalten eine lokale Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md)|Enthält Informationen zum Partitionieren von Daten mit Filtern oder unterschiedlichen Faktentabellen, ohne dass Daten dupliziert werden.|  
|[Festlegen des Partitionsspeichers &#40;Analysis Services – mehrdimensional&#41;](set-partition-storage-analysis-services-multidimensional.md)|Beschreibt die Speicherkonfiguration für Partitionen.|  
|[Bearbeiten oder Löschen von Partitionen &#40;Analysis Services – mehrdimensional&#41;](edit-or-delete-partitions-analyisis-services-multidimensional.md)|Beschreibt, wie Partitionen angezeigt und bearbeitet werden.|  
|[Zusammenführen von Partitionen in Analysis Services &#40;SSAS – mehrdimensional&#41;](merge-partitions-in-analysis-services-ssas-multidimensional.md)|Enthält Informationen zum Zusammenführen von Partitionen, die unterschiedliche Faktentabellen oder Datenslices aufweisen, ohne dass Daten dupliziert werden.|  
|[Festlegen des Rückschreibens von Partitionen](set-partition-writeback.md)|Enthält Anweisungen zum Aktivieren des Schreibzugriffs für eine Partition.|  
|[Erstellen und verwalten eine Remotepartition &#40;Analysis Services&#41;](create-and-manage-a-remote-partition-analysis-services.md)|Beschreibt, wie eine Remotepartition erstellt und verwaltet wird.|  
  
  
