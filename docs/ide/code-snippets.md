---
title: "Frammenti di codice | Microsoft Docs"
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
  - "vs.ExpansionManagerImport"
  - "vs.codesnippetmanager"
helpviewer_keywords: 
  - "frammenti di codice"
  - "frammenti di codice, espansione"
  - "frammenti di codice, parametri di sostituzione"
  - "frammenti di codice, racchiudi tra"
  - "parametri di sostituzione"
  - "racchiudi tra"
ms.assetid: 85976ad9-4c9a-4e7b-896e-66ec6f955199
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Frammenti di codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I frammenti di codice sono piccoli blocchi di codice riutilizzabili che possono essere inseriti in un file di codice usando un comando di menu di scelta rapida o una combinazione di tasti di scelta rapida.  In genere contengono blocchi di codice comunemente usati, ad esempio blocchi try\-finally o if\-else, ma possono essere usati per inserire intere classi o metodi.  
  
## Frammenti di espansione e frammenti Racchiudi tra  
 In Visual Studio sono disponibili due tipi di frammento di codice: frammenti di espansione, che vengono aggiunti in un punto di inserimento specificato e possono sostituire un collegamento al frammento, e frammenti Racchiudi tra \(solo C\# e C\+\+\), che vengono aggiunti a un blocco di codice selezionato.  
  
 Un esempio di un frammento di inserimento: in C\# viene usato il collegamento tryf per inserire un blocco try\-finally:  
  
```  
try  
{  
  
}  
finally  
{  
  
}  
  
```  
  
 È possibile inserire questo frammento di codice facendo clic su **Inserisci frammento di codice** nel menu di scelta rapida della finestra del codice, quindi **Visual C\#**, quindi digitare `tryf`, quindi TAB oppure è possibile digitare `tryf` e premere TAB \+ TAB.  
  
 Un esempio di un frammento Racchiudi tra: in C\+\+ il collegamento `if` può essere usato come frammento di inserimento o come frammento Racchiudi tra.  Se si seleziona una riga di codice \(ad esempio `return FALSE;`\), quindi si fa clic su **Racchiudi tra**, quindi **if**, il frammento viene espanso intorno alla riga:  
  
```  
if (true)  
{  
    return FALSE;  
}  
  
```  
  
## Parametri di sostituzione del frammento  
 I frammenti di codice possono contenere parametri di sostituzione, cioè segnaposto che è necessario sostituire per adattare il codice preciso che si scrive.  Nell'esempio precedente `true` è un parametro di sostituzione, che è possibile sostituire con la condizione appropriata.  La sostituzione effettuata viene ripetuta per ogni istanza dello stesso parametro di sostituzione nel frammento.  
  
 Ad esempio, in Visual Basic è presente un frammento di codice che inserisce una proprietà.  Fare clic su **Inserisci frammento di codice** nel menu di scelta rapida della finestra del codice, quindi su **Criteri di codice**, quindi su **Proprietà, procedure, eventi**, infine su Definisci una proprietà.  Viene inserito il codice seguente:  
  
```  
Private newPropertyValue As String  
Public Property NewProperty() As String  
    Get  
        Return newPropertyValue  
    End Get  
    Set(ByVal value As String)  
        newPropertyValue = value  
    End Set  
End Property  
  
```  
  
 Se si modifica `newPropertyValue` in `m_property`, tutte le istanze di `newPropertyValue` vengono modificate.  Se si modifica `String` in `Int` nella dichiarazione di proprietà, anche il valore nel metodo set viene modificato in `Int`.  
  
## Gestione frammenti di codice  
 È possibile visualizzare tutti i frammenti di codice attualmente installati, nonché il relativo percorso su disco, facendo clic su **Strumenti\/Gestione frammenti di codice**.  I frammenti di codice vengono visualizzati in base al linguaggio.  
  
 È possibile aggiungere e rimuovere le directory del frammento di codice con i pulsanti **Aggiungi** e **Rimuovi** nella finestra di dialogo **Gestione frammenti di codice**.  Per aggiungere frammenti di codice singoli, usare il pulsante **Importa**.  
  
## Vedere anche  
 [Procedura dettagliata: creazione di un frammento di codice](../ide/walkthrough-creating-a-code-snippet.md)   
 [Procedura: distribuire i frammenti di codice](../ide/how-to-distribute-code-snippets.md)   
 [Procedure consigliate per l'utilizzo dei frammenti di codice](../ide/best-practices-for-using-code-snippets.md)   
 [Risoluzione dei problemi relativi ai frammenti di codice](../ide/troubleshooting-snippets.md)   
 [Frammenti di codice Visual C\#](../ide/visual-csharp-code-snippets.md)   
 [Frammenti di codice Visual C\#](../ide/visual-cpp-code-snippets.md)   
 [Riferimento dello schema dei frammenti di codice](../ide/code-snippets-schema-reference.md)