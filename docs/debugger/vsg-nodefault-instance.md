---
title: "VSG_NODEFAULT_INSTANCE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSG_NODEFAULT_INSTANCE
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definisce grazie alla propria presenza se è disponibile un'istanza predefinita della classe [Classe VsgDbg](../debugger/vsgdbg-class.md), che fornisce a livello di codice l'interfaccia di acquisizione.  
  
## Sintassi  
  
```cpp  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## Valore  
 Un simbolo del preprocessore che tramite la propria presenza o l'assenza determina se viene fornita un'istanza predefinita della classe `VsgDbg`.  Se viene definito questo simbolo, non viene fornita alcuna istanza predefinita della classe `VsgDbg`; in caso contrario, viene fornita e inizializzata un'istanza predefinita prima che il programma esegua.  
  
 A livello di codice l'interfaccia di acquisizione viene fornita tramite un puntatore con ambito globale, `g_pVsgDbg`.  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## Note  
 L'istanza predefinita è in genere sufficiente, ma per utilizzare l'interfaccia di acquisizione a livello di codice in una DLL quando il dispositivo D3D è stato creato esternamente a tale DLL, è necessario creare e gestire la propria istanza della classe `VsgDbg`.  A livello di codice se si gestisce la propria interfaccia per l'API di acquisizione in questo modo, disabilitare l'istanza predefinita definendo `VSG_NODEFAULT_INSTANCE` per evitare il sovraccarico.  
  
 Se l'istanza predefinita non è disattivata, questa verrà automaticamente inizializzata prima che il programma venga eseguito e automaticamente distrutta quando il programma termina.  Non è necessario inizializzare o annullare l'inizializzazione di questa istanza in modo esplicito.  
  
 Per disabilitare l'istanza predefinita, è necessario definire `VSG_NODEFAULT_INSTANCE` prima di includere `vsgcapture.h` nel programma.  
  
## Esempio  
 In questo esempio viene illustrato come disabilitare l'istanza predefinita:  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```