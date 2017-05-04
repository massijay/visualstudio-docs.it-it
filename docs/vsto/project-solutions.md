---
title: "Soluzioni Project | Microsoft Docs"
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
  - "progetti [sviluppo per Office in Visual Studio], Project"
  - "soluzioni Office [sviluppo per Office in Visual Studio], Project"
  - "Project [sviluppo per Office in Visual Studio]"
  - "modelli [sviluppo per Office in Visual Studio], Project"
  - "progetti di Office [sviluppo per Office in Visual Studio], Project"
  - "soluzioni [sviluppo per Office in Visual Studio], Project"
ms.assetid: 4ce92269-eb6d-44aa-bee3-6d38ec9995f9
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Soluzioni Project
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office Project. È possibile usare i componenti aggiuntivi VSTO per automatizzare Project, estenderne le funzionalità o personalizzarne l'interfaccia utente.  
  
 Per altre informazioni sui componenti aggiuntivi VSTO, vedere [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) e [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md). Se non si ha esperienza di programmazione con Microsoft Office, vedere [Guida introduttiva &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
## Automazione di Project con il modello a oggetti di Project  
 Il modello a oggetti di Project espone diversi tipi che è possibile usare per automatizzare Project. Questi tipi consentono di scrivere codice per eseguire attività comuni, ad esempio la creazione e la modifica di attività in un progetto a livello di codice.  
  
 Per accedere al modello a oggetti di Project da un componente aggiuntivo VSTO, usare il campo `Application` della classe `ThisAddIn` nel progetto. Il campo `Application` restituisce un oggetto Microsoft.Office.Interop.MsProject.Application  che rappresenta l'istanza corrente di Project. Per altre informazioni, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Quando si effettuano chiamate nel modello a oggetti di Project, si usano i tipi forniti nell'assembly di interoperabilità primario per Project. L'assembly di interoperabilità primario agisce da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in Project. Tutti i tipi dell'assembly di interoperabilità primario di Project sono definiti nello spazio dei nomi Microsoft.Office.Interop.MSProject. Per altre informazioni sugli assembly di interoperabilità primari, vedere [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) e [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).  
  
## Uso della documentazione del modello a oggetti di Project  
 Per informazioni complete sul modello a oggetti di Project, vedere la documentazione di riferimento del modello a oggetti VBA di Project. Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di Project esposto al codice Visual Basic Applications \(VBA\). Per altre informazioni, vedere [Riferimento del modello a oggetti di Project 2010](http://go.microsoft.com/fwlink/?LinkId=199771).  
  
 Tutti gli oggetti e i membri nel riferimento del modello a oggetti VBA corrispondono a tipi e membri nell'assembly di interoperabilità primario \(PIA\) di Project. Ad esempio, l'oggetto Calendar del riferimento del modello a oggetti VBA corrisponde al tipo Microsoft.Office.Interop.MSProject.Calendar nell'assembly di interoperabilità primario di Project. Sebbene il riferimento del modello a oggetti VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA di questo riferimento in Visual Basic o Visual C\# se si vuole usarli in un progetto di componente aggiuntivo VSTO di Project creato con Visual Studio.  
  
> [!NOTE]  
>  Attualmente non è prevista la documentazione di riferimento per l'assembly di interoperabilità primario di Project.  
  
### Tipi di infrastruttura nell'assembly di interoperabilità primario di Project  
 Quando si scrive un codice che usa l'assembly di interoperabilità primario di Project, si può notare che molti tipi non sono descritti nel riferimento di VBA. Questi tipi aggiuntivi, che consentono di convertire in codice gestito gli oggetti del modello a oggetti basato su COM di Project, non possono essere usati direttamente nel codice.  
  
 Per altre informazioni, vedere [Panoramica di classi e interfacce negli assembly di interoperabilità primari di Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
## Personalizzazione dell'interfaccia utente di Project  
 È possibile personalizzare l'interfaccia utente di Project nei modi seguenti.  
  
|Attività|Per altre informazioni|  
|--------------|----------------------------|  
|Aggiungere schede personalizzate alla barra multifunzione in Project|[Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)|  
  
 Per altre informazioni sulla personalizzazione dell'interfaccia utente di Project e di altre applicazioni di Microsoft Office, vedere [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
## Vedere anche  
 [Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Project 2010 e Project Server 2010 nello sviluppo di Office](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  