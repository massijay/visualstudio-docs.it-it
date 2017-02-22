---
title: "CA1020: Evitare l&#39;utilizzo di spazi dei nomi con un numero ridotto di tipi | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1020"
  - "AvoidNamespacesWithFewTypes"
helpviewer_keywords: 
  - "AvoidNamespacesWithFewTypes"
  - "CA1020"
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1020: Evitare l&#39;utilizzo di spazi dei nomi con un numero ridotto di tipi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidNamespacesWithFewTypes|  
|CheckId|CA1020|  
|Categoria|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Uno spazio dei nomi diverso dallo spazio dei nomi globale contiene meno di cinque tipi.  
  
## Descrizione della regola  
 Accertarsi che sia presente un'organizzazione logica per ognuno degli spazi dei nomi e che esista un motivo valido per inserire tipi in uno spazio dei nomi scarsamente compilato.  Gli spazi dei nomi devono contenere tipi che vengono utilizzati insieme in molti scenari.  Se le relative applicazioni si escludono a vicenda, i tipi devono essere inseriti in spazi dei nomi separati.  Lo spazio dei nomi <xref:System.Web.UI>, ad esempio, contiene tipi utilizzati in applicazioni Web, mentre lo spazio dei nomi <xref:System.Windows.Forms> contiene tipi utilizzati in applicazioni [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)].  Anche se entrambi gli spazi dei nomi presentano tipi che consentono di controllare gli aspetti dell'interfaccia utente, questi tipi non sono progettati per essere utilizzati nella stessa applicazione.  Pertanto, si trovano in spazi dei nomi distinti.  Un'attenta organizzazione degli spazi dei nomi può essere utile anche perché agevola l'individuazione di una funzionalità.  Esaminando la gerarchia degli spazi dei nomi, i consumer di librerie dovrebbero essere in grado di individuare i tipi che implementano una funzionalità.  
  
> [!NOTE]
>  In conformità a questa linea guida, le autorizzazioni e i tipi della fase di progettazione non devono essere uniti in altri spazi dei nomi.  Questi tipi appartengono a propri spazi dei nomi all'interno dello spazio dei nomi principale e gli spazi dei nomi devono terminare rispettivamente con `.Design` e `.Permissions`.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, tentare di combinare gli spazi dei nomi che contengono un numero limitato di tipi in un unico spazio dei nomi.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se lo spazio dei nomi non contiene tipi utilizzati con tipi di altri spazi dei nomi.