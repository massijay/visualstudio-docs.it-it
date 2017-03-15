---
title: "Refactoring di ridenominazione (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.rename"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#], Rinomina"
  - "Refactoring di ridenominazione (C#)"
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
caps.handback.revision: 45
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Refactoring di ridenominazione (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Rinomina** è una funzionalità di refactoring presente nell'ambiente di sviluppo integrato \(IDE\) di Visual Studio che consente rinominare facilmente gli identificatori per i simboli del codice ad esempio campi, variabili locali, metodi, spazi dei nomi, proprietà e tipi.  È possibile utilizzare **Rinomina** per modificare i nomi in commenti e stringhe, oltre alle dichiarazioni e alle chiamate di un identificatore.  
  
> [!NOTE]
>  Quando si utilizza Controllo del codice sorgente per Visual Studio, è opportuno ottenere la versione più recente delle origini prima di eseguire il refactoring di ridenominazione.  
  
 Il refactoring di ridenominazione è disponibile tramite le seguenti funzionalità di Visual Studio:  
  
|Funzionalità|Comportamento di Refactoring nell'IDE|  
|------------------|-------------------------------------------|  
|Editor di codice|Nell'editor del codice il refactoring di ridenominazione è disponibile quando si posiziona il cursore su determinati tipi di simboli di codice.  Quando il cursore è posizionato in questa sede, è possibile richiamare il comando **Rinomina** digitando la scelta rapida \(CTRL \+ R, CTRL \+ R, oppure scegliendo il comando **Rinomina** da uno smart tag, dal menu di scelta rapida, o dal menu **Refactoring**.|  
|Visualizzazione classi|Quando si seleziona un identificatore in Visualizzazione classi, il refactoring di ridenominazione è disponibile dal menu di scelta rapida e dal menu **Effettua refactoring**.|  
|Visualizzatore oggetti|Quando si seleziona un identificatore in Visualizzatore oggetti, il refactoring di ridenominazione è disponibile solo dal menu **Effettua refactoring**.|  
|Griglia delle proprietà di Progettazione Windows Form|Se si modifica il nome di un controllo in **Griglia delle proprietà** di Progettazione Windows Form, verrà avviata un'operazione di ridenominazione per tale controllo.  La finestra di dialogo **Rinomina** non verrà visualizzata.|  
|Esplora soluzioni|In **Esplora soluzioni** è disponibile un comando **Rinomina** nel menu di scelta rapida.  Se il file di origine selezionato contiene una classe il cui nome corrisponde al nome del file, è possibile utilizzare questo comando per rinominare il file di origine ed eseguire contemporaneamente il refactoring di ridenominazione.<br /><br /> Se, ad esempio, si crea un'applicazione basata su Windows predefinita, quindi si rinomina Form1.cs in TestForm.cs, il nome del file di origine Form1.cs verrà modificato in TestForm.cs e la classe Form1 e tutti i riferimenti a essa verranno rinominati in TestForm. **Note:**  Il comando **Annulla** \(CTRL\+Z\) può essere utilizzato solo per annullare il refactoring di ridenominazione all'interno del codice e non per ripristinare il nome originale del file. <br /><br /> Se il file di origine selezionato non contiene una classe il cui nome corrisponde al nome del file, il comando **Rinomina** in **Esplora soluzioni** consentirà solo di rinominare il file di origine e non di eseguire il refactoring di ridenominazione.|  
  
## Operazioni di ridenominazione  
 Quando si esegue il comando **Rinomina**, il motore di refactoring effettua un'operazione di ridenominazione specifica per ciascun simbolo di codice, come descritto nella tabella seguente.  
  
|Simbolo di codice|Operazione di ridenominazione|  
|-----------------------|-----------------------------------|  
|Campo|Consente di applicare il nuovo nome alla dichiarazione e agli utilizzi del campo.|  
|Variabile locale|La dichiarazione e gli utilizzi della variabile vengono modificati nel nuovo nome.|  
|Metodo|Consente di applicare il nuovo nome al metodo e a tutti i riferimenti a tale metodo. **Note:**  Quando si rinomina un metodo di estensione, l'operazione di ridenominazione viene propagata a tutte le istanze del metodo incluse nell'ambito, indipendentemente dal fatto che il metodo di estensione venga utilizzato come un metodo statico o come metodo di un'istanza.  Per ulteriori informazioni, vedere [Metodi di estensione](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods).|  
|Spazio dei nomi|Consente di applicare il nuovo nome allo spazio dei nomi nella dichiarazione, in tutte le istruzioni `using` e in tutti i nomi completi. **Note:**  Quando si rinomina uno spazio dei nomi, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene aggiornata anche la proprietà **Spazio dei nomi predefinito** nella pagina dell'applicazione di **Progettazione progetti**.  Questa proprietà non può essere reimpostata selezionando **Annulla** dal menu **Modifica**.  Per reimpostare il valore della proprietà **Default Namespace**, è necessario modificare la proprietà in **Progettazione progetti**.  Per ulteriori informazioni, vedere [Pagina dell'applicazione](../ide/reference/application-page-project-designer-csharp.md).|  
|Proprietà|Consente di applicare il nuovo nome alla dichiarazione e agli utilizzi della proprietà.|  
|Type|Consente di applicare il nuovo nome a tutte le dichiarazioni e a tutti gli utilizzi del tipo, inclusi costruttori e distruttori.  Per i tipi parziali, l'operazione di ridenominazione viene propagata a tutte le parti.|  
  
#### Per rinominare un identificatore  
  
1.  Creare un'applicazione console denominata `RenameIdentifier` quindi sostituire `Program` con il codice riportato di seguito  
  
    ```c#  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Posizionare il cursore su `MethodB`, nella dichiarazione di metodo o nella chiamata di metodo.  
  
3.  Scegliere **Rinomina** dal menu **Effettua refactoring**.  Viene visualizzata la finestra di dialogo **Rinomina**.  
  
     È inoltre possibile fare clic con il pulsante destro del mouse sul cursore, scegliere **Effettua refactoring** dal menu di scelta rapida, quindi fare clic su **Rinomina** per visualizzare la finestra di dialogo **Rinomina**.  
  
4.  Nella casella **Nuovo nome** digitare `MethodC`.  
  
5.  Selezionare la casella di controllo **Cerca in commenti**.  
  
6.  Scegliere **OK**.  
  
7.  Nella finestra di dialogo **Anteprima modifiche** fare clic su **Applica**.  
  
#### Per rinominare un identificatore utilizzando gli smart tag  
  
1.  Creare un'applicazione console denominata `RenameIdentifier` quindi sostituire `Program` con il codice riportato di seguito  
  
    ```c#  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Nella dichiarazione relativa a `MethodB` digitare o premere Backspace sull'identificatore del metodo.  Verrà visualizzato un prompt di smart tag sotto l'identificatore.  
  
    > [!NOTE]
    >  Alla dichiarazione di un identificatore, è possibile richiamare soltanto il refactoring di ridenominazione utilizzando gli smart tag.  
  
3.  Premere i tasti di scelta rapida MAIUSC\+ALT\+F10, quindi premere la freccia GIÙ per visualizzare il menu degli smart tag.  
  
     In alternativa  
  
     Spostare il puntatore del mouse sul prompt di smart tag per visualizzare lo smart tag.  Spostare quindi il puntatore del mouse sullo smart tag e fare clic sulla freccia in giù per visualizzare il menu degli smart tag.  
  
4.  Selezionare la voce di menu **Rinomina '**\<identificatore1\>**' in '**\<identificatore2\>**'** per richiamare il refactoring di ridenominazione senza visualizzare in anteprima le modifiche apportate al codice.  Tutti i riferimenti a \<identificatore1\> verranno aggiornati automaticamente in \<identificatore2\>.  
  
     In alternativa  
  
     Selezionare la voce di menu **Rinomina con anteprima** per richiamare il refactoring di ridenominazione visualizzando in anteprima le modifiche apportate al codice.  Verrà visualizzata la finestra di dialogo **Anteprima modifiche**.  
  
## Note  
  
## Ridenominazione di membri implementati o sottoposti a override  
 Quando si utilizza il comando **Rinomina** per un membro che esegue l'override o implementa altri membri oppure è sottoposto a override o è implementato da membri in altri tipi, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene visualizzata una finestra di dialogo in cui è indicato che l'operazione di ridenominazione comporterà l'esecuzione di aggiornamenti a cascata.  Se si sceglie **Continua**, il motore di refactoring cerca e rinomina in modo ricorsivo tutti i membri nei tipi di base e derivati che hanno rapporti di implementazione\/override con il membro rinominato.  
  
 Nell'esempio di codice seguente sono inclusi membri con rapporti di implementazione\/override.  
  
 [!code-cs[CsUsingCsIDERefactor#1](../csharp-ide/codesnippet/CSharp/rename-refactoring-csharp_1.cs)]  
  
 Nell'esempio precedente la ridenominazione di `C.Method()` comporta la ridenominazione anche di `Ibase.Method()` perché `C.Method()` implementa `Ibase.Method()`.  Quindi, il motore di refactoring rileva in modo ricorsivo che `Ibase.Method()` è implementato da `Derived.Method()` e rinomina `Derived.Method()`.  Il motore di refactoring non rinomina `Base.Method()` perché `Derived.Method()` non esegue l'override di `Base.Method()`.  Il motore di refactoring si ferma a questo punto, a meno che non sia stata selezionata l'opzione **Rinomina overload** nella finestra di dialogo **Rinomina**.  
  
 Se **Rinomina overload** è selezionata, il motore di refactoring rinomina `Derived.Method(int i)` perché esegue l'overload di `Derived.Method()`, `Base.Method(int i)` perché è sottoposto a override da parte di `Derived.Method(int i)` e `Base.Method()` perché è un overload di `Base.Method(int i)`.  
  
> [!NOTE]
>  Quando si rinomina un membro definito in un assembly a cui si fa riferimento, una finestra di dialogo informa che l'operazione di ridenominazione causerà errori di compilazione.  
  
## Ridenominazione di proprietà di tipi anonimi  
 Quando si rinomina una proprietà nei tipi anonimi, l'operazione di ridenominazione verrà propagata alle proprietà in altri tipi anonimi con le stesse proprietà.  Questo comportamento è illustrato nell'esempio seguente:  
  
```c#  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 Nel codice precedente, la ridenominazione dell'`ID` comporterà la modifica dell'`ID` in entrambe le istruzioni perché hanno lo stesso tipo anonimo sottostante.  
  
```c#  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 Nel codice precedente, la ridenominazione di `ID` comporterà la ridenominazione solo di un'istanza di `ID` perché `companyIDs` e `orderIDs` non hanno le stesse proprietà.  
  
## Vedere anche  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)   
 [Tipi anonimi](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)