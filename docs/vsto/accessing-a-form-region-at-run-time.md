---
title: "Accesso a un&#39;area del modulo in fase di esecuzione"
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
  - "Controlli [sviluppo per Office in Visual Studio]"
  - "Explorers [sviluppo per Office in Visual Studio]"
  - "aree del modulo [sviluppo per Office in Visual Studio], accesso in fase di esecuzione"
ms.assetid: 58eaa9e0-acba-4a13-a6dd-b7e37a38156e
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Accesso a un&#39;area del modulo in fase di esecuzione
  
  
|Si applica a|  
|------------------|  
|Le informazioni fornite in questo argomento sono valide solo per i tipi di progetto e le versioni di Microsoft Office seguenti. Per altre informazioni, vedere [Funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Tipo di progetto**<br /><br /> -   Progetti di componente aggiuntivo VSTO<br /><br /> **Versione di Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|  
  
 Usare la classe `Globals` per accedere alle aree del modulo da qualsiasi punto del progetto Outlook. Per altre informazioni sulla classe `Globals`, vedere [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Accesso alle aree del modulo visualizzate in una specifica finestra di controllo Outlook  
 Per accedere a tutte le aree del modulo visualizzate in uno specifico controllo Outlook, chiamare la proprietà `FormRegions` della classe `Globals` e passare un oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> che rappresenta il controllo.  
  
 Nell'esempio seguente viene recuperata la raccolta di aree del modulo visualizzate nel controllo che ha attualmente lo stato attivo. Viene quindi effettuato l'accesso a un'area del modulo della raccolta denominata `formRegion1` e il testo visualizzato in una casella di testo viene impostato su `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#2)]
 [!code-vb[Trin_Outlook_FR_Access#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#2)]  
  
## Accesso alle aree del modulo visualizzate in una specifica finestra di esplorazione Outlook  
 Per accedere a tutte le aree del modulo visualizzate in una specifica finestra di esplorazione Outlook, chiamare la proprietà `FormRegions` della classe `Globals` e passare un oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> che rappresenta la finestra di esplorazione.  
  
 Nell'esempio seguente viene recuperata la raccolta di aree del modulo visualizzate nella finestra di esplorazione che ha attualmente lo stato attivo. Viene quindi effettuato l'accesso a un'area del modulo della raccolta denominata `formRegion1` e il testo visualizzato in una casella di testo viene impostato su `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#3)]
 [!code-vb[Trin_Outlook_FR_Access#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#3)]  
  
## Accesso a tutte le aree del modulo  
 Per accedere a tutte le aree del modulo visualizzate in tutte le finestre di esplorazione e in tutti i controlli, chiamare la proprietà `FormRegions` della classe `Globals`.  
  
 Nell'esempio seguente viene recuperata la raccolta di aree del modulo visualizzate in tutte le finestre di esplorazione e in tutti i controlli. Viene quindi effettuato l'accesso a un'area del modulo denominata `formRegion1` e il testo visualizzato in una casella di testo viene impostato su `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#1)]
 [!code-vb[Trin_Outlook_FR_Access#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#1)]  
  
## Accesso ai controlli presenti in un'area del modulo  
 Per accedere ai controlli presenti in un'area del modulo usando la classe `Globals`, è necessario rendere tali controlli accessibili al codice dall'esterno del file di codice dell'area del modulo.  
  
### Aree del modulo progettate nella finestra di progettazione dell'area del modulo  
 Per C\# cambiare il modificatore di ogni controllo a cui si vuole accedere. Per eseguire questa operazione, selezionare ogni controllo nella finestra di progettazione dell'area del modulo e impostare la proprietà **Modificatori** su **Interna** o **pubblica** nella finestra **Proprietà**. Ad esempio, se si imposta la proprietà **Modifier** di `textBox1` su **Internal**, è possibile accedere a `textBox1` digitando `Globals.FormRegions.FormRegion1.textBox1`.  
  
 Per Visual Basic non è necessario cambiare il modificatore.  
  
### Aree del modulo importate  
 Quando si importa un'area del modulo progettata in Outlook, il modificatore di accesso di ogni controllo presente nell'area del modulo diventa privato. Dal momento che non è possibile usare la finestra di progettazione dell'area del modulo per modificare un'area del modulo importata, non esiste alcun modo per cambiare il modificatore di un controllo nella finestra **Proprietà**.  
  
 Per consentire l'accesso a un controllo dall'esterno del file di codice dell'area del modulo, creare una proprietà in tale file di codice per la restituzione del controllo.  
  
 Per altre informazioni su come creare proprietà in C\#, vedere [Procedura: dichiarare e usare proprietà Read Write &#40;Guida per programmatori C&#35;&#41;](http://msdn.microsoft.com/library/a4962fef-af7e-4c4b-a929-4ae4d646ab8a).  
  
 Per altre informazioni su come creare proprietà in Visual Basic, vedere [NON INCLUSO NELLA BUILD: Procedura: Aggiungere campi e proprietà a una classe](http://msdn.microsoft.com/it-it/ae53f61b-3abc-413e-8931-703c5f5e8fc2).  
  
## Vedere anche  
 [Linee guida per la creazione delle aree di modulo di Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Procedura dettagliata: progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo per Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Azioni personalizzate nelle aree di modulo di Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Associazione di un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Procedura dettagliata: Importazione di un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Procedura: impedire la visualizzazione di un'area del modulo in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)   
 [Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Accesso alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  