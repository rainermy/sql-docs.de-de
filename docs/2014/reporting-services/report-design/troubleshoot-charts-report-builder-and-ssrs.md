---
title: Problembehandlung bei Diagrammen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 10774fbba43f2aea9b2e3565169ed9a856c86ae9
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56288228"
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a>Problembehandlung bei Diagrammen (Berichts-Generator und SSRS)
  Beim Arbeiten mit Diagrammen können diese Punkte hilfreich sein.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a>Warum zählt das Diagramm die Werte auf der Wertachse, statt sie zu addieren?  
 Die meisten Diagrammtypen erfordern numerische Werte an der Wertachse (normalerweise der y-Achse), damit sie ordnungsgemäß gezeichnet werden. Wenn der Datentyp des Wertfelds `String` lautet, kann das Diagramm keinen numerischen Wert anzeigen, selbst wenn sich in den Feldern Zahlen befinden. Stattdessen zeigt das Diagramm die Anzahl der Zeilen an, die in diesem Feld einen Wert enthalten. Zur Vermeidung dieses Verhaltens sollten Sie sicherstellen, dass die Felder, die Sie für Wertereihen verwenden, numerische Datentypen und keine Zeichenfolgen mit formatierten Zahlen aufweisen.  
  
## <a name="see-also"></a>Siehe auch  
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  
