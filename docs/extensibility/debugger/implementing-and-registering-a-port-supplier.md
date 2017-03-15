---
title: "Implementazione e la registrazione di un fornitore di porta | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [Debugging SDK], la registrazione di fornitori di porte"
  - "fornitori di porte, la registrazione"
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Implementazione e la registrazione di un fornitore di porta
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il ruolo di un fornitore di porte è gli hole della modalità e di rilevare, che a sua volta gestiscono i processi.  Quindi una porta deve essere creata, il fornitore di porte viene creata un'istanza utilizzando CoCreate con il GUID del fornitore di porte \(la sessione l'amministratore di debug che \[SDM\] utilizzerà il fornitore di porte l'utente selezionato o il fornitore di porte specificato dal sistema del progetto\).  Lo SDM chiamerà [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) per vedere se le porte è possibile aggiungere.  Se una porta è possibile aggiungere, una nuova porta è necessaria chiamandola [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) e passando [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) che descrive la porta.  `AddPort` restituirà una nuova porta rappresentata [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) da un'interfaccia.  
  
## Descrizione  
 Una porta viene creata da un fornitore di porte, che è a sua volta associato a un computer o un server di debug.  Un server può enumerare i fornitori di porte con[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) il metodo e un fornitore di porte possibile enumerare le porte dal [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) metodo.  
  
 Oltre alla registrazione tipica COM, un fornitore di porte necessario registrarsi con Visual Studio inserendo il relativo CLSID e nome in percorsi specifici del Registro di sistema.  Un debug l'sdk `SetMetric` chiamato funzione di supporto che gestisce questo lavoretto: viene chiamato una volta per ciascun elemento venga registrato, nel modo seguente:  
  
```cpp#  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricCLSID,  
          <CLSID of your port supplier>,  
          false,  
          NULL)  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricName,  
          <name of your port supplier>,  
          false,  
          NULL);  
```  
  
 Un fornitore di porte si annulla la registrazione chiamando `RemoveMetric` \(un'altra funzione di supporto di debug SDK\) una volta per ogni elemento che è stato registrato, nel modo seguente:  
  
```cpp#  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricCLSID,  
             NULL);  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricName,  
             NULL);  
```  
  
> [!NOTE]
>  [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` e `RemoveMetric` sono funzioni statiche definite in dbgmetric.h e compilate in ad2de.lib.  `metrictypePortSupplier`, `metricCLSID`e gli helper`metricName` vengono inoltre definiti in dbgmetric.h.  
  
 Un fornitore di porte possibile fornire il nome e GUID dai metodi [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) e [GetPortSupplierId](../Topic/IDebugPortSupplier2::GetPortSupplierId.md), rispettivamente.  
  
## Vedere anche  
 [Implementazione di un fornitore di porta](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)