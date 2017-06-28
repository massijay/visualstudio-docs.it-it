---
title: "Panoramica del modello a oggetti di Outlook"
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
  - "VST.ProjectItem.OutlookAddin"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Outlook [sviluppo per Office in Visual Studio], panoramica del modello a oggetti"
  - "modelli a oggetti [sviluppo per Office in Visual Studio], Office"
  - "oggetti [sviluppo per Office in Visual Studio], modelli a oggetti di Office"
  - "modelli a oggetti [sviluppo per Office in Visual Studio], Outlook"
  - "modelli a oggetti di Office"
ms.assetid: 59704974-b7d9-46d6-949c-e97349c75279
caps.latest.revision: 59
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 58
---
# Panoramica del modello a oggetti di Outlook
  Per sviluppare componenti aggiuntivi VSTO per Microsoft Office Outlook, è possibile interagire con gli oggetti forniti dal modello a oggetti di Outlook. Il modello a oggetti di Outlook fornisce classi e interfacce che rappresentano elementi nell'interfaccia utente. Ad esempio, l'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> rappresenta l'intera applicazione, l'oggetto <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> rappresenta una cartelle che contiene messaggi di posta elettronica o altri elementi e l'oggetto <xref:Microsoft.Office.Interop.Outlook.MailItem> rappresenta un messaggio di posta elettronica.  
  
 Questo argomento fornisce una breve panoramica di alcuni degli oggetti principali del modello a oggetti di Outlook. Per risorse con altre informazioni sull'intero modello a oggetti di Outlook, vedere [Uso della documentazione del modello a oggetti di Outlook](#refdoc).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 ![Collegamento a video](../vsto/media/playvideo.png "Collegamento a video") Per una dimostrazione correlata, vedere il video su [come usare Outlook per creare una relazione attività personalizzata](http://go.microsoft.com/fwlink/?LinkID=130315).  
  
## Accesso agli oggetti in un progetto di Outlook  
 Outlook offre numerosi oggetti con cui è possibile interagire. Per usare in modo efficace il modello a oggetti, è necessaria una familiarità con gli oggetti principali seguenti:  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Explorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Inspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MailItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.TaskItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ContactItem>  
  
### Oggetto Application  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> rappresenta l'applicazione Outlook ed è l'oggetto di livello massimo nel modello a oggetti di Outlook. Alcuni dei membri più importanti di questo oggetto includono i seguenti:  
  
-   Il metodo [CreateItem](http://msdn.microsoft.com/it-it/771707fb-5f34-473d-9fdf-09a6a7f55ece), che può essere usato per creare un nuovo elemento, ad esempio un messaggio di posta elettronica, un'attività o un appuntamento.  
  
-   La proprietà <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A>, che permette di accedere alle finestre che mostrano i contenuti di una cartella nell'interfaccia utente di Outlook.  
  
-   La proprietà <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A>, che permette di accedere alle finestre che mostrano i contenuti di un singolo elemento, ad esempio un messaggio di posta elettronica o una convocazione riunione.  
  
 Per ottenere un'istanza dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Application>, usare il campo Application della classe `ThisAddIn` nel progetto. Per altre informazioni, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
> [!NOTE]  
>  Per evitare avvisi di sicurezza durante l'uso di proprietà e metodi bloccati dalla protezione del modello a oggetti di Outlook, ottenere gli oggetti di Outlook dal campo Application della classe `ThisAddIn`. Per altre informazioni, vedere [Considerazioni specifiche sulla sicurezza per le soluzioni Office](../vsto/specific-security-considerations-for-office-solutions.md).  
  
### Oggetto Explorer  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> rappresenta una finestra che mostra i contenuti di una cartella che include elementi quali messaggi di posta elettronica, attività o appuntamenti. L'oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> include metodi e proprietà che possono essere usati per modificare la finestra ed eventi che vengono generati quando la finestra viene modificata.  
  
 Per ottenere un oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer>, eseguire una delle operazioni seguenti:  
  
-   Usare la proprietà <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> per accedere a tutti gli oggetti <xref:Microsoft.Office.Interop.Outlook.Explorer> in Outlook.  
  
-   Usare il metodo <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> per ottenere l'oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> che ha attualmente lo stato attivo.  
  
-   Usare il metodo GetExplorer dell'oggetto <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> per ottenere l'oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> per la cartella corrente.  
  
### Oggetto Inspector  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> rappresenta una finestra che mostra un singolo elemento, ad esempio un messaggio di posta elettronica, un'attività o un appuntamento. L'oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> include metodi e proprietà che possono essere usati per modificare la finestra ed eventi che vengono generati quando la finestra viene modificata.  
  
 Per ottenere un oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector>, eseguire una delle operazioni seguenti:  
  
-   Usare la proprietà <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> per accedere a tutti gli oggetti <xref:Microsoft.Office.Interop.Outlook.Inspector> in Outlook.  
  
-   Usare il metodo <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> per ottenere l'oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> che ha attualmente lo stato attivo.  
  
-   Usare il metodo GetInspector di un elemento specifico, ad esempio <xref:Microsoft.Office.Interop.Outlook.MailItem> o <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>, per ottenere l'oggetto Inspector associato.  
  
### Oggetto MAPIFolder  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> rappresenta una cartella che contiene messaggi di posta elettronica, contatti, attività e altri elementi. Outlook offre 16 oggetti <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> predefiniti.  
  
 Gli oggetti <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> predefiniti vengono definiti dai valori di enumerazione <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders>. Ad esempio:  
  
 Microsoft.Office.Interop.Outlook.OlDefaultFolders.olFolderInbox corrisponde alla cartella **Posta in arrivo** in Outlook.  
  
 Per un esempio che illustra come accedere a un oggetto <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> predefinito e creare un nuovo oggetto <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>, vedere [Procedura: creare cartelle personalizzate a livello di codice](../vsto/how-to-programmatically-create-custom-folder-items.md).  
  
### Oggetto MailItem  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.MailItem> rappresenta un messaggio di posta elettronica. Gli oggetti <xref:Microsoft.Office.Interop.Outlook.MailItem> si trovano in genere nelle cartelle, ad esempio **Posta in arrivo**, **Posta inviata** e **Posta in uscita**.<xref:Microsoft.Office.Interop.Outlook.MailItem> espone proprietà e metodi che possono essere usati per creare e inviare messaggi di posta elettronica.  
  
 Per un esempio che illustra come creare un messaggio di posta elettronica, vedere [Procedura: Creare un elemento di posta elettronica a livello di codice](../vsto/how-to-programmatically-create-an-e-mail-item.md).  
  
### Oggetto AppointmentItem  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> rappresenta una riunione, un appuntamento singolo o un appuntamento o riunione ricorrente nella cartella **Calendario**. L'oggetto <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> include metodi che eseguono azioni, quali la risposta o l'inoltro di una convocazione riunione, e proprietà che specificano i dettagli della riunione, ad esempio luogo e ora.  
  
 Per un esempio che illustra come creare un appuntamento, vedere [Procedura: Creare una convocazione riunione a livello di codice](../vsto/how-to-programmatically-create-a-meeting-request.md).  
  
### Oggetto TaskItem  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.TaskItem> rappresenta un'attività da eseguire entro un intervallo di tempo specificato. Gli oggetti <xref:Microsoft.Office.Interop.Outlook.TaskItem> si trovano nella cartella **Attività**.  
  
 Per creare un'attività, usare il metodo [CreateItem](http://msdn.microsoft.com/it-it/771707fb-5f34-473d-9fdf-09a6a7f55ece) dell'ogetto <xref:Microsoft.Office.Interop.Outlook.Application> e passare il valore <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> per il parametro.  
  
### Oggetto ContactItem  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.ContactItem>rappresenta un contatto nella cartella **Contatti**. Gli oggetti <xref:Microsoft.Office.Interop.Outlook.ContactItem> contengono diverse informazioni di contatto per le persone rappresentate, ad esempio via e numero civico, indirizzo di posta elettronica e numeri di telefono.  
  
 Per un esempio che illustra come creare un nuovo contatto, vedere [Procedura: aggiungere una voce ai contatti di Outlook a livello di codice](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Per un esempio che illustra come cercare un contatto esistente, vedere [Procedura: Eseguire la ricerca di un contatto specifico a livello di codice](../vsto/how-to-programmatically-search-for-a-specific-contact.md).  
  
##  <a name="refdoc"></a> Uso della documentazione del modello a oggetti di Outlook  
 Per informazioni complete sul modello a oggetti di Outlook, è possibile usare il riferimento di assembly di interoperabilità primario di Outlook e il riferimento del modello a oggetti VBA.  
  
### Riferimento dell'assembly di interoperabilità primario  
 Il riferimento degli assembly di interoperabilità primari di Outlook documenta i tipi disponibili negli assembly di interoperabilità primari per Outlook 2010. Per altre informazioni, vedere la [guida di riferimento per gli assembly di interoperabilità primari di Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=189580).  
  
 Oltre a fornire informazioni per tutti i tipi disponibili negli assembly di interoperabilità primari, questa documentazione fornisce anche informazioni aggiuntive sulla struttura degli assembly di interoperabilità primari ed esempi di codice per attività di automazione comuni di Outlook.  
  
### Riferimento del modello a oggetti VBA  
 Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di Outlook esposto al codice Visual Basic Applications \(VBA\). Per altre informazioni, vedere [Riferimento del modello a oggetti di Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=199769).  
  
 Tutti gli oggetti e i membri del riferimento del modello a oggetti VBA corrispondono ai tipi e ai membri dell'assembly di interoperabilità primario di Outlook. Ad esempio, l'oggetto Inspector del riferimento del modello a oggetti VBA corrisponde all'oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> nell'assembly di interoperabilità primario di Outlook. Sebbene il riferimento del modello a oggetti di VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA in questo riferimento a Visual Basic o a Visual C\# se si vuole usarli in un progetto di componente aggiuntivo VSTO di Outlook creato con Visual Studio.  
  
### Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Uso dei contatti](../vsto/working-with-contact-items.md)|Fornisce argomenti che illustrano come eseguire attività con i contatti.|  
|[Utilizzo degli elementi di posta](../vsto/working-with-mail-items.md)|Fornisce argomenti che illustrano come eseguire attività con gli elementi di posta elettronica.|  
|[Uso delle cartelle](../vsto/working-with-folders.md)|Fornisce argomenti che illustrano come eseguire attività con le cartelle.|  
|[Uso degli elementi di calendario](../vsto/working-with-calendar-items.md)|Fornisce argomenti che illustrano come eseguire attività con gli elementi di calendario.|  
|[Procedura: determinare l'elemento corrente di Outlook a livello di codice](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Illustra come visualizzare il nome della cartella corrente e alcune informazioni sull'elemento selezionato.|  
  
  