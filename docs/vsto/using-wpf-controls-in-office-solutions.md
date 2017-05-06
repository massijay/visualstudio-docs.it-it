---
title: "Utilizzo dei controlli WPF nelle soluzioni Office"
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
  - "WPF [sviluppo per Office in Visual Studio]"
ms.assetid: 305a212b-0a95-40ad-87aa-22896fe80a04
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Utilizzo dei controlli WPF nelle soluzioni Office
  Anche se le soluzioni create tramite gli strumenti di sviluppo di Office in Visual Studio sono progettate per essere usate direttamente con i controlli Windows Form, è possibile usare anche i controlli WPF nelle soluzioni.  Windows Presentation Foundation \(WPF\) è un'alternativa a Windows Form per progettare interfacce utente.  In WPF viene usato un linguaggio di markup, denominato Extensible Application Markup Language \(XAML\), che offre nuove tecniche per l'incorporazione di interfacce utente, supporti e documenti.  Per altre informazioni, vedere [Introduzione a WPF in Visual Studio 2015](http://msdn.microsoft.com/library/582a314e-e23d-4144-b45b-acbbd5579252).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Qualsiasi elemento dell'interfaccia utente che può contenere i controlli Windows Form in una soluzione Office può ospitare anche i controlli WPF,  tra cui:  
  
-   Documenti e fogli di lavoro nelle personalizzazioni a livello di documento.  
  
-   Riquadri azione nelle personalizzazioni a livello di documento.  
  
-   Riquadri attività personalizzati nei componenti aggiuntivi VSTO.  
  
-   Aree del modulo nei componenti aggiuntivi VSTO per Outlook.  
  
## Aggiunta di controlli WPF a progetti Office in fase di progettazione  
 Non è possibile aggiungere i controlli WPF direttamente agli elementi dell'interfaccia utente nelle soluzioni Office.  È possibile, invece, aggiungere un elemento **Controllo utente \(WPF\)** al progetto e usarlo come area di progettazione per i controlli WPF.  Aggiungere quindi il controllo utente WPF a un elemento dell'interfaccia utente nel progetto.  
  
#### Per aggiungere i controlli WPF a un riquadro azioni, un riquadro attività personalizzato o un'area del modulo  
  
1.  Aprire un progetto al quale si vuole aggiungere un riquadro attività personalizzato, un riquadro azioni o un'area del modulo.  
  
2.  Aggiungere un nuovo elemento **Controllo utente \(WPF\)** al progetto.  
  
3.  Dalla **Casella degli strumenti** aggiungere i controlli WPF all'area di progettazione dei controlli utente WPF.  
  
     Per impostazione predefinita, quando la finestra di progettazione dei controlli utente WPF è aperta, nella **Casella degli strumenti** sono presenti solo controlli WPF.  
  
4.  Compilare il progetto.  
  
5.  Aggiungere un riquadro azioni, un'area del modulo o un riquadro attività personalizzato al progetto:  
  
    -   Per le aree del modulo aggiungere un elemento **Area del modulo di Outlook** al progetto.  Per altre informazioni, vedere [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo per Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
    -   Per i riquadri azioni aggiungere un elemento **Controllo riquadro azioni** o **Controllo utente** al progetto.  Per altre informazioni, vedere [Procedura: aggiungere un riquadro ai documenti Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) e [Procedura: aggiungere un riquadro ai documenti Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
    -   Per i riquadri attività personalizzati aggiungere un elemento **Controllo utente** al progetto.  Per altre informazioni, vedere [Procedura: aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
6.  Dalla scheda *ProjectName* **Controlli utente WPF** della **Casella degli strumenti** trascinare il controllo utente WPF nella finestra di progettazione per il riquadro azioni, l'area del modulo o il riquadro attività personalizzato.  
  
     Visual Studio crea automaticamente un oggetto <xref:System.Windows.Forms.Integration.ElementHost> che contiene il controllo utente WPF nell'elemento dell'interfaccia utente.  
  
7.  Ricompilare il progetto.  
  
#### Per aggiungere controlli WPF a un documento o un foglio di lavoro in un progetto a livello di documento  
  
1.  Aprire un progetto a livello di documento per Word o Excel.  
  
2.  Aggiungere un nuovo elemento **Controllo utente \(WPF\)** al progetto.  
  
3.  Dalla **Casella degli strumenti** aggiungere i controlli WPF all'area di progettazione dei controlli utente WPF.  
  
4.  Compilare il progetto.  
  
5.  Aggiungere al progetto un elemento **Controllo utente** \(ovvero, un controllo utente Windows Form\).  
  
6.  Aprire la finestra di progettazione per il controllo utente Windows Form.  
  
7.  Dalla scheda *ProjectName* **Controlli utente WPF** della **Casella degli strumenti**, trascinare il controllo utente WPF nella finestra di progettazione.  
  
     Visual Studio crea automaticamente un oggetto <xref:System.Windows.Forms.Integration.ElementHost> che contiene il controllo utente WPF nel controllo utente Windows Form.  
  
8.  Scrivere il codice che aggiunge a livello di codice il controllo utente Windows Form al documento o alla cartella di lavoro.  Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
    > [!NOTE]  
    >  Non è possibile trascinare il controllo utente Windows Form nel documento o nel foglio di lavoro nella finestra di progettazione.  
  
9. Ricompilare il progetto.  
  
## Hosting dei controlli WPF mediante la classe ElementHost  
 In Visual Studio vengono fornite funzionalità che consentono di usare i controlli Windows Form nelle soluzioni Office, ma non vengono fornite funzionalità simili per i controlli WPF.  Ad esempio, è possibile aggiungere i controlli Windows Form a documenti e fogli di lavoro in fase di progettazione trascinandoli dalla **Casella degli strumenti** o in fase di esecuzione usando metodi di supporto.  Questi strumenti non sono tuttavia disponibili per i controlli WPF.  
  
 I controlli WPF usano la classe <xref:System.Windows.Forms.Integration.ElementHost> come livello di integrazione tra un form o un controllo Windows Form e i controlli WPF.  Quando si aggiungono i controlli WPF alla soluzione in fase di progettazione, Visual Studio genera automaticamente un oggetto <xref:System.Windows.Forms.Integration.ElementHost>.  
  
## Risorse WPF  
 Per altre informazioni sulle problematiche di progettazione e architettura per l'hosting dei controlli WPF in form e controlli Windows Form, vedere gli argomenti seguenti:  
  
-   [Architettura di input per l'interoperabilità tra Windows Form e WPF](http://msdn.microsoft.com/library/0eb6f137-f088-4c5e-9e37-f96afd28f235)  
  
-   [Mapping di proprietà di Windows Form e WPF](http://msdn.microsoft.com/library/999d8298-9c04-467d-a453-86e41002057d)  
  
-   [Interoperatività di WPF e Windows Form](http://msdn.microsoft.com/library/9e8aa6b6-112c-4579-98d1-c974917df499)  
  
-   [Controlli Windows Form e controlli WPF equivalenti](http://msdn.microsoft.com/library/8a157e6b-8054-46db-a5cf-a78966acc7a1)  
  
 Per altre informazioni sull'aggiunta dei controlli WPF a form e controlli Windows Form in Visual Studio in fase di progettazione, vedere gli argomenti seguenti:  
  
-   [Procedura dettagliata: creazione di nuovo contenuto WPF in Windows Form in fase di progettazione](http://msdn.microsoft.com/library/2e92d8e8-f0e4-4df7-9f07-2acf35cd798c)  
  
-   [Procedura dettagliata: disposizione del contenuto WPF in Windows Form in fase di progettazione](http://msdn.microsoft.com/library/5efb1c53-1484-43d6-aa8a-f4861b99bb8a)  
  
-   [Procedura dettagliata: applicazione di stili al contenuto WPF](http://msdn.microsoft.com/library/e574aac7-7ea4-4cdb-8034-bab541f000df)  
  
## Vedere anche  
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Panoramica dei controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md)   
 [Riquadri attività personalizzati](../vsto/custom-task-panes.md)   
 [Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procedura: aggiungere un riquadro ai documenti Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procedura: aggiungere un riquadro ai documenti Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procedura: aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo per Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)  
  
  