---
title: "Implementazione di un fornitore di porta | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [Debugging SDK], l'implementazione di fornitori di porte"
  - "fornitori di porte, implementazione"
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Implementazione di un fornitore di porta
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gli hole della alimentazioni di un fornitore di porte a richiesta all'amministratore di debug della sessione \(SDM\).  Un fornitore di porte deve essere distribuito quando si esegue il debug in un computer non DCOM o quando un nuovo dispositivo deve essere supportato.  Ad esempio, per fornire il debug in un telefono cellulare, è possibile implementare un fornitore di porte che fornisce le porte che si connettono al telefono cellulare ad esempio si utilizza il IR o di una connessione della cella\) ed enumera i processi e i programmi in esecuzione su telefono.  
  
 Per i programmi di debug su computer basati su Windows \(debug remoto incluso\), Visual Studio fornisce i fornitori di porte per nativo e i processi \(CLR\) di Common Language Runtime, pertanto non è necessario implementare per contenere il fornitore di porte in tali casi.  
  
## In questa sezione  
 [Implementazione e la registrazione di un fornitore di porta](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Viene illustrato lo SDM interagisce con il fornitore di porte e le porte.  
  
 [Porta richiesta fornitore interfacce](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Vengono illustrate le interfacce che devono essere implementate per ottenere un fornitore di porte.  
  
## Sezioni correlate  
 [Concetti del debugger](../../extensibility/debugger/debugger-concepts.md)  
 Vengono descritti i concetti di architettura di debug principali.  
  
## Vedere anche  
 [Estensibilità del Debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)