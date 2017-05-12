---
title: "Utilizzo di controlli Windows Form nei fogli di lavoro di Excel"
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
  - "controlli [sviluppo per Office in Visual Studio], controlli Windows Form"
  - "Excel [sviluppo per Office in Visual Studio], controlli Windows Form"
  - "Windows Form (controlli) [sviluppo per Office in Visual Studio], Excel"
ms.assetid: bbda7461-0d69-4b56-8ba3-418d63ba49db
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Utilizzo di controlli Windows Form nei fogli di lavoro di Excel
  È possibile aggiungere controlli Windows Form a cartelle di lavoro di Microsoft Office Excel utilizzando la stessa procedura per aggiungere controlli ai Windows Form.  Per informazioni generali sull'utilizzo dei controlli nei documenti, vedere [Panoramica dei controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Considerazioni sui controlli per Excel  
 È necessario fare alcune considerazioni specifiche su Excel.  
  
### Corrispondenza tra la dimensione del controllo e la dimensione della cella  
 È possibile impostare il ridimensionamento automatico del controllo quando la dimensione della cella padre viene modificata.  Per ulteriori informazioni, vedere [Procedura: ridimensionare i controlli nelle celle di un foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### Aggiunta di componenti condivisi da tutti i fogli di lavoro  
 È possibile aggiungere i componenti che si desidera condividere con tutti i fogli di lavoro, ad esempio una classe <xref:System.Data.DataSet>, sulla finestra di progettazione della cartella di lavoro anziché nei fogli di lavoro.  Il componente verrà visualizzato nella barra dei componenti.  
  
### Formula per l'incorporamento dei controlli  
 Quando si seleziona un controllo in Excel, nella **Barra della formula** verrà visualizzato **\=EMBED\("WinForms.Control.Host",""\)**.  Questo testo è necessario e non deve essere cancellato.  
  
## Vedere anche  
 [Procedura: ridimensionare i controlli nelle celle di un foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Procedura: nascondere i controlli contenuti nei fogli di lavoro durante la stampa](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Procedura dettagliata: modifica della formattazione dei fogli di lavoro mediante i controlli CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Procedura dettagliata: visualizzazione di testo in una casella di testo di un foglio di lavoro tramite un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Procedura dettagliata: aggiornamento di un grafico in un foglio di lavoro mediante i pulsanti di opzione](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  