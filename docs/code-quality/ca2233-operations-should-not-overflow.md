---
title: "CA2233: Evitare l&#39;overflow delle operazioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperationsShouldNotOverflow"
  - "CA2233"
helpviewer_keywords: 
  - "CA2233"
  - "OperationsShouldNotOverflow"
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2233: Evitare l&#39;overflow delle operazioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OperationsShouldNotOverflow|  
|CheckId|CA2233|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo esegue un'operazione aritmetica e non convalida gli operandi in anticipo per impedire l'overflow.  
  
## Descrizione della regola  
 Le operazioni aritmetiche non devono essere eseguite senza prima convalidare gli operandi per assicurarsi che il risultato dell'operazione sia compreso nell'intervallo dei valori possibili per i tipi di dati utilizzati.  A seconda del contesto di esecuzione e dai tipi di dati utilizzati, l'overflow aritmetico può generare <xref:System.OverflowException?displayProperty=fullName> oppure fare sì che i bit più significativi del risultato vengano ignorati.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, convalidare gli operandi prima di eseguire l'operazione.  
  
## Esclusione di avvisi  
 La soppressione di un avviso da questa regola è sicura se i valori possibili degli operandi non possono causare l'overflow dell'operazione aritmetica.  
  
## Esempio di una violazione  
  
### Descrizione  
 Un metodo nell'esempio riportato di seguito per la modifica di un numero intero che viola la regola.  Affinché l'operazione possa riuscire, in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] è necessario che l'opzione di overflow di numeri interi **Rimuovi** sia disabilitata.  
  
### Codice  
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-cs[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]  
  
### Commenti  
 Se al metodo in questo esempio viene passato <xref:System.Int32.MinValue?displayProperty=fullName>, si verificherà un underflow dell'operazione.  Di conseguenza, il bit più significativo del risultato verrà scartato.  Nel codice riportato di seguito viene illustrata questa operazione.  
  
 \[C\#\]  
  
```  
public static void Main()  
{  
    int value = int.MinValue;    // int.MinValue is -2147483648   
    value = Calculator.Decrement(value);   
    Console.WriteLine(value);  
}  
```  
  
 \[VB\]  
  
```  
Public Shared Sub Main()       
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648   
    value = Calculator.Decrement(value)   
    Console.WriteLine(value)   
End Sub  
```  
  
### Output  
  
```  
2147483647  
```  
  
## Correzione tramite convalida dei parametri di input  
  
### Descrizione  
 Nell'esempio seguente viene corretta la violazione precedente convalidando il valore di input.  
  
### Codice  
 [!CODE [FxCop.Usage.OperationOverflowFixed#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed#1)]  
  
## Correzione tramite blocco checked  
  
### Descrizione  
 Nell'esempio seguente viene corretta la violazione precedente eseguendo il wrapping dell'operazione in un blocco checked.  Se l'operazione provoca un overflow, verrà generata un'<xref:System.OverflowException?displayProperty=fullName>.  
  
 Si noti che i blocchi checked non sono supportati in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
### Codice  
 [!CODE [FxCop.Usage.OperationOverflowChecked#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked#1)]  
  
## Attivazione dell'overflow\/underflow aritmetico  
 L'attivazione dell'overflow\/underflow aritmetico checked in C\#, è equivalente all'esecuzione del wrapping di ciascuna operazione su numeri interi in un blocco checked.  
  
 **Per attivare l'overflow\/underflow aritmetico checked in C\#**  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**.  
  
2.  Nella scheda **Compilazione** scegliere **Avanzate**.  
  
3.  Selezionare **Controlla overflow\/underflow aritmetico** e fare clic su **OK**.  
  
## Vedere anche  
 <xref:System.OverflowException?displayProperty=fullName>   
 [Operatori](/dotnet/csharp/language-reference/operators/index)   
 [Checked e Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)