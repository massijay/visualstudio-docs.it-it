---
title: "CA1711: Gli identificatori non devono contenere un suffisso non corretto | Microsoft Docs"
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
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
helpviewer_keywords: 
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1711: Gli identificatori non devono contenere un suffisso non corretto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|  
|CheckId|CA1711|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## Causa  
 Un identificatore contiene un suffisso non corretto.  
  
## Descrizione della regola  
 Per convenzione, solo i nomi di tipi che estendono determinati tipi di base o che implementano determinate interfacce o i tipi derivati da questi tipi devono terminare con suffissi specifici riservati.  Gli altri nomi di tipi non devono utilizzare questi suffissi riservati.  
  
 Nella tabella riportata di seguito sono elencati i suffissi riservati e i tipi di base e le interfacce a cui sono associati.  
  
|Suffisso|Tipo di base\/Interfaccia|  
|--------------|-------------------------------|  
|Attributo|<xref:System.Attribute?displayProperty=fullName>|  
|Collection|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|  
|Dictionary|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|  
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|  
|EventHandler|Delegato del gestore eventi|  
|Eccezione|<xref:System.Exception?displayProperty=fullName>|  
|Autorizzazione|<xref:System.Security.IPermission?displayProperty=fullName>|  
|Queue|<xref:System.Collections.Queue?displayProperty=fullName>|  
|Stack|<xref:System.Collections.Stack?displayProperty=fullName>|  
|Stream|<xref:System.IO.Stream?displayProperty=fullName>|  
  
 Inoltre, **non** devono essere utilizzati i seguenti suffissi:  
  
-   Delegato  
  
-   Enum  
  
-   Impl \- Utilizzare in alternativa "Core"  
  
-   Ex o suffisso analogo per distinguerlo da una versione precedente dello stesso tipo  
  
 Le convenzioni di denominazione forniscono un aspetto comune alle librerie che si avvalgono di Common Language Runtime.  In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e i clienti possono confidare nel fatto che la libreria è stata sviluppata da un esperto nello sviluppo di codice gestito.  
  
## Come correggere le violazioni  
 Rimuovere il suffisso dal nome del tipo.  
  
## Esclusione di avvisi  
 Non eliminare un avviso da questa regola a meno che il suffisso abbia un significato ambiguo nel dominio dell'applicazione.  
  
## Regole correlate  
 [CA1710: Gli identificatori devono contenere il suffisso corretto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)  
  
## Vedere anche  
 [Attributi](../Topic/Attributes1.md)   
 [Eventi e delegati](http://msdn.microsoft.com/it-it/d98fd58b-fa4f-4598-8378-addf4355a115)