---
title: "Quando vengono effettuate centinaia di chiamate di una funzione, come &#232; possibile individuare la chiamata che ha avuto esito negativo? | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.functions"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "punti di interruzione, risoluzione dei problemi"
  - "punti di interruzione condizionali"
  - "errori [debugger], ricerca della chiamata di funzione non riuscita"
  - "errori [debugger], chiamate di funzione"
  - "errori [Visual Studio], chiamate di funzione"
  - "errori"
  - "chiamate di funzione, errore"
  - "funzioni [debugger]"
  - "passaggi"
  - "errori di chiamata ai punti di interruzione del percorso"
  - "conteggio ignorato"
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Quando vengono effettuate centinaia di chiamate di una funzione, come &#232; possibile individuare la chiamata che ha avuto esito negativo?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Descrizione del problema  
 Il programma si blocca in corrispondenza di una chiamata a una data funzione, `CnvtV`.  Il programma probabilmente chiama tale funzione un paio di centinaia di volte prima di bloccarsi.  Impostando un punto di interruzione di posizione su `CnvtV`, il programma si arresta a ciascuna chiamata a tale funzione e questo non è auspicabile.  Non sapendo quali condizioni hanno causato l'esito negativo della funzione, non è possibile impostare un punto di interruzione condizionale.  Come è possibile procedere?  
  
## Soluzione  
 È possibile impostare un punto di interruzione sulla funzione specificando nel campo **Passaggi** un valore così alto da non poter essere raggiunto.  In questo caso, poiché si ritiene che la funzione `CnvtV` venga chiamata circa duecento volte, è possibile impostare **Passaggi** su 1000 o su un valore maggiore.  Eseguire quindi il programma e attendere l'arresto della chiamata.  A questo punto, aprire la finestra Punti di interruzione ed esaminare l'elenco dei punti di interruzione.  Il punto di interruzione impostato per `CnvtV` è presente nell'elenco ed è seguito dal conteggio di passaggi e dal numero delle iterazioni rimanenti:  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 A questo punto la funzione con esito negativo risulta essere la chiamata 101.  Se si reimposta il punto di interruzione con un conteggio di passaggi di 101 e si esegue nuovamente il programma, esso si arresterà in corrispondenza della chiamata a `CnvtV` che ha causato il blocco.  
  
## Vedere anche  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)   
 [Setting Breakpoints](http://msdn.microsoft.com/it-it/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)