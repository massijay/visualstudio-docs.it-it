---
title: "Soluzioni Visio"
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
  - "progetti di Office [sviluppo per Office in Visual Studio], Visio"
  - "soluzioni [sviluppo per Office in Visual Studio], Visio"
  - "Visio [sviluppo per Office in Visual Studio]"
  - "modelli [sviluppo per Office in Visual Studio], Visio"
  - "progetti [sviluppo per Office in Visual Studio], Visio"
  - "soluzioni Office [sviluppo per Office in Visual Studio], Visio"
ms.assetid: c52948c6-6891-43ec-93ff-c54c74ec6016
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Soluzioni Visio
  Visual Studio fornisce modelli di progetto che è possibile usare per creare componenti aggiuntivi VSTO per Microsoft Office Visio. È possibile usare i componenti aggiuntivi VSTO per automatizzare Visio, estenderne le funzionalità o personalizzarne l'interfaccia utente Visio.  
  
 Per altre informazioni sui componenti aggiuntivi VSTO, vedere [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md) e [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md). Se non si ha esperienza di programmazione con Microsoft Office, vedere [Guida introduttiva &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 **Si applica a:** le informazioni in questo argomento si applicano a progetti di componente aggiuntivo VSTO per Visio 2010. Per altre informazioni, vedere [Funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
## Automazione di Visio usando il modello a oggetti di Visio  
 Il modello a oggetti di Visio espone molte classi utilizzabili per automatizzare Visio affinché crei diagrammi per risorse di vario tipo, fra cui organigrammi, diagrammi di flusso, pianificazioni di progetto, diagrammi di rete e spazi di ufficio. L'API consente di scrivere codice per eseguire attività comuni:  
  
-   Creare e posizionare forme e testo nei diagrammi.  
  
-   Gestire il comportamento delle forme in base alla logica di business e all'input dell'utente.  
  
-   Controllare la visualizzazione dei diagrammi, ad esempio mediante panoramica e zoom.  
  
-   Personalizzare l'interfaccia utente dell'applicazione.  
  
-   Importare dati esterni in Visio, connetterli a forme e visualizzarli graficamente in una pagina.  
  
 È possibile visualizzare procedure dettagliate ed esempi di codice per usare il modello a oggetti di Visio per usare documenti e forme in [Utilizzo di documenti di Visio](../vsto/working-with-visio-documents.md) e [Utilizzo di forme di Visio](../vsto/working-with-visio-shapes.md).  
  
 Per accedere al modello a oggetti di Visio da un componente aggiuntivo VSTO, usare nel progetto il campo `Application` della classe `ThisAddIn`. Il campo `Application` restituisce un oggetto Microsoft.Office.Interop.Visio.Application che rappresenta l'istanza corrente di Visio. Per altre informazioni, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Quando si effettuano chiamate nel modello a oggetti di Visio, si usano i tipi che sono stati forniti nell'assembly di interoperabilità primario \(PIA\) per Visio. L'assembly di interoperabilità primario funge da ponte tra il codice gestito nel componente aggiuntivo VSTO e il modello a oggetti COM in Visio. Tutti i tipi dell'assembly di interoperabilità primario di Visio sono definiti nello spazio dei nomi Microsoft.Office.Interop.Visio. Per altre informazioni sugli assembly di interoperabilità primari, vedere [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) e [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).  
  
## Panoramica del modello a oggetti di Visio  
 È possibile trovare una panoramica del modello a oggetti Visio in [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md), che include i collegamenti al riferimento del modello a oggetti Visio e agli SDK.  
  
## Personalizzazione dell'interfaccia utente di Visio  
 L'interfaccia utente di Visio offre le opzioni di personalizzazione seguenti.  
  
|Attività|Per altre informazioni|  
|--------------|----------------------------|  
|Personalizzare la barra multifunzione.|[Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)|  
  
 Per informazioni sulla personalizzazione dell'interfaccia utente di Visio, vedere la documentazione di riferimento di VBA relativa alla classe [Visio.UIObject](HV10077129).  
  
## Vedere anche  
 [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)   
 [Visio 2010 nello sviluppo per Office](http://go.microsoft.com/fwlink/?LinkId=199017)  
  
  