---
title: "Deploying COM Components with ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "registration-free COM deployment"
  - "ClickOnce deployment, COM components"
  - "COM components, deploying"
  - "deploying applications [ClickOnce], COM components"
  - "components, deploying"
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Deploying COM Components with ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La distribuzione di componenti COM legacy ha sempre presentato delle difficoltà.  I componenti devono essere registrati a livello globale e possono quindi causare effetti non desiderati in eventuali applicazioni sovrapposte.  Questa situazione non costituisce in genere un problema nelle applicazioni .NET Framework, poiché in questo caso i componenti sono circoscritti a un'applicazione \(isolati\) oppure supportano l'affiancamento.  Visual Studio consente di distribuire componenti COM isolati sul sistema operativo Windows XP o versioni successive.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fornisce un meccanismo semplice e sicuro per la distribuzione di applicazioni .NET.  Se tuttavia le applicazioni utilizzano componenti COM legacy, sarà necessario eseguire alcune operazioni aggiuntive per distribuirle.  In questo argomento viene descritto come distribuire componenti COM isolati e fare riferimento a componenti nativi, ad esempio da Visual Basic 6.0 o Visual C\+\+.  
  
 Per ulteriori informazioni sulla distribuzione di componenti COM isolati, vedere "Simplify App Deployment with [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] and Registration\-Free COM" all'indirizzo [http:\/\/msdn.microsoft.com\/msdnmag\/issues\/05\/04\/RegFreeCOM\/default.aspx](http://msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx) \(informazioni in lingua inglese\).  
  
## COM senza registrazione  
 COM senza registrazione è una nuova tecnologia per la distribuzione e l'attivazione di componenti COM isolati.  Funziona con l'inserimento di tutte le informazioni di registrazione e della libreria dei tipi del componente generalmente installate nel Registro di sistema in un file XML denominato manifesto e memorizzato nella cartella dell'applicazione.  
  
 Per isolare un componente COM, il componente deve essere registrato nel computer dello sviluppatore, ma non occorre che lo sia nel computer dell'utente finale.  Per isolare un componente COM, è sufficiente impostare la proprietà **Isolated** del relativo riferimento su **True**.  Per impostazione predefinita, questa proprietà è impostata su **False**, per indicare che il riferimento verrà considerato come un riferimento COM registrato.  Se questa proprietà è impostata su **True**, verrà creato un manifesto per il componente in fase di compilazione  Inoltre, i file corrispondenti verranno copiati nella cartella dell'applicazione durante l'installazione.  
  
 Quando il generatore del manifesto incontra un riferimento COM isolato, enumera tutte le voci `CoClass` presenti nella libreria dei tipi del componente, facendo corrispondere ogni voce ai relativi dati di registrazione e generando definizioni del manifesto per tutte le classi COM presenti nel file della libreria dei tipi.  
  
## Distribuzione di componenti COM senza registrazione con ClickOnce  
 La tecnologia di distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è particolarmente adatta per distribuire componenti COM isolati, in quanto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e COM senza registrazione richiedono per la distribuzione che il componente disponga di un manifesto,  
  
 che è generalmente fornito dall'autore del componente stesso.  Se tuttavia il manifesto del componente COM non è disponibile, è possibile generarlo automaticamente tramite Visual Studio.  La generazione del manifesto viene eseguita durante il processo di pubblicazione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Per ulteriori informazioni, vedere [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md).  Questa funzionalità consente anche di sfruttare i componenti legacy creati in ambienti di sviluppo precedenti, ad esempio Visual Basic 6.0.  
  
 La distribuzione di componenti COM tramite [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] può essere eseguita in due modi:  
  
-   Utilizzando il programma di avvio automatico per distribuire i componenti COM. Questo metodo funziona su tutte le piattaforme supportate.  
  
-   Utilizzando l'isolamento dei componenti nativi, detto anche "metodo di distribuzione COM senza registrazione".  Questo metodo, tuttavia, funziona solo con il sistema operativo Windows XP o versione successiva.  
  
### Esempio di isolamento e distribuzione di un componente COM semplice  
 Per illustrare la distribuzione di un componente tramite COM senza registrazione, in questo esempio verrà creata un'applicazione per Windows con Visual Basic che farà riferimento a un componente COM nativo isolato creato con Visual Basic 6.0. L'applicazione verrà distribuita tramite [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 È necessario innanzitutto creare il componente COM nativo:  
  
##### Per creare un componente COM nativo  
  
1.  In Visual Basic 6.0 scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** fare clic sul nodo **Visual Basic** e selezionare un progetto **DLL ActiveX**.  Nella casella **Nome** digitare `VB6Hello`.  
  
    > [!NOTE]
    >  Solo i tipi di progetto DLL ActiveX e controllo ActiveX sono supportati dalla tecnologia COM senza registrazione. I tipi di progetto EXE ActiveX e documento ActiveX non sono supportati.  
  
3.  In **Esplora soluzioni** fare doppio clic su **Class1.vb** per aprire l'editor di testo.  
  
4.  In Class1.vb aggiungere il codice seguente dopo il codice generato per il metodo `New`:  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Compilare il componente.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
> [!NOTE]
>  La tecnologia COM senza registrazione supporta solo i tipi di progetto DLL e controllo COM.  Non è possibile utilizzare eseguibili con tale tecnologia.  
  
 È ora possibile creare un'applicazione per Windows e aggiungervi un riferimento al componente COM.  
  
##### Per creare un'applicazione per Windows utilizzando un componente COM  
  
1.  In Visual Basic scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** fare clic sul nodo **Visual Basic** e selezionare un progetto **Applicazione Windows**.  Nella casella **Nome** digitare `RegFreeComDemo`.  
  
3.  In **Esplora soluzioni** fare clic sul pulsante **Mostra tutti i file** per visualizzare i riferimenti del progetto.  
  
4.  Fare clic con il pulsante destro del mouse sul nodo **Riferimenti** e scegliere **Aggiungi riferimento** dal menu di scelta rapida.  
  
5.  Nella finestra di dialogo **Aggiungi riferimento** fare clic sulla scheda **Sfoglia**, passare a VB6Hello.dll, quindi selezionare il file.  
  
     Nell'elenco dei riferimenti verrà aggiunto un riferimento a **VB6Hello**.  
  
6.  Nella **Casella degli strumenti** selezionare un controllo **Button** e trascinarlo nel form **Form1**.  
  
7.  Nella finestra **Proprietà** impostare la proprietà **Text** del pulsante su Hello.  
  
8.  Fare doppio clic sul pulsante per aggiungere il codice del gestore e, nel file del codice, aggiungere codice in modo da ottenere il seguente gestore:  
  
    ```  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
        Dim VbObj As New VB6Hello.Class1  
        VbObj.SayHello()  
    End Sub  
    ```  
  
9. Eseguire l'applicazione.  Scegliere **Avvia debug** dal menu **Debug**.  
  
 A questo punto, è necessario isolare il controllo.  Ogni componente COM utilizzato dall'applicazione è rappresentato nel progetto come riferimento COM.  Questi riferimenti sono riportati al di sotto del nodo **Riferimenti** nella finestra **Esplora soluzioni**.  Si tenga presente che è possibile aggiungere riferimenti direttamente tramite il comando **Aggiungi riferimento** del menu **Progetto** oppure indirettamente trascinando un controllo ActiveX nel form.  
  
 I passaggi indicati di seguito illustrano come isolare il componente COM e pubblicare l'applicazione aggiornata contenente il controllo isolato:  
  
##### Per isolare un componente COM  
  
1.  In **Esplora soluzioni** passare al nodo **Riferimenti** e selezionare il riferimento **VB6Hello**.  
  
2.  Nella finestra **Proprietà** modificare il valore della proprietà **Isolated** da **False** a **True**.  
  
3.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
 A questo punto, quando si premerà F5, l'applicazione funzionerà come previsto, ma in modalità COM senza registrazione.  Per verificare questa condizione, tentare di annullare la registrazione del componente VB6Hello.dll e di eseguire RegFreeComDemo1.exe esternamente all'IDE di Visual Studio.  In questo caso, facendo clic sul pulsante, è possibile verificare che l'applicazione funziona.  Se si rinomina temporaneamente il manifesto dell'applicazione, questa non funzionerà.  
  
> [!NOTE]
>  È possibile simulare l'assenza di un componente COM annullandone temporaneamente la registrazione.  Aprire una finestra del prompt dei comandi, digitare `cd /d %windir%\system32` per passare alla cartella di sistema, quindi annullare la registrazione del componente digitando `regsvr32 /u VB6Hello.dll`.  Sarà possibile registrarlo nuovamente digitando `regsvr32 VB6Hello.dll`.  
  
 Il passaggio finale consiste nella pubblicazione dell'applicazione tramite [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]:  
  
##### Per pubblicare un aggiornamento dell'applicazione con un componente COM isolato  
  
1.  Scegliere **Pubblica RegFreeComDemo** dal menu **Compila**.  
  
     Verrà visualizzata la Pubblicazione guidata.  
  
2.  Specificare un percorso nel disco del computer locale a cui è possibile accedere ed esaminare i file pubblicati.  
  
3.  Scegliere **Fine** per pubblicare l'applicazione.  
  
 Se si esaminano i file pubblicati, è possibile notare che è incluso il file sysmon.ocx.  Il controllo è completamente isolato dall'applicazione, pertanto, se nel computer dell'utente finale è presente un'altra applicazione che utilizza una versione diversa del controllo, il controllo non può interferire con tale applicazione.  
  
## Riferimenti ad assembly nativi  
 Visual Studio supporta i riferimenti agli assembly nativi di Visual Basic 6.0 o C\+\+. Tali riferimenti sono definiti riferimenti nativi.  Per stabilire se un riferimento è nativo, controllare se la proprietà **File Type** del riferimento è impostata su **Native** o su **ActiveX**.  
  
 Per aggiungere un riferimento nativo, utilizzare il comando **Aggiungi riferimento**, quindi passare al manifesto.  Per alcuni componenti il manifesto è incluso all'interno della DLL.  In questo caso, è sufficiente selezionare la DLL stessa affinché venga aggiunta come riferimento nativo se viene rilevato che il componente contiene un manifesto incorporato.  In Visual Studio tutti i file o gli assembly dipendenti elencati nel manifesto vengono inclusi automaticamente se si trovano nella stessa cartella del componente a cui si fa riferimento.  
  
 L'isolamento dei controlli COM semplifica la distribuzione dei componenti COM che non dispongono ancora di manifesti.  Tuttavia, se un componente viene fornito con un manifesto, è possibile fare riferimento direttamente a tale manifesto.  In effetti, se possibile, è sempre consigliabile utilizzare il manifesto fornito dall'autore del componente anziché utilizzare la proprietà **Isolated**.  
  
## Limiti della distribuzione di componenti COM senza registrazione  
 La tecnologia COM senza registrazione offre chiari vantaggi rispetto alle tecniche di distribuzione tradizionali.  Esistono tuttavia alcuni limiti e alcune particolarità a cui è opportuno prestare attenzione.  Il limite maggiore consiste nel fatto che questa funzionalità è utilizzabile solo con Windows XP o versione successiva.  L'implementazione di COM senza registrazione ha richiesto una serie di modifiche relative alla modalità di caricamento dei componenti nel sistema operativo di base  e quindi non è disponibile un livello di supporto inferiore.  
  
 Non tutti i componenti sono adatti alla distribuzione COM senza registrazione.  Un componente non è adatto se una delle seguenti affermazioni è vera:  
  
-   Il componente è un server out\-of\-process.  I server EXE non sono supportati. È possibile utilizzare solo DLL.  
  
-   Il componente fa parte del sistema operativo o è un componente di sistema, come XML, Internet Explorer o Microsoft Data Access Components \(MDAC\).  È consigliabile attenersi ai criteri di ridistribuzione stabiliti dall'autore del componente. Per informazioni, contattare il produttore.  
  
-   Il componente fa parte di un'applicazione, quale Microsoft Office.  È sconsigliabile tentare, ad esempio, di isolare il modello a oggetti di Microsoft Excel.  Questo modello è parte di Office e può essere utilizzato esclusivamente in un computer in cui è installata una versione completa di Office.  
  
-   Il componente deve essere utilizzato come componente aggiuntivo o snap\-in, ad esempio un componente aggiuntivo di Office o un controllo di un browser.  Tali componenti richiedono in genere un tipo di schema di registrazione definito dall'ambiente host che esula dall'ambito del manifesto.  
  
-   Il componente gestisce una periferica fisica o virtuale per il sistema, ad esempio un driver di periferica per uno spooler di stampa.  
  
-   Il componente è un componente ridistribuibile di accesso ai dati.  Le applicazioni basate su dati richiedono in genere l'installazione di un componente ridistribuibile di accesso ai dati per essere eseguite.  Non tentare di isolare componenti quali i controlli dati Microsoft ADO o i componenti Microsoft OLE DB e MDAC \(Microsoft Data Access Components\).  Se l'applicazione utilizza MDAC o SQL Server Express, è invece necessario impostarli. Per ulteriori informazioni, vedere [How to: Install Prerequisites with a ClickOnce Application](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md).  
  
 In alcuni casi, lo sviluppatore del componente può riprogettarlo per la tecnologia COM senza registrazione.  Se questo non è possibile, è comunque possibile compilare e pubblicare applicazioni dipendenti tramite lo schema di registrazione standard utilizzando il programma di avvio automatico.  Per ulteriori informazioni, vedere [Creazione di programmi di avvio automatico](../deployment/creating-bootstrapper-packages.md).  
  
 Un componente COM può essere isolato una sola volta per applicazione.  Non è possibile, ad esempio, isolare lo stesso componente COM per due progetti **Libreria di classi** diversi che fanno parte della stessa applicazione.  In tal modo, si provocherebbe un avviso di compilazione e l'applicazione non verrebbe caricata in fase di esecuzione.  Per evitare questo problema, è consigliabile incapsulare i componenti COM in un'unica libreria di classi.  
  
 Esistono casi in cui la registrazione COM è richiesta nel computer dello sviluppatore, anche se non è necessaria per la distribuzione dell'applicazione.  La proprietà `Isolated` richiede che il componente COM sia registrato nel computer dello sviluppatore per generare automaticamente il manifesto durante il processo di compilazione.  Non sono disponibili funzionalità di acquisizione della registrazione che avviano la registrazione automatica durante la fase di compilazione.  Inoltre, tutte le classi non definite in modo esplicito nella libreria dei tipi non verranno riflesse nel manifesto.  Quando si utilizza un componente COM con un manifesto preesistente, ad esempio un riferimento nativo, potrebbe non essere necessario registrare il componente in fase di sviluppo.  La registrazione è tuttavia obbligatoria se il componente è un controllo ActiveX e si desidera includerlo nella **Casella degli strumenti** e in Progettazione Windows Form.  
  
## Vedere anche  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)