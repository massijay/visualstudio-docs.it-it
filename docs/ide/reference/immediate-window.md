---
title: "Finestra di controllo immediato | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ImmediateWindow"
helpviewer_keywords: 
  - "valutazione delle espressioni per la fase di progettazione"
  - "Controllo immediato (finestra)"
  - "notifica di eccezioni first-chance"
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Finestra di controllo immediato
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La finestra **Controllo immediato** viene utilizzata per eseguire il debug e valutare espressioni, eseguire istruzioni, stampare valori variabili e così via.  Consente di immettere le espressioni che il linguaggio di sviluppo deve valutare o eseguire durante il debug.  Per visualizzare la finestra **Controllo immediato**, aprire un progetto da modificare e selezionare **Espressioni di controllo** dal menu **Debug**, quindi selezionare **Controllo immediato** o digitare CTRL\+ALT\+I.  
  
 Da questa finestra è possibile eseguire singoli comandi di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Tra i comandi disponibili è compreso `EvaluateStatement` che consente di assegnare dei valori alle variabili.  Anche la finestra **Controllo immediato** supporta IntelliSense.  
  
## Visualizzazione dei valori delle variabili  
 Questa finestra è particolarmente utile per l'esecuzione del debug di un'applicazione.  Ad esempio, per verificare il valore di una variabile `varA`, è possibile utilizzare [Comando Print](../../ide/reference/print-command.md):  
  
```  
>Debug.Print varA  
```  
  
 Il punto interrogativo \(?\) è un alias per `Debug.Print`, quindi questo comando può essere scritto anche nel seguente modo:  
  
```  
>? varA  
```  
  
 Entrambe le versioni del comando restituiscono il valore della variabile `varA`.  
  
> [!NOTE]
>  Per eseguire un comando di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nella finestra **Controllo immediato**, è necessario inserire, prima del comando, il segno di maggiore \(\>\).  Per immettere più comandi, aprire la finestra **Comando**.  
  
## Valutazione delle espressioni in fase di progettazione  
 È possibile utilizzare la finestra **Controllo immediato** per eseguire una funzione o una subroutine in fase di progettazione.  
  
#### Per eseguire una funzione in fase di progettazione  
  
1.  Copiare il codice seguente in un'applicazione console di [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MyFunction(5)  
        End Sub  
  
        Function MyFunction(ByVal input as Integer) As Integer  
            Return input * 2  
        End Function  
  
    End Module  
    ```  
  
2.  Scegliere **Finestre** dal menu **Debug**, quindi fare clic su **Controllo immediato**.  
  
3.  Digitare `?MyFunction(2)` nella finestra **Controllo immediato** e premere INVIO.  
  
     Nella finestra **Controllo immediato** verrà eseguito `MyFunction` e verrà visualizzato `4`.  
  
 Se la funzione o subroutine contiene un punto di interruzione, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] determinerà l'interruzione dell'esecuzione nel punto appropriato.  È quindi possibile utilizzare le finestre del debugger per esaminare lo stato del programma.  Per ulteriori informazioni, vedere [Procedura dettagliata: debug in fase di progettazione](../../debugger/walkthrough-debugging-at-design-time.md).  
  
 Non è possibile utilizzare la valutazione di espressioni in fase di progettazione nei tipi di progetto che richiedono l'avvio di un ambiente di esecuzione, compresi i progetti [!INCLUDE[trprVSTOshort](../../ide/reference/includes/trprvstoshort_md.md)], i progetti Web, i progetti Smart Device e i progetti SQL.  
  
### Valutazione di espressioni in fase di progettazione nelle soluzioni multiprogetto  
 Per determinare il contesto per la valutazione di espressioni in fase di progettazione, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fa riferimento al progetto selezionato in Esplora soluzioni.  Se in Esplora soluzioni non è selezionato alcun progetto, in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si tenta di valutare la funzione utilizzando il progetto di avvio.  Se non è possibile valutare la funzione nel contesto corrente, verrà visualizzato un messaggio di errore.  Se si sta tentando di valutare una funzione in un progetto che non è il progetto di avvio per la soluzione e viene segnalato un errore, provare a selezionare il progetto in Esplora soluzioni e tentare nuovamente la valutazione.  
  
## Immissione di comandi  
 Aggiungere il segno "maggiore di" \(\>\) quando si eseguono i comandi di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nella finestra di **controllo immediato**.  Utilizzare i tasti FRECCIA GIÙ e FRECCIA SU per scorrere i comandi precedentemente immessi.  
  
|Task|Soluzione|Esempio|  
|----------|---------------|-------------|  
|Valutare un'espressione.|Inserire l'espressione preceduta da un punto interrogativo \(?\).|`? a+b`|  
|Attivare temporaneamente la modalità comando mentre si è in modalità immediata per eseguire un singolo comando.|Inserire il comando preceduto da un segno di maggiore \(\>\).|`>alias`|  
|Aprire la finestra Comando.|Immettere `cmd` nella finestra, anteponendo il segno di maggiore \(\>\).|`>cmd`|  
|Tornare alla finestra Controllo immediato.|Immettere `immed` nella finestra, senza il segno di maggiore \(\>\).|`immed`|  
  
## Modalità indicatore  
 Facendo clic su una qualsiasi riga precedente nella finestra **Controllo immediato**, si passa automaticamente in modalità Indicatore.  Questa modalità consente di selezionare, modificare e copiare il testo dei comandi precedenti come in un qualsiasi editor di testo e incollarlo nella riga corrente.  
  
## Il segno di uguale \(\=\)  
 La finestra utilizzata per immettere il comando `EvaluateStatement` determina se il segno uguale \(\=\) deve essere interpretato come operatore di confronto o operatore di assegnazione.  
  
 Nella finestra di **Controllo immediato**, il segno uguale \(\=\) viene interpretato come operatore di assegnazione.  Ad esempio, il comando  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 assegna alla variabile `varA` il valore della variabile `varB`.  
  
 Nella finestra **Comando**, il segno uguale invece \(\=\) viene interpretato come operatore di confronto.  Non è possibile utilizzare gli operatori di assegnazione nella finestra **Comando**.  Pertanto, se, ad esempio, i valori delle variabili `varA` e `varB` sono diversi, il comando  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 restituisce il valore `False`.  
  
## Notifiche di eccezioni first\-chance  
 In alcune configurazioni, le notifiche di eccezioni first\-chance vengono visualizzate nella finestra **Controllo immediato**.  
  
#### Per attivare e disattivare le notifiche di eccezioni first\-chance nella finestra di controllo immediato  
  
1.  Scegliere **Altre finestre** dal menu **Visualizza**, quindi fare clic su **Output**.  
  
2.  Fare clic con il pulsante destro del mouse nell'area di testo della finestra **Output** e selezionare o deselezionare **Messaggi di eccezione**.  
  
## Vedere anche  
 [Spostarsi nel codice con il Debugger](../../debugger/navigating-through-code-with-the-debugger.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Debug in Visual Studio](../../debugger/debugging-in-visual-studio.md)   
 [Nozioni di base sul debugger](../../debugger/debugger-basics.md)   
 [Procedura dettagliata: debug in fase di progettazione](../../debugger/walkthrough-debugging-at-design-time.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)   
 [Utilizzo delle espressioni regolari in Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)