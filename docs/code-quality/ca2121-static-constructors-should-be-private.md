---
title: "CA2121: I costruttori statici devono essere privati | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2121"
  - "StaticConstructorsShouldBePrivate"
helpviewer_keywords: 
  - "CA2121"
  - "StaticConstructorsShouldBePrivate"
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2121: I costruttori statici devono essere privati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StaticConstructorsShouldBePrivate|  
|CheckId|CA2121|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo presenta un costruttore statico non privato.  
  
## Descrizione della regola  
 Un costruttore statico, noto anche come costruttore di classe, viene utilizzato per inizializzare un tipo.  Il costruttore statico viene chiamato prima che venga creata la prima istanza del tipo o venga fatto riferimento a qualsiasi membro statico.  L'utente non dispone di alcun controllo quando viene chiamato il costruttore statico.  Se un costruttore statico non è privato, può essere chiamato da codice esterno al sistema.  A seconda delle operazioni eseguite nel costruttore, questa situazione può causare comportamenti imprevisti.  
  
 Questa regola è applicata dai compilatori C\# e Visual Basic .NET.  
  
## Come correggere le violazioni  
 Le violazioni sono in genere causate da una delle seguenti azioni:  
  
-   Si è definito un costruttore statico per il tipo e non lo si è reso privato.  
  
-   Il compilatore del linguaggio di programmazione ha aggiunto un costruttore statico predefinito al tipo e non lo ha reso privato.  
  
 Per correggere il primo tipo di violazione, rendere privato il costruttore statico.  Per correggere il secondo tipo, aggiungere un costruttore statico privato al tipo.  
  
## Esclusione di avvisi  
 Non escludere queste violazioni.  Se la progettazione del software richiede una chiamata esplicita a un costruttore statico, è probabile che la progettazione contenga gravi difetti e debba essere rivista.