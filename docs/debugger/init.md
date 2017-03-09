---
title: "Init | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Init
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Prepara il componente integrato nell'applicazione di diagnostiche grafiche per acquisire attivamente e registrare informazioni grafiche nei file di log grafici.  
  
## Sintassi  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### Parametri  
 `vsgLogGetter`  
 Un entità richiamabile, come ad esempio una funzione, un puntatore ad una funziona, una funzione lambda o un oggetto funzione, che accetta come parametri la lunghezza del buffer composto da `wchar_t` e un puntatore al buffer, e restituisce `void`.  Una volta invocato, l'entità richiamabile determina il nome del file che verrà utilizzato per registrare informazioni grafiche, e lo scrive nel buffer specificato prima di ritornare.  
  
## Note  
 La funzione `Init` viene chiamata automaticamente quando viene creata un'istanza della classe `VsgDbg` impostando il parametro `bDefaultInit` del costruttore a `true`; in caso contrario, `Init` deve essere chiamata in modo esplicito prima di poter attivamente acquisire e registrare le informazioni grafiche.  
  
 È possibile finalizzare e chiudere il file di log grafico attivo richiamando `UnInit`, quindi acquisire e registrare più informazioni grafiche in un nuovo file di log grafico chiamando nuovamente `Init`.  È possibile ripetere questo procedimento tutte le volte che si desidera creare diversi file di log grafici indipendenti utilizzando la stessa istanza `VsgDbg`.  
  
## Vedere anche  
 [UnInit](../debugger/init.md)