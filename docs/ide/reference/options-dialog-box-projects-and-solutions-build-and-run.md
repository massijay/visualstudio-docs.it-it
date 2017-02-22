---
title: "Finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.Build_and_Run"
  - "VS.ToolsOptionsPag.Projects.Build_and_Run"
helpviewer_keywords: 
  - "compilazioni [Visual Studio], impostazione"
  - "esecuzione di azioni"
  - "debugger, opzioni di esecuzione"
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In questa finestra di dialogo, è possibile specificare il numero massimo di progetti Visual C\+\+ o Visual C\# che è possibile compilare allo stesso tempo, determinati comportamenti di compilazione predefiniti e alcune impostazioni del log di compilazione.  Per aprire la finestra di dialogo **Opzioni**, scegliere **Strumenti**, **Opzioni** nella barra dei menu.  Per accedere a questo set di opzioni, espandere **Progetti e soluzioni**, quindi scegliere **Compila ed esegui**.  
  
## Elenco UIElement  
 **numero massimo di compilazioni di progetto parallele**  
 Specifica il numero massimo di progetti Visual C\+\+ e Visual C\# che è possibile compilare contemporaneamente.  Per ottimizzare il processo di compilazione, il numero massimo di compilazioni di progetti in parallelo viene impostato automaticamente sul numero di CPU del computer.  Il numero massimo è 32.  
  
 **Compila progetti di avvio e dipendenze solo in fase di esecuzione**  
 Se si seleziona questa casella di controllo quando si preme il tasto F5, vengono compilati solo il progetto di avvio e le relative dipendenze; scegliere **Debug**, **Avvia** oppure **Compila**, **Compila** sulla barra dei menu.  Se si seleziona questa casella di controllo quando si preme il tasto F5, vengono compilati tutti i progetti, le dipendenze e i file di soluzione; scegliere **Debug**, **Avvia** oppure **Compila**, **Compila** sulla barra dei menu.  Per impostazione predefinita, questa opzione è deselezionata.  
  
 **Durante l'esecuzione, quando i progetti non sono aggiornati**  
 > [!NOTE]
>  Questo elenco si applica solo ai progetti [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 Per impostazione predefinita, viene visualizzato un messaggio se una configurazione del progetto non è aggiornata quando si preme il tasto F5 o si sceglie **Debug**, **Avvia** sulla barra dei menu.  È possibile specificare se generare comunque il progetto e se viene visualizzato il messaggio.  Usare questa opzione per specificare se viene visualizzato il messaggio e quale deve essere il comportamento di compilazione se non viene visualizzato il messaggio.  
  
 **Compila sempre**  
 Non viene visualizzata la finestra di messaggio e il progetto viene compilato nonostante la configurazione non aggiornata.  Questa opzione viene impostata quando si seleziona la casella **Non visualizzare più questo messaggio** e quindi si sceglie il pulsante **Sì**.  
  
 **Non compilare mai**  
 Non viene visualizzata la finestra di messaggio e il progetto non viene compilato.  Questa opzione viene impostata quando si seleziona la casella **Non visualizzare più questo messaggio** e quindi si sceglie il pulsante **No**.  
  
 **Richiedi compilazione**  
 Mostra la finestra di messaggio ogni volta che una configurazione del progetto non è aggiornata.  
  
 **Durante l'esecuzione, quando si verificano errori di compilazione o distribuzione**  
 Se si verificano errori di compilazione quando si avvia una compilazione dal menu **Compila**, viene visualizzato un messaggio.  È possibile specificare se continuare avviando l'applicazione e se il messaggio viene visualizzato ogni volta che si verificano errori di compilazione.  Usare questa opzione per specificare se viene visualizzato il messaggio e quale deve essere il comportamento se non viene visualizzato il messaggio.  
  
> [!NOTE]
>  Questa opzione si applica solo ai progetti [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 **Richiedi avvio**  
 Mostra una finestra di messaggio ogni volta che si verificano errori di compilazione.  
  
 **Non avviare**  
 Non viene visualizzata la finestra di messaggio e l'applicazione non viene avviata.  Questa opzione viene impostata quando si seleziona la casella di controllo **Non visualizzare più questo messaggio** nella finestra di messaggio e quindi si sceglie il pulsante **No**.  
  
 **Avvia versione precedente**  
 Non viene visualizzata la finestra di messaggio e la versione dell'applicazione appena compilata non viene avviata.  Questa opzione viene impostata quando si seleziona la casella di controllo **Non visualizzare più questo messaggio** nella finestra di messaggio e quindi si sceglie il pulsante **Sì**.  
  
 **Per nuove soluzioni utilizza il progetto selezionato come progetto di avvio**  
 Se questa casella di controllo è selezionata, le nuove soluzioni usano il progetto selezionato come progetto di avvio.  
  
 **Livello di dettaglio output in compilazione progetto MSBuild**  
 Determina la quantità di informazioni che viene visualizzata nella finestra per la compilazione **Output**.  
  
 **Livello di dettaglio file di log di compilazione progetto MSBuild**  
 > [!NOTE]
>  Questa opzione si applica solo ai progetti Visual C\+\+.  
  
 Determina la quantità di informazioni che viene scritta nel file di log di compilazione che si trova in \\...  \\*NomeProgetto*\\Debug\\*NomeProgetto*.log.  
  
## Vedere anche  
 [Compilazione di applicazioni in Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)