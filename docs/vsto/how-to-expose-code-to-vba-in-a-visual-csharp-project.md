---
title: "Procedura: esporre il codice a VBA in un progetto Visual C# | Microsoft Docs"
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
  - "VBA [sviluppo per Office in Visual Studio], esposizione di codice nelle personalizzazioni a livello di documento"
  - "Visual C# [sviluppo per Office in Visual Studio], esposizione di codice a VBA"
ms.assetid: 56d5894b-4823-42f4-8c7e-d8739b859c52
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Procedura: esporre il codice a VBA in un progetto Visual C# #
  È possibile esporre il codice di un progetto Visual C\# al codice di Visual Basic, Applications Edition \(VBA\) se si desidera che i due tipi di codice interagiscano l'uno con l'altro.  
  
 Il processo di Visual C\# è diverso dal processo di Visual Basic.  Per ulteriori informazioni, vedere [Procedura: esporre il codice a VBA in un progetto Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Esposizione del codice in un progetto Visual C\#  
 Per consentire al codice VBA di chiamare il codice di un progetto Visual C\#, modificare il codice in modo da renderlo visibile a COM e quindi impostare la proprietà **ReferenceAssemblyFromVbaProject** su **True** nella finestra di progettazione.  
  
 Per una procedura dettagliata che dimostra come chiamare un metodo in un progetto Visual C\# da VBA, vedere [Procedura dettagliata: chiamata di codice da VBA in un progetto Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
#### Per esporre il codice di un progetto Visual C\# a VBA  
  
1.  Aprire o creare un progetto a livello di documento basato su un documento di Word, una cartella di lavoro di Excel o un modello di Excel che supporta macro e che già contiene codice VBA.  
  
     Per ulteriori informazioni sui formati di file del documento che supportano macro, vedere [Combinazione di VBA con le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Questa funzionalità non può essere utilizzata nei progetti Modello di Word,  
  
2.  Assicurarsi che il codice VBA del documento possa essere eseguito senza richiedere all'utente di attivare le macro.  È possibile considerare attendibile l'esecuzione del codice VBA aggiungendo il percorso del progetto di Office all'elenco di percorsi attendibili nelle impostazioni del Centro protezione per Word o Excel.  
  
3.  Aggiungere il membro che si desidera esporre a VBA a una classe pubblica nel progetto e dichiarare il nuovo membro come **public**.  
  
4.  Applicare gli attributi <xref:System.Runtime.InteropServices.ComVisibleAttribute> e <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> alla classe che si sta esponendo a VBA.  Questi attributi rendono la classe visibile a COM, senza tuttavia generare un'interfaccia di classe.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  Eseguire l'override del metodo **GetAutomationObject** di una classe di elemento host del progetto per restituire un'istanza della classe che si sta esponendo a VBA:  
  
    -   Se si sta espondendo una classe di elemento host a VBA, eseguire l'override del metodo **GetAutomationObject** che appartiene a questa classe e restituire un'istanza della classe.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   Se si sta esponendo a VBA una classe di un elemento non host, eseguire l'override del metodo **GetAutomationObject** di una classe di ogni elemento host del progetto e restituire un'istanza della classe di un elemento non host.  L'esempio di codice seguente presuppone che si stia esponendo a VBA una classe denominata `DocumentUtilities`.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     Per ulteriori informazioni sugli elementi host, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md).  
  
6.  Estrarre un'interfaccia dalla classe che si sta esponendo a VBA.  Nella finestra di dialogo **Estrai interfaccia**, selezionare i membri pubblici da includere nella dichiarazione dell'interfaccia.  Per ulteriori informazioni, vedere [Extract Interface Refactoring &#40;C&#35;&#41;](../csharp-ide/extract-interface-refactoring-csharp.md).  
  
7.  Aggiungere la parola chiave **public** alla dichiarazione dell'interfaccia.  
  
8.  Rendere l'interfaccia visibile a COM aggiungendo l'attributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> all'interfaccia.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. Aprire il documento \(per Word\) o il foglio di lavoro \(per Excel\) nella finestra di progettazione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. Nella finestra **Proprietà** selezionare la proprietà **ReferenceAssemblyFromVbaProject** e modificarne il valore impostandola su **True**.  
  
    > [!NOTE]  
    >  Se la cartella di lavoro o il documento non contiene già codice VBA o se il codice VBA nel documento non è considerato attendibile per l'esecuzione, si riceverà un messaggio di errore quando si imposta la proprietà **ReferenceAssemblyFromVbaProject** su **True**.  Ciò avviene perché Visual Studio non può modificare il progetto VBA nel documento in questa situazione.  
  
11. Fare clic su **OK** nel messaggio visualizzato.  Questo messaggio ricorda che se si aggiunge codice VBA alla cartella di lavoro o al documento quando si sta eseguendo il progetto da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], il codice VBA andrà perso la prossima volta che si compila il progetto.  Ciò avviene perché il documento nella cartella dell'output di compilazione viene sovrascritta ogni volta che si compila il progetto.  
  
     A questo punto, in Visual Studio il progetto viene configurato in modo da consentire le chiamate nell'assembly dal progetto VBA.  In Visual Studio viene inoltre aggiunto al progetto VBA un metodo denominato `GetManagedClass`.  È possibile chiamare questo metodo da qualsiasi punto del progetto VBA per accedere alla classe esposta a VBA.  
  
12. Compilare il progetto.  
  
## Vedere anche  
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combinazione di VBA con le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Procedura dettagliata: chiamata di codice da VBA in un progetto Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Procedura: esporre il codice a VBA in un progetto Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  