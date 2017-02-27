---
title: "Riferimento API (debug di Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [Debugging SDK], riferimenti alle API"
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Riferimento API (debug di Visual Studio)
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

La sezione di riferimento include una panoramica sui concetti relativi all'API, di una guida che visualizza la sintassi e l'utilizzo per tutti gli elementi API e di un'ampia gamma di esempi di codice.  Tutti i riferimenti sono elencati in ordine alfabetico in base alla categoria.  
  
 Nella tabella seguente vengono mostrati i valori di `HRESULT` comuni restituiti dai metodi.  
  
|Nome|Descrizione|Valore|  
|----------|-----------------|------------|  
|S\_OK|Riuscita.|0x00000000|  
|E\_UNEXPECTED|errore imprevisto.|0x8000FFFF|  
|E\_NOTIMPL|Non implementato.|0x80004001|  
|E\_OUTOFMEMORY|Memoria insufficiente per completare l'operazione.|0x8007000E|  
|E\_INVALIDARG|Uno o più argomenti non sono validi.|0x80070057|  
|E\_NOINTERFACE|nessun tali interfaccia supportata.|0x80004002|  
|E\_POINTER|puntatore non valido.|0x80004003|  
|E\_HANDLE|handle non valide.|0x80070006|  
|E\_ABORT|operazione interrotta.|0x80004004|  
|E\_FAIL|errore imprevisto.|0x80004005|  
|E\_ACCESSDENIED|Errore di accesso negato di generale.|0x80070005|  
  
> [!NOTE]
>  Quando un metodo di debug di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] restituisce `S_OK`, si presume che tutti i puntatori di parametro out sono validi, ovvero, alcuna convalida le operazioni sui puntatori di parametro out quando `S_OK` viene restituito.  
  
> [!NOTE]
>  I parametri di `NULL` o \[out\] non validi possono causare l'ide un arresto anomalo.  
  
## Vedere anche  
 [Interfacce](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Estensibilità del Debugger di Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)