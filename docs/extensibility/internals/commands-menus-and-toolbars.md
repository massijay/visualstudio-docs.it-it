---
title: "I comandi, menu e barre degli strumenti | Microsoft Docs"
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
  - "menu [Visual Studio SDK], comandi"
  - "comandi [Visual Studio]"
  - "i comandi di barre degli strumenti [Visual Studio]"
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: 60
caps.handback.revision: 60
ms.author: "gregvanl"
manager: "ghogen"
---
# I comandi, menu e barre degli strumenti
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Menu e barre degli strumenti sono che i modo gli utenti di accedere ai comandi di VSPackage. I comandi sono funzioni che eseguono attività, ad esempio la stampa del documento, aggiornamento di una vista o la creazione di un nuovo file. Menu e barre degli strumenti sono agevolmente con interfaccia grafica per presentare i comandi per gli utenti. I comandi correlati sono in genere raggruppati nello stesso menu o sulla barra degli strumenti.  
  
-   In genere, i menu vengono visualizzati come stringhe di parola in cluster in una riga nella parte superiore dell'ambiente di sviluppo integrato \(IDE\) o una finestra degli strumenti. Anche i menu possono essere visualizzati come risultato di un evento mouse e vengono definiti i menu di scelta rapida in tale contesto. Quando si fa clic, menu espandono per visualizzare uno o più comandi. Comandi, quando si fa clic, possono eseguire operazioni o avviare sottomenu contenenti altri comandi. Alcuni nomi noti menu sono File, modifica, visualizzazione e finestra. Per altre informazioni, vedere [Estensione menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
-   Barre degli strumenti sono in genere le righe di pulsanti e altri controlli, ad esempio le caselle combinate, caselle di riepilogo, caselle di testo e controller di menu. Tutti i controlli della barra degli strumenti sono associati i comandi. Quando si fa clic su un pulsante della barra degli strumenti, viene attivato il comando associato. Pulsanti della barra degli strumenti sono in genere le icone che suggeriscono i comandi sottostanti, ad esempio una stampante per un comando di stampa. In un controllo elenco a discesa, ogni elemento nell'elenco è associato a un comando diverso. Un controller di menu è un ibrido in cui un lato del controllo è un pulsante della barra degli strumenti e l'altro lato è una freccia in giù visualizzata altri comandi quando si fa clic. Per altre informazioni, vedere [Aggiunta di un Controller di Menu per una barra degli strumenti](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
-   Quando si crea un comando, è inoltre necessario creare un gestore eventi per esso. Il gestore eventi determina quando il comando è visibile o abilitata, consente di modificare il testo e garantisce che il comando risponde in modo appropriato \("route"\) quando attivato. Nella maggior parte dei casi, l'IDE gestisce i comandi tramite il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. I comandi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] route in modo gerarchico, a partire dal contesto del comando più interna, in base alla selezione locale e procedere con il contesto più esterno, in base alla selezione globale. I comandi aggiunti al menu principale sono immediatamente disponibili per lo script. Per altre informazioni, vedere [Confronto tra oggetti MenuCommand e OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md) e [Selezione oggetti di contesto](../../extensibility/internals/selection-context-objects.md).  
  
 Per definire nuovi menu e barre degli strumenti, è necessario descrivere tali in un file di tabella comandi di Visual Studio \(vsct\). Il modello di pacchetto di Visual Studio crea il file, con gli elementi necessari per supportare qualsiasi comandi, barre degli strumenti ed editor selezionato nel modello. In alternativa, è possibile scrivere il proprio file. vsct, utilizzando lo schema xml descritto qui: [Riferimento allo Schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
 Per ulteriori informazioni sull'utilizzo dei file. vsct, vedere [Tabella di comandi di Visual Studio \(. File Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Negli argomenti di questa sezione viene descritta il comandi, menu e barre degli strumenti in VSPackage.  
  
## In questa sezione  
 [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Una descrizione approfondita della specifica di formato di tabella comandi.  
  
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Viene descritto un compilatore per le tabelle di comando e la sintassi basata su XML.  
  
 [Comando predefinito, gruppo e il posizionamento della barra degli strumenti](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Descrive barre degli strumenti, gruppi, menu e comandi predefiniti.  
  
 [Gruppi, menu e comandi definiti dall'IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Specifica il menu predefiniti, comandi e i gruppi di comando disponibili per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Progettazione di comando](../../extensibility/internals/command-design.md)  
 Viene illustrato come progettare i comandi.  
  
 [Ottimizzazione di Menu e comandi della barra degli strumenti](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Vengono fornite indicazioni per i comandi.  
  
 [Rendere disponibili i comandi](../../extensibility/internals/making-commands-available.md)  
 Viene illustrato come rendere disponibili i comandi di Visual Studio.  
  
 [Comandi e menu che utilizzano gli assembly di interoperabilità](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Viene illustrato come implementare i comandi che usano gli assembly di interoperabilità.  
  
## Sezioni correlate  
 [Routing dei comandi in VS](../../extensibility/internals/command-routing-in-vspackages.md)  
 Viene illustrato il routing dei comandi in VSPackage.