---
title: "Metodo SetNotificationForWaitCompletion | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Metodo SetNotificationForWaitCompletion, classe di attività [motori di debug di .NET Framework]"
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Metodo SetNotificationForWaitCompletion
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Imposta o Cancella il bit di stato TASK\_STATE\_WAIT\_COMPLETION\_NOTIFICATION.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib \(in mscorlib. dll\)  
  
## Sintassi  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### Parametri  
 `enabled`  
  
 `true` impostare il bit; `false` a non impostato il bit.  
  
## Eccezioni  
  
## Note  
 Il debugger imposta questo bit consentono di uscire dal corpo di un metodo asincrono. Se `enabled` è `true`, questo metodo deve essere chiamato solo su un'attività che non è ancora stata completata. Se `enabled` è `false`, questo metodo può essere chiamato su attività completate. In entrambi i casi è consigliabile utilizzarla solo per operazioni di promessa stile.  
  
## Requisiti  
  
## Vedere anche  
 [Classe attività](../../extensibility/debugger/task-class-internal-members.md)