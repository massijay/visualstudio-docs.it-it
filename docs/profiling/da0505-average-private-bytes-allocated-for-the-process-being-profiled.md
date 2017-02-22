---
title: "DA0505: Byte privati medi allocati per il processo sottoposto a profilatura | Microsoft Docs"
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
  - "vs.performance.DA0505"
  - "vs.performance.rules.DA0505"
  - "vs.performance.505"
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0505: Byte privati medi allocati per il processo sottoposto a profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0505|  
|Categoria|Gestione delle risorse|  
|Metodo di profilatura|Tutto|  
|Messaggio|Dati raccolti a solo scopo informativo.  Il contatore di byte privati di processo misura la memoria virtuale allocata dal processo sottoposto a profilatura che non può essere condivisa con altri processi.  Il valore restituito corrisponde al valore medio rilevato per tutti gli intervalli di misurazione.|  
|Tipo regola|Informazioni|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## Descrizione della regola  
 Questo messaggio indica la quantità media di memoria virtuale che il processo ha attualmente allocato in byte \(byte privati\).  I byte privati rappresentano percorsi di memoria virtuale allocati dal processo al quale possono accedere solo thread in esecuzione all'interno del processo.  
  
 Per i processi a 32 bit in esecuzione su un computer a 32 bit, il limite superiore della parte privata dello spazio degli indirizzi del processo è di 2 GB.  Utilizzando l'opzione [\/3GB](http://go.microsoft.com/fwlink/?LinkId=177831) Boot.ini switch, i processi a 32 bit possono acquisire fino a 3 GB di memoria virtuale.  Un processo a 32 bit in esecuzione su un computer a 64 bit può acquisire fino a 4 GB di memoria virtuale privata.  
  
 Un processo a 64 bit in esecuzione su un computer a 64 bit può acquisire fino a 8 TB di memoria virtuale privata.  
  
 Il valore indicato è il valore medio fra tutti gli intervalli di misurazione nei quali il processo profilato era attivo.  
  
 Per ulteriori informazioni sugli spazi degli indirizzi del processo, vedere [Spazio degli indirizzi virtuali](http://go.microsoft.com/fwlink/?LinkId=177832) nella documentazione relativa alla gestione della memoria di Windows \(la pagina potrebbe essere in inglese\).  
  
## Come utilizzare i dati della regola  
 Utilizzare il valore indicato per confrontare le prestazioni di versioni o compilazioni diverse del programma o per ottenere informazioni sulle prestazioni dell'applicazione in scenari di profilatura diversi.