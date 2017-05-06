---
title: "Accessibilit&#224; nei progetti di Office"
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
  - "accessibilità [sviluppo per Office in Visual Studio]"
  - "sviluppo per Office in Visual Studio, accessibilità"
  - "barra multifunzione [sviluppo per Office in Visual Studio], tasti di scelta rapida"
  - "tasti di scelta rapida [sviluppo per Office in Visual Studio]"
ms.assetid: 48efcf1f-ca49-47ce-99f0-cc99f051aeae
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Accessibilit&#224; nei progetti di Office
  Microsoft Visual Studio e Microsoft Office includono numerose funzionalità di accessibilità che consentono di compilare soluzioni personalizzate per soddisfare i requisiti standard di accessibilità.  Le linee guida di Microsoft per l'accessibilità vengono pubblicate sul Web.  Per informazioni dettagliate, vedere il [sito Web relativo all'accessibilità](http://go.microsoft.com/fwlink/?LinkID=37113) \(la pagina potrebbe essere in inglese\).  
  
 Nella maggior parte dei casi i progetti di Office in Visual Studio soddisfano i requisiti standard di accessibilità oppure espongono le proprietà da impostare per soddisfare tali requisiti nell'ambito della soluzione.  Alcune funzionalità tuttavia hanno un'accessibilità limitata.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Accessibilità in fase di progettazione  
  
### Utilizzo dei tasti di scelta rapida nei progetti a livello di documento  
 Quando si apre un documento Microsoft Office Word o una cartella di lavoro Microsoft Office Excel in Visual Studio, i comandi dei tasti di scelta rapida vengono ricevuti da un'applicazione alla volta.  Per impostazione predefinita, Visual Studio riceve tutti i comandi dei tasti di scelta rapida, ma è possibile fare in modo che vengano ricevuti da Word o Excel quando il documento ha lo stato attivo selezionando **Schema della tastiera dinamico** nella pagina **Impostazioni della tastiera** della finestra di dialogo **Opzioni**.  Per ulteriori informazioni, vedere [Tastiera di Microsoft Office Word, impostazioni della tastiera di Microsoft Office, finestra di dialogo Opzioni](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) e [Tastiera di Microsoft Office Excel, impostazioni della tastiera di Microsoft Office, finestra di dialogo Opzioni](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).  
  
### Visualizzazione dei tasti di scelta rapida per la barra multifunzione nei progetti a livello di documento  
 Quando si apre un documento di Word o una cartella di lavoro di Excel in Visual Studio, non è possibile premere il tasto ALT per visualizzare i tasti di scelta rapida per le schede e i controlli della barra multifunzione.  Per visualizzare i tasti di scelta rapida quando il documento o la cartella di lavoro è aperto nella finestra di progettazione, attenersi ai passaggi indicati di seguito.  
  
##### Per visualizzare i tasti di scelta rapida per schede e i controlli della barra multifunzione nella finestra di progettazione  
  
1.  In Visual Studio scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Espandere il nodo **Strumenti di Office** e selezionare **Tastiera di Microsoft Office Excel** o **Tastiera di Microsoft Office Word**, in base alle proprie esigenze.  
  
3.  Selezionare **Schema della tastiera dinamico**.  
  
     Viene visualizzato un messaggio indicante che per rendere effettiva la modifica è necessario riavviare Visual Studio.  
  
4.  Fare clic su **OK**.  
  
5.  Riavviare Visual Studio e riaprire il progetto.  
  
6.  Aprire la finestra di progettazione del documento o della cartella di lavoro per il progetto.  
  
7.  Premere F6 per visualizzare i tasti di scelta rapida per la barra multifunzione.  
  
## Accessibilità in fase di esecuzione  
  
### Controlli Windows Form nei documenti di Office  
 I controlli Windows Form espongono proprietà di accessibilità per fornire informazioni sul controllo agli strumenti di accessibilità, quali le utilità per la lettura dello schermo.  È possibile sfruttare queste proprietà di accessibilità quando i controlli sono inclusi in un documento di Office in una personalizzazione a livello di documento.  Per ulteriori informazioni, vedere [Aggiunta di informazioni per l'Accesso facilitato ai controlli in un Windows Form](http://msdn.microsoft.com/library/887dee6f-5059-4d57-957d-7c6fcd4acb10).  
  
 Esistono tuttavia alcuni limiti di accessibilità in fase di esecuzione quando i controlli Windows Form sono contenuti in una cartella di lavoro di Excel o un documento di Word.  
  
-   Non è possibile passare da un controllo a un altro utilizzando il tasto di tabulazione.  
  
-   I controlli inclusi in un documento sono disabilitati quando si modifica l'impostazione dello zoom del documento in un valore diverso da 100%.  
  
 Per informazioni sulle limitazioni dei controlli Windows Form inclusi nei documenti, vedere [Limitazioni dei controlli Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
### Riquadri delle azioni e riquadri attività personalizzati  
 Quando un riquadro azioni o un riquadro attività personalizzato ha lo stato attivo, è possibile accedere ai controlli nello stesso modo in cui si accede ai controlli di un'applicazione Windows Form.  Per spostare il cursore tra il riquadro azioni e il documento, è possibile premere **F6**.  
  
 Per ulteriori informazioni sui riquadri azione e sui riquadri attività personalizzati, vedere [Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md) e [Riquadri attività personalizzati](../vsto/custom-task-panes.md).  
  
### Modalità di visualizzazione  
 In Visual Studio sono incluse le seguenti limitazioni correlate alle modalità di visualizzazione:  
  
-   I controlli inclusi in un documento di Word o in un foglio di lavoro di Excel vengono disabilitati quando si modifica l'impostazione dello zoom del documento in un valore diverso da 100%.  
  
-   Nella finestra di dialogo **Nuovo progetto** i controlli non vengono visualizzati correttamente se un utente modifica le opzioni di accessibilità del computer in **Usa Contrasto elevato**.  
  
 Per ovviare a queste limitazioni, è possibile utilizzare Lente di ingrandimento,  un'utilità di visualizzazione disponibile in Windows che crea una finestra distinta nella quale viene visualizzata una porzione ingrandita dello schermo.  
  
## Vedere anche  
 [Sviluppo di soluzioni Office](../vsto/developing-office-solutions.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Accessibilità per utenti con particolari esigenze](../ide/reference/accessibility-for-people-with-disabilities.md)   
 [Funzionalità di accessibilità di Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)  
  
  