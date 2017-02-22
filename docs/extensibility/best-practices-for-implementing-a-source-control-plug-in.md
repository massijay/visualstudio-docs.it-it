---
title: "Procedure consigliate per implementare un plug-in del controllo del codice sorgente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "origine plug-in del controllo, le procedure consigliate"
  - "le procedure consigliate, plug-in del controllo codice sorgente"
  - "controllo del codice sorgente [Visual Studio SDK], plug-in"
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedure consigliate per implementare un plug-in del controllo del codice sorgente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I dettagli tecnici seguenti consentono di implementare in modo affidabile un plug\-in di controllo del codice sorgente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Problemi di gestione della memoria  
 Nella maggior parte dei casi, l'ambiente di sviluppo integrato \(IDE\), che è il chiamante, rilascia e alloca la memoria. Il plug\-in del controllo del codice sorgente restituisce stringhe e altri elementi nel buffer allocata dal chiamante. Le eccezioni sono indicate nelle descrizioni delle funzioni specifiche in cui si verificano.  
  
## Matrici dei nomi di File  
 Quando viene passata una matrice di file, non viene passato come una matrice contigua di nomi di file. Viene passato come matrice di puntatori ai nomi dei file. Ad esempio, nel [SccGet](../extensibility/sccget-function.md), i nomi dei file vengono passati tramite il `lpFileNames` parametro, in cui `lpFileNames` è effettivamente un puntatore a un `char **`.`lpFileNames`\[0\] è un puntatore al nome, `lpFileNames`\[1\] è un puntatore al nome della seconda e così via.  
  
## Modelli di grandi dimensioni  
 Tutti i puntatori sono a 32 bit, anche nei sistemi operativi a 16 bit.  
  
## Percorsi completi  
 In cui i nomi di file o directory vengono specificate come argomenti, devono essere percorsi completi o i percorsi UNC, senza la barra rovesciata finale. È responsabilità del plug\-in per convertire questi elementi per i percorsi relativi, se vale a dire un requisito del sistema di controllo di origine sottostante il controllo del codice sorgente.  
  
## Specificare il percorso completo della DLL registrato  
 L'IDE non carica DLL da percorsi relativi \(ad esempio,.\\NewProvider.dll\). \(Ad esempio, C:\\Providers\\NewProvider.dll\), è necessario specificare un percorso completo della DLL. Questo requisito aumenta la protezione dell'IDE impedendo il caricamento del controllo del codice sorgente non autorizzati o Delegate DLL.  
  
## Cercare un plug\-in VSSCI esistente quando si installa il plug\-in del controllo del codice sorgente  
 Un utente che prevede di installare il plug\-in del controllo del codice sorgente disponga già di un controllo codice sorgente esistente plug\-in installato nel computer. Il programma di installazione \(setup\) per il plug\-in creati deve determinare se sono presenti i valori esistenti per le chiavi del Registro di sistema pertinente. Se queste chiavi sono già impostate, il programma di installazione deve chiedere all'utente se registrare il plug\-in come il controllo del codice sorgente predefinito plug\-in e sostituire quello che è già installato.  
  
## Codici di risultato di errore e Reporting  
 Il `SCC_OK` restituiscono il codice per una funzione di controllo di origine indica che l'operazione è riuscita per tutti i file. Se l'operazione non riesce, si prevede per restituire l'ultimo codice di errore rilevato.  
  
 La regola per la segnalazione è che se si verifica un errore nell'IDE, è responsabile della segnalazione dell'IDE. Se si verifica un errore nel sistema di controllo di origine, il plug\-in del controllo del codice sorgente è responsabile per segnalarlo. Ad esempio, "attualmente selezionato alcun file" sarebbe stato segnalato dall'IDE, mentre "questo file è già estratto" sarebbe stato segnalato il plug\-in.  
  
## La struttura di contesto  
 Durante la chiamata di [SccInitialize](../extensibility/sccinitialize-function.md), il chiamante passa il `ppvContext` parametro, ovvero un handle inizializzato su un valore void. Il plug\-in del controllo del codice sorgente è possibile ignorare questo parametro o può allocare una struttura di qualsiasi tipo e inserire il puntatore passato un puntatore a tale struttura. L'IDE non riconosce questa struttura, ma passa un puntatore alla struttura in ogni altra chiamata nel plug\-in. Fornisce informazioni di cache di contesto utili al plug\-in che è possibile utilizzare per gestire le informazioni di stato globale permanente tra le chiamate di funzione senza utilizzare le variabili globali. Il plug\-in è responsabile per la struttura in una chiamata a liberare i [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Se i set di plug\-in di `SCC_CAP_REENTRANT` bit il [SccInitialize](../extensibility/sccinitialize-function.md) \(in particolare, nel `lpSccCaps` parametro\), più strutture di contesto vengono utilizzate per tenere traccia di tutti i progetti aperti.  
  
## Flag di bit e altre opzioni di comando  
 Per ogni comando, ad esempio il [SccGet](../extensibility/sccget-function.md), l'IDE è possibile specificare numerose opzioni che modificano il comportamento del comando.  
  
 L'API supporta l'impostazione di determinate opzioni per l'IDE tramite il `fOptions` parametro. Queste opzioni sono descritte in [Flag di bit utilizzati dai comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) con i comandi che influiscano su. In generale, queste sono le opzioni per il quale non verrebbe richiesto all'utente.  
  
 Più opzioni di impostazione configurabile dall'utente non sono definite in questo modo perché variano notevolmente tra plug\-in del controllo codice sorgente. Pertanto, il metodo consigliato è un **Avanzate** pulsante. Ad esempio, nel **ottenere** la finestra di dialogo, l'IDE visualizza soltanto le informazioni che riconosca, ma visualizza inoltre un **Avanzate** se il plug\-in sono disponibili opzioni per questo comando. Quando l'utente sceglie il **Avanzate** pulsante, le chiamate IDE il [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) per abilitare il controllo del codice sorgente del plug\-in per richiedere all'utente informazioni aggiuntive, come flag di bit o una data\/ora. Il plug\-in restituisce queste informazioni in una struttura che viene passata nuovamente durante la `SccGet` comando.  
  
## Vedere anche  
 [Plug\-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [Creazione di plug\-in un controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md)