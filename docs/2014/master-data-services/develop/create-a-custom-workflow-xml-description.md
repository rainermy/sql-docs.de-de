---
title: Benutzerdefinierte Workflow-XML-Beschreibung (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: e267e5f4-38bb-466d-82e8-871eabeec07e
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: cec0a0378acceef269b17c93cdc0e2f5e816e437
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52789772"
---
# <a name="custom-workflow-xml-description-master-data-services"></a>Benutzerdefinierte Workflow-XML-Beschreibung (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] wird die <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A>-Methode beim Start eines Workflows vom SQL Server MDS Workflow Integration Service aufgerufen. Diese Methode empfängt Metadaten und Daten zum Element, das die Workflowgeschäftsregel als XML-Block ausgelöst hat. Beispielcode zum Implementieren eines Workflowhandlers finden Sie unter [Beispiel für einen benutzerdefinierten Workflow &#40;Master Data Services&#41;](create-a-custom-workflow-example.md).  
  
 Das folgende Beispiel zeigt eine mögliche Darstellung der XML, die an den Workflowhandler gesendet wird:  
  
```scr  
<ExternalAction>  
  <Type>TEST</Type>  
  <SendData>1</SendData>  
  <Server_URL>This is my test!</Server_URL>  
  <Action_ID>Test Workflow</Action_ID>  
  <Model_ID>5</Model_ID>  
  <Model_Name>Customer</Model_Name>  
  <Entity_ID>34</Entity_ID>  
  <Entity_Name>Customer</Entity_Name>  
  <Version_ID>8</Version_ID>  
  <MemberType_ID>1</MemberType_ID>  
  <Member_ID>12</Member_ID>  
  <MemberData>  
    <ID>12</ID>  
    <Version_ID>8</Version_ID>  
    <ValidationStatus_ID>3</ValidationStatus_ID>  
    <ChangeTrackingMask>0</ChangeTrackingMask>  
    <EnterDTM>2011-02-25T20:16:36.650</EnterDTM>  
    <EnterUserID>2</EnterUserID>  
    <EnterUserName>MyUserName</EnterUserName>  
    <EnterUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</EnterUserMuid>  
    <EnterVersionId>8</EnterVersionId>  
    <EnterVersionName>VERSION_1</EnterVersionName>  
    <EnterVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</EnterVersionMuid>  
    <LastChgDTM>2011-02-25T20:16:36.650</LastChgDTM>  
    <LastChgUserID>2</LastChgUserID>  
    <LastChgUserName>MyUserName</LastChgUserName>  
    <LastChgUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</LastChgUserMuid>  
    <LastChgVersionId>8</LastChgVersionId>  
    <LastChgVersionName>VERSION_1</LastChgVersionName>  
    <LastChgVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</LastChgVersionMuid>  
    <Name>Test Customer</Name>  
    <Code>TC</Code>  
  </MemberData>  
</ExternalAction>  
```  
  
 In der folgenden Tabelle werden einige der Tags beschrieben, die in dieser XML enthalten sind:  
  
|Tag|Description|  
|---------|-----------------|  
|\<Type>|Der von Ihnen im Textfeld **Workflowtyp** in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] eingegebene Text, der zum Identifizieren der zu ladenden benutzerdefinierten Workflowassembly dient.|  
|\<SendData>|Ein boolescher Wert, der mithilfe des Kontrollkästchens **Elementdaten in die Meldung einschließen** in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] gesteuert wird. Der Wert 1 bedeutet, dass der Abschnitt \<MemberData> gesendet wird. Andernfalls wird der Abschnitt \<MemberData> nicht gesendet.|  
|<Server_URL>|Der Text, den Sie im Textfeld **Workflowsite** in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] eingegeben haben.|  
|<Action_ID>|Der Text, den Sie im Textfeld **Workflowname** in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] eingegeben haben.|  
|\<MemberData>|Enthält die Daten des Elements, das die Workflowaktion ausgelöst hat. Dies ist nur enthalten, wenn der Wert von \<SendData> 1 ist.|  
|\<Enter*xxx*>|Dieser Tagsatz enthält Metadaten zur Erstellung des Elements, beispielsweise den Zeitpunkt der Erstellung und den Ersteller.|  
|\<LastChg*xxx*>|Dieser Tagsatz enthält Metadaten zur letzten Änderung des Elements, beispielsweise den Zeitpunkt und Autor.|  
|\<Name>|Das erste Attribut des Elements, das geändert wurde. Dieses Beispielelement enthält nur Namens- und Codeattribute.|  
|\<Code>|Das nächste Attribut des Elements, das geändert wurde. Enthielt dieses Beispielelement mehr Attribute, würden sie diesem nachfolgen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines benutzerdefinierten Workflows &#40;Master Data Services&#41;](create-a-custom-workflow-master-data-services.md)   
 [Beispiel für einen benutzerdefinierten Workflow &#40;Master Data Services&#41;](create-a-custom-workflow-example.md)  
  
  
