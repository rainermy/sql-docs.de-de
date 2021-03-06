---
title: Hinzufügen von Skalierungsunterbrechungen zu einem Diagramm (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 84d66436-ed62-4967-bbbd-b457593ee787
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 77ff537ddac854981c79624fef84c4a2918ec7dc
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56285408"
---
# <a name="add-scale-breaks-to-a-chart-report-builder-and-ssrs"></a>Hinzufügen von Skalierungsunterbrechungen zu einem Diagramm (Berichts-Generator und SSRS)
  Eine Skalierungsunterbrechung ist ein Streifen, der über den Zeichnungsbereich eines Diagramms gezogen wird, um eine Unterbrechung in der Kontinuität zwischen den hohen und den niedrigen Werten auf einer Wertachse (normalerweise die vertikale oder y-Achse) zu kennzeichnen. Verwenden Sie eine Skalierungsunterbrechung, um zwei unterschiedliche Bereiche in der gleichen Diagrammfläche anzuzeigen.  
  
 ![Diagramm mit Skalierungsunterbrechung](../media/rs-multipledatarangeschart-scalebreak.gif "Chart with scale break")  
  
> [!NOTE]  
>  Sie können nicht angeben, an welcher Stelle im Diagramm eine Skalierungsunterbrechung platziert werden soll. Das Diagramm bestimmt anhand eigener, auf den Werten im Dataset basierenden Berechnungen, ob eine ausreichende Trennung zwischen den Datenbereichen vorhanden ist, um eine Skalierungsunterbrechung auf der Wertachse (Y-Achse) zur Laufzeit zu zeichnen.  
  
 Ein Beispiel eines Diagramms mit Skalierungsunterbrechungen ist als Beispielbericht verfügbar. Weitere Informationen zum Herunterladen des Beispielberichts und anderer Berichte finden Sie unter [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Beispielberichte zu Berichts-Generator und Berichts-Designer](https://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-enable-scale-breaks-on-the-chart"></a>So aktivieren Sie Skalierungsunterbrechungen für das Diagramm  
  
1.  Klicken Sie mit der rechten Maustaste auf die vertikale Achse, und klicken Sie dann auf **Achseneigenschaften**. Das Dialogfeld **Eigenschaften für vertikale Achsen** wird angezeigt.  
  
2.  Aktivieren Sie das Kontrollkästchen **Skalierungsunterbrechungen aktivieren** .  
  
### <a name="to-change-the-style-of-the-scale-break"></a>So ändern Sie den Stil der Skalierungsunterbrechung  
  
1.  Öffnen Sie den Bereich Eigenschaften.  
  
2.  Klicken Sie auf der Entwurfsoberfläche mit der rechten Maustaste auf die Y-Achse des Diagramms. Die Eigenschaften für das Y-Achsenobjekt (standardmäßig als Diagrammachse bezeichnet) werden im Bereich Eigenschaften angezeigt.  
  
3.  Erweitern Sie im Abschnitt **Skala** die ScaleBreakStyle-Eigenschaft.  
  
4.  Ändern Sie die Werte für ScaleBreakStyle-Eigenschaften, z.B. BreakLineType und Spacing. Weitere Informationen zu Skalierungsunterbrechungseigenschaften finden Sie unter [Anzeigen einer Reihe mit mehreren Datenbereichen in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](displaying-a-series-with-multiple-data-ranges-on-a-chart.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Formatieren eines Diagramms &#40;Berichts-Generator und SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Achseneigenschaften &#40;Dialogfeld, Achsenoptionen, Berichts-Generator und SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)  
  
  
