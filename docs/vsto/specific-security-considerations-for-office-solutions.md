---
title: "Considerazioni specifiche sulla sicurezza per le soluzioni Office"
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
  - "risoluzione dei problemi di sviluppo per Office in Visual Studio, sicurezza"
  - "codice attendibile [sviluppo per Office in Visual Studio]"
  - "codice bloccato [sviluppo per Office in Visual Studio]"
  - "Outlook [sviluppo per Office in Visual Studio], protezione del modello a oggetti"
  - "codice dannoso [sviluppo per Office in Visual Studio]"
  - "Outlook (protezione del modello a oggetti) [sviluppo per Office in Visual Studio]"
  - "sicurezza [sviluppo per Office in Visual Studio], risoluzione dei problemi"
ms.assetid: 6a8b3e12-26c6-4ee2-a37e-d5bc8df9c5d1
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Considerazioni specifiche sulla sicurezza per le soluzioni Office
  Le funzionalità di sicurezza fornite da Microsoft .NET Framework e Microsoft Office consentono di proteggere le soluzioni Office da potenziali rischi di sicurezza. Questo argomento illustra alcuni di tali rischi e fornisce suggerimenti utili su come proteggersi. Sono incluse anche informazioni su come le impostazioni di sicurezza di Microsoft Office possono influire sulle soluzioni Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Modifica dello scopo del codice attendibile in un nuovo documento dannoso  
 Un utente malintenzionato potrebbe eseguire codice attendibile che dovrà essere usato per uno scopo specifico, ad esempio il download di informazioni personali per un'applicazione di occupazione, e riutilizzarlo in un altro documento, ad esempio un foglio di lavoro. Il codice non può stabilire che il documento originale non è in esecuzione e può introdurre altre minacce, ad esempio la divulgazione di informazioni personali o l'esecuzione di codice con privilegi di livello superiore, quando viene aperto da un altro utente. In alternativa, l'utente malintenzionato può semplicemente modificare i dati nel foglio di lavoro in modo da determinare un comportamento imprevisto in caso di invio a un altro utente. Modificando i valori, le formule o le caratteristiche di presentazione di un foglio di lavoro collegato al codice, un utente malintenzionato può attaccare un altro utente inviando un file modificato. La modifica dei valori nel foglio di lavoro può anche consentire agli utenti di accedere a informazioni che non dovrebbero poter visualizzare.  
  
 Dal momento che per l'esecuzione è necessario che il percorso dell'assembly e quello del documento abbiano evidenze sufficienti, questo tipo di attacco non è facilmente realizzabile. I documenti allegati a messaggi di posta elettronica o su server Intranet non attendibili, ad esempio, non hanno autorizzazioni sufficienti per essere eseguiti.  
  
 Per consentire questo attacco, il codice deve essere scritto in modo da supportare decisioni basate su dati potenzialmente non attendibili. Si supponga di creare un foglio di lavoro che presenta una cella nascosta contenente il nome di un server di database. L'utente invia il foglio di lavoro a una pagina ASPX, che prova a connettersi a tale server usando l'autenticazione SQL e una password hardcoded dell'account sa. Un intruso potrebbe sostituire il contenuto della cella nascosta con un altro nome computer e ottenere la password dell'account sa. Per evitare questo problema non usare mai le password hardcoded e verificare sempre gli ID del server a fronte di un elenco interno di server noti come affidabili prima di accedere al server.  
  
### Suggerimenti  
  
-   Convalidare sempre l'input e i dati, che derivino dall'utente, dal documento, da un database, da un servizio Web, o da qualsiasi altra origine.  
  
-   Prestare attenzione nell'esposizione di determinati tipi di funzionalità, come l'acquisizione di dati privilegiati per conto dell'utente e il relativo inserimento in un foglio di lavoro non protetto.  
  
-   A seconda del tipo di applicazione, può rivelarsi utile verificare che il documento originale sia in esecuzione prima di eseguire qualsiasi codice. Ad esempio, verificare che venga eseguito da un documento archiviato in un percorso noto e sicuro.  
  
-   Se nell'applicazione vengono eseguite operazioni privilegiate, può essere opportuno visualizzare un avviso all'apertura del documento. È ad esempio possibile creare una schermata iniziale o una finestra di dialogo di avvio in cui viene segnalato che l'applicazione accederà a informazioni personali, consentendo all'utente di scegliere se continuare o annullare l'operazione. Se un avviso di questo tipo viene visualizzato da un documento apparentemente innocuo, l'utente finale potrà chiudere l'applicazione prima che si verifichino danni.  
  
## Codice bloccato dalla protezione del modello a oggetti di Outlook  
 Microsoft Office può limitare l'uso da parte del codice di determinate proprietà, metodi e oggetti nel modello a oggetti. Limitando l'accesso a tali oggetti, Outlook aiuta a impedire a virus e a programmi distruttivi di usare il modello a oggetti a scopo dannoso. Questa funzionalità di sicurezza è nota come protezione del modello a oggetti di Outlook. Se un componente aggiuntivo VSTO prova a usare una proprietà o un metodo per cui sono stati imposti determinati limiti, mentre la protezione del modello a oggetti è attivata, in Outlook viene visualizzato un avviso di sicurezza che consente all'utente di interrompere l'operazione in corso oppure di permettere l'accesso alla proprietà o al metodo per un periodo di tempo limitato. Se l'utente interrompe l'operazione, i componenti aggiuntivi di Outlook creati con le soluzioni Office in Visual Studio generano un'eccezione <xref:System.Runtime.InteropServices.COMException>.  
  
 La protezione del modello a oggetti ha effetto sui componenti aggiuntivi in diversi modi, in base al fatto che Outlook venga usato o meno con Microsoft Exchange Server:  
  
-   Se Outlook non viene usato con Exchange, l'amministratore può abilitare o disabilitare la protezione del modello a oggetti per tutti i componenti aggiuntivi nel computer.  
  
-   Se Outlook viene usato con Exchange, l'amministratore può abilitare o disabilitare la protezione del modello a oggetti per tutti i componenti aggiuntivi nel computer oppure specificare che determinati componenti aggiuntivi possano essere eseguiti senza la protezione del modello a oggetti. È anche possibile modificare il comportamento della protezione del modello a oggetti per alcune aree del modello a oggetti. Ad esempio, l'amministratore può consentire automaticamente l'invio di messaggi di posta elettronica da parte dei componenti aggiuntivi, a livello di codice, anche se la protezione del modello a oggetti è attivata.  
  
 A partire da Outlook 2007, il comportamento della protezione del modello a oggetti è stato modificato per migliorare l'esperienza utente e dello sviluppatore, aiutando al contempo a mantenere Outlook sicuro. Per altre informazioni, vedere l'articolo relativo alle [modifiche per la sicurezza del codice in Outlook 2007](http://go.microsoft.com/fwlink/?LinkId=73429).  
  
### Riduzione degli avvisi di sicurezza del modello a oggetti  
 Per evitare la visualizzazione di avvisi di sicurezza quando si usano proprietà e metodi sottoposti a limitazioni, assicurarsi che il componente aggiuntivo VSTO ottenga oggetti di Outlook dal campo `Application` della classe `ThisAddIn` nel progetto. Per altre informazioni su questo campo, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Per la protezione del modello a oggetti possono essere considerati attendibili solo gli oggetti Outlook ottenuti da questo oggetto. Al contrario, oggetti ottenuti da un nuovo oggetto Microsoft.Office.Interop.Outlook.Application non vengono considerati attendibili e, se la protezione del modello a oggetti è attivata, le proprietà e i metodi sottoposti a limitazioni genereranno avvisi di sicurezza.  
  
 Se la protezione del modello a oggetti è attivata, nell'esempio di codice seguente viene visualizzato un avviso di sicurezza. La proprietà To della classe Microsoft.Office.Interop.Outlook.MailItem è limitata dalla protezione del modello a oggetti. L'oggetto Microsoft.Office.Interop.Outlook.MailItem non viene considerato attendibile perché il codice lo ottiene da un oggetto Microsoft.Office.Interop.Outlook.Application creato usando l'operatore **new** invece che dal campo `Application`.  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreOutlookSecurity/CS/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreOutlookSecurity/VB/ThisAddIn.vb#1)]  
  
 L'esempio di codice seguente illustra come usare la proprietà limitata To di un oggetto Microsoft.Office.Interop.Outlook.MailItem considerato attendibile dalla protezione del modello a oggetti. Il codice usa il campo `Application` attendibile per ottenere l'oggetto Microsoft.Office.Interop.Outlook.MailItem.  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreOutlookSecurity/CS/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreOutlookSecurity/VB/ThisAddIn.vb#2)]  
  
> [!NOTE]  
>  Se Outlook viene usato con Exchange, il fatto che tutti gli oggetti Outlook siano ottenuti da `ThisAddIn.Application` non garantisce che il componente aggiuntivo VSTO riuscirà ad accedere al modello a oggetti di Outlook completo. Ad esempio, se un amministratore di Exchange imposta Outlook in modo che vengano respinti tutti i tentativi di accedere alle informazioni sugli indirizzi usando il modello a oggetti di Outlook, non verrà consentito al codice di esempio precedente di accedere alla proprietà To, anche se il codice usa il campo `ThisAddIn.Application` attendibile.  
  
### Indicazione dei componenti aggiuntivi da considerare attendibili se si usa Exchange  
 Quando si usa Outlook con Exchange, gli amministratori possono specificare che per determinati componenti aggiuntivi è consentita l'esecuzione senza la protezione del modello a oggetti. I componenti aggiuntivi di Outlook creati usando le soluzioni Office in Visual Studio non possono essere considerati attendibili singolarmente, ma attendibili solo come gruppo.  
  
 In Outlook un componente aggiuntivo VSTO viene considerato attendibile in base a un codice hash della DLL del punto di ingresso del componente aggiuntivo VSTO. Tutti i componenti aggiuntivi VSTO di Outlook destinati a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] usano la stessa DLL per il punto di ingresso \(VSTOLoader.dll\). In questo modo, se un amministratore considera attendibile uno qualsiasi dei componenti aggiuntivi destinati a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ai fini dell'esecuzione senza la protezione del modello a oggetti, anche tutti gli altri componenti aggiuntivi destinati a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] verranno considerati attendibili. Per altre informazioni sull'attendibilità di componenti aggiuntivi specifici per l'esecuzione senza la protezione del modello a oggetti, vedere [Specificare il metodo usato da Outlook per gestire le caratteristiche di prevenzione dei virus](http://go.microsoft.com/fwlink/?LinkId=128773).  
  
## Effetto non immediato delle modifiche delle autorizzazioni  
 Se l'amministratore modifica le autorizzazioni per un documento o un assembly, per rendere effettive le modifiche gli utenti devono chiudere e quindi riavviare tutte le applicazioni di Office.  
  
 L'applicazione delle nuove autorizzazioni può essere impedita anche da altre applicazioni che ospitano applicazioni Microsoft Office. Quando vengono modificati i criteri di sicurezza, è consigliabile che gli utenti chiudano tutte le applicazioni che usano Office in modo autonomo o tramite hosting.  
  
## Le impostazioni del Centro protezione in Microsoft Office System non influiscono sui componenti aggiuntivi né sulle personalizzazioni a livello di documento  
 Gli utenti possono impedire il caricamento dei componenti aggiuntivi VSTO impostando un'opzione nel **Centro protezione**. Tuttavia, i componenti aggiuntivi VSTO a livello di applicazione e le personalizzazioni a livello di documento creati con le soluzioni Office in Visual Studio non sono interessati da tali impostazioni di attendibilità.  
  
 Se l'utente impedisce il caricamento dei componenti aggiuntivi usando il **Centro protezione**, non verranno caricati i tipi di componenti aggiuntivi seguenti:  
  
-   Componenti aggiuntivi VSTO COM gestiti e non gestiti  
  
-   Smart document gestiti e non gestiti  
  
-   Componenti aggiuntivi VSTO di automazione gestiti e non gestiti  
  
-   Componenti dati in tempo reale gestiti e non gestiti  
  
 Le procedure seguenti descrivono come usare **Centro protezione** per limitare il caricamento dei componenti aggiuntivi in Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e Microsoft Office 2010. Queste procedure non influiscono sui componenti aggiuntivi o le personalizzazioni create usando gli strumenti di sviluppo di Office in Visual Studio.  
  
#### Per disabilitare i componenti aggiuntivi VSTO nelle applicazioni Microsoft Office 2010 e Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]  
  
1.  Scegliere la scheda **File**.  
  
2.  Scegliere il pulsante *ApplicationName***Opzioni**.  
  
3.  Nel riquadro delle categorie, scegliere **Centro protezione**.  
  
4.  Nel riquadro dei dettagli scegliere Impostazioni **Centro protezione**.  
  
5.  Nel riquadro delle categorie scegliere **Componenti aggiuntivi**.  
  
6.  Nel riquadro dei dettagli selezionare **Richiedi che i componenti aggiuntivi di applicazioni siano firmati da un autore attendibile** o **Disabilita tutti i componenti aggiuntivi delle applicazioni**.  
  
## Vedere anche  
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)  
  
  