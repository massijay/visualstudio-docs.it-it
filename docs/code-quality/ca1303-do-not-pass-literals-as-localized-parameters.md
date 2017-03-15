---
title: "CA1303: Non passare valori letterali come parametri localizzati | Microsoft Docs"
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
  - "Do not pass literals as localized parameters"
  - "DoNotPassLiteralsAsLocalizedParameters"
  - "CA1303"
helpviewer_keywords: 
  - "CA1303"
  - "DoNotPassLiteralsAsLocalizedParameters"
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1303: Non passare valori letterali come parametri localizzati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotPassLiteralsAsLocalizedParameters|  
|CheckId|CA1303|  
|Category|Microsoft.Globalization|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo passa un valore letterale stringa come parametro a un costruttore o a un metodo nella libreria di classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e questa stringa deve essere localizzabile.  
  
 Questo avviso viene generato quando una stringa letterale passata come un valore a un parametro o proprietà e uno o più dei casi seguenti è true:  
  
-   L'attributo <xref:System.ComponentModel.LocalizableAttribute> del parametro o proprietà è impostato su true.  
  
-   Il parametro o il nome della proprietà contiene "Testo", "Messaggio" o "Barra del titolo."  
  
-   Il nome del parametro di stringa passato a un metodo Console.Write o Console.WriteLine è "valore" o "formato."  
  
## Descrizione della regola  
 Le stringhe letterali incorporate nel codice sorgente sono difficili da localizzare.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, sostituire la stringa letterale con una stringa recuperata attraverso un'istanza della classe <xref:System.Resources.ResourceManager>.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se la libreria di codice non verrà localizzata o se la stringa non è esposta all'utente finale o a uno sviluppatore che utilizza la libreria di codice.  
  
 Gli utenti possono eliminare le segnalazioni sui metodi a cui non devono essere passate stringhe localizzate rinominando il parametro o la proprietà indicata o contrassegnando questi elementi come condizionali.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un metodo che genera un'eccezione quando uno dei due argomenti relativi non è compreso nell'intervallo.  Per il primo argomento, il costruttore di eccezioni viene passato come stringa letterale, violando questa regola.  Per il secondo argomento, il costruttore è passato correttamente come una stringa recuperata tramite un oggetto <xref:System.Resources.ResourceManager>.  
  
 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-cs[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]  
  
## Vedere anche  
 [Risorse nelle applicazioni desktop](../Topic/Resources%20in%20Desktop%20Apps.md)