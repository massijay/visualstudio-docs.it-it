---
title: "Interfaccia ISetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Interfaccia ISetNextStatement
L'interfaccia viene implementata da un interprete per consentire all'amministratore del processo di debug aggiornare l'istruzione corrente.  Viene implementata da un oggetto stack frame e il PDM ottiene l'interfaccia con QueryInterface.  
  
 l'interfaccia fornisce metodi utili per impostare il punto di esecuzione, che determina l'istruzione successiva da eseguire.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `ISetNextStatement` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Determina se il punto di esecuzione può essere impostato nella posizione specificata.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Impostare il punto di esecuzione nella posizione specificata.|