---
title: "Rappresentazioni DateTime e TimeSpan di Windows Runtime | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DateTime [JavaScript]"
  - "JavaScript, Date e ore di Windows Runtime"
  - "TimeSpan [JavaScript]"
ms.assetid: 9743e9ac-9054-463e-8264-427183e4905f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Rappresentazioni DateTime e TimeSpan di Windows Runtime
La rappresentazione JavaScript di date e ore è diversa rispetto alla versione di Windows Runtime.  La struttura [DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx) di Windows Runtime è rappresentata in JavaScript come [Date](../javascript/reference/date-object-javascript.md) con archivio di backup corrispondente alla data `DateTime` e con intervallo e precisione diversa rispetto a `Date` di JavaScript.  Se lo si modifica, questo oggetto `Date` personalizzato diventa un oggetto `Date` di JavaScript standard e perde precisione.  I valori `Date` di JavaScript possono essere passati a Windows Runtime `DateTime`. Ne sarà verificato l'intervallo e ciò potrebbe comportare eccezioni di marshalling.  
  
 La struttura [TimeSpan](http://msdn.microsoft.com/it-it/c5defb66-819c-4796-85b5-07ed249a5d86) di Windows Runtime è convertita in millisecondi e restituita come numero JavaScript.  
  
## Vedere anche  
 [Utilizzo di Windows Runtime in JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)