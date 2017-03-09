---
title: "CA1409: I tipi visibili a COM devono essere creabili | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
helpviewer_keywords: 
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1409: I tipi visibili a COM devono essere creabili
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComVisibleTypesShouldBeCreatable|  
|CheckId|CA1409|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo di riferimento contrassegnato specificatamente come visibile a Component Object Model \(COM\) contiene un costruttore con parametri pubblico, ma non contiene un costruttore predefinito pubblico senza parametri.  
  
## Descrizione della regola  
 Un tipo senza un costruttore predefinito pubblico non può essere creato da client COM.  Il tipo è comunque accessibile ai client COM se è disponibile un altro mezzo per creare il tipo e passarlo al client \(ad esempio tramite il valore restituito di una chiamata a un metodo\).  
  
 La regola ignora i tipi derivati da <xref:System.Delegate?displayProperty=fullName>.  
  
 Per impostazione predefinita, i seguenti elementi sono visibili a COM: assembly, tipi pubblici, membri di istanza pubblici in tipi pubblici e tutti i membri di tipi di valore pubblici.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere un costruttore predefinito pubblico o rimuovere l'oggetto <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> dal tipo.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se sono disponibili altri modi per creare e passare l'oggetto al client COM.  
  
## Regole correlate  
 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Vedere anche  
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)