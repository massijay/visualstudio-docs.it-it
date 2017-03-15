---
title: "CA1710: Gli identificatori devono contenere il suffisso corretto | Microsoft Docs"
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
  - "CA1710"
  - "IdentifiersShouldHaveCorrectSuffix"
helpviewer_keywords: 
  - "IdentifiersShouldHaveCorrectSuffix"
  - "CA1710"
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1710: Gli identificatori devono contenere il suffisso corretto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectSuffix|  
|CheckId|CA1710|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## Causa  
 Un identificatore non contiene il suffisso corretto.  
  
## Descrizione della regola  
 Per convenzione i nomi dei tipi che estendono determinati tipi di base o che implementano determinate interfacce o dei tipi derivati da questi tipi contengono un suffisso associato al tipo di base o all'interfaccia.  
  
 Le convenzioni di denominazione forniscono un aspetto comune alle librerie che si avvalgono di Common Language Runtime.  In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e i clienti possono confidare nel fatto che la libreria è stata sviluppata da un esperto nello sviluppo di codice gestito.  
  
 Nella tabella riportata di seguito sono elencati i tipi di base e le interfacce a cui sono associati suffissi.  
  
|Tipo di base\/Interfaccia|Suffisso|  
|-------------------------------|--------------|  
|<xref:System.Attribute?displayProperty=fullName>|Attributo|  
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|  
|<xref:System.Exception?displayProperty=fullName>|Eccezione|  
|<xref:System.Collections.ICollection?displayProperty=fullName>|Collection|  
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Dictionary|  
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Collection|  
|<xref:System.Collections.Queue?displayProperty=fullName>|Collection o Queue|  
|<xref:System.Collections.Stack?displayProperty=fullName>|Collection o Stack|  
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Collection|  
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dictionary|  
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|  
|<xref:System.Data.DataTable?displayProperty=fullName>|Collection o DataTable|  
|<xref:System.IO.Stream?displayProperty=fullName>|Stream|  
|<xref:System.Security.IPermission?displayProperty=fullName>|Autorizzazione|  
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Condizione|  
|Delegato del gestore eventi.|EventHandler|  
  
 Per i tipi che implementano <xref:System.Collections.ICollection> e rappresentano un tipo generalizzato di struttura di dati, ad esempio dizionario, stack o coda, sono consentiti nomi che forniscono informazioni significative relative all'utilizzo previsto del tipo.  
  
 I tipi che implementano <xref:System.Collections.ICollection> e rappresentano una raccolta di elementi specifici, presentano nomi che terminano con la parola "Collection".  Una raccolta di oggetti <xref:System.Collections.Queue>, ad esempio, presenterebbe il nome "QueueCollection".  Il suffisso "Collection" indica che i membri della raccolta possono essere enumerati utilizzando l'istruzione `foreach` \(`For Each` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
 I tipi che implementano <xref:System.Collections.IDictionary> presentano nomi che terminano con la parola "Dictionary" anche se il tipo implementa anche <xref:System.Collections.IEnumerable> o <xref:System.Collections.ICollection>.  Le convenzioni di denominazione dei suffissi "Collection" e "Dictionary" consentono agli utenti di fare distinzione tra i due modelli di enumerazione riportati di seguito.  
  
 I tipi con il suffisso "Collection" seguono questo modello di enumerazione.  
  
```  
foreach(SomeType x in SomeCollection) { }  
```  
  
 I tipi con il suffisso "Dictionary" seguono questo modello di enumerazione.  
  
```  
foreach(SomeType x in SomeDictionary.Values) { }  
```  
  
 Un oggetto <xref:System.Data.DataSet> è dato da una raccolta di oggetti <xref:System.Data.DataTable> formati a loro volta da raccolte di oggetti <xref:System.Data.DataColumn?displayProperty=fullName> e <xref:System.Data.DataRow?displayProperty=fullName>, tra gli altri.  Queste raccolte implementano <xref:System.Collections.ICollection> tramite la classe base <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName>.  
  
## Come correggere le violazioni  
 Rinominare il tipo in modo da utilizzare come suffisso il termine corretto.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso è sicura per utilizzare il suffisso "Collection" se il tipo è una struttura dei dati generalizzata che può essere estesa o che contiene un set arbitrario di elementi diversi.  In questo caso, può essere opportuno utilizzare un nome che fornisca informazioni significative relative all'implementazione, alle prestazioni o ad altre caratteristiche della struttura di dati, ad esempio BinaryTree.  Nei casi in cui il tipo rappresenta una raccolta di un tipo specifico, ad esempio StringCollection, non escludere un avviso da questa regola poiché il suffisso indica che il tipo può essere enumerato con un'istruzione `foreach`.  
  
 Per gli altri suffissi, non escludere un avviso da questa regola.  Il suffisso consente di rendere evidente l'utilizzo previsto dal nome del tipo.  
  
## Regole correlate  
 [CA1711: Gli identificatori non devono contenere un suffisso non corretto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)  
  
## Vedere anche  
 [Attributi](../Topic/Attributes1.md)   
 [Eventi e delegati](http://msdn.microsoft.com/it-it/d98fd58b-fa4f-4598-8378-addf4355a115)