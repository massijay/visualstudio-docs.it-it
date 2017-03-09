---
title: "Classe VsgDbg | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Classe VsgDbg
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Rappresenta un'interfaccia per controllare a livello di codice il componente di diagnostica di grafica integrato nell'applicazione.  
  
## Sintassi  
  
```cpp  
class VsgDbg;  
```  
  
## Membri  
 La classe `VsgDbg` supporta i membri seguenti:  
  
### Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[VsgDbg::VsgDbg \(costruttore\)](../debugger/vsgdbg-vsgdbg-constructor.md)|Costruisce un'istanza della classe `VsgDbg` e facoltativamente prepara il componente di diagnostica grafica integrato nell'applicazione ad acquisire e registrare attivamente le informazioni grafiche.|  
|[VsgDbg::~VsgDbg \(distruttore\)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|Distrugge un'istanza della classe `VsgDbg`.|  
  
### Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[AddMessage](../debugger/addmessage.md)|Aggiunge un messaggio personalizzato alla diagnostica grafica HUD \(Head\-Up Display\).|  
|[BeginCapture](../debugger/begincapture.md)|Inizia un intervallo di acquisizione che termina con `EndCapture`.|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|Acquisisce il resto del frame corrente nel file di log degli elementi grafici.|  
|[Copia \(acquisizione a livello di codice\)](../debugger/copy-programmatic-capture.md)|Copiare il contenuto dei log grafici attivi \(.vsglog\) in un nuovo file.|  
|[EndCapture](../debugger/endcapture.md)|Termina un intervallo di acquisizione che è stato avviato con `BeginCapture`.|  
|[Init](../debugger/init.md)|Prepara il componente di diagnostica grafica integrato nell'applicazione ad acquisire e registrare attivamente le informazioni grafiche.|  
|[ToggleHUD](../debugger/togglehud.md)|Alterna l'HUD di diagnostica grafica da attiva a spento.|  
|[UnInit](../debugger/uninit.md)|Finalizza il file di log degli elementi grafici, lo chiude e libera le risorse utilizzate durante la registrazione delle informazioni grafiche dell'applicazione.|  
  
## Note  
 La classe `VsgDbg` rappresenta un'interfaccia utilizzabile per controllare le funzionalità di diagnostica grafica a livello di codice.  È possibile utilizzare alcune funzionalità anche se non si stanno acquisendo e registrando attivamente informazioni grafiche; tra cui la funzione membro `AddMessage` e la funzione membro `ToggleHUD`.  Le altre funzioni membro o preparano il componente di diagnostica grafica integrato nell'applicazione ad avviarsi o interrompersi, o devono essere chiamate mentre l'applicazione sta attivamente catturando e registrando informazioni grafiche nel file di log degli elementi grafici.