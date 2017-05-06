---
title: "Soluzioni PowerPoint"
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
  - "soluzioni Office [sviluppo per Office in Visual Studio], PowerPoint"
  - "modelli [sviluppo per Office in Visual Studio], PowerPoint"
  - "soluzioni [sviluppo per Office in Visual Studio], PowerPoint"
  - "progetti [sviluppo per Office in Visual Studio], PowerPoint"
  - "PowerPoint [sviluppo per Office in Visual Studio]"
  - "progetti di Office [sviluppo per Office in Visual Studio], PowerPoint"
ms.assetid: 02ebad64-9fd3-495f-ab27-4f6206b3d6d2
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Soluzioni PowerPoint
  Visual Studio fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office PowerPoint. È possibile usare i componenti aggiuntivi VSTO per automatizzare PowerPoint, estenderne le funzionalità o personalizzarne l'interfaccia utente.  
  
 Per altre informazioni sui componenti aggiuntivi VSTO, vedere [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) e [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md). Se non si ha esperienza di programmazione con Microsoft Office, vedere [Guida introduttiva &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 ![Collegamento a video](../vsto/media/playvideo.png "Collegamento a video") Per una dimostrazione video correlata, vedere la [procedura di creazione di un componente aggiuntivo per Microsoft PowerPoint](http://go.microsoft.com/fwlink/?LinkId=132767).  
  
## Automazione di PowerPoint usando il modello a oggetti di PowerPoint  
 Il modello a oggetti di PowerPoint espone molti tipi che è possibile usare per automatizzare PowerPoint. Questi tipi consentono di scrivere il codice per eseguire attività comuni:  
  
-   Creare e formattare presentazioni a livello di codice.  
  
-   Aggiungere o rimuovere diapositive dalle presentazioni.  
  
-   Aggiungere o modificare forme su una diapositiva.  
  
 Per accedere al modello a oggetti di PowerPoint da un componente aggiuntivo VSTO, usare il campo `Application` della classe `ThisAddIn` nel progetto. Il campo `Application` restituisce un oggetto <xref:Microsoft.Office.Interop.PowerPoint.Application> che rappresenta l'istanza corrente di PowerPoint. Per altre informazioni, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Quando si effettuano chiamate nel modello a oggetti di PowerPoint, si USANO i tipi forniti nell'assembly di interoperabilità primario per PowerPoint. L'assembly di interoperabilità primario agisce da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in PowerPoint. Tutti i tipi dell'assembly di interoperabilità primario di PowerPoint sono definiti nello spazio dei nomi <xref:Microsoft.Office.Interop.PowerPoint>. Per altre informazioni sugli assembly di interoperabilità primari, vedere [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) e [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).  
  
##  <a name="WordOMDocumentation"></a> Uso della documentazione del modello a oggetti di PowerPoint  
 Per informazioni complete sul modello a oggetti di PowerPoint, è possibile usare il riferimento di assembly di interoperabilità primario \(PIA\) di PowerPoint e il riferimento del modello a oggetti VBA.  
  
### Riferimento dell'assembly di interoperabilità primario  
 Nella documentazione di riferimento dell'assembly di interoperabilità primario \(PIA\) di PowerPoint sono descritti i tipi di assembly di interoperabilità primario per PowerPoint. Questa documentazione è disponibile al seguente percorso: [Riferimento dell'assembly di interoperabilità primario di PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Per altre informazioni sulla progettazione dell'assembly di interoperabilità primario \(PIA\) di PowerPoint, ad esempio sulle differenze tra classi e interfacce nell'assembly di interoperabilità primario \(PIA\) e sulla modalità di implementazione degli eventi nell'assembly di interoperabilità primario \(PIA\), vedere [Panoramica di classi e interfacce negli assembly di interoperabilità primari di Office](http://go.microsoft.com/fwlink/?LinkId=199885).  
  
### Riferimento del modello a oggetti VBA  
 Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di PowerPoint esposto al codice Visual Basic Applications \(VBA\). Per altre informazioni, vedere [Riferimento del modello a oggetti di PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770)  
  
 Tutti gli oggetti e i membri nel riferimento del modello a oggetti VBA corrispondono a tipi e membri nell'assembly di interoperabilità primario \(PIA\) di PowerPoint. Ad esempio, l'oggetto Presentation del riferimento del modello a oggetti VBA corrisponde al tipo <xref:Microsoft.Office.Interop.PowerPoint.Presentation> nell'assembly di interoperabilità primario di PowerPoint. Nonostante il riferimento del modello a oggetti VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA in questo riferimento a Visual Basic o a Visual C\# se si vuole usarli in un progetto di componente aggiuntivo VSTO PowerPoint creato con Visual Studio.  
  
## Personalizzazione dell'interfaccia utente di PowerPoint  
 È possibile modificare l'interfaccia utente di PowerPoint nei modi seguenti.  
  
|Attività|Per altre informazioni|  
|--------------|----------------------------|  
|Creare un riquadro attività personalizzato.|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|  
|Aggiungere schede personalizzate alla barra multifunzione.|[Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)|  
|Aggiungere gruppi personalizzati a una scheda incorporata nella barra multifunzione.|[Procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 Per altre informazioni sulla personalizzazione dell'interfaccia utente di PowerPoint e di altre applicazioni di Microsoft Office, vedere [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
## Vedere anche  
 [Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [PowerPoint 2010 nello sviluppo di applicazioni per Office](http://go.microsoft.com/fwlink/?LinkId=199015)  
  
  