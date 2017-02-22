---
title: "CA2212: Non contrassegnare componenti serviti con WebMethod | Microsoft Docs"
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
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
helpviewer_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2212: Non contrassegnare componenti serviti con WebMethod
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotMarkServicedComponentsWithWebMethod|  
|CheckId|CA2212|  
|Category|Microsoft.Usage|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo in un tipo che eredita da <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> è contrassegnato con <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.  
  
## Descrizione della regola  
 <xref:System.Web.Services.WebMethodAttribute> si applica ai metodi all'interno di un servizio Web XML creati mediante ASP.NET. Mediante questo oggetto il metodo potrà essere chiamato da client Web remoti.  È necessario che il metodo e la classe siano pubblici e in esecuzione in un'applicazione Web ASP.NET.  I tipi <xref:System.EnterpriseServices.ServicedComponent> sono contenuti da applicazioni COM\+ e possono utilizzare i servizi COM\+.  <xref:System.Web.Services.WebMethodAttribute> non è applicato ai tipi <xref:System.EnterpriseServices.ServicedComponent> poiché non sono previsti per gli stessi scenari.  In particolare, l'aggiunta dell'attributo al metodo <xref:System.EnterpriseServices.ServicedComponent> non consente di chiamare il metodo da client Web remoti.  Poiché <xref:System.Web.Services.WebMethodAttribute> e un metodo <xref:System.EnterpriseServices.ServicedComponent> presentano comportamenti e requisiti di contesto e flusso di transazioni in conflitto tra loro, il comportamento del metodo non sarà corretto in determinati scenari.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere l'attributo dal metodo <xref:System.EnterpriseServices.ServicedComponent>.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  Non sono previsti scenari in cui la combinazione di questi elementi sia corretta.  
  
## Vedere anche  
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>   
 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>