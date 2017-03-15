---
title: "Pseudo variabili | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debug [Visual Studio], pseudo variabili"
  - "pseudo variabili"
  - "Espressioni di controllo (finestra), pseudo variabili"
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Pseudo variabili
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le pseudo variabili sono termini usati per visualizzare determinate informazioni in una finestra delle variabili o nella finestra di dialogo **Controllo immediato**.  È possibile immettere una pseudo variabile in modo analogo all'immissione di una variabile normale.  Tuttavia, le pseudo variabili non sono variabili e non corrispondono a nomi di variabili presenti nel programma.  
  
## Esempio  
 Si supponga di scrivere un'applicazione in codice nativo e di voler visualizzare il numero di handle allocati nell'applicazione.  Nella finestra **Espressioni di controllo**, è possibile immettere la seguente pseudo variabile nella colonna **Nome**, quindi premere Invio per valutarla:  
  
```  
$handles  
```  
  
 In codice nativo, è possibile usare le pseudo variabili riportate nella seguente tabella:  
  
|Pseudo variabile|Funzione|  
|----------------------|--------------|  
|`$err`|Visualizza l'ultimo set di valori di errore con la funzione SetLastError.  Il valore visualizzato rappresenta ciò che viene restituito dalla funzione GetLastError.<br /><br /> Usare `$err,hr` per vedere il formato decodificato di questo valore.  Ad esempio, se l'ultimo errore era 3, `$err,hr` visualizza `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Consente di visualizzare il numero di handle allocati nell'applicazione.|  
|`$vframe`|Consente di visualizzare l'indirizzo dello stack frame corrente.|  
|`$tid`|Consente di visualizzare l'ID del thread corrente.|  
|`$env`|Visualizza il blocco di ambiente nel visualizzatore stringhe.|  
|`$cmdline`|Visualizza la stringa della riga di comando che ha avviato il programma.|  
|`$pid`|Visualizza l'ID del processo.|  
|`$` *registername*<br /><br /> oppure<br /><br /> `@` *registername*|Visualizza i contenuti del registro *registername*.<br /><br /> In genere, è possibile visualizzare il contenuto del registro immettendone semplicemente il nome.  È necessario usare questa sintassi unicamente quando il nome del registro esegue l'overload di un nome di variabile.  Se il nome del registro è uguale a un nome di variabile nell'ambito corrente, il debugger lo interpreta come nome di variabile.  In questo caso, è opportuno usare `$`*registername* o `@`*registername*.|  
|`$clk`|Consente di visualizzare il tempo in cicli di orologio.|  
|`$user`|Consente di visualizzare una struttura con le informazioni sull'account in cui viene eseguita l'applicazione.  Per motivi di sicurezza non vengono visualizzate informazioni sulla password.|  
|`$exceptionstack`|Visualizza la traccia dello stack dell'eccezione corrente di Windows Runtime.  `$ exceptionstack` funziona solo nelle applicazioni di Windows Store in esecuzione su Windows 8.1 o versioni successive.  `$ exceptionstack` non è supportata per eccezioni C\+\+ e SHE|  
|`$ReturnValue`|Visualizza il valore restituito di un metodo .NET Framework.  Vedere [Esaminare i valori restituiti dalle chiamate di metodo](../Topic/Examine%20return%20values%20of%20method%20calls.md)|  
  
 In C\# e Visual Basic, è possibile usare le pseudo variabili riportate nella seguente tabella:  
  
|Pseudo variabile|Funzione|  
|----------------------|--------------|  
|`$exception`|Visualizza informazioni sull'ultima eccezione.  Se non si è verificata alcuna eccezione, la valutazione di `$exception` produce un messaggio di errore.<br /><br /> Solo in Visual C\#, quando le Informazioni sulle eccezioni sono disattivate, `$exception` viene automaticamente aggiunto alla finestra **Variabili locali** quando si verifica un'eccezione.|  
|`$user`|Consente di visualizzare una struttura con le informazioni sull'account in cui viene eseguita l'applicazione.  Per motivi di sicurezza non vengono visualizzate informazioni sulla password.|  
  
 In Visual Basic, è possibile usare le pseudo variabili riportate nella tabella seguente:  
  
|Pseudo variabile|Funzione|  
|----------------------|--------------|  
|`$delete` oppure `$$delete`|Elimina una variabile implicita creata nella finestra **Immediata**.  La sintassi è `$delete,` *variable* o `$delete,` *variable*`.`|  
|`$objectids` oppure `$listobjectids`|Visualizza tutti gli ID oggetto attivi come figli dell'espressione specificata.  La sintassi è `$objectid,` *expression* o `$listobjectids,` *expression*`.`|  
|`$` *N* `#`|Visualizza l'oggetto con ID dell'oggetto uguale a *N*.|  
|`$dynamic`|Visualizza il nodo **Visualizzazione dinamica** speciale per un oggetto che implementa `IDynamicMetaObjectProvider`.  Interfaccia.  La sintassi è `$dynamic,` *object*.  Questa funzionalità si applica solo al codice che usa .NET Framework versione 4.  Vedere [Visualizzazione dinamica](../Topic/Dynamic%20View.md).|  
  
## Vedere anche  
 [Finestre Espressioni di controllo e Controllo immediato](../debugger/watch-and-quickwatch-windows.md)   
 [Finestre delle variabili](../Topic/Variable%20Windows.md)