---
title: "Creazione di controlli utente riutilizzabili per web part o pagine applicazione"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, controlli utente"
  - "controlli utente [sviluppo per SharePoint in Visual Studio], creazione"
ms.assetid: 8fcafd98-c002-47f1-b4a9-cbb500232616
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Creazione di controlli utente riutilizzabili per web part o pagine applicazione
  In Visual Studio, è possibile creare controlli personalizzati, che possono essere utilizzati dalle pagine dell'applicazione e dai Web part eseguiti in SharePoint.  Questi controlli sono denominati controlli utente.  Per ulteriori informazioni sui controlli utente, vedere [ASP.NET User Controls](http://msdn.microsoft.com/library/5e601b3d-bb16-4dbe-9e35-7e92a34565ca).  
  
## Creazione di un controllo utente  
 Per creare un controllo utente, aggiungere un **Controllo utente** a un **Progetto SharePoint vuoto**.  Per ulteriori informazioni, vedere [Procedura: creare un controllo utente per una web part o una pagina applicazione di SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).  
  
 Quando si aggiunge un elemento **Controllo utente**, in Visual Studio viene creata una cartella nel progetto, quindi vengono aggiunti alcuni file alla cartella.  Nella tabella riportata di seguito viene descritto ogni file.  
  
|File|Descrizione|  
|----------|-----------------|  
|File di controllo utente|Definisce il controllo utente.  Per progettare il controllo utente, aggiungere controlli e markup a questo file.|  
|File di codice|Contiene il file code\-behind del controllo utente.  Aggiungere codice a questo file per gestire gli eventi.|  
|File di codice della finestra di progettazione|Contiene codice generato tramite la finestra di progettazione e non deve essere modificato direttamente.|  
  
## Progettazione del controllo utente  
 Per progettare il controllo utente, utilizzare la finestra di progettazione di Visual Web Developer in Visual Studio.  Questa finestra di progettazione viene visualizzata quando si apre il file di controllo utente nel progetto e viene scelta la scheda **Progettazione**.  Per ulteriori informazioni sull'utilizzo di questa finestra di progettazione, vedere [Visual Studio Web Development Content Map](http://msdn.microsoft.com/it-it/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
## Utilizzo del controllo utente  
 I controlli utente non sono visualizzati in SharePoint finché non vengono inclusi in una pagina applicazione o in una web part.  
  
 Per includere un controllo utente in una pagina applicazione, aggiungere un'istruzione [@ Register](http://msdn.microsoft.com/it-it/66f34922-be41-4e36-9dc8-1774d85311d1) alla pagina applicazione, quindi dichiarare il controllo utente all'interno di uno o più segnaposto contento nella pagina.  Per un esempio su come portare a termine questa attività in una pagina Web ASP.NET standard, vedere [How to: Include a User Control in an ASP.NET Web Page](http://msdn.microsoft.com/library/7c3bfd74-846c-4b88-b1ef-45d75860af92).  
  
 Per includere un controllo utente in una web part, aggiungere il controllo utente alla raccolta di web part <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> nel file di codice della web part.  Nell'esempio riportato di seguito viene aggiunto un controllo utente alla raccolta di web part <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A>.  
  
 [!code-csharp[SP_VisualWebPart#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1.cs#5)]
 [!code-vb[SP_VisualWebPart#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1.vb#5)]  
  
## Debug di un controllo utente  
 Per eseguire il debug di un controllo utente, assicurarsi che sia incluso in una pagina applicazione o in una web part nel progetto SharePoint.  Sarà quindi possibile eseguire il debug del codice nel controllo utente procedendo come per qualsiasi progetto di Visual Studio.  
  
 Quando si avvia il debugger di Visual Studio, viene aperto il sito di SharePoint.  
  
 In SharePoint aprire la pagina applicazione che include il controllo utente.  Se tale controllo utente è incluso in una web part, aggiungere quest'ultima a una pagina web part in SharePoint.  
  
 Per ulteriori informazioni sul debug di progetti SharePoint, vedere [Risoluzione dei problemi relativi alle soluzioni SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Procedura: creare un controllo utente per una web part o una pagina applicazione di SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Viene illustrato come creare controlli riutilizzabili e personalizzati che possono essere utilizzati nelle pagine applicazione e nelle Web part eseguite in SharePoint.|  
|[Utilizzo di Visual Web Developer](http://msdn.microsoft.com/it-it/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|Viene descritto come utilizzare la finestra di progettazione visualizzata quando si apre una pagina Web nel progetto.|  
  
  