---
title: "CA2243: Valori letterali stringa di attributo devono essere analizzate correttamente | Microsoft Docs"
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
  - "CA2243"
  - "AttributeStringLiteralsShouldParseCorrectly"
helpviewer_keywords: 
  - "AttributeStringLiteralsShouldParseCorrectly"
  - "CA2243"
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2243: Valori letterali stringa di attributo devono essere analizzate correttamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AttributeStringLiteralsShouldParseCorrectly|  
|CheckId|CA2243|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Il parametro del valore letterale stringa di un attributo non analizza correttamente un URL, un GUID o una versione.  
  
## Descrizione della regola  
 Poiché gli attributi sono derivati da <xref:System.Attribute?displayProperty=fullName> e vengono utilizzati in fase di compilazione, solo i valori costanti possono essere passati ai relativi costruttori.  I parametri di attribuito che devono rappresentare URL, GUID e versioni non possono essere tipizzati come <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName> e <xref:System.Version?displayProperty=fullName>, perché questi tipi non possono essere rappresentati come costanti.  Devono invece essere rappresentati da stringhe.  
  
 Poiché il parametro è tipizzato come stringa, è possibile che un parametro in formato non corretto venga passato in fase di compilazione.  
  
 Questa regola utilizza un'euristica di denominazione per individuare parametri che rappresentano un URI \(Uniform Resource Identifier\), un GUI \(Globally Unique Identifier\) o una versione e verifica che il valore passato sia corretto.  
  
## Come correggere le violazioni  
 Impostare la stringa del parametro su un URL, un GUID o una versione in formato corretto.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se il parametro non rappresenta un URL, un GUID o una versione.  
  
## Esempio  
 Nell'esempio riportato di seguito è illustrato il codice per AssemblyFileVersionAttribute che viola questa regola.  
  
 [!code-cs[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]  
  
 La regola viene attivata da quanto segue:  
  
-   Parametri che contengono "version" e non possono essere analizzati in System.Version.  
  
-   Parametri che contengono "guid" e non possono essere analizzato in System.Guid.  
  
-   Parametri che contengono "uri", "urn" o "url" e non possono essere analizzati in System.Uri.  
  
## Vedere anche  
 [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)