---
title: "Procedura: esporre il codice a VBA in un progetto Visual Basic"
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
  - "personalizzazioni a livello di documento [sviluppo per Office in Visual Studio], esposizione di codice"
  - "esposizione di codice a VBA"
  - "elementi host [sviluppo per Office in Visual Studio], esposizione di codice a VBA"
  - "VBA [sviluppo per Office in Visual Studio], esposizione di codice nelle personalizzazioni a livello di documento"
  - "Visual Basic [sviluppo per Office in Visual Studio], esposizione di codice a VBA"
ms.assetid: dc74f3ea-3f78-47f8-8a82-a67896144dd9
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Procedura: esporre il codice a VBA in un progetto Visual Basic
  È possibile esporre codice in un progetto [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] al codice di Visual Basic, Applications Edition \(VBA\) se si desidera che i due tipi di codice interagiscano l'uno con l'altro.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Il processo di Visual Basic è diverso dal processo di Visual C\#.  Per ulteriori informazioni, vedere [Procedura: esporre il codice a VBA in un progetto Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
 Il processo è diverso per il codice in una classe dell'elemento host rispetto al codice nelle altre classi:  
  
-   [Esposizione di codice in una classe dell'elemento host](#HostItemCode)  
  
-   [Esposizione di codice non incluso in una classe dell'elemento host](#NonHostItem)  
  
 ![Collegamento a video](~/docs/data-tools/media/playvideo.gif "Collegamento a video") Per una dimostrazione video correlata, vedere l'articolo relativo [alla chiamata di codice VSTO da VBA](http://go.microsoft.com/fwlink/?LinkId=136757) \(la pagina potrebbe essere in inglese\).  
  
##  <a name="HostItemCode"></a> Esposizione di codice in una classe dell'elemento host  
 Per consentire al codice VBA di chiamare il codice di Visual Basic in una classe dell'elemento host, impostare la proprietà **EnableVbaCallers** dell'elemento host su **True**.  
  
 Per una procedura dettagliata che dimostra come esporre un metodo di una classe dell'elemento host e quindi chiamarlo da VBA, vedere [Procedura dettagliata: Chiamata di codice da VBA in un progetto Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).  Per ulteriori informazioni sugli elementi host, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md).  
  
#### Per esporre il codice in un elemento host a VBA  
  
1.  Aprire o creare un progetto [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] a livello di documento basato su un documento di Word, una cartella di lavoro di Excel o un modello di Excel che supporta macro e che già contiene codice VBA.  
  
     Per ulteriori informazioni sui formati di file del documento che supportano macro, vedere [Combinazione di VBA con le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Questa funzionalità non può essere utilizzata nei progetti Modello di Word,  
  
2.  Assicurarsi che il codice VBA del documento possa essere eseguito senza richiedere all'utente di attivare le macro.  È possibile considerare attendibile l'esecuzione del codice VBA aggiungendo il percorso del progetto di Office all'elenco di percorsi attendibili nelle impostazioni del Centro protezione per Word o Excel.  
  
3.  Aggiungere la proprietà, il metodo o l'evento che si desidera esporre a VBA a una delle classi dell'elemento host nel progetto e dichiarare il nuovo membro come **Public**.  Il nome della classe dipende dall'applicazione:  
  
    -   In un progetto Word, la classe dell'elemento host è denominata `ThisDocument` per impostazione predefinita.  
  
    -   In un progetto Excel, le classi dell'elemento host sono denominate `ThisWorkbook`, `Sheet1`, `Sheet2` e `Sheet3` per impostazione predefinita.  
  
4.  Impostare la proprietà **EnableVbaCallers** per l'elemento host su **True**.  Questa proprietà è disponibile nella finestra **Proprietà** quando l'elemento host è aperto nella finestra di progettazione.  
  
     Dopo avere impostato questa proprietà, Visual Studio imposta automaticamente la proprietà **ReferenceAssemblyFromVbaProject** su **True**.  
  
    > [!NOTE]  
    >  Se la cartella di lavoro o il documento non contiene già codice VBA, o se il codice VBA nel documento non è considerato attendibile per l'esecuzione, si riceverà un messaggio di errore quando si imposta la proprietà **EnableVbaCallers** su **True**.  Ciò avviene perché Visual Studio non può modificare il progetto VBA nel documento in questa situazione.  
  
5.  Fare clic su **OK** nel messaggio visualizzato.  Questo messaggio ricorda che se si aggiunge codice VBA alla cartella di lavoro o al documento mentre si sta eseguendo il progetto da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], il codice VBA andrà perso la prossima volta che si compila il progetto.  Ciò avviene perché il documento nella cartella dell'output di compilazione viene sovrascritta ogni volta che si compila il progetto.  
  
     A questo punto, in Visual Studio il progetto viene configurato in modo da consentire le chiamate nell'assembly dal progetto VBA.  Visual Studio aggiunge inoltre una proprietà denominata `CallVSTOAssembly` al modulo `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2` o `Sheet3` nel progetto VBA.  È possibile utilizzare questa proprietà per accedere a membri pubblici della classe che si espone a VBA.  
  
6.  Compilare il progetto.  
  
##  <a name="NonHostItem"></a> Esposizione di codice non incluso in una classe dell'elemento host  
 Per consentire al codice VBA di chiamare il codice di Visual Basic in una classe non inclusa in un elemento host, modificare il codice in modo che sia visibile a VBA.  
  
#### Per esporre codice non incluso in una classe dell'elemento host a VBA  
  
1.  Aprire o creare un progetto [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] a livello di documento basato su un documento di Word, una cartella di lavoro di Excel o un modello di Excel che supporta macro e che già contiene codice VBA.  
  
     Per ulteriori informazioni sui formati di file del documento che supportano macro, vedere [Combinazione di VBA con le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Questa funzionalità non può essere utilizzata nei progetti Modello di Word,  
  
2.  Assicurarsi che il codice VBA del documento possa essere eseguito senza richiedere all'utente di attivare le macro.  È possibile considerare attendibile l'esecuzione del codice VBA aggiungendo il percorso del progetto di Office all'elenco di percorsi attendibili nelle impostazioni del Centro protezione per Word o Excel.  
  
3.  Aggiungere il membro che si desidera esporre a VBA a una classe pubblica nel progetto e dichiarare il nuovo membro come **public**.  
  
4.  Applicare gli attributi <xref:System.Runtime.InteropServices.ComVisibleAttribute> e <xref:Microsoft.VisualBasic.ComClassAttribute> seguenti alla classe che si sta esponendo a VBA.  Questi attributi rendono visibile la classe a VBA.  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  Eseguire l'override del metodo **GetAutomationObject** di una classe dell'elemento host nel progetto per restituire un'istanza della classe che si sta esponendo a VBA.  L'esempio di codice seguente presuppone che si stia esponendo a VBA una classe denominata `DocumentUtilities`.  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  Aprire il documento \(per Word\) o la finestra di progettazione del foglio di lavoro \(per Excel\) in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
7.  Nella finestra **Proprietà** selezionare la proprietà **ReferenceAssemblyFromVbaProject** e modificarne il valore impostandola su **True**.  
  
    > [!NOTE]  
    >  Se la cartella di lavoro o il documento non contiene già codice VBA, o se il codice VBA nel documento non è considerato attendibile per l'esecuzione, si riceverà un messaggio di errore quando si imposta la proprietà **ReferenceAssemblyFromVbaProject** su **True**.  Ciò avviene perché Visual Studio non può modificare il progetto VBA nel documento in questa situazione.  
  
8.  Fare clic su **OK** nel messaggio visualizzato.  Questo messaggio ricorda che se si aggiunge codice VBA alla cartella di lavoro o al documento mentre si sta eseguendo il progetto da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], il codice VBA andrà perso la prossima volta che si compila il progetto.  Ciò avviene perché il documento nella cartella dell'output di compilazione viene sovrascritta ogni volta che si compila il progetto.  
  
     A questo punto, in Visual Studio il progetto viene configurato in modo da consentire le chiamate nell'assembly dal progetto VBA.  In Visual Studio viene inoltre aggiunto al progetto VBA un metodo denominato `GetManagedClass`.  È possibile chiamare questo metodo da qualsiasi punto del progetto VBA per accedere alla classe esposta a VBA.  
  
9. Compilare il progetto.  
  
## Vedere anche  
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combinazione di VBA con le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Procedura dettagliata: Chiamata di codice da VBA in un progetto Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Procedura: esporre il codice a VBA in un progetto Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  