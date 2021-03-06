---
title: Pseudo variabili | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: "35"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b92b070641e4eed47b0094e1611f78cd799e6952
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/11/2017
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Pseudo variabili nel debugger di Visual Studio
Pseudo variabili sono termini usati per visualizzare determinate informazioni in una finestra delle variabili o **controllo immediato** la finestra di dialogo. È possibile immettere una pseudo variabile in modo analogo all'immissione di una variabile normale. Tuttavia, le pseudo variabili non sono variabili e non corrispondono a nomi di variabili presenti nel programma.  
  
## <a name="example"></a>Esempio  
 Si supponga di scrivere un'applicazione in codice nativo e di voler visualizzare il numero di handle allocati nell'applicazione. Nel **espressioni di controllo** finestra, è possibile immettere la seguente pseudo variabile nel **nome** colonna, quindi premere INVIO per valutarla:  
  
```  
$handles  
```  
  
 In codice nativo, è possibile usare le pseudo variabili riportate nella seguente tabella:  
  
|Pseudo variabile|Funzione|  
|--------------------|--------------|  
|`$err`|Visualizza l'ultimo set di valori di errore con la funzione SetLastError. Il valore visualizzato rappresenta ciò che viene restituito dalla funzione GetLastError.<br /><br /> Usare `$err,hr` per vedere il formato decodificato di questo valore. Ad esempio, se l'ultimo errore era 3, `$err,hr` visualizza `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Consente di visualizzare il numero di handle allocati nell'applicazione.|  
|`$vframe`|Consente di visualizzare l'indirizzo dello stack frame corrente.|  
|`$tid`|Consente di visualizzare l'ID del thread corrente.|  
|`$env`|Visualizza il blocco di ambiente nel visualizzatore stringhe.|  
|`$cmdline`|Visualizza la stringa della riga di comando che ha avviato il programma.|  
|`$pid`|Visualizza l'ID del processo.|  
|`$`*registername*<br /><br /> oppure<br /><br /> `@`*registername*|Visualizza il contenuto del registro *registername*.<br /><br /> In genere, è possibile visualizzare il contenuto del registro immettendone semplicemente il nome. È necessario usare questa sintassi unicamente quando il nome del registro esegue l'overload di un nome di variabile. Se il nome del registro è uguale a un nome di variabile nell'ambito corrente, il debugger lo interpreta come nome di variabile. Ovvero quando `$` *registername* o `@` *registername* si rivela utile.|  
|`$clk`|Consente di visualizzare il tempo in cicli di orologio.|  
|`$user`|Consente di visualizzare una struttura con le informazioni sull'account in cui viene eseguita l'applicazione. Per motivi di sicurezza non vengono visualizzate informazioni sulla password.|  
|`$exceptionstack`|Visualizza la traccia dello stack dell'eccezione corrente di Windows Runtime. `$ exceptionstack`funziona solo nelle App UWP e Windows 8.1 o versioni successive. `$ exceptionstack` non è supportata per eccezioni C++ e SHE|  
|`$ReturnValue`|Visualizza il valore restituito di un metodo .NET Framework.|  
  
 In C# e Visual Basic, è possibile usare le pseudo variabili riportate nella seguente tabella:  
  
|Pseudo variabile|Funzione|  
|--------------------|--------------|  
|`$exception`|Visualizza informazioni sull'ultima eccezione. Se non si è verificata alcuna eccezione, la valutazione di `$exception` produce un messaggio di errore.<br /><br /> In Visual c#, solo quando le informazioni sulle eccezioni è disabilitato, `$exception` viene aggiunto automaticamente al **variabili locali** finestra quando si verifica un'eccezione.|  
|`$user`|Consente di visualizzare una struttura con le informazioni sull'account in cui viene eseguita l'applicazione. Per motivi di sicurezza non vengono visualizzate informazioni sulla password.|  
  
 In Visual Basic, è possibile usare le pseudo variabili riportate nella tabella seguente:  
  
|Pseudo variabile|Funzione|  
|--------------------|--------------|  
|`$delete` o `$$delete`|Elimina una variabile implicita creata con la **immediato** finestra. La sintassi è `$delete,` *variabile* o`$delete,` *variabile*`.`|  
|`$objectids` o `$listobjectids`|Visualizza tutti gli ID oggetto attivi come figli dell'espressione specificata. La sintassi è `$objectid,` *espressione* o`$listobjectids,` *espressione*`.`|  
|`$`*N*`#`|Visualizza l'oggetto con ID di oggetto uguale a *N*.|  
|`$dynamic`|Visualizza speciale **visualizzazione dinamica** nodo per un oggetto che implementa il `IDynamicMetaObjectProvider`. Interfaccia. La sintassi è `$dynamic,` *oggetto*. Questa funzionalità si applica solo al codice che usa .NET Framework versione 4.|  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni di controllo e finestre di controllo immediato](../debugger/watch-and-quickwatch-windows.md)   
 [Finestre delle variabili](../debugger/debugger-windows.md)