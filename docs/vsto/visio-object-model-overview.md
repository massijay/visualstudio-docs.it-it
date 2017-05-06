---
title: "Panoramica del modello a oggetti di Visio"
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
  - "Visio [sviluppo per Office in Visual Studio], modello a oggetti"
  - "modelli a oggetti [sviluppo per Office in Visual Studio], Office"
  - "modelli a oggetti [sviluppo per Office in Visual Studio], Visio"
  - "oggetti [sviluppo per Office in Visual Studio], modelli a oggetti di Office"
  - "modelli a oggetti di Office"
  - "modelli a oggetti di Visio"
ms.assetid: 11f0ae0c-feff-46c7-9885-b968391718f7
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Panoramica del modello a oggetti di Visio
  Per sviluppare soluzioni Office per Microsoft Office Visio è possibile interagire con il modello a oggetti di Visio. Questo modello a oggetti è costituito da classi e interfacce fornite nell'assembly di interoperabilità primario per Visio ed è definito nello spazio dei nomi Microsoft.Office.Interop.Visio.  
  
 Questo argomento contiene una breve panoramica del modello a oggetti di Visio. Per informazioni sull'uso del modello a oggetti di Visio per eseguire attività nei progetti di Office, vedere gli argomenti seguenti:  
  
-   [Utilizzo di documenti di Visio](../vsto/working-with-visio-documents.md)  
  
-   [Utilizzo di forme di Visio](../vsto/working-with-visio-shapes.md)  
  
## Informazioni sul modello a oggetti di Visio  
 In Visio sono disponibili numerosi oggetti con cui è possibile interagire. Questi oggetti sono organizzati in una gerarchia che corrisponde strettamente all'interfaccia utente. Il vertice della gerarchia è occupato dall'oggetto [Microsoft.Office.Interop.Visio.Application](HV10077088). Questo oggetto rappresenta l'istanza corrente di Visio. L'oggetto Microsoft.Office.Interop.Visio.Application contiene gli oggetti Microsoft.Office.Interop.Visio.Document e Microsoft.Office.Interop.Visio.Page  nonché le raccolte Microsoft.Office.Interop.Visio.Documents e Microsoft.Office.Interop.Visio.Pages. È possibile modificare e usare ogni oggetto e raccolta con i numerosi metodi e le varie proprietà di cui dispone.  
  
 Per altre informazioni, vedere la documentazione di riferimento di VBA sugli oggetti [Microsoft.Office.Interop.Visio.Application](HV10077088), [Microsoft.Office.Interop.Visio.Document](HV10077095) e [Microsoft.Office.Interop.Visio.Page](HV10077063) nonché sulle raccolte [Microsoft.Office.Interop.Visio.Documents](HV10077062) e [Microsoft.Office.Interop.Visio.Pages](HV10077074).  
  
 Le sezioni riportate di seguito forniscono una breve descrizione degli oggetti di livello superiore e della loro reciproca interazione. Tali oggetti comprendono quelli elencati di seguito:  
  
-   Oggetto Application  
  
-   Oggetto Document  
  
-   Oggetto Page  
  
### Oggetto Application  
 L'oggetto Microsoft.Office.Interop.Visio.Application rappresenta l'applicazione Visio e costituisce l'elemento padre di tutti gli altri oggetti. I membri di tale oggetto in genere vengono applicati a Visio nel suo complesso. È possibile usare le proprietà e i metodi degli oggetti Microsoft.Office.Interop.Visio.Application e Microsoft.Office.Interop.Visio.ApplicationSettings per controllare l'ambiente di Visio.  
  
 Nei progetti di componente aggiuntivo VSTO è possibile accedere all'oggetto Microsoft.Office.Interop.Visio.Application usando il campo `Application` della classe `ThisAddIn`. Per altre informazioni, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
### Oggetto Document  
 L'oggetto Microsoft.Office.Interop.Visio.Document svolge un ruolo centrale nell'ambito della programmazione di Visio. Rappresenta un disegno, uno stencil o un file modello. Quando si apre un documento di Visio o se ne crea uno nuovo, viene creato un nuovo oggetto Microsoft.Office.Interop.Visio.Document, che viene aggiunto alla raccolta Microsoft.Office.Interop.Visio.Documents dell'oggetto Microsoft.Office.Interop.Visio.Application.  
  
 Il documento con lo stato attivo è definito documento attivo. È rappresentato dalla proprietà Microsoft.Office.Interop.Visio.Application.ActiveDocument dell'oggetto Microsoft.Office.Interop.Visio.Application.  
  
### Oggetto Page  
 L'oggetto Microsoft.Office.Interop.Visio.Page rappresenta l'area di disegno di una pagina di primo piano o di sfondo. Per determinare se una pagina è di primo piano o di sfondo è possibile usare la proprietà Microsoft.Office.Interop.Visio.Page.Background.  
  
 Per creare forme, è possibile usare metodi che includono i metodi Microsoft.Office.Interop.Visio.Page.DrawSpline e Microsoft.Office.Interop.Visio.Page.DrawOval. Con il metodo Microsoft.Office.Interop.Visio.Page.Drop o Microsoft.Office.Interop.Visio.Page.DropMany è anche possibile recuperare master dagli stencil e posizionare le forme in una pagina.  
  
## Uso della documentazione del modello a oggetti di Visio  
 Per informazioni complete sul modello a oggetti di Visio, vedere la documentazione di riferimento del modello a oggetti di VBA. Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di Visio esposto al codice Visual Basic Applications \(VBA\). Per altre informazioni, vedere [Riferimento del modello a oggetti di Visio 2010](http://go.microsoft.com/fwlink/?LinkId=199775).  
  
 Tutti gli oggetti e i membri nel riferimento del modello a oggetti di VBA corrispondono a tipi e membri nell'assembly di interoperabilità primario \(PIA\) di Visio. Ad esempio, l'oggetto Document del riferimento del modello a oggetti VBA corrisponde al tipo Microsoft.Office.Interop.Visio.Document nell'assembly di interoperabilità primario di Visio. Nonostante il riferimento del modello a oggetti di VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA in questo riferimento a Visual Basic o a Visual C\# per usarli in un progetto di componente aggiuntivo VSTO di Visio creato con Visual Studio.  
  
> [!NOTE]  
>  Attualmente non è prevista la documentazione di riferimento per l'assembly di interoperabilità primario di Visio.  
  
 Per esempi di codice correlati e strumenti aggiuntivi per creare soluzioni di Visio, vedere [Visio 2010 Software Development Kit](http://go.microsoft.com/fwlink/?LinkId=196501).  
  
### Tipi aggiuntivi negli assembly di interoperabilità primari  
 È possibile cercare negli assembly di interoperabilità primari tipi che non sono visibili a VBA a causa delle differenze di implementazione. VBA offre una visualizzazione del modello a oggetti di Visio che include solo gli oggetti e i membri che è possibile usare direttamente. Gli assembly di interoperabilità primari espongono lo stesso modello a oggetti, ma includono anche le altre interfacce, classi e membri che traducono gli oggetti del modello a oggetti COM nel codice gestito. Questi elementi aggiuntivi non devono essere usati direttamente nel codice.  
  
 Per altre informazioni, vedere [Panoramica di classi e interfacce negli assembly di interoperabilità primari di Office](http://go.microsoft.com/fwlink/?LinkId=189592) e [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).  
  
## Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Utilizzo di documenti di Visio](../vsto/working-with-visio-documents.md)   
 [Utilizzo di forme di Visio](../vsto/working-with-visio-shapes.md)  
  
  