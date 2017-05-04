---
title: "Copia, passaggio e confronto di dati (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "matrici [Visual Studio], copia di dati"
  - "matrici [Visual Studio], passaggio di valori"
  - "matrici [Visual Studio], impostazione dei tipi di dati"
  - "argomento ByRef"
  - "argomento ByVal"
  - "funzione (parametri)"
  - "funzione (parametri), informazioni"
  - "stringhe (confronto)"
  - "stringhe (confronto), verifica dei dati"
ms.assetid: fbccd877-7249-45d4-bd9f-6bcd8ba94a6b
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Copia, passaggio e confronto di dati (JavaScript)
In [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] la modalità di gestione dei dati dipende dal tipo di dati.  
  
## Per valore e per riferimento  
 I numeri e i valori booleani \(**true** e **false**\) vengono copiati, passati e confrontati *per valore*.  Quando effettui la copia o il passaggio per valore, allochi uno spazio nella memoria del computer in cui copi il valore dell'originale.  Le eventuali modifiche all'originale non hanno alcun effetto sulla copia \(e viceversa\). Valore originale e copia sono infatti due entità distinte.  
  
 Gli oggetti, le matrici e le funzioni sono copiati, passati e confrontati *per riferimento*.  Quando effettui la copia o il passaggio per riferimento, essenzialmente crei un puntatore all'elemento originale e lo utilizzi come se fosse una copia.  Le eventuali modifiche all'originale vengono riportate anche nella copia e viceversa.  In effetti esiste una sola entità, in quanto la "copia" non è che un altro riferimento ai dati.  
  
 Quando si esegue un confronto per riferimento, le due variabili devono fare riferimento esattamente alla stessa entità. Solo così il confronto verrà eseguito correttamente.  Due oggetti **Array** distinti, ad esempio, risulteranno sempre diversi dopo il confronto, pur contenendo gli stessi elementi.  Affinché il confronto abbia esito positivo, una delle variabili deve costituire un riferimento dell'altra.  Per controllare se due matrici contengono gli stessi elementi, confrontare i risultati del metodo **toString\(\)**.  
  
 Infine, le stringhe vengono copiate e passate per riferimento, ma vengono confrontate per valore.  Due oggetti **String** creati con **new** String\("something"\) vengono confrontati per riferimento. Se uno o entrambi i valori è un valore stringa, questi vengono confrontati per valore.  
  
> [!NOTE]
>  A causa della struttura dei set di caratteri ASCII e ANSI, se ordinate in sequenza, le lettere maiuscole precedono le lettere minuscole.  Per questo motivo in un confronto, "Zoo" risulterebbe *minore* di "aardvark". Se si desidera eseguire un confronto senza distinzione tra maiuscole e minuscole, è possibile utilizzare **toUpperCase\(\)** o **toLowerCase\(\)** per entrambe le stringhe.  
  
## Passaggio dei parametri alle funzioni  
 Quando passi un parametro a una funzione per valore, crei una copia distinta del parametro che esiste soltanto nell'ambito della funzione.  Benché gli oggetti e le matrici vengano passati per riferimento, se li sovrascrivi direttamente con un nuovo valore nella funzione, tale valore non verrà riflesso all'esterno della funzione.  Solo le modifiche alle proprietà degli oggetti o agli elementi delle matrici saranno visibili all'esterno della funzione.  
  
 Ad esempio \(utilizzando il modello a oggetti di Internet Explorer\):  
  
```javascript  
// This clobbers (over-writes) its parameter, so the change  
// is not reflected in the calling code.  
function Clobber(param)   
{  
    // clobber the parameter; this will not be seen in   
    // the calling code  
    param = new Object();  
    param.message = "This will not work";  
}  
  
// This modifies a property of the parameter, which  
// can be seen in the calling code.  
function Update(param)  
{  
    // Modify the property of the object; this will be seen  
    // in the calling code.  
    param.message = "I was changed";  
}  
  
// Create an object, and give it a property.  
var obj = new Object();  
obj.message = "This is the original";  
  
// Call Clobber, and print obj.message. Note that it hasn't changed.  
Clobber(obj);  
window.alert(obj.message); // Still displays "This is the original".  
  
// Call Update, and print obj.message. Note that is has changed.  
Update(obj);  
window.alert(obj.message); // Displays "I was changed".  
```  
  
## Test dei dati  
 Quando esegui un test per valore, metti a confronto due elementi distinti per verificare se sono uguali.  Tale confronto viene in genere eseguito byte per byte.  Quando esegui un test per riferimento, verifichi se due elementi sono puntatori a un singolo elemento originale.  In caso affermativo, verranno considerati uguali. In caso contrario, verranno considerati diversi, anche se includono gli stessi valori byte per byte.  
  
 Se effettui la copia o il passaggio delle stringhe per riferimento, potrai risparmiare memoria. Poiché però non puoi modificare le stringhe una volta create, diventa possibile confrontarle per valore.  Ciò ti consente di testare se due stringhe hanno lo stesso contenuto anche se una è stata generata separatamente dall'altra.  
  
## Vedere anche  
 [Calcolo di date e ore \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)