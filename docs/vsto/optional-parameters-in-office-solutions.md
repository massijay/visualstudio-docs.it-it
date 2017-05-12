---
title: "Parametri facoltativi nelle soluzioni Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo di applicazioni [sviluppo per Office in Visual Studio], parametri facoltativi"
  - "campo mancante [sviluppo per Office in Visual Studio]"
  - "Applicazioni Office [sviluppo per Office in Visual Studio], parametri facoltativi"
  - "parametri facoltativi [sviluppo per Office in Visual Studio]"
  - "parametri [sviluppo per Office in Visual Studio], facoltativi"
  - "Visual Basic [sviluppo per Office in Visual Studio], parametri facoltativi"
  - "Visual C# [sviluppo per Office in Visual Studio], parametri facoltativi"
ms.assetid: 109eaef6-08bb-4b59-a29e-921f856027cc
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Parametri facoltativi nelle soluzioni Office
  Molti dei metodi nei modelli a oggetti delle applicazioni di Microsoft Office accettano parametri facoltativi.  Se si utilizza Visual Basic per sviluppare una soluzione Office in Visual Studio, non è necessario passare un valore per i parametri facoltativi. Infatti, per ogni parametro mancante vengono utilizzati automaticamente i valori predefiniti.  Nella maggior parte dei casi, è anche possibile omettere i parametri facoltativi nei progetti Visual C\#. Tuttavia, non è possibile omettere i parametri **ref** facoltativi della classe `ThisDocument` nei progetti Word a livello di documento.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Per ulteriori informazioni sull'utilizzo dei parametri facoltativi in progetti Visual C\# e Visual Basic, vedere [Argomenti denominati e facoltativi &#40;Guida per programmatori C&#35;&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) e [Optional Parameters &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters).  
  
> [!NOTE]  
>  Nelle versioni precedenti di Visual Studio è necessario passare un valore per ogni parametro facoltativo nei progetti Visual C\#.  Per comodità, questi progetti includono una variabile globale denominata `missing` che è possibile passare a un parametro facoltativo quando si desidera utilizzare il valore predefinito del parametro.  I progetti Visual C\# per Office in Visual Studio continuano a includere la variabile `missing`. In genere non è necessario utilizzarla se si sviluppano soluzioni Office in [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], tranne quando si chiamano metodi con parametri **ref** facoltativi nella classe `ThisDocument` nei progetti Word a livello di documento.  
  
## Esempio in Excel  
 Il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> presenta numerosi parametri facoltativi.  È possibile specificare i valori per alcuni parametri e accettare il valore predefinito di altri utenti, come illustrato nell'esempio di codice riportato di seguito.  In questo esempio è richiesto un progetto a livello di documento con una classe del foglio di lavoro denominata `Sheet1`.  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralExcel/CS/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstrefGeneralExcel/VB/Sheet1.vb#1)]  
  
## Esempio in Word  
 Il metodo <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> presenta numerosi parametri facoltativi.  È possibile specificare i valori per alcuni parametri e accettare il valore predefinito di altri utenti, come illustrato nell'esempio di codice riportato di seguito.  
  
 [!code-csharp[Trin_VstrefGeneralWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_VstrefGeneralWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/VB/ThisDocument.vb#1)]  
  
## Utilizzo dei parametri facoltativi di metodi nella classe ThisDocument nei progetti Visual C\# a livello di documento per Word  
 Nel modello a oggetti di Word sono contenuti molti metodi con parametri **ref** facoltativi che accettano valori <xref:System.Object>.  Tuttavia, non è possibile omettere parametri **ref** facoltativi di metodi della classe `ThisDocument` generata nei progetti Visual C\# a livello di documento per Word.  Visual C\# consente di omettere i parametri **ref** facoltativi solo per i metodi delle interfacce, non delle classi.  Ad esempio, il codice riportato di seguito non viene compilato perché non è possibile omettere i parametri **ref** facoltativi del metodo <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> della classe `ThisDocument`.  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#3)]  
  
 Quando si chiamano metodi della classe `ThisDocument`, attenersi le linee guida seguenti:  
  
-   Per accettare il valore predefinito di un parametro **ref** facoltativo, passare la variabile `missing` al parametro.  La variabile `missing` viene definita automaticamente nei progetti Office di Visual C\# e viene assegnata al valore <xref:System.Type.Missing> nel codice di progetto generato.  
  
-   Per specificare il proprio valore per un parametro **ref** facoltativo, dichiarare un oggetto assegnato al valore che si desidera specificare, quindi passare l'oggetto al parametro.  
  
 Nell'esempio di codice seguente viene illustrato come chiamare il metodo <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> specificando un valore per il parametro *ignoreUppercase* e accettando il valore predefinito per gli altri parametri.  
  
 [!code-csharp[Trin_VstrefGeneralWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#4)]  
  
 In alternativa, se si desidera scrivere un codice che consente di omettere i parametri **ref** facoltativi di un metodo nella classe `ThisDocument`, è possibile chiamare lo stesso metodo nell'oggetto <xref:Microsoft.Office.Interop.Word.Document> restituito dalla proprietà <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> e omettere i parametri da quel metodo.  È possibile eseguire questa operazione perché <xref:Microsoft.Office.Interop.Word.Document> è un'interfaccia, non una classe.  
  
 [!code-csharp[Trin_VstrefGeneralWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#5)]  
  
 Per ulteriori informazioni sui parametri di tipo valore e riferimento, vedere [Passing Arguments by Value and by Reference &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) \(per Visual Basic\) e [Passaggio di parametri &#40;Guida per programmatori C&#35;&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## Vedere anche  
 [Sviluppo di soluzioni Office](../vsto/developing-office-solutions.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)  
  
  