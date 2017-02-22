---
title: "Opzioni, Editor di testo, Base (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Visual_Basic.Editor"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.Editor"
  - "VS.ToolsOptionsPages.Visual_Basic_Editor.Editor"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage"
  - "VS.ToolsOptionsPages.Text_Editor.Basic"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific"
helpviewer_keywords: 
  - "Di base (finestra di dialogo Opzioni dell'editor di testo)"
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Opzioni, Editor di testo, Base (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La pagina delle proprietà **Specifiche di VB**, nella cartella **Di base** della cartella **Editor di testo** della finestra di dialogo **Opzioni** \(menu **Strumenti**\), contiene le seguenti proprietà:  
  
 **Inserimento automatico di costrutti End**  
 Quando si digita, ad esempio, la prima riga della dichiarazione di una routine `Sub Main—` e si preme INVIO, nell'editor di testo viene aggiunta una riga `End Sub` corrispondente.  Analogamente, se si aggiunge un ciclo [For](/dotnet/visual-basic/language-reference/statements/for-next-statement), nell'editor di testo viene aggiunta una corrispondente istruzione `Next`.  Quando è selezionata questa opzione, nell'editor del codice viene aggiunto automaticamente il costrutto End.  
  
 **Riformatta il listato di codice**  
 L'editor di testo riformatta opportunamente il codice.  Se l'opzione è selezionata, l'editor di codice esegue quanto riportato di seguito.  
  
-   Allineamento del codice alla posizione di tabulazione corretta  
  
-   Corretto impiego di maiuscole e minuscole in parole chiave, variabili e oggetti  
  
-   Aggiunta di un parametro `Then` mancante nelle istruzioni `If...Then`  
  
-   Aggiunta di parentesi alle chiamate di funzione  
  
-   Aggiunta di virgolette finali mancanti alle stringhe  
  
-   Riformattazione di notazioni esponenziali  
  
-   Riformattazione di date  
  
 **Attiva modalità struttura**  
 Quando si apre un file in un editor del codice, è possibile visualizzare il documento in modalità struttura.  Per ulteriori informazioni, vedere [Struttura](../../ide/outlining.md).  Quando è selezionata questa opzione, la modalità struttura viene attivata all'apertura di un file.  
  
 **Inserimento automatico di membri Interface e MustOverride**  
 Quando si esegue il commit di istruzioni `Implements` o `Inherits` di una classe, l'editor di testo inserisce un prototipo per i membri che, rispettivamente, devono essere implementati o di cui deve essere eseguito l'override.  
  
 **Mostra separatori di riga routine**  
 L'editor di testo indica l'ambito di visualizzazione delle procedure.  Nei file di origine VB del progetto viene inserita una riga, nelle posizioni indicate nella tabella seguente:  
  
|Posizione nei file di origine VB|Esempio di posizione nella riga|  
|--------------------------------------|-------------------------------------|  
|Dopo la chiusura di un costrutto di dichiarazione di un blocco|-   Alla fine di una classe, struttura, modulo, interfaccia o enumerazione<br />-   Dopo una proprietà, funzione o sottofunzione<br />-   Non tra le clausole get e set di una proprietà|  
|Dopo un set di costrutti a riga singola|-   Dopo le istruzioni Import, prima di una definizione di tipo in un file di classe<br />-   Dopo le variabili dichiarate in una classe, prima di qualsiasi routine|  
|Dopo dichiarazioni a riga singola, \(dichiarazioni non a livello di blocco\)|-   Dopo istruzioni Import, istruzioni Inherits, dichiarazioni di variabili, dichiarazioni di eventi, dichiarazioni di delegati e istruzioni DLL declare|  
  
 **Attiva suggerimenti per la correzione di errore**  
 L'editor di testo può suggerire soluzioni per gli errori più comuni e consentire di selezionare la correzione appropriata da applicare al codice.  
  
 **Abilita evidenziazione di riferimenti e parole chiave.**  
 L'editor di testo può evidenziare tutte le istanze di un simbolo o tutte le parole chiave in una clausola quale `If..Then`, `While...End While`o `Try...Catch...Finally`.  È possibile spostarsi tra i riferimenti o parole chiave evidenziati premendo CTRL\+SHIFT\+DOWN ARROW or CTRL\+SHIFT\+UP ARROW.  
  
## Vedere anche  
 [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)   
 [Opzioni, Editor di testo, Tutti i linguaggi, Schede](../../ide/reference/options-text-editor-all-languages-tabs.md)