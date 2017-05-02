---
title: "Considerazioni sull&#39;utilizzo dell&#39;API Windows Runtime | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, API di Windows Runtime"
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Considerazioni sull&#39;utilizzo dell&#39;API Windows Runtime
È possibile utilizzare quasi tutti gli elementi dell'API di Windows Runtime in JavaScript.  Tuttavia, è necessario tenere presenti alcuni aspetti della rappresentazione JavaScript degli elementi di Windows Runtime.  
  
> [!IMPORTANT]
>  Per informazioni sulla creazione di componenti Windows Runtime, in C\+\+, C\# o Visual Basic e sul relativo utilizzo in JavaScript, vedere [Creazione di componenti Windows Runtime](../Topic/Creating%20Windows%20Runtime%20Components.md).  
  
## Casi speciali nella rappresentazione JavaScript dei tipi di Windows Runtime  
  
-   Stringhe: una stringa non inizializzata viene passata a un metodo di Windows Runtime come stringa "undefined" e una stringa impostata su `null` viene passata come stringa "null". Questo avviene ogni volta che un valore `undefined` o `null` viene assegnato a una stringa. Prima di passare una stringa a un metodo di Windows Runtime, è necessario inizializzarla come stringa vuota \(""\).  
  
-   Interfacce: non è possibile implementare un'interfaccia di Windows Runtime in JavaScript.  
  
-   Matrici: le matrici di Windows Runtime non sono ridimensionabili, pertanto i metodi che ridimensionano le matrici in JavaScript non funzionano sulle matrici di Windows Runtime.  
  
-   Matrici: se si passa un valore di matrice JavaScript a un metodo di Windows Runtime, la matrice viene copiata.  Il metodo di Windows Runtime non è in grado di modificare la matrice o i relativi membri e restituirla all'applicazione JavaScript.  Tuttavia, è possibile utilizzare le matrici tipizzate, \(ad esempio [Oggetto Int32Array](../javascript/reference/int32array-object.md)\), che non vengono copiate.  
  
-   Strutture: le strutture di Windows Runtime sono oggetti in JavaScript.  Se si desidera passare una struttura di Windows Runtime a un metodo di Windows Runtime, non creare un'istanza della struttura con la parola chiave `new`.  Al contrario, creare un oggetto e aggiungere i membri appropriati e i relativi valori.  Per i nomi dei membri deve essere utilizzata la convenzione camel: `SomeStruct.firstMember`.  
  
-   Oggetti: gli oggetti JavaScript non corrispondono agli oggetti di codice gestito \(`System.Object`\).  Non è possibile passare un oggetto JavaScript a un metodo di Windows Runtime che richiede `System.Object`.  
  
-   Identità dell'oggetto: nella maggior parte dei casi, gli oggetti scambiati tra Windows Runtime e JavaScript non cambiano.  Il motore JavaScript gestisce una mappa di oggetti noti.  Un oggetto restituito da Windows Runtime viene confrontato con la mappa e se non esiste, viene creato un nuovo oggetto.  La stessa procedura viene seguita per gli oggetti che rappresentano le interfacce restituite dai metodi di Windows Runtime.  Esistono due tipi di eccezioni:  
  
    -   Gli oggetti restituiti da una chiamata di Windows Runtime e ai quali vengono aggiunte nuove proprietà \(expando\) non mantengono le nuove proprietà quando vengono passati nuovamente a Windows Runtime.  Tuttavia, quando vengono restituiti all'applicazione JavaScript, perché vengono associati all'oggetto esistente, l'oggetto restituito dispone delle proprietà expando.  
  
    -   Strutture e delegati in Windows Runtime non possono essere identificati come identici alle strutture o ai delegati utilizzati in precedenza.  Ogni volta in cui una struttura o un delegato viene restituito, ottiene un nuovo riferimento.  
  
-   Conflitti di nomi: più interfacce di Windows Runtime possono avere membri con gli stessi nomi.  Se vengono combinati in un singolo oggetto JavaScript \(che può essere una rappresentazione di una classe di runtime o un'interfaccia\), i membri sono rappresentati con nomi completi.  È possibile chiamare questi membri utilizzando la seguente sintassi: `Class["MemberName"](parameter)`.  
  
     Nel codice riportato di seguito due interfacce hanno un metodo Draw e una classe di runtime implementa entrambe le interfacce.  
  
    ```cpp#  
    namespace CollisionExample {  
        interface InterfaceA  
        {  
            HRESULT Draw([in] Int32 a);  
        }  
        interface InterfaceB  
        {  
            HRESULT Draw([in] HString a);  
        }  
        runtimeclass ExampleObject {  
          interface InterfaceA  
          interface InterfaceB  
        }  
    }  
    ```  
  
     Di seguito viene illustrato come è possibile chiamare il codice precedente in JavaScript.  
  
    ```javascript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   Parametri `Out`: se un metodo di Windows Runtime ha più parametri `out`, in JavaScript il metodo dispone di un oggetto JavaScript come valore restituito e l'oggetto dispone di proprietà che corrispondono al parametro `out`.  Si consideri ad esempio la firma di Windows Runtime in C\+\+ riportata di seguito.  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     La versione JavaScript di questa firma è:  
  
    ```javascript  
    var returnValue = exampleMethod();  
  
    ```  
  
     In questo esempio, `returnValue` è un oggetto JavaScript con due campi: `first` e `second`.  
  
-   Membri statici: Windows Runtime definisce sia i membri statici che i membri di istanza.  In JavaScript, i membri statici vengono aggiunti all'oggetto associato alla classe o all'interfaccia di Windows Runtime.  
  
    ```javascript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 Per ulteriori informazioni sulla rappresentazione JavaScript dei tipi di base di Windows Runtime, vedere [Rappresentazione JavaScript dei tipi di Windows Runtime](../jswinrt/javascript-representation-of-windows-runtime-types.md).