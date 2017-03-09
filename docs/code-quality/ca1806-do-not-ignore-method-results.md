---
title: "CA1806: Non ignorare i risultati dei metodi | Microsoft Docs"
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
  - "CA1806"
  - "DoNotIgnoreMethodResults"
helpviewer_keywords: 
  - "CA1806"
  - "DoNotIgnoreMethodResults"
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1806: Non ignorare i risultati dei metodi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Le cause di questo avviso possono essere molteplici:  
  
-   Viene creato un nuovo oggetto, ma non viene mai utilizzato.  
  
-   Viene chiamato un metodo per la creazione e la restituzione di una nuova stringa e la nuova stringa non viene mai utilizzata.  
  
-   Un metodo COM o P\/Invoke che restituisce un codice di errore o HRESULT che non viene mai utilizzato.  Descrizione della regola  
  
 La creazione di oggetti superflui e la Garbage Collection associata per l'oggetto non utilizzato influiscono negativamente sulle prestazioni.  
  
 Le stringhe non possono essere modificate e i metodi come String.ToUpper restituiscono una nuova istanza di una stringa anziché modificare l'istanza della stringa nel metodo chiamante.  
  
 Se si ignora il codice di errore o HRESULT si rischia di causare un comportamento imprevisto in caso di errore o una condizione di insufficienza delle risorse.  
  
## Come correggere le violazioni  
 Se con il metodo A viene creata una nuova istanza dell'oggetto B che non viene mai utilizzata, passare l'istanza come un argomento a un altro metodo o assegnare l'istanza a una variabile.  Se la creazione dell'oggetto non è necessaria, rimuoverla. In alternativa  
  
 Se il metodo A chiama il metodo B, ma la nuova istanza della stringa restituita dal metodo B non viene utilizzata.  Passare l'istanza come argomento a un altro metodo, assegnare l'istanza a una variabile  oppure rimuovere la chiamata se non è necessaria.  
  
 In alternativa  
  
 Se il metodo A chiama il metodo B, ma il codice di errore o HRESULT restituito dal metodo non viene utilizzato.  Utilizzare il risultato in un'istruzione condizionale, assegnare il risultato a una variabile oppure passarlo come argomento di un altro metodo.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola a meno che l'atto di creazione dell'oggetto non abbia uno scopo preciso.  
  
## Esempio  
 Nell'esempio seguente viene illustrata una classe che ignora il risultato della chiamata a String.Trim.  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  
  
## Esempio  
 Nell'esempio seguente viene risolta la precedente violazione mediante l'assegnazione del risultato del metodo String.Trim alla variabile su cui era stata effettuata la chiamata.  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un metodo che non utilizza un oggetto creato dal metodo stesso.  
  
> [!NOTE]
>  Questa violazione non può essere riprodotta in Visual Basic.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]  
  
## Esempio  
 Nell'esempio riportato di seguito viene risolta la precedente violazione mediante la rimozione della creazione non necessaria di un oggetto.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]  
  
## Esempio  
 Nell'esempio seguente viene illustrato un metodo che ignora il codice di errore restituito dal metodo GetShortPathName nativo.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]  
  
## Esempio  
 Nell'esempio riportato di seguito viene risolta la precedente violazione mediante il controllo del codice di errore e la generazione di un'eccezione quando la chiamata ha esito negativo.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]