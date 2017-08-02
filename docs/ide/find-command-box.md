---
title: "Casella Trova/Comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.findcommandbox"
helpviewer_keywords: 
  - "Trova/Comando (casella)"
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Casella Trova/Comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile cercare testo ed eseguire i comandi di Visual Studio dalla casella **Trova\/Comando**.  La casella **Trova\/Comando** è ancora disponibile come controllo toolbar, ma non è più visibile per impostazione predefinita.  È possibile visualizzare la casella di **Trova\/Comando** scegliendo **Aggiungi o rimuovi pulsanti** sulla barra degli strumenti **Standard** e scegliendo **Trova**.  
  
 Per eseguire un comando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], introducala con un maggiore \(\>\) del simbolo.  
  
 La casella **Trova\/Comando** memorizza gli ultimi 20 elementi immessi e li visualizza in una casella di riepilogo a discesa  È possibile scorrere l'elenco dei tasti di direzione.  
  
 ![Casella Trova&#47;Comando](~/docs/ide/media/findcommandbox.png "FindCommandBox")  
Casella Trova\/Comando  
  
## Ricerca del testo  
 Per impostazione predefinita, quando si specifica il testo nella casella **Trova\/Comando** quindi scegliere il tasto INVIO, Visual Studio cerca il documento corrente o la finestra degli strumenti mediante le opzioni specificate nella finestra di dialogo **Cerca nei file**.  Per ulteriori informazioni, vedere [Ricerca e sostituzione di testo](../ide/finding-and-replacing-text.md).  
  
## Immissione di comandi  
 Per utilizzare la casella di **Trova\/Comando** per pubblicare un solo comando o alias [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] anziché la ricerca di testo, il comando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], introdotto con un maggiore \(\>\) del simbolo.  Ad esempio:  
  
```  
>File.NewFile c:\temp\MyFile /t:"General\Text File"  
```  
  
 In alternativa è possibile utilizzare la finestra di comando per immettere ed eseguire uno o più comandi.  Alcuni comandi o alias possono essere immessi ed eseguiti direttamente, mentre altri richiedono una sintassi comprendente determinati argomenti.  Per un elenco dei comandi con argomenti, vedere [Comandi di Visual Studio](../ide/reference/visual-studio-commands.md).  
  
## Caratteri di escape  
 La presenza di un accento circonflesso \(^\) in una riga di comando indica che il carattere immediatamente successivo viene interpretato letteralmente e non come carattere di controllo.  Questo consente di incorporare virgolette diritte \("\), spazi, barre iniziali, accenti circonflessi o qualsiasi altro carattere effettivo nel valore di un parametro o di un'opzione, ad eccezione dei nomi di opzioni.  Di seguito è riportato un esempio:  
  
```  
>Edit.Find ^^t /regex  
```  
  
 L'accento circonflesso presenta lo stesso funzionamento sia all'interno sia all'esterno delle virgolette.  Se corrisponde all'ultimo carattere sulla riga, viene ignorato.  
  
## Vedere anche  
 [Finestra di comando](../ide/reference/command-window.md)   
 [Ricerca e sostituzione di testo](../ide/finding-and-replacing-text.md)