---
title: Berichts-Konzept (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: b0aa2159-4e49-4713-8824-5ef9a9edbc62
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: b2b7eec3230c4bd08eb866d31b20cdeecc50d6cc
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56288178"
---
# <a name="report-parameters-concept-report-builder-and-ssrs"></a>Berichtsparameter-Konzept (Berichts-Generator und SSRS)
  Sie können einem Bericht Parameter hinzufügen, um verknüpfte Berichte zu verknüpfen, die Berichtsdarstellung zu steuern, Berichtsdaten zu filtern oder den Bereich eines Berichts auf bestimmte Benutzer oder Orte einzugrenzen.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Berichtsparameter werden wie folgt erstellt:  
  
-   Automatisch, wenn Sie eine Datasetabfrage definieren, die Abfragevariablen enthält. Für jede Abfragevariable werden ein entsprechender Dataset-Abfrageparameter und ein Berichtsparameter mit den gleichen Namen erstellt. Ein Abfrageparameter kann ein Verweis auf eine Abfragevariable oder einen Eingabeparameter für eine gespeicherte Prozedur sein.  
  
-   Automatisch, wenn Sie einem freigegebenen Dataset einen Verweis hinzufügen, der Abfrageparameter enthält.  
  
-   Manuell, wenn Sie im Bereich "Berichtsdaten" Berichtsparameter erstellen. Parameter gehören zu den integrierten Auflistungen, die Sie in einen Ausdruck in einem Bericht einschließen können. Da Ausdrücke verwendet werden, um Werte in der gesamten Berichtsdefinition zu definieren, können Sie Parameter verwenden, um die Berichtsdarstellung zu steuern oder um Werte an verwandte Unterberichte oder Berichte zu übergeben, die ebenfalls Parameter verwenden.  
  
 Weitere Informationen finden Sie unter [Berichtsparameter &#40;Berichts-Generator und Berichts-Designer&#41;](report-parameters-report-builder-and-report-designer.md)" basiert.  
  
 Parameter werden häufig verwendet, um Berichtsdaten zu filtern, bevor und nachdem die Daten an den Bericht zurückgegeben werden. Weitere Informationen finden Sie unter [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).  
  
 Wenn Sie einen Bericht entwerfen, werden Berichtsparameter in der Berichtsdefinition gespeichert. Wenn Sie einen Bericht veröffentlichen, werden Berichtsparameter getrennt von der Berichtsdefinition gespeichert und verwaltet. Nachdem Sie den Bericht auf dem Berichtsserver gespeichert haben, können Sie wie folgende Aufgaben ausführen:  
  
-   Ändern Sie Berichtsparameterwerte direkt auf dem Berichtsserver, unabhängig von der Berichtsdefinition.  
  
-   Erstellen Sie mehrere verknüpfte Berichte. Jeder verknüpfte Bericht ist ein Link zur Berichtsdefinition mit einem separaten Satz von Parameterwerten, die auf dem Berichtsserver unabhängig verwaltet werden können.  
  
 Wenn Sie vorhaben, Berichtsmomentaufnahmen, Verläufe oder Abonnements für einen veröffentlichten Bericht zu erstellen, müssen Sie die Auswirkungen von Berichtsparametern auf die Entwurfsanforderungen für den Bericht kennen.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichterstellungskonzepte &#40;Berichts-Generator und SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md)   
 [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41; (Tutorial: Hinzufügen eines Parameters zu einem Bericht (Berichts-Generator))](../tutorial-add-a-parameter-to-your-report-report-builder.md).  
  
  
