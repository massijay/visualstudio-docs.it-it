---
title: "Enumerazione JsRuntimeAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsRuntimeAttributes"
helpviewer_keywords: 
  - "JsRuntimeAttributes (enumerazione)"
ms.assetid: f76d82e9-a695-4d6a-96c1-b3a4d27fed68
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Enumerazione JsRuntimeAttributes
Attributi di un runtime.  
  
## Sintassi  
  
```  
enum JsRuntimeAttributes;  
```  
  
## Membri  
  
### Valori  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`JsRuntimeAttributeAllowScriptInterrupt`|Il runtime deve supportare l'interruzione affidabile dello script. In questo modo viene aumentato il numero di posizioni in cui verrà verificata una richiesta di interruzione di script da parte del runtime; questa operazione comporta un lieve calo in termini di prestazioni.|  
|`JsRuntimeAttributeDisableBackgroundWork`|Non verrà eseguita alcuna operazione \(quali Garbage Collection\) sui thread in background da parte del runtime.|  
|`JsRuntimeAttributeDisableEval`|L'utilizzo del costruttore `eval` o `function` genererà un'eccezione.|  
|`JsRuntimeAttributeDisableNativeCodeGeneration`|Il runtime non genererà codice nativo.|  
|`JsRuntimeAttributeEnableExperimentalFeatures`|Il runtime abiliterà tutte le funzionalità sperimentali.|  
|`JsRuntimeAttributeEnableIdleProcessing`|L'host chiamerà `JsIdle`, in modo da consentire l'elaborazione in periodi di inattività. In caso contrario, il runtime gestirà in modo leggermente più deciso la memoria.|  
|`JsRuntimeAttributeDispatchSetExceptionsToDebugger`|In seguito alla chiamata a `JsSetException` l'eccezione verrà inviata anche al debugger di script \(se presente\), che potrà interrompersi in corrispondenza dell'eccezione.|  
|`JsRuntimeAttributeNone`|Nessun attributo speciale.|  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)