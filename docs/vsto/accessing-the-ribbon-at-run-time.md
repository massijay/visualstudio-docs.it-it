---
title: "Accesso alla barra multifunzione in fase di esecuzione | Microsoft Docs"
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
  - "classe Globals, barra multifunzione"
  - "barra multifunzione [sviluppo per Office in Visual Studio], accesso"
  - "RibbonManager (classe)"
ms.assetid: 8a7c7c6d-1a18-4d6b-98ee-e483d41f0cd8
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Accesso alla barra multifunzione in fase di esecuzione
  È possibile scrivere codice per mostrare, nascondere o modificare la barra multifunzione e consentire agli utenti di eseguire il codice dai controlli in un riquadro attività personalizzato, un riquadro azioni o un'area del modulo di Outlook.  
  
 È possibile accedere alla barra multifunzione mediante la classe `Globals`.  Per progetti Outlook è possibile accedere alla barra multifunzione che viene visualizzata in una finestra di esplorazione o di controllo di Outlook specifica.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## Accesso alla barra multifunzione usando la classe Globals  
 È possibile usare la classe `Globals` per accedere alla barra multifunzione in un progetto a livello di documento o un progetto di componente aggiuntivo VSTO da qualsiasi posizione nel progetto.  
  
 Per altre informazioni sulla classe `Globals`, vedere [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 Il seguente esempio usa la classe `Globals` per accedere a una barra multifunzione personalizzata denominata `Ribbon1` e impostare il testo visualizzato in una casella combinata nella barra multifunzione su `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#4)]
 [!code-vb[Trin_Outlook_FR_Access#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#4)]  
  
## Accesso a una raccolta di barre multifunzione visualizzate in una finestra di controllo di Outlook specifica  
 È possibile accedere a una raccolta di barre multifunzione visualizzate nei *controlli* di Outlook.  Un controllo rappresenta una finestra che viene aperta in Outlook quando gli utenti eseguono determinate attività, ad esempio la creazione di messaggi di posta elettronica.  Per accedere alla barra multifunzione di una finestra di controllo, chiamare la proprietà `Ribbons` della classe `Globals` e passare un oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> che rappresenta il controllo.  
  
 Il seguente esempio ottiene una raccolta della barra multifunzione del controllo attualmente attivo.  In questo esempio quindi si accede a una barra multifunzione denominata `Ribbon1` e imposta il testo visualizzato su una casella combinata nella barra multifunzione su `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#5)]
 [!code-vb[Trin_Outlook_FR_Access#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#5)]  
  
## Accesso a una raccolta di barre multifunzione visualizzate in una finestra di esplorazione di Outlook specifica  
 È possibile accedere a una raccolta di barre multifunzione visualizzate in una *finestra di esplorazione* di Outlook.  Una finestra di esplorazione è l'interfaccia utente dell'applicazione principale per un'istanza di Outlook.  Per accedere alla barra multifunzione di una finestra di esplorazione, chiamare la proprietà `Ribbons` della classe `Globals` e passare un oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> che rappresenta la finestra di esplorazione.  
  
 Il seguente esempio ottiene una raccolta della barra multifunzione della finestra di esplorazione attualmente attiva.  In questo esempio quindi si accede a una barra multifunzione denominata `Ribbon1` e imposta il testo visualizzato su una casella combinata nella barra multifunzione su `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#6)]
 [!code-vb[Trin_Outlook_FR_Access#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#6)]  
  
## Vedere anche  
 [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md)   
 [Cenni preliminari sul modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura dettagliata: aggiornamento dei controlli di una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Personalizzazione di una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Accesso a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)  
  
  