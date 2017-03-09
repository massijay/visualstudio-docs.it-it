---
title: "Utilizzo dell&#39;attributo DebuggerTypeProxy | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "attributi [C#], debugger"
  - "DebuggerTypeProxy (attributo)"
  - "DebuggerTypeProxyAttribute (classe)"
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Utilizzo dell&#39;attributo DebuggerTypeProxy
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> specifica un proxy, o stand\-in, per un tipo e modifica il modo in cui il tipo viene visualizzato nelle finestre del debugger.  Quando viene visualizzata una variabile che dispone di proxy, questo sostituisce il tipo originale nella **visualizzazione**.  Nella finestra delle variabili del debugger vengono visualizzati soltanto i membri pubblici del tipo proxy.  I membri privati non vengono visualizzati.  
  
 Questo attributo può essere applicato a:  
  
-   Strutture  
  
-   Classi  
  
-   Assembly  
  
 Una classe proxy del tipo deve disporre di un costruttore che accetta un argomento del tipo sostituito dal proxy.  Il debugger crea una nuova istanza della classe proxy del tipo ogni volta che è necessario visualizzare una variabile del tipo di destinazione.  Ciò può incidere sulle prestazioni.  Di conseguenza, è opportuno eseguire solo gli interventi strettamente necessari nel costruttore.  
  
 Per ridurre gli effetti negativi sulle prestazioni, l'analizzatore di espressioni non esamina gli attributi nel proxy visualizzato per il tipo a meno che il tipo non venga espanso dall'utente facendo clic sul simbolo \+ nella finestra del debugger o tramite <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  È pertanto sconsigliabile inserire attributi nel tipo visualizzato.  È possibile e consigliabile utilizzare gli attributi nel corpo del tipo visualizzato.  
  
 È opportuno che il proxy del tipo sia una classe annidata privata all'interno della classe di destinazione dell'attributo.  In questo modo l'attributo può accedere facilmente ai membri interni.  
  
 Se <xref:System.Diagnostics.DebuggerTypeProxyAttribute> viene utilizzato a livello di assembly, il parametro `Target` specifica il tipo che verrà sostituito dal proxy.  
  
 Per un esempio sulla modalità di utilizzo di questo attributo con <xref:System.Diagnostics.DebuggerDisplayAttribute> e <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, vedere [Utilizzo dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
## Utilizzo di generics con DebuggerTypeProxy  
 Il supporto per generics è limitato.  In C\# `DebuggerTypeProxy` supporta solo tipi aperti.  Un tipo aperto, noto anche come tipo non costruito, è un tipo generico per il quale non è stata creata un'istanza con argomenti relativi ai parametri di tipo.  I tipi chiusi, noti anche come tipi costruiti, non sono supportati.  
  
 La sintassi per un tipo aperto è simile alla seguente:  
  
 `Namespace.TypeName<,>`  
  
 Se si utilizza un tipo generico come destinazione in `DebuggerTypeProxy`, è necessario adottare questa sintassi.  Il meccanismo di `DebuggerTypeProxy` deduce automaticamente i parametri di tipo.  
  
 Per ulteriori informazioni sui tipi aperti e chiusi in C\#, vedere la sezione 20.5.2 relativa nella [Specifiche del linguaggio C\#](/dotnet/csharp/language-reference/language-specification).  
  
 In Visual Basic non è disponibile la sintassi dei tipi aperti, pertanto non è possibile eseguire la stessa operazione in questo linguaggio,  ma è necessario utilizzare una rappresentazione del nome del tipo aperto in formato stringa.  
  
 `"Namespace.TypeName'2"`  
  
## Vedere anche  
 [Utilizzo dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Visualizzazione di tipi di dati personalizzati](../debugger/create-custom-views-of-dot-managed-objects.md)   
 [Enhancing Debugging with the Debugger Display Attributes](../Topic/Enhancing%20Debugging%20with%20the%20Debugger%20Display%20Attributes.md)