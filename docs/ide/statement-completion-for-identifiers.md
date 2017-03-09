---
title: "Completamento delle istruzioni per gli identificativi | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense [JavaScript], completamento delle istruzioni"
  - "completamento delle istruzioni, IntelliSense per JavaScript"
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Completamento delle istruzioni per gli identificativi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

JavaScript non consente di esplicito dei dati per le dichiarazioni di variabili.  Di conseguenza, IntelliSense non può sempre fornire elenchi di completamento per gli oggetti.  Ciò può verificarsi in diverse situazioni.  Di seguito sono alcuni operatori logici più comuni.  
  
-   Un parametro dichiarato, ma esso non è stato chiamato altrove nel documento attivo, come illustrato nell'esempio riportato di seguito.  
  
    ```javascript  
    function illuminate(light) {  
             light.  // Accurate statement completion is not available   
                     // unless illuminate is called elsewhere with a   
                     // parameter that has a value. If it is called only  
                     // in a function that is a sibling to   
                     // illuminate(light) in the call hierarchy, the   
                     // IntelliSense engine also cannot determine the   
                     // parameter type.  
         }  
  
    // Sibling function. No statement completion for light   
    // object in preceding code.  
    function lightLamp() {  
        var x = illuminate(1);  
    }  
  
    // Uncomment the next line to obtain statement completion for  
    // light object in preceding code.  
    // var x = illuminate(1);  
    ```  
  
-   Un oggetto è una funzione che viene chiamata in risposta a un evento.  In fase di progettazione, il motore IntelliSense Impossibile determinare il tipo degli oggetti utilizzati in questa situazione.  
  
     Se il modulo di IntelliSense possibile determinare che l'evento deve essere chiamato, in genere tramite l'utilizzo di `addEventListener` per l'evento nel documento attivo, vengono fornite informazioni di IntelliSense più accurate.  
  
 Quando IntelliSense è in grado di identificare un oggetto, il motore IntelliSense compila l'elenco di completamento con entità denominate o identificatori, che sono presenti nel documento attivo.  Quando l'elenco di completamento contiene questi identificatori, informazioni icone vengono visualizzate accanto a essi.  Inoltre, una descrizione comandi per ciascun identificatore indica che l'espressione è sconosciuto.  La seguente illustrazione mostra istruzione le opzioni di completamento per un oggetto di tipo `light` che non può essere identificato perché l'oggetto e le relative proprietà sono indefinite.  Tuttavia, la `intensity` proprietà è disponibile nell'elenco identificatore perché è stato utilizzato nel `illuminate` funzione.  
  
 **Opzioni di completamento per un oggetto che non possono essere identificati**  
  
 ![JavaScript IntelliSense per identificatori](../ide/media/js_intellisense_identifiers.png "js\_intellisense\_identifiers")  
  
 È possibile ignorare l'elenco di completamento di un oggetto utilizzando i commenti di documentazione XML o funzioni di estensibilità JavaScript IntelliSense.  Utilizzo di queste funzionalità, è possibile fornire informazioni di tipo più informazioni descrittive e IntelliSense quando non in caso contrario è disponibile.  Per ulteriori informazioni, vedere [Estensione di IntelliSense in JavaScript](../ide/extending-javascript-intellisense.md) e [Procedura: creare i commenti della documentazione XLM in JavaScript](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).  
  
## Vedere anche  
 [IntelliSense per JavaScript](../ide/javascript-intellisense.md)