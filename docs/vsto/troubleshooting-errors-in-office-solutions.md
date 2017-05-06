---
title: "Risoluzione degli errori nelle soluzioni Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Project.DesignerDisabled"
  - "VST.Designer.CannotActivate"
  - "VST.Project.ExcelBusy"
  - "VST.SelectDocWizard.AlreadyCustomized"
  - "VST.SelectDocWizard.DocPath"
  - "VST.Project.CannotOpen"
  - "VST.Designer.ErrorsOccurred"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "risoluzione dei problemi [sviluppo per Office in Visual Studio]"
ms.assetid: 8bbf5433-1992-4ecf-ae1b-19117b8ebe43
caps.latest.revision: 69
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 68
---
# Risoluzione degli errori nelle soluzioni Office
  Questi problemi possono verificarsi quando si eseguono le attività seguenti durante lo sviluppo di soluzioni Office in Visual Studio:  
  
-   [Creazione, aggiornamento e apertura di progetti](#creating)  
  
-   [Uso delle finestre di progettazione](#designers)  
  
-   [Scrittura di codice](#code)  
  
-   [Compilazione di progetti](#building)  
  
-   [Debug di progetti](#debugging)  
  
##  <a name="creating"></a> Creazione, aggiornamento e apertura di progetti  
 Gli errori seguenti possono verificarsi quando si creano o si aprono progetti di Office.  
  
### Impossibile creare il progetto  
 Si è verificato un errore durante un tentativo di creare o aprire un progetto di Office, ma Visual Studio non dispone di informazioni sufficienti per determinare la causa.  Provare a chiudere il progetto, uscire da Visual Studio e avviarlo di nuovo.  
  
 Se si sta cercando di creare un progetto a livello di documento, è possibile che un altro documento con lo stesso nome di quello nel nuovo progetto sia già aperto in Excel o Word.  Assicurarsi che tutte le altre istanze di Excel o Word siano chiuse.  
  
### Le proprietà dei controlli vengono perse quando si crea un nuovo progetto basato su un documento da un progetto esistente  
 Se si crea un nuovo progetto di Office basato su un documento da un progetto esistente, le proprietà dei controlli presenti nel documento non vengono copiate nel nuovo progetto.  È necessario reimpostare manualmente le proprietà per tutti i controlli preesistenti.  In alternativa, è possibile mantenere le proprietà dei controlli creando una copia del progetto esistente anziché creare un nuovo progetto oppure caricando il progetto esistente nella nuova soluzione \(nella finestra di progettazione\) e copiando e incollando i controlli dal documento esistente al nuovo documento.  
  
### Errori durante la creazione di un progetto cartella di lavoro di Excel basato su una cartella di lavoro esistente  
 Se si crea un nuovo progetto cartella di lavoro di Excel basato su una cartella di lavoro esistente, si potrebbe verificare una combinazione degli errori seguenti.  
  
 Da Excel: "Avviso per la privacy: questo documento contiene macro, controlli ActiveX, informazioni del pacchetto di espansione XML o componenti Web.  Potrebbero essere presenti informazioni personali che non possono essere rimosse tramite Controllo documento."  
  
 Da Visual Studio: "Impossibile caricare correttamente la finestra di progettazione."  
  
 Questi errori possono verificarsi se si cerca di creare un progetto basato su una cartella di lavoro in cui le informazioni personali sono state rimosse tramite Controllo documento.  Per evitare questo errore, eseguire la procedura seguente prima di creare il progetto.  
  
1.  Aprire la cartella di lavoro in Excel.  
  
2.  In Excel aprire il Centro protezione.  
  
3.  Nella scheda **Opzioni privacy** deselezionare la casella di controllo **Rimuovi le informazioni personali dalle proprietà del file al momento del salvataggio**.  
  
4.  Salvare la cartella di lavoro e chiudere Excel.  
  
### Impossibile aprire un progetto dopo la migrazione  
 Dopo la migrazione di una soluzione Office a Microsoft Office 2010, non è possibile aprire il progetto in un computer di sviluppo in cui è installato solo Microsoft Office System 2007.  Potrebbero venire visualizzati gli errori seguenti.  
  
 "Uno o più progetti della soluzione non sono stati caricati correttamente.  Per dettagli, vedere la finestra di output".  
  
 "Impossibile creare il progetto perché l'applicazione associata al tipo di progetto non è installata nel computer.  È necessario installare l'applicazione di Microsoft Office associata al tipo di progetto corrente."  
  
 Per risolvere il problema, modificare il file con estensione vbproj o csproj.  Per un progetto di Word, sostituire HostPackage\="{763FDC83\-64E5\-4651\-AC9B\-28C4FEB985A1}" con HostPackage\="{6CE98B71\-D55A\-4305\-87A8\-0D6E368D9600}".  Per un progetto di Excel, sostituire HostPackage\="{B284B16A\-C42C\-4438\-BDCD\-B72F4AC43CFB}" con HostPackage\="{825100CF\-0BA7\-47EA\-A084\-DCF3308DAF74}".  Per un progetto di Outlook, sostituire HostPackage\="{D2B20FF5\-A6E5\-47E1\-90E8\-463C6860CB05}" con HostPackage\="{20A848B8\-E01F\-4801\-962E\-25DB0FF57389}".  
  
 In alternativa, assicurarsi che i progetti migrati vengano aperti solo nei computer di sviluppo in cui è già installato Microsoft Office 2010.  
  
### Errori nei progetti a livello di documento di Office 2003 aggiornati che contengono controlli Windows Form  
 Se si aggiorna un progetto a livello di documento di Microsoft Office 2003 e il documento contiene controlli Windows Form, il progetto aggiornato potrebbe presentare errori di compilazione o di runtime.  Per evitare questo problema, installare Visual Studio 2005 Tools per Office Second Edition Runtime nel computer di sviluppo prima di aggiornare il progetto.  Questa versione del runtime è disponibile come pacchetto ridistribuibile dall'Area download Microsoft in [Microsoft Visual Studio 2005 Tools per Office Second Edition Runtime \(VSTO 2005 SE\) \(x86\)](http://go.microsoft.com/fwlink/?linkid=49612).  
  
 Dopo aver completato l'aggiornamento del progetto, è possibile disinstallare Visual Studio 2005 Tools per Office Second Edition Runtime dal computer di sviluppo se non viene usato da altre soluzioni Office.  
  
##  <a name="designers"></a> Uso delle finestre di progettazione  
 Gli errori seguenti possono verificarsi quando si lavora con la finestra di progettazione di documenti, cartelle di lavoro o fogli di lavoro nei progetti a livello di documento.  
  
### Errore di caricamento della finestra di progettazione  
 Visual Studio non può aprire la finestra di progettazione nei casi seguenti:  
  
-   Excel o Word è già aperto ed è visualizzata una finestra di dialogo modale.  Per aprire la finestra di progettazione, verificare se in Excel o in Word è aperta una finestra di dialogo modale e chiudere eventuali finestre di dialogo modali aperte.  Se non ci sono finestre di dialogo modali aperte, potrebbe essere necessario eseguire altre azioni affinché Excel o Word risponda.  
  
-   Il progetto corrente è in fase di debug.  Per aprire la finestra di progettazione, interrompere o terminare il debug.  
  
-   Un componente aggiuntivo VSTO di Excel installato nel computer di sviluppo provoca la visualizzazione di una finestra di dialogo all'avvio di Excel.  Per creare un progetto a livello di documento di Excel, è prima necessario disabilitare il componente aggiuntivo VSTO.  
  
### I controlli vengono visualizzati come rettangoli neri nel documento o nel foglio di lavoro  
 Se si raggruppano i controlli in un documento o in un foglio di lavoro, Visual Studio non li riconosce più.  Non è possibile accedere ai controlli raggruppati nella finestra **Proprietà** e i controlli vengono visualizzati come rettangoli neri nel documento o nel foglio di lavoro.  Per ripristinare le relative funzionalità, è necessario separare i controlli.  
  
### I controlli in un modello di Word non sono visibili in Visual Studio  
 Se si apre un modello di Word nella finestra di progettazione di Visual Studio, i controlli del modello che non sono in linea con il testo potrebbero non essere visibili.  Ciò accade perché Visual Studio apre i modelli di Word in visualizzazione **Normale**.  Per visualizzare i controlli, scegliere **Visualizzazione di Microsoft Office Word** dal menu **Visualizza** e quindi fare clic su **Layout di stampa**.  
  
### Il comando Inserisci ClipArt non funziona nella finestra di progettazione di Visual Studio  
 Quando Excel o Word è aperto nella finestra di progettazione di Visual Studio, se si fa clic sul pulsante **ClipArt** nella scheda **Illustrazioni** della barra multifunzione, il riquadro attività **ClipArt** non viene aperto.  Per aggiungere ClipArt, è necessario aprire la copia della cartella di lavoro o del documento che si trova nella cartella di progetto principale \(non la copia nella cartella \\bin\) all'esterno di Visual Studio, aggiungere la ClipArt e quindi salvare la cartella di lavoro o il documento.  
  
##  <a name="code"></a> Scrittura di codice  
 Gli errori seguenti possono verificarsi quando si scrive codice nei progetti di Office.  
  
### Non è possibile accedere ad alcuni eventi degli oggetti di Office quando si usa C\#  
 In alcuni casi, potrebbe venire visualizzato un errore del compilatore simile al seguente quando si tenta di accedere a un evento specifico di un'istanza di un tipo di assembly di interoperabilità primario di Office in un progetto Visual C\#.  
  
 "Ambiguità tra 'Microsoft.Office.Interop.Excel.\_Application.NewWorkbook' e 'Microsoft.Office.Interop.Excel.AppEvents\_Event.NewWorkbook'"  
  
 Questo errore indica che si sta tentando di accedere a un evento che ha lo stesso nome di un'altra proprietà o un altro metodo dell'oggetto.  Per accedere all'evento, è necessario eseguire il cast dell'oggetto alla relativa *interfaccia eventi*.  
  
 I tipi di assembly di interoperabilità primari di Office che dispongono di eventi implementano due interfacce: un'interfaccia principale con tutte le proprietà e i metodi e un'interfaccia eventi che contiene gli eventi esposti dall'oggetto.  Queste interfacce eventi usano la convenzione di denominazione *nomeoggetto*Events*n*\_Event, ad esempio <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> e <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event>.  Se è possibile accedere a un evento che si prevede di trovare in un oggetto, eseguire il cast dell'oggetto alla relativa interfaccia eventi.  
  
 Ad esempio, gli oggetti <xref:Microsoft.Office.Interop.Excel.Application> dispongono di un evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> e una proprietà <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A>.  Per gestire l'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook>, eseguire il cast di <xref:Microsoft.Office.Interop.Excel.Application> all'interfaccia <xref:Microsoft.Office.Interop.Excel.AppEvents_Event>.  L'esempio di codice seguente illustra come eseguire questa operazione in un progetto a livello di documento per Excel.  
  
 [!code-csharp[Trin_VstcoreTroubleshootingExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingExcel/CS/ThisWorkbook.cs#1)]  
  
 Per altre informazioni sulle interfacce eventi negli assembly di interoperabilità primari di Office, vedere [Panoramica di classi e interfacce negli assembly di interoperabilità primari di Office](http://msdn.microsoft.com/it-it/da92dc3c-8209-44de-8095-a843659368d5).  
  
### Non è possibile fare riferimento alle classi di assembly di interoperabilità primari di Office nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] il codice che fa riferimento a una classe definita in un assembly di interoperabilità primario di Office non verrà compilato per impostazione predefinita.  Le classi negli assembly di interoperabilità primari usano la convenzione di denominazione *nomeoggetto*Class, ad esempio <xref:Microsoft.Office.Interop.Word.DocumentClass> e <xref:Microsoft.Office.Interop.Excel.WorkbookClass>.  Ad esempio, il codice seguente di un progetto di componente aggiuntivo VSTO di Word non verrà compilato.  
  
```vb  
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 Questo codice genera gli errori di compilazione seguenti:  
  
-   Visual Basic: "Il riferimento alla classe 'DocumentClass' non è consentito se il relativo assembly è collegato in modalità No\-PIA."  
  
-   Visual C\#: "Impossibile incorporare il tipo di interoperabilità 'Microsoft.Office.Interop.Word.DocumentClass'.  Utilizzare l'interfaccia applicabile."  
  
 Per risolvere l'errore, modificare il codice in modo che faccia riferimento all'interfaccia corrispondente.  Ad esempio, anziché fare riferimento a un oggetto <xref:Microsoft.Office.Interop.Word.DocumentClass>, fare riferimento a un'istanza dell'interfaccia <xref:Microsoft.Office.Interop.Word.Document>.  
  
```vb  
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 I progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] incorporano automaticamente per impostazione predefinita tutti i tipi di interoperabilità dagli assembly di interoperabilità primari di Office.  Questo errore di compilazione si verifica perché la funzionalità dei tipi di interoperabilità incorporati funziona solo con le interfacce e non con le classi.  Per altre informazioni sulle interfacce e sulle classi negli assembly di interoperabilità primari di Office, vedere [Panoramica di classi e interfacce negli assembly di interoperabilità primari di Office](http://go.microsoft.com/fwlink/?LinkId=189592).  Per altre informazioni sulla funzionalità dei tipi di interoperabilità incorporati nei progetti di Office, vedere [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md).  
  
### I riferimenti alle classi di Office non vengono riconosciuti  
 Alcuni nomi di classi, ad esempio Application, si trovano in più spazi dei nomi, come <xref:Microsoft.Office.Interop.Word> e <xref:System.Windows.Forms>.  Per questo motivo, l'istruzione **Imports**\/**using** nella parte superiore dei modelli di progetto include una costante qualificativa a sintassi abbreviata, ad esempio:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/CS/ThisDocument.cs#2)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/VB/ThisDocument.vb#2)]  
  
 Questo utilizzo dell'istruzione **Imports**\/**using** richiede la differenziazione dei riferimenti alle classi di Office con il qualificatore di Word o Excel, ad esempio:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/CS/ThisDocument.cs#3)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/VB/ThisDocument.vb#3)]  
  
 Se si usa una dichiarazione non qualificata, vengono generati errori, ad esempio:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/CS/ThisDocument.cs#4)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/VB/ThisDocument.vb#4)]  
  
 Anche se lo spazio dei nomi di Word o Excel è stato importato ed è stato effettuato l'accesso a tutte le classi al suo interno, è necessario usare un nome completo per tutti i tipi con Word o Excel per rimuovere l'ambiguità relativa allo spazio dei nomi.  
  
##  <a name="building"></a> Compilazione di progetti  
 Gli errori seguenti possono verificarsi quando si compilano progetti di Office.  
  
### Non è possibile compilare un progetto a livello di documento basato su un documento con autorizzazioni limitate  
 Visual Studio non può compilare progetti a livello di documento se il documento ha autorizzazioni limitate.  Se il progetto contiene un documento con autorizzazioni limitate, non verrà compilato e verrà visualizzato il messaggio seguente nella finestra **Elenco errori**.  
  
 "Impossibile aggiungere la personalizzazione."  
  
 Se si vuole includere un documento con autorizzazioni limitate, usare un documento senza restrizioni quando si sviluppa e si compila la soluzione.  Applicare quindi le autorizzazioni limitate al documento nel percorso di pubblicazione, dopo aver pubblicato la soluzione.  
  
### Si verificano errori del compilatore dopo l'eliminazione di un controllo NamedRange  
 Se si elimina un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> da un foglio di lavoro che non è il foglio di lavoro attivo nella finestra di progettazione, il codice generato automaticamente potrebbe non venire rimosso dal progetto e potrebbero verificarsi errori del compilatore.  Per assicurarsi che il codice venga rimosso, è consigliabile selezionare sempre il foglio di lavoro contenente il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> per renderlo attivo prima di eliminare il controllo.  Se il codice generato automaticamente non viene eliminato quando si elimina il controllo, è possibile fare in modo che venga eliminato dalla finestra di progettazione attivando il foglio di lavoro e apportando una modifica, in modo che il foglio di lavoro venga contrassegnato come modificato.  Quando si ricompila il progetto, il codice viene rimosso.  
  
##  <a name="debugging"></a> Debug di progetti  
 Gli errori seguenti possono verificarsi quando si esegue il debug di progetti di Office.  
  
### Viene visualizzata una richiesta di disinstallazione quando si pubblica e si installa una soluzione nel computer di sviluppo  
 Quando si esegue il debug di una soluzione Office, è possibile che venga visualizzato il messaggio di errore seguente.  
  
 "Impossibile installare la personalizzazione perché ne è installata un'altra versione che non può essere aggiornata da questo percorso."  
  
 Questo errore indica che la soluzione Office è stata pubblicata e installata in precedenza nel computer di sviluppo.  Per impedire la visualizzazione del messaggio, disinstallare la soluzione dall'elenco dei programmi installati nel computer prima di eseguire il debug della soluzione.  In alternativa, è possibile creare un altro account utente nel computer di sviluppo per testare l'installazione della soluzione pubblicata.  
  
### I progetti a livello di documento creati in percorsi di rete UNC non vengono eseguiti da Visual Studio  
 Se si crea un progetto a livello di documento per Excel o Word in un percorso di rete UNC, è necessario aggiungere il percorso del documento all'elenco di percorsi attendibili in Excel o Word.  In caso contrario, la personalizzazione non verrà caricata quando si tenta di eseguire il progetto o il relativo debug in Visual Studio.  Per altre informazioni sui percorsi attendibili, vedere [Concessione dell'attendibilità ai documenti](../vsto/granting-trust-to-documents.md).  
  
### I thread non vengono arrestati correttamente dopo il debug  
 I progetti di Office in Visual Studio seguono una convenzione di denominazione dei thread che consente al debugger di chiudere correttamente il programma.  Se si creano thread nella soluzione, è necessario denominare ogni thread con il prefisso VSTA\_ per garantire che questi thread vengano gestiti correttamente quando si arresta il debug.  Ad esempio, è possibile impostare la proprietà `Name` di un thread in attesa di un evento di rete su VSTA\_NetworkListener.  
  
### Non è possibile eseguire qualsiasi soluzione Office o il relativo debug nel computer di sviluppo  
 Se non è possibile eseguire o sviluppare un progetto di Office nel computer di sviluppo, potrebbe venire visualizzato il messaggio di errore seguente.  
  
 "Impossibile creare il dominio applicazione. Personalizzazione non caricata."  
  
 Visual Studio usa Fusion, il caricatore di assembly .NET Framework, per memorizzare nella cache gli assembly prima di caricare le soluzioni Office.  Assicurarsi che Visual Studio possa scrivere nella cache Fusion e riprovare.  Per altre informazioni, vedere [Creazione di copie replicate di assembly](http://msdn.microsoft.com/library/de8b8759-fca7-4260-896b-5a4973157672).  
  
### Errore durante l'arresto del debugger in un progetto a livello di documento dopo l'uso del comando Modifica e continuazione  
 Se si usa il comando Modifica e continuazione per apportare modifiche al codice in un progetto a livello di documento per Excel o Word mentre il progetto è in modalità interruzione, potrebbe venire visualizzata una finestra di dialogo con il messaggio di errore seguente se successivamente si arresta il debugger.  
  
 "L'interruzione del processo nello stato corrente può causare effetti indesiderati, incluse la perdita dei dati e l'instabilità del sistema."  
  
 Indipendentemente dal fatto che si faccia clic su **Sì** o su **No** nella finestra di dialogo, Visual Studio termina il processo di Excel o Word e il debugger viene arrestato.  Per interrompere il debug del progetto senza visualizzare questa finestra di dialogo, uscire da Excel o Word direttamente anziché arrestare il debugger in Visual Studio.  
  
## Vedere anche  
 [Risoluzione dei problemi relativi alle soluzioni Office](../vsto/troubleshooting-office-solutions.md)   
 [Risoluzione dei problemi relativi alla sicurezza delle soluzioni Office](../vsto/troubleshooting-office-solution-security.md)   
 [Risoluzione dei problemi relativi alla distribuzione di soluzioni Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  