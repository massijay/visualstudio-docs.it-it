---
title: "Miglioramento delle prestazioni di un componente aggiuntivo VSTO"
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
ms.assetid: 03ef25c2-6308-4737-a655-74bbbb472dc2
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Miglioramento delle prestazioni di un componente aggiuntivo VSTO
  È possibile offrire agli utenti un'esperienza migliore ottimizzando i componenti aggiuntivi VSTO creati per le applicazioni di Office per poterli avviare rapidamente, interromperli o usarli per aprire gli elementi ed eseguire altre attività. Se il componente aggiuntivo VSTO è per Outlook, è anche possibile ridurre la probabilità che il componente aggiuntivo VSTO venga disabilitato a causa delle prestazioni ridotte. È possibile incrementare le prestazioni del componente aggiuntivo VSTO implementando le strategie seguenti:  
  
-   [Caricare componenti aggiuntivi VSTO su richiesta](#Load).  
  
-   [Pubblicare soluzioni Office usando Windows Installer](#Publish).  
  
-   [Disabilitare la reflection della barra multifunzione](#Bypass).  
  
-   [Eseguire operazioni complesse in un thread di esecuzione separato](#Perform).  
  
 Per altre informazioni su come ottimizzare un componente aggiuntivo VSTO di Outlook, vedere [Criteri delle prestazioni per mantenere i componenti aggiuntivi abilitati](http://go.microsoft.com/fwlink/?LinkID=266503).  
  
##  <a name="Load"></a> Caricare componenti aggiuntivi VSTO su richiesta  
 È possibile configurare un componente aggiuntivo VSTO da caricare solo nelle circostanze seguenti:  
  
-   La prima volta che l'utente avvia l'applicazione dopo aver installato il componente aggiuntivo VSTO.  
  
-   La prima volta che l'utente interagisce con il componente aggiuntivo VSTO dopo l'avvio dell'applicazione in un qualsiasi momento successivo.  
  
 Ad esempio, il componente aggiuntivo VSTO potrebbe popolare un foglio di lavoro con i dati quando l'utente seleziona un pulsante personalizzato con etichetta **Ottieni dati personali**. L'applicazione deve caricare il componente aggiuntivo VSTO almeno una volta in modo che sia possibile visualizzare il pulsante **Ottieni dati personali** nella barra multifunzione. Tuttavia, il componente aggiuntivo VSTO non viene caricato di nuovo quando l'utente avvia l'applicazione in un momento successivo. Il componente aggiuntivo VSTO viene caricato solo quando l'utente seleziona il pulsante **Ottieni dati personali**.  
  
#### Per configurare una soluzione ClickOnce per caricare componenti aggiuntivi VSTO su richiesta  
  
1.  Scegliere il nodo di progetto in **Esplora soluzioni**.  
  
2.  Sulla barra dei menu, scegliere **Visualizza**, **Pagine delle proprietà**.  
  
3.  Nella scheda **Pubblica** scegliere il pulsante **Opzioni**.  
  
4.  Nella finestra di dialogo **Opzioni di pubblicazione** scegliere l'elemento elenco **Impostazioni Office**, selezionare l'opzione **Carica su richiesta**, quindi il pulsante **OK**.  
  
#### Per configurare una soluzione Windows Installer per caricare componenti aggiuntivi VSTO su richiesta  
  
1.  Nel Registro di sistema impostare la voce `LoadBehavior` della chiave *Root*\\Software\\Microsoft\\Office\\*ApplicationName*\\Addins\\*Add\-in ID* su **0x10**.  
  
     Per altre informazioni, vedere [Voci del Registro di sistema per i componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
#### Per configurare una soluzione per caricare componenti aggiuntivi VSTO su richiesta durante il debug della soluzione  
  
1.  Creare uno script che consenta di impostare la voce `LoadBehavior` della chiave *Root*\\Software\\Microsoft\\Office\\*ApplicationName*\\Addins\\*Add\-in ID* su **0x10**.  
  
     Nel codice seguente viene illustrato un esempio di questo script.  
  
    ```  
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn] "Description"="MyAddIn" "FriendlyName"="MyAddIn" "LoadBehavior"=dword:00000010 "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"  
  
    ```  
  
2.  Creare un evento di post\-compilazione in grado di aggiornare il Registro di sistema usando lo script.  
  
     Nel codice seguente viene illustrato un esempio di una stringa di comando che è possibile aggiungere a un evento di post\-compilazione.  
  
    ```  
    regedit /s "$(SolutionDir)$(SolutionName).reg"  
  
    ```  
  
     Per informazioni su come creare eventi di post\-compilazione in un progetto C\#, vedere [Procedura: specificare eventi di compilazione &#40;C&#35;&#41;](~/ide/how-to-specify-build-events-csharp.md).  
  
     Per informazioni su come creare eventi di post\-compilazione in un progetto Visual Basic, vedere [Procedura: specificare eventi di compilazione &#40;C&#35;&#41;](~/ide/how-to-specify-build-events-csharp.md).  
  
##  <a name="Publish"></a> Pubblicare soluzioni Office usando Windows Installer  
 Se si pubblica la soluzione usando Windows Installer, Visual Studio 2010 Tools per Office Runtime consente di ignorare i passaggi seguenti quando viene caricato il componente aggiuntivo VSTO.  
  
-   Convalida dello schema manifesto.  
  
-   Controllo automatico della disponibilità di aggiornamenti.  
  
-   Convalida della firma digitale dei manifesti della distribuzione.  
  
    > [!NOTE]  
    >  Questo approccio non è necessario se si distribuisce il componente aggiuntivo VSTO in una posizione sicura nei computer degli utenti.  
  
 Per altre informazioni, vedere [Distribuzione di una soluzione Office tramite Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Bypass"></a> Disabilitare la reflection della barra multifunzione  
 Se si compila una soluzione usando [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], assicurarsi che gli utenti abbiano installato la versione più recente di Visual Studio 2010 Tools per Office Runtime quando si distribuisce la soluzione. Le versioni precedenti di quel runtime effettuavano la reflection negli assembly della soluzione per individuare le personalizzazioni della barra multifunzione. Questo processo può rallentare il caricamento del componente aggiuntivo VSTO.  
  
 In alternativa, è possibile impedire a qualsiasi versione di Visual Studio 2010 Tools per Office Runtime di usare la reflection per identificare le personalizzazioni della barra multifunzione. Per seguire questa strategia, eseguire l'override del metodo `CreateRibbonExtensibility` e restituire gli oggetti della barra multifunzione in modo esplicito. Se il componente aggiuntivo VSTO non contiene tutte le personalizzazioni della barra multifunzione, restituire `null` all'interno del metodo.  
  
 Nell'esempio seguente viene restituito un oggetto della barra multifunzione in base al valore di un campo.  
  
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/VB/ThisWorkbook.vb#1)]  
  
##  <a name="Perform"></a> Eseguire operazioni complesse in un thread di esecuzione separato  
 Si consiglia di eseguire le attività che richiedono tempo \(ad esempio le attività a esecuzione prolungata, le connessioni di database o altri tipi di chiamate di rete\) in un thread separato. Per altre informazioni, vedere [Supporto del threading in Office](../vsto/threading-support-in-office.md).  
  
> [!NOTE]  
>  Tutto il codice che effettua chiamate nel modello a oggetti di Office deve essere eseguito nel thread principale.  
  
## Vedere anche  
 [Caricamento su richiesta di componenti aggiuntivi VSTO](http://blogs.msdn.com/b/andreww/archive/2008/07/14/demand-loading-vsto-add-ins.aspx)   
 [Caricamento ritardato di CLR nei componenti aggiuntivi di Office](http://blogs.msdn.com/b/andreww/archive/2008/04/19/delay-loading-the-clr-in-office-add-ins.aspx)   
 [Prestazioni di VSTO: il caricamento ritardato e l'utente \(Stephen Peters\)](http://blogs.msdn.com/b/vsto/archive/2010/01/07/vsto-performance-delay-loading-and-you.aspx)   
 [Miglioramenti delle prestazioni previsti per un Service Pack vicino alle esigenze degli utenti \(Stephen Peters\)](http://blogs.msdn.com/b/vsto/archive/2010/11/30/performance-improvements-coming-soon-to-a-service-pack-near-you-stephen-peters.aspx)   
 [Prestazioni di VSTO: reflection della barra multifunzione \(Stephen Peters\)](http://blogs.msdn.com/b/vsto/archive/2010/06/03/vsto-performance-ribbon-reflection.aspx)  
  
  