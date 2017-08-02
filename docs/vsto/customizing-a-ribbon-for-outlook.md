---
title: "Personalizzazione di una barra multifunzione per Outlook"
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
  - "barra multifunzione personalizzata, informazioni sulla personalizzazione della barra multifunzione"
  - "personalizzazione della barra multifunzione, informazioni sulla personalizzazione della barra multifunzione"
  - "Controlli [sviluppo per Office in Visual Studio]"
  - "Outlook [sviluppo per Office in Visual Studio], barra multifunzione"
  - "barra multifunzione [sviluppo per Office in Visual Studio], Outlook"
ms.assetid: 11d10e72-806d-4d5e-b080-139bd8633eaa
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Personalizzazione di una barra multifunzione per Outlook
  Quando si personalizza la barra multifunzione in Microsoft Office Outlook, è necessario considerare la posizione in cui la barra multifunzione personalizzata verrà visualizzata nell'applicazione.  Outlook visualizza la barra multifunzione nell'interfaccia utente principale dell'applicazione e nelle finestre aperte quando gli utenti eseguono determinate attività, ad esempio la creazione di messaggi di posta elettronica.  Queste finestre dell'applicazione sono denominate controlli.  
  
 ![Collegamento a video](~/docs/data-tools/media/playvideo.gif "Collegamento a video") Per una dimostrazione video correlata, vedere la procedura relativa all'[uso della finestra di progettazione della barra multifunzione per personalizzare la barra multifunzione in Outlook](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Aggiunta di una barra multifunzione personalizzata all'interfaccia utente principale dell'applicazione  
 L'interfaccia utente principale in Outlook è denominata Explorer.  Se si usa l'elemento **Barra multifunzione \(finestra di progettazione visiva\)** è possibile aggiungere una barra multifunzione all'interfaccia Explorer facendo clic sulla proprietà **RibbonType** della barra multifunzione nella finestra **Proprietà** e quindi selezionando **Microsoft.Outlook.Explorer**.  
  
## Assegnazione di una barra multifunzione a un controllo  
 Per identificare il controllo che si vuole personalizzare, specificare il tipo di barra multifunzione corrispondente alla classe messaggio per il controllo.  
  
 Se si usa l'elemento **Barra multifunzione \(finestra di progettazione visiva\)**, fare clic sulla proprietà **RibbonType** della barra multifunzione nella finestra **Proprietà**, quindi selezionare uno o più ID di barra multifunzione nell'elenco di valori.  
  
 È possibile aggiungere più barre multifunzione a un progetto.  Se più barre multifunzione condividono uno stesso ID, eseguire l'override del metodo CreateRibbonExtensibilityObject nella classe `ThisAddin` del progetto per specificare la barra multifunzione da visualizzare in fase di esecuzione.  Per altre informazioni, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).  Per altre informazioni su ogni tipo di barra multifunzione, vedere l'articolo tecnico [Personalizzazione della barra multifunzione in Outlook 2007](http://msdn.microsoft.com/it-it/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
## Specifica del tipo di barra multifunzione con l'elemento XML della barra multifunzione  
 Se si usa l'elemento **Barra multifunzione \(XML\)**, controllare il valore del parametro *ribbonID* nel metodo <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> e restituire la barra multifunzione appropriata.  
  
 Il metodo <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> viene generato automaticamente da Visual Studio nel file di codice della barra multifunzione.  Il parametro *ribbonID* è una stringa che identifica l'interfaccia Explorer o un tipo di controllo specifico.  Per un elenco completo dei valori possibili del parametro *ribbonID*, vedere l'articolo tecnico [Personalizzazione della barra multifunzione in Outlook 2007](http://msdn.microsoft.com/it-it/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
 L'esempio di codice seguente illustra come visualizzare una barra multifunzione personalizzata solo nel controllo `Microsoft.Outlook.Mail.Compose`.  Questo controllo viene visualizzato quando un utente crea un nuovo messaggio di posta elettronica.  La barra multifunzione da visualizzare viene specificata nel metodo `GetResourceText()`, generato nella classe **Ribbon**.  Per altre informazioni sulla classe **Ribbon**, vedere [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/CS/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/VB/Ribbon1.vb#1)]  
  
## Vedere anche  
 [Accesso alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md)  
  
  