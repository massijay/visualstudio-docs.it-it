---
title: "CA2001: Evitare le chiamate a metodi problematici | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2001"
  - "AvoidCallingProblematicMethods"
helpviewer_keywords: 
  - "CA2001"
  - "AvoidCallingProblematicMethods"
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2001: Evitare le chiamate a metodi problematici
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidCallingProblematicMethods|  
|CheckId|CA2001|  
|Categoria|Microsoft.Reliability|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un membro chiama un metodo potenzialmente pericoloso o problematico.  
  
## Descrizione della regola  
 Evitare di effettuare chiamate a metodi potenzialmente pericolosi e superflui.  
  
 Quando un membro chiama uno dei seguenti metodi, si verifica una violazione di questa regola.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|<xref:System.GC.Collect%2A?displayProperty=fullName>|La chiamata di GC.Collect può incidere in modo significativo sulle prestazioni dell'applicazione ed è raramente necessaria.  Per ulteriori informazioni, vedere il post [Considerazioni di Rico Mariani](http://go.microsoft.com/fwlink/?LinkId=169256) sul blog di MSDN.|  
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread.Suspend e Thread.Resume sono stati deprecati a causa del comportamento imprevedibile.  Utilizzare le altre classi nello spazio dei nomi <xref:System.Threading>, ad esempio <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex%2C>, <xref:System.Threading.Mutex> e <xref:System.Threading.Semaphore> per sincronizzare i thread o proteggere le risorse.|  
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Il metodo DangerousGetHandle pone un problema di sicurezza perché può restituire un handle che non è valido.  Per ulteriori informazioni su come utilizzare il metodo DangerousGetHandle in modo sicuro, vedere i metodi <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> e <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A>.|  
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Questi metodi possono caricare assembly dai percorsi non previsti.  Ad esempio, vedere i post del blog delle note di CLR .NET di Suzanne Cook's [LoadFile vs. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) e [Choosing a Binding Context](http://go.microsoft.com/fwlink/?LinkId=164451) nel sito Web MSDN per informazioni sui metodi di caricamento degli assembly.|  
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) \(Ole32\)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) \(Ole32\)|Una volta avviata l'esecuzione del codice utente in un processo gestito, è troppo tardi per chiamare CoSetProxyBlanket in modo affidabile.  In CLR \(Common Language Runtime\) vengono adottate misure che potrebbero impedire l'esito positivo di P\/Invoke.<br /><br /> Se è necessario chiamare CoSetProxyBlanket per un'applicazione gestita, si consiglia di avviare il processo utilizzando un file eseguibile di codice nativo \(C\+\+\), chiamare CoSetProxyBlanket nel codice nativo, quindi avviare l'applicazione in codice gestito nel processo. Assicurarsi di specificare un numero di versione di runtime.|  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere o sostituire la chiamata al metodo pericoloso o problematico.  
  
## Esclusione di avvisi  
 È necessario eliminare i messaggi da questa regola solo quando non sono disponibili alternative al metodo problematico.  
  
## Vedere anche  
 [Avvisi di affidabilità](../code-quality/reliability-warnings.md)