---
title: "Estensione Excel di esempio: classe ActionFilter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 11
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 11
---
# Estensione Excel di esempio: classe ActionFilter
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa classe interna estende la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> e rappresenta un filtro per le azioni di test su un elemento [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
## Proprietà semplici  
 Queste proprietà di sola lettura consentono allo sviluppatore di specificare come questo filtro delle azioni di test deve essere eseguito dal framework dei test codificati dell'interfaccia utente.  Ad esempio, la proprietà <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> fornisce il nome del filtro azioni.  Altre proprietà ottengono l'oggetto <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> del filtro azioni, l'oggetto <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, il nome di <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> per le azioni di test filtrate in base a tale filtro.  Altre indicano se impostare <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> e anche se l'azione di test è <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>.  
  
## Metodo ProcessRule  
 Questo metodo viene chiamato dal framework dei test codificati dell'interfaccia utente ed esegue il filtro sull'oggetto <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> fornito.  Questo particolare override rimuove un'azione di clic del mouse su una cella quando l'azione successiva nello stack invia sequenze di tasti alla cella.  Restituisce quindi `false`.  
  
## Metodi privati  
 Il metodo `IsLeftClick` determina se l'azione fornita rappresenta un clic con il pulsante sinistro del mouse.  Il metodo `AreActionsOnSameExcelCell` determina se due azioni fornite vengono eseguite sulla stessa cella in Excel.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)