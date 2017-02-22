---
title: "How to: Enable ClickOnce Security Settings | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "security [Visual Studio], ClickOnce applications"
  - "ClickOnce deployment, security settings"
  - "security settings, ClickOnce deployment"
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Enable ClickOnce Security Settings
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per poter pubblicare un'applicazione ClickOnce, è necessario attivare la sicurezza per l'accesso al codice per le applicazioni ClickOnce.  Questa operazione viene eseguita automaticamente quando si pubblica un'applicazione utilizzando la Pubblicazione guidata.  
  
 In alcuni casi, l'attivazione della sicurezza per l'accesso al codice può ridurre le prestazioni durante la compilazione o il debug dell'applicazione. In questi casi, è possibile disabilitare temporaneamente le impostazioni di sicurezza.  
  
 Per attivare o disabilitare le impostazioni di sicurezza ClickOnce, è possibile utilizzare la scheda **Sicurezza** di **Progettazione progetti**.  
  
### Per attivare le impostazioni di sicurezza ClickOnce  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Sicurezza**.  
  
3.  Selezionare la casella di controllo **Attiva le impostazioni di sicurezza ClickOnce**.  
  
     È ora possibile personalizzare le impostazioni di sicurezza per l'applicazione nella scheda Sicurezza.  
  
    > [!NOTE]
    >  Questa casella di controllo viene selezionata automaticamente ogni volta che l'applicazione viene pubblicata utilizzando la **Pubblicazione guidata**.  
  
### Per disabilitare le impostazioni di sicurezza ClickOnce  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Sicurezza**.  
  
3.  Deselezionare la casella di controllo **Attiva le impostazioni di sicurezza ClickOnce**.  
  
     L'applicazione verrà eseguita con le impostazioni di sicurezza di attendibilità totale. Qualsiasi impostazione definita nella scheda **Sicurezza** verrà ignorata.  
  
    > [!NOTE]
    >  Ogni volta che l'applicazione viene pubblicata utilizzando la Pubblicazione guidata, la casella di controllo verrà selezionata. Al termine di ogni pubblicazione, la casella di controllo dovrà quindi essere nuovamente deselezionata.  
  
## Vedere anche  
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)