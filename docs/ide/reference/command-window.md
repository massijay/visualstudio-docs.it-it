---
title: "Finestra di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.CommandWindow"
helpviewer_keywords: 
  - "modalità comando nella finestra di comando"
  - "finestra di comando"
  - "IDE (finestra di comando)"
  - "IDE, finestra di comando"
  - "modalità indicatore nella finestra di comando"
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Finestra di comando
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La finestra **Comando** consente di eseguire dei comandi o degli alias direttamente nell'ambiente IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  È possibile eseguire sia i comandi di menu che comandi non visualizzati in alcun menu.  Per visualizzare la finestra **Comando**, scegliere **Altre finestre** dal menu **Visualizza** e selezionare **Finestra di comando**.  
  
## Visualizzazione dei valori delle variabili  
 Per verificare il valore di una variabile `varA`, utilizzare [Comando Print](../../ide/reference/print-command.md):  
  
```  
>Debug.Print varA  
```  
  
 Il punto interrogativo \(?\) è un alias per `Debug.Print`, quindi questo comando può essere scritto anche nel seguente modo:  
  
```  
>? varA  
```  
  
 Entrambe le versioni del comando restituiscono il valore della variabile `varA`.  
  
## Immissione di comandi  
 Il simbolo di maggiore \(`>`\) viene visualizzato sul lato sinistro della finestra Comando come prompt per le nuove righe.  Utilizzare i tasti FRECCIA GIÙ e FRECCIA SU per scorrere i comandi precedentemente immessi.  
  
|Task|Soluzione|Esempio|  
|----------|---------------|-------------|  
|Valutare un'espressione.|Inserire l'espressione preceduta da un punto interrogativo \(`?`\).|`? myvar`|  
|Visualizzazione della finestra di controllo immediato.|Immettere `immed` nella finestra senza il segno di maggiore \(\>\)|`immed`|  
|Tornare alla finestra Comando dalla finestra di controllo immediato.|Immettere `cmd` nella finestra.|`>cmd`|  
  
 I collegamenti riportati di seguito agevolano gli spostamenti in modalità comando.  
  
|Azione|Posizione del cursore|Associazione di tasti|  
|------------|---------------------------|---------------------------|  
|Scorrere l'elenco dei comandi immessi precedentemente.|Riga di input|FRECCIA & GIÙ DEL FRECCIA SU|  
|Scorrere la finestra verso l'alto.|Contenuto della finestra di comando|CTRL\+FRECCIA SU|  
|Scorrere la finestra verso il basso.|Contenuto della finestra di comando|FRECCIA GIÙ oppure CTRL\+FRECCIA GIÙ|  
  
> [!TIP]
>  Per copiare nella riga di input tutto o una parte di un comando precedente, spostarsi su di esso, selezionarlo interamente o in parte, quindi premere INVIO.  
  
## Modalità indicatore  
 Facendo clic su una qualsiasi riga precedente nella finestra **Comando**, si passa automaticamente in modalità Indicatore.  Questa modalità consente di selezionare, modificare e copiare il testo dei comandi precedenti come in un qualsiasi editor di testo e incollarlo nella riga corrente.  
  
## Il segno di uguale \(\=\)  
 La finestra utilizzata per immettere il comando `EvaluateStatement` determina se il segno uguale \(\=\) deve essere interpretato come operatore di confronto o operatore di assegnazione.  
  
 Nella finestra **Comando**, il segno uguale \(\=\) viene interpretato come operatore di confronto.  Non è possibile utilizzare gli operatori di assegnazione nella finestra **Comando**.  Pertanto, se, ad esempio, i valori delle variabili `varA` e `varB` sono diversi, il comando  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 restituisce il valore `False`.  
  
 Nella finestra di **Controllo immediato**, invece, il segno uguale \(\=\) viene interpretato come operatore di assegnazione.  Ad esempio, il comando  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 assegna alla variabile `varA` il valore della variabile `varB`.  
  
## Parametri, opzioni e valori  
 Per alcuni comandi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sono disponibili argomenti obbligatori e opzionali, opzioni e valori.  All'utilizzo di tali comandi vengono applicate determinate regole.  Di seguito viene riportato un esempio di comando complesso allo scopo di illustrare la terminologia.  
  
```  
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar   
```  
  
 Nell’esempio:  
  
-   `Edit.ReplaceInFiles` è il comando  
  
-   `/case` e `/pattern:regex` sono opzioni \(precedute dal carattere barra \[\/\]\)  
  
-   `regex` è il valore dell'opzione `/pattern`; all'opzione `/case` non è assegnato alcun valore  
  
-   `var[1-3]+` e `oldpar` sono parametri  
  
    > [!NOTE]
    >  Qualsiasi comando, parametro, opzione o valore contenente degli spazi deve essere racchiuso tra virgolette doppie.  
  
 La posizione delle opzioni e dei parametri sulla riga di comando è in genere intercambiabile. L'unica eccezione è rappresentata dal comando [Shell](../../ide/reference/shell-command.md), che richiede uno specifico ordine per le opzioni e i parametri.  
  
 Quasi tutte le opzioni supportate da un comando sono disponibili in due formati: un formato breve \(costituito da un unico carattere\) e uno lungo.  Le opzioni in formato breve possono essere raggruppate.  Le opzioni `/p /g /m` possono ad esempio essere espresse anche come `/pgm`.  
  
 Se alle opzioni in formato breve raggruppate viene assegnato un valore, tale valore si applica a ciascuna opzione.  Ad esempio, `/pgm:123` equivale a `/p:123 /g:123 /m:123`.  Se una delle opzioni raggruppate non accetta un valore, viene generato un errore.  
  
## Caratteri di escape  
 La presenza di un accento circonflesso \(^\) in una riga di comando indica che il carattere immediatamente successivo viene interpretato letteralmente e non come carattere di controllo.  Questo consente di incorporare virgolette diritte \("\), spazi, barre iniziali, accenti circonflessi o qualsiasi altro carattere effettivo nel valore di un parametro o di un'opzione, ad eccezione dei nomi di opzioni.  Di seguito è riportato un esempio:  
  
```  
>Edit.Find ^^t /regex  
```  
  
 L'accento circonflesso presenta lo stesso funzionamento sia all'interno sia all'esterno delle virgolette.  Se corrisponde all'ultimo carattere sulla riga, viene ignorato.  Nell'esempio riportato di seguito viene illustrato come trovare il modello "^t".  
  
## Virgolette di utilizzo per i nomi di percorso con spazi  
 Se, ad esempio, si desidera aprire un file con un percorso che contiene spazi, è necessario inserire le virgolette intorno al percorso o il segmento di percorso contenente spazi: C:\\" file di programma" o "C:\\Program " file".  
  
## Vedere anche  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)   
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)