---
title: "Associazione di un&#39;area del modulo a una classe messaggio di Outlook"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTO.NewFormRegionWizard.InvalidMessageClassName"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "aree di modulo [sviluppo per Office in Visual Studio], classi di messaggio"
  - "FormRegionMessageClassAttribute"
ms.assetid: e2db8d61-fd5f-4059-beec-33b66970f520
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Associazione di un&#39;area del modulo a una classe messaggio di Outlook
  È possibile specificare gli elementi Microsoft Office Outlook che visualizzano un'area di modulo associando l'area di modulo alla classe di messaggio di ogni elemento.  Ad esempio, se si vuole aggiungere un'area di modulo alla fine di un elemento di posta, è possibile associare l'area di modulo alla classe di messaggio IPM.Note.  
  
 Per associare un'area di modulo a una classe di messaggio, specificare il nome della classe di messaggio nella procedura guidata **Nuova area del modulo di Outlook** o applicare un attributo alla classe factory dell'area di modulo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Informazioni sulle classi di messaggio di Outlook  
 Una classe di messaggio di Outlook identifica un tipo di elemento di Outlook.  Nella tabella seguente sono elencati questi otto tipi di elementi standard e i relativi nomi della classe di messaggio.  
  
|Tipo di elemento di Outlook|Nome della classe di messaggio|  
|---------------------------------|------------------------------------|  
|AppointmentItem|IPM.Appointment|  
|ContactItem|IPM.Contact|  
|DistListItem|IPM.DistList|  
|JournalItem|IPM.Activity|  
|MailItem|IPM.Note|  
|PostItem|IPM.Post o IPM.Post.RSS|  
|TaskItem|IPM.Task|  
  
 È anche possibile specificare i nomi delle classi di messaggio personalizzate.  Le classi di messaggio personalizzate identificano i moduli personalizzati definiti in Outlook.  
  
> [!NOTE]  
>  Per le aree di modulo sostituzione e sostituzione completa, è possibile specificare un nuovo nome di classe di messaggio personalizzata.  Non è necessario utilizzare il nome della classe di messaggio di un modulo personalizzato esistente.  Il nome della classe di messaggio personalizzata deve essere univoco.  Per essere certi che il nome sia univoco, utilizzare una convenzione di denominazione simile alla seguente:  \<*StandardMessageClassName*\>. \<*Company*\>. \<*MessageClassName*\> \(ad esempio: IPM.Note.Contoso.MyMessageClass\).  
  
## Associazione di un'area del modulo a una classe messaggio di Outlook  
 Ci sono due modi per associare un'area di modulo a una classe di messaggio:  
  
-   Utilizzare la procedura guidata **Nuova area del modulo di Outlook**.  
  
-   Applicare gli attributi di classe.  
  
### Utilizzo della procedura guidata Nuova area del modulo di Outlook  
 Nella pagina finale della procedura guidata **Nuova area del modulo di Outlook** , è possibile selezionare le classi di messaggio standard e digitare i nomi delle classi di messaggio personalizzate da associare all'area di modulo.  
  
 Le classi di messaggio standard non sono disponibili se l'area di modulo è progettata per sostituire l'intero modulo o la pagina predefinita di un modulo.  I nomi delle classi di messaggio standard possono essere specificati solo per i moduli che aggiungono una pagina nuova a un modulo o che vengono aggiunti alla fine di un modulo.  Per ulteriori informazioni, vedere [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo per Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Per includere una o più classi di messaggio personalizzate, digitare i nomi nella casella **Fornire le classi di messaggi per la visualizzazione dell'area del modulo**.  
  
 I nomi digitati devono essere conformi alle linee guida seguenti:  
  
-   Utilizzare il nome completo della classe di messaggio, ad esempio: "IPM.Note.Contoso".  
  
-   Utilizzare un punto e virgola per separare più nomi di classe di messaggio.  
  
-   Non includere classi di messaggio standard di Outlook, ad esempio "IPM.Note" o "IPM.Contact."  Includere solo classi di messaggio personalizzate, ad esempio "IPM.Note.Contoso."  
  
-   Non specificare la classe di messaggio di base da sola \(ad esempio: "IPM"\).  
  
-   Non superare 256 caratteri per ogni nome della classe di messaggio.  
  
 La procedura guidata **Nuova area del modulo di Outlook** convalida il formato dell'input quando si fa clic su **Fine**.  
  
> [!NOTE]  
>  La procedura guidata **Nuova area del modulo di Outlook** non verifica che i nomi delle classi di messaggio forniti siano corretti o validi.  
  
 Al termine, la procedura guidata **Nuova area del modulo di Outlook** applica gli attributi alla classe dell'area di modulo che contiene i nomi delle classi di messaggio specificati.  È possibile applicare questi attributi anche manualmente.  
  
### Applicazione degli attributi di classe  
 È possibile associare un'area di modulo a una classe di messaggio di Outlook dopo avere completato la procedura guidata **Nuova area del modulo di Outlook** .  A tale scopo, applicare attributi alla classe factory dell'area di modulo.  
  
 Nell'esempio seguente sono illustrati due attributi <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> applicati a una classe factory dell'area di modulo denominata `myFormRegion`.  Il primo attributo associa l'area di modulo a una classe di messaggio standard per un modulo di messaggio di posta.  Il secondo attributo associa l'area di modulo a una classe di messaggio personalizzata denominata `IPM.Task.Contoso`.  
  
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Attributes/CS/FormRegion1.cs#1)]
 [!code-vb[Trin_Outlook_FR_Attributes#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Attributes/VB/FormRegion1.vb#1)]  
  
 Gli attributi devono essere conformi alle linee guida seguenti:  
  
-   Per le classi di messaggio personalizzate, utilizzare il nome completo della classe di messaggio, ad esempio: "IPM.Note.Contoso".  
  
-   Non specificare la classe di messaggio di base da sola \(ad esempio: "IPM"\).  
  
-   Non superare 256 caratteri per ogni nome della classe di messaggio.  
  
-   Non includere i nomi delle classi di messaggio standard se l'area di modulo sostituisce l'intero modulo o la pagina predefinita di un modulo.  I nomi delle classi di messaggio standard possono essere specificati solo per i moduli che aggiungono una pagina nuova a un modulo o che vengono aggiunti alla fine di un modulo.  Per ulteriori informazioni, vedere [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo per Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Visual Studio convalida il formato dei nomi delle classi di messaggio quando il progetto viene compilato.  
  
> [!NOTE]  
>  Visual Studio non verifica che i nomi delle classi di messaggio forniti siano corretti o validi.  
  
## Vedere anche  
 [Accesso a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)   
 [Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procedura dettagliata: progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Linee guida per la creazione delle aree di modulo di Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Sulla classe di nome e di messaggio del form](HV01044315)   
 [Come Outlook forme e gli elementi offrono](HV01044298)  
  
  