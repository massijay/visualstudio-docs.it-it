---
title: "Procedura: impedire la visualizzazione di un&#39;area del modulo in Outlook"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "annullamento della visualizzazione di aree di modulo"
  - "aree di modulo [sviluppo per Office in Visual Studio], annullamento della visualizzazione"
ms.assetid: 82a25def-776a-476a-a72d-d0a48a827d3c
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Procedura: impedire la visualizzazione di un&#39;area del modulo in Outlook
  È possibile che in alcune situazioni non si desideri visualizzare in Microsoft Office Outlook un'area di modulo relativa a un determinato elemento.  Ad esempio, se un elemento contatto non contiene alcun indirizzo aziendale, è possibile impedire la visualizzazione di un'area di modulo che indica l'ubicazione aziendale in una mappa.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### Per impedire la visualizzazione di un'area di modulo  
  
1.  Aprire il file di codice per l'area di modulo da modificare.  
  
2.  Espandere l'area di codice **Factory area del modulo**.  
  
3.  Aggiungere il codice al gestore eventi  `FormRegionInitializing` che imposta la proprietà <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> della classe <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> su **true**.  
  
 In questo esempio, se l'elemento contatto non contiene un indirizzo, la proprietà <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> è impostata su **true** e l'area di modulo non viene visualizzata.  
  
## Esempio  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#1)]  
  
## Vedere anche  
 [Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procedura dettagliata: progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo per Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Procedura dettagliata: progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Procedura dettagliata: Importazione di un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  