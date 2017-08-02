---
title: "Procedura: cercare testo negli intervalli dei fogli di lavoro a livello di codice"
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
  - "testo [sviluppo per Office in Visual Studio], ricerca nei fogli di lavoro"
  - "ricerche di testo, fogli di lavoro"
  - "fogli di lavoro, ricerca"
ms.assetid: a6902711-fefb-450a-a76b-b1446d11c423
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Procedura: cercare testo negli intervalli dei fogli di lavoro a livello di codice
  Il metodo <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> dell'oggetto <xref:Microsoft.Office.Interop.Excel.Range> consente di cercare testo all'interno di un intervallo.  Questo testo può rappresentare anche una delle stringhe di errore visualizzate in una cella del foglio di lavoro, ad esempio `#NULL!` o `#VALUE!`.  Per ulteriori informazioni sulle stringhe di errore, vedere [Valori di errori delle celle](HV10038459).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Nell'esempio seguente viene ricercato un intervallo denominato `Fruits` e viene modificato il tipo di carattere delle celle contenenti la parola "apples".  In questa procedura viene utilizzato anche il metodo <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>, che ripete la ricerca in base alle impostazioni configurate in precedenza.  Per applicare il metodo <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>, è sufficiente specificare la cella dopo la quale effettuare la ricerca.  
  
> [!NOTE]  
>  Quando viene raggiunta la fine dell'intervallo, la ricerca effettuata dal metodo <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> riprende dall'inizio dell'intervallo.  È necessario assicurarsi che il codice non ripeta la ricerca all'infinito.  Nella routine di esempio viene illustrato un metodo per gestire questo problema mediante la proprietà <xref:Microsoft.Office.Interop.Excel.Range.Address%2A>.  
  
 ![Collegamento a video](~/docs/data-tools/media/playvideo.gif "Collegamento a video") Per una dimostrazione video correlata, vedere la procedura dettagliata relativa all'[utilizzo del metodo Find in un componente aggiuntivo di Excel](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
### Per cercare testo in un intervallo di fogli di lavoro  
  
1.  Dichiarare le variabili per tenere traccia dell'intero intervallo, del primo intervallo trovato e dell'intervallo corrente trovato.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#58)]  
  
2.  Cercare la prima corrispondenza, specificando tutti i parametri tranne la cella dopo la quale effettuare la ricerca.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#59)]  
  
3.  Continuare la ricerca finché non viene individuata una corrispondenza.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#60)]  
  
4.  Confrontare il primo intervallo trovato \(`firstFind`\) con **Nothing**.  Se `firstFind` non contiene alcun valore, il codice consente di memorizzare l'intervallo trovato \(`currentFind`\).  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#61)]  
  
5.  Se l'indirizzo dell'intervallo trovato corrisponde all'indirizzo del primo intervallo trovato, uscire dal ciclo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#62)]  
  
6.  Impostare l'aspetto dell'intervallo trovato.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#63)]  
  
7.  Effettuare un'altra ricerca.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#64)]  
  
 Nell'esempio riportato di seguito viene illustrato il metodo completo.  
  
## Esempio  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#57)]  
  
## Vedere anche  
 [Utilizzo degli intervalli](../vsto/working-with-ranges.md)   
 [Procedura: Applicare stili agli intervalli nei fogli di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Procedura: fare riferimento agli intervalli dei fogli di lavoro nel codice a livello di codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  