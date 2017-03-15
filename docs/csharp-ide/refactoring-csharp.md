---
title: "Refactoring (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.preview"
  - "vs.csharp.refactoring.issues"
  - "vs.csharp.refactoring.buildwarning"
  - "VS.PreviewChanges"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#]"
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per refactoring si intende il processo di miglioramento del codice scritto che prevede la modifica della struttura interna del codice senza modificarne il comportamento esterno.  
  
 Nel menu **Refactoring** di Visual C\# sono disponibili i seguenti comandi di refactoring:  
  
-   [Refactoring Estrai Metodo \(C\#\)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
-   [Refactoring di ridenominazione \(C\#\)](../csharp-ide/rename-refactoring-csharp.md)  
  
-   [Encapsulate Field Refactoring \(C\#\)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
-   [Extract Interface Refactoring \(C\#\)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
-   [Refactoring Rimuovi parametri \(C\#\)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
-   [Reorder Parameters Refactoring \(C\#\)](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## Refactoring multiprogetto  
 Visual Studio supporta il refactoring multiprogetto per i progetti che fanno parte della stessa soluzione.  Tutte le operazioni di refactoring che correggono riferimenti tra file estendono tale correzione a tutti i progetti dello stesso linguaggio.  Questa operazione si applica a qualsiasi riferimento da progetto a progetto.  Ad esempio, se si dispone di un'applicazione console che fa riferimento a una libreria di classi, quando si rinomina il tipo di una libreria di classi tramite l'operazione di refactoring `Rename`, vengono aggiornati anche i riferimenti al tipo di libreria di classi nell'applicazione console.  
  
## Anteprima delle modifiche  
 Molte operazioni di refactoring offrono la possibilità di esaminare tutte le modifiche ai riferimenti che verranno eseguite nel codice da un'operazione di refactoring prima del commit.  Per queste operazioni di refactoring, viene visualizzata l'opzione **Anteprima modifiche riferimento** nella finestra di dialogo di refactoring.  Dopo avere selezionato tale opzione e accettato l'operazione di refactoring, verrà visualizzata la finestra di dialogo **Anteprima modifiche**.  Nella finestra di dialogo **Anteprima modifiche** sono disponibili due visualizzazioni.  Nella visualizzazione inferiore viene visualizzato il codice con tutti gli aggiornamenti ai riferimenti determinati dall'operazione di refactoring.  Se si sceglie **Annulla** nella finestra di dialogo **Anteprima modifiche** l'operazione di refactoring verrà interrotta e non verrà apportata alcuna modifica al codice.  
  
## Avvisi di refactoring  
 Se il compilatore non conosce in modo approfondito il programma e vi è la possibilità che il motore di refactoring non aggiorni tutti i riferimenti appropriati, verrà visualizzata la finestra di dialogo di avviso.  Questa finestra consente inoltre di visualizzare in anteprima il codice, nella finestra di dialogo **Anteprima modifiche**, prima di applicare le modifiche.  
  
> [!NOTE]
>  Se un metodo contiene un errore di sintassi \(contrassegnato dall'IDE con una sottolineatura ondulata rossa\), il motore di refactoring non aggiornerà i riferimenti a un elemento all'interno di quel metodo.  Nell'esempio riportato di seguito viene illustrato questo comportamento.  
  
 Per impostazione predefinita, se si esegue un'operazione di refactoring senza visualizzare in anteprima le modifiche ai riferimenti e nel programma viene rilevato un errore di compilazione, nell'ambiente di sviluppo verrà visualizzata questa finestra di avviso.  
  
 Se si esegue un'operazione di refactoring con l'opzione **Anteprima modifiche riferimento** abilitata e nel programma viene rilevato un errore di compilazione, nell'ambiente di sviluppo verrà visualizzato il seguente messaggio di avviso nella parte inferiore della finestra di dialogo **Anteprima modifiche**, anziché la finestra di dialogo **Avviso di refactoring**:  
  
 **Impossibile compilare attualmente il progetto o una delle relative dipendenze.  Probabilmente i riferimenti non sono stati aggiornati.**  
  
 Questo avviso di refactoring è disponibile solo per le operazioni di refactoring che includono l'opzione **Anteprima modifiche riferimento**.  
  
## Refactoring a tolleranza di errore e risultati di verifica  
 Il processo di refactoring offre la funzionalità di tolleranza di errore.  In altre parole, è possibile eseguire un'operazione di refactoring in un progetto che non può essere compilato.  Tuttavia, in questi casi il processo di refactoring potrebbe non aggiornare correttamente i riferimenti ambigui.  
  
 La finestra di dialogo **Risultati verifica** può visualizzare una notifica nel caso in cui il motore di refactoring rilevi errori di compilazione o che, in seguito a un'operazione di refactoring, il riferimento di un codice viene inavvertitamente associato a un elemento diverso da quello a cui era associato in origine \(problema di riassociazione\).  
  
 Per attivare la funzionalità dei risultati di verifica fare clic su **Opzioni** nel menu **Strumenti**.  Nella finestra di dialogo **Opzioni** espandere **Editor di testo**, quindi **C\#**.  Fare clic su **Avanzate** e selezionare la casella di controllo **Verifica risultati del refactoring**.  
  
 Nella finestra di dialogo **Risultati verifica** vengono distinti due tipi di problemi di riassociazione.  
  
### Riferimenti la cui definizione non è più il simbolo rinominato  
 Questo tipo di problema di riassociazione si verifica quando un riferimento non si riferisce più a un simbolo rinominato.  Si consideri il codice di esempio seguente:  
  
```c#  
class Example  
{  
    private int a;  
    public Example(int b)  
    {  
        a = b;  
    }  
}  
```  
  
 Se si utilizza il refactoring per rinominare `a` in `b`, verrà visualizzata questa finestra di dialogo.  Il riferimento alla variabile rinominata `a` è ora associato al parametro passato al costruttore anziché al campo.  
  
### Riferimenti la cui definizione diventa il simbolo rinominato  
 Questo tipo di problema di riassociazione si verifica quando un riferimento che in precedenza non si riferiva al simbolo rinominato ora si riferisce al simbolo rinominato.  Si consideri il codice di esempio seguente:  
  
```c#  
class Example  
{  
    private static void Method(object a) { }  
    private static void OtherMethod(int a) { }  
    static void Main(string[] args)  
    {  
        Method(5);  
    }  
}  
```  
  
 Se si utilizza il refactoring per rinominare `OtherMethod` in `Method`, verrà visualizzata questa finestra di dialogo.  Il riferimento in `Main` si riferisce ora al metodo di overload che accetta un parametro `int` anziché al metodo di overload che accetta un parametro `object`.  
  
## Vedere anche  
 [Using the Visual C\# Development Environment](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [Procedura: ripristinare refactoring di frammenti C\#](../Topic/How%20to:%20Restore%20C%23%20Refactoring%20Snippets.md)