---
title: Definieren Sie Attributbeziehungen | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e49207e99887e13cdd5321821e7325b4a2dac7dc
ms.sourcegitcommit: 38076f423663bdbb42f325e3d0624264e05beda1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/06/2018
ms.locfileid: "52983961"
---
# <a name="attribute-relationships---define"></a>Attributbeziehungen – Definieren
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]sind Attribute der grundlegende Baustein einer Dimension. Eine Dimension enthält einen Satz von Attributen, die auf Basis von Attributbeziehungen organisiert sind.  
  
 Für jede Tabelle in einer Dimension existiert eine Attributbeziehung, die das Schlüsselattribut der Tabelle mit anderen Attributen aus der Tabelle verknüpft. Diese Beziehung kommt zustande, wenn Sie die Dimension erstellen.  
  
 Eine Attributbeziehung bietet die folgenden Vorteile:  
  
-   Sie reduziert den für die Dimensionsverarbeitung erforderlichen Speicherplatz. Dies beschleunigt die Dimensions-, Partitions- und Abfrageverarbeitung.  
  
-   Sie erhöht die Abfrageleistung, da der Speicherzugriff beschleunigt wird und Ausführungspläne besser optimiert werden können.  
  
-   Sie führt aufgrund der Aggregationsentwurfsalgorithmen zur Auswahl effektiverer Aggregate, sofern benutzerdefinierte Hierarchien entlang den Beziehungspfaden definiert wurden.  
  
  
## <a name="attribute-relationship-considerations"></a>Überlegungen zu Attributbeziehungen  
 Sofern die zugrunde liegenden Daten dies unterstützen, sollten Sie auch eindeutige Attributbeziehungen zwischen Attributen definieren. Um eindeutige Attributbeziehungen zu definieren, verwenden Sie die Registerkarte **Attributbeziehungen** des Dimensions-Designers.  
  
 Jedes Attribut, das über eine ausgehende Beziehung verfügt, muss über einen eindeutigen Schlüssel relativ zu seinem verknüpften Attribut verfügen. Anders ausgedrückt darf ein Element in einem Quellattribut nur ein Element in einem verknüpften Attribut identifizieren. Betrachten Sie z. B. die Beziehung "City -> State". In dieser Beziehung ist "City" das Quellattribut und "State" das verknüpfte Attribut. Das Quellattribut ist der n-Seite, und die verknüpfte Seite entspricht der Seite "1", der viele-zu-eins-Beziehung. Der Schlüssel für das Quellattribut lautet "City + Status". Weitere Informationen finden Sie unter [Gewusst wie: Erstellen, Ändern oder Löschen einer Attributbeziehung](../../analysis-services/multidimensional-models/attribute-relationships-create-modify-or-delete-relationship.md).  
  
 Weitere Informationen zu Eigenschaften einer Attributbeziehung finden Sie unter [Konfigurieren von Attributbeziehungseigenschaften](../../analysis-services/multidimensional-models/attribute-relationships-configure-attribute-properties.md).  
  
> [!NOTE]  
>  Eine falsche Definition von Attributbeziehungen kann zu ungültigen Abfrageergebnissen führen.  
  
## <a name="see-also"></a>Siehe auch  
 [Attributbeziehungen](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)  
  
  
