---
title: "CA1720: Gli identificatori non devono contenere nomi di tipo | Microsoft Docs"
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
  - "CA1720"
  - "IdentifiersShouldNotContainTypeNames"
helpviewer_keywords: 
  - "IdentifiersShouldNotContainTypeNames"
  - "CA1720"
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1720: Gli identificatori non devono contenere nomi di tipo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainTypeNames|  
|CheckId|CA1720|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## Causa  
 Il nome di un parametro in un membro visibile esternamente contiene un nome del tipo di dati.  
  
 In alternativa  
  
 Il nome di un membro visibile esternamente contiene un nome del tipo di dati specifico del linguaggio.  
  
## Descrizione della regola  
 I nomi dei parametri e dei membri sono prevalentemente utilizzati per comunicare il loro significato piuttosto che per descriverne il tipo, il quale viene in genere fornito dagli strumenti di sviluppo.  Per i nomi dei membri, se è necessario utilizzare un nome del tipo di dati, utilizzare un nome indipendente dal linguaggio anziché uno specifico del linguaggio.  Anziché il nome del tipo C\# 'int', ad esempio, utilizzare il nome del tipo di dati indipendente dal linguaggio Int32.  
  
 Ogni token discreto nel nome del parametro o del membro viene confrontato con i seguenti nomi del tipo di dati specifici del linguaggio senza distinzione tra maiuscole e minuscole:  
  
-   Bool  
  
-   WChar  
  
-   Int8  
  
-   UInt8  
  
-   Short  
  
-   UShort  
  
-   Int  
  
-   UInt  
  
-   Integer  
  
-   UInteger  
  
-   Long  
  
-   ULong  
  
-   Unsigned  
  
-   Signed  
  
-   Float  
  
-   Float32  
  
-   Float64  
  
 I nomi di un parametro vengono inoltre confrontati con i seguenti nomi del tipo di dati indipendenti dal linguaggio senza distinzione tra maiuscole e minuscole:  
  
-   Object  
  
-   Obj  
  
-   Boolean  
  
-   Char  
  
-   String  
  
-   SByte  
  
-   Byte  
  
-   UByte  
  
-   Int16  
  
-   UInt16  
  
-   Int32  
  
-   UInt32  
  
-   Int64  
  
-   UInt64  
  
-   IntPtr  
  
-   Ptr  
  
-   Puntatore  
  
-   UInptr  
  
-   UPtr  
  
-   UPointer  
  
-   Single  
  
-   Double  
  
-   Decimal  
  
-   Guid  
  
## Come correggere le violazioni  
 **Se generate rispetto a un parametro:**  
  
 Sostituire l'identificatore del tipo di dati nel nome del parametro con un termine che ne descrive meglio il significato o con un termine più generico, ad esempio 'value'.  
  
 **Se generate rispetto a un membro:**  
  
 Sostituire l'identificatore del tipo di dati specifico del linguaggio nel nome del membro con un termine che ne descrive meglio il significato, con un equivalente indipendente dal linguaggio oppure con un termine più generico, ad esempio 'value'.  
  
## Esclusione di avvisi  
 L'utilizzo occasionale di nomi di parametri e membri basati sul tipo potrebbe essere appropriato.  Tuttavia, per i nuovi sviluppi, non vi sono scenari noti in cui sia necessario escludere un avviso da questa regola.  Per le librerie fornite in precedenza, potrebbe essere necessario escludere un avviso da questa regola.  
  
## Regole correlate  
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: Gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1719: I nomi dei parametri non devono corrispondere ai nomi dei membri](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)