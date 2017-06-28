---
title: "Procedura: creare frammenti XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Procedura: creare frammenti XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'editor XML può essere utilizzato per creare nuovi frammenti di codice XML.L'editor comprende un frammento di codice XML, denominato "Snippet", ovvero un frammento standard per la creazione di nuovi frammenti di codice XML.  
  
## Per creare un nuovo frammento di codice XML  
 Per creare un nuovo frammento di codice XML, creare un nuovo file XML e utilizzare la funzionalità **Inserisci frammento**.  
  
1.  Scegliere **Nuovo** dal menu **File**, quindi **File**.  
  
2.  Scegliere **File XML**, quindi fare clic su **Apri**.  
  
3.  Fare clic con il pulsante destro del mouse e scegliere **Inserisci frammento**.  
  
4.  Selezionare **Frammento** dall'elenco e premere INVIO.  
  
5.  Se necessario, apportare modifiche al nuovo frammento.  
  
6.  Scegliere **Salva XMLFile.xml** dal menu **File**.  
  
     Viene visualizzata la finestra di dialogo **Salva file con nome**.  
  
7.  Immettere un nome per il nuovo frammento di codice e scegliere **Snippet Files** dall'elenco a discesa **Salva come**.  
  
8.  Utilizzare l'elenco a discesa **Salva in** per modificare il percorso del file nella cartella Documenti\\Visual Studio 2005\\Code Snippets\\XML\\My XML Snippets e quindi scegliere **Salva**.  
  
## Descrizione del frammento di codice  
 In questa sezione vengono descritti alcuni elementi chiave del frammento di codice standard.Per ulteriori informazioni sugli elementi dello schema utilizzati dai frammenti di codice XML, vedere [Riferimento dello schema dei frammenti di codice](../ide/code-snippets-schema-reference.md).  
  
### Elemento SnippetType  
 L'editor supporta due tipi di frammento di codice:  
  
```  
<SnippetTypes>  
  <SnippetType>SurroundsWith</SnippetType>  
  <SnippetType>Expansion</SnippetType>  
</SnippetTypes>  
```  
  
 Il tipo `Expansion` determina la visualizzazione del frammento di codice quando viene richiamato il comando **Inserisci frammento**.Il tipo `SurroundsWith` determina la visualizzazione del frammento di codice quando viene richiamato il comando **Racchiudi tra**.  
  
### Elemento di codice  
 L'elemento `Code` definisce il testo XML che verrà inserito quando viene richiamato il frammento di codice.  
  
> [!NOTE]
>  Il testo del frammento di codice XML deve essere racchiuso in una sezione `<![CDATA[...]]>`.  
  
 Di seguito viene riportato l'elemento `Code` creato dal frammento standard.  
  
```  
<Code Language="XML">  
  <![CDATA[<test>  
  <name>$name$</name>  
  $selected$ $end$</test>]]>  
</Code>  
```  
  
 L'elemento `Code` comprende tre variabili.  
  
-   $name$ è la variabile definita dall'utentee consente di creare un elemento `name`, che presenta un valore modificabile il cui valore predefinito è "name".Le variabili definite dall'utente vengono definite utilizzando l'elemento `Literal`.  
  
-   $selected$ è una variabile predefinitae rappresenta il testo che era stato selezionato nell'editor XML prima di richiamare il frammento di codice.La posizione di questa variabile determina la posizione del testo selezionato nel frammento di codice che racchiude la selezione.  
  
-   $end$ è una variabile predefinita.Quando l'utente preme INVIO per terminare la modifica dei campi del frammento di codice, la variabile determina la posizione in cui viene spostato l'accento circonflesso \(^\).  
  
 L'elemento `Code` consente l'inserimento del testo XML seguente:  
  
```  
<test>  
  <name>name</name>  
</test>  
```  
  
 Il valore dell'elemento nome viene contrassegnato come area modificabile.  
  
### Elemento Literal  
 L'elemento `Literal` viene utilizzato per identificare il testo di sostituzione che è possibile personalizzare dopo che è stato inserito nel file.Ad esempio, le stringhe letterali, i valori numerici e alcuni nomi di variabili possono essere dichiarati come letterali.È possibile definire un qualsiasi numero di valori formali nel frammento di codice XML e farvi riferimento più volte dall'interno del frammento.Di seguito viene riportato un esempio di elemento `Literal` che definisce una variabile $name$ il cui valore predefinito è "name."  
  
```  
<Literal>  
  <ID>name</ID>  
  <Default>name</Default>  
</Literal  
```  
  
 I valori formali possono anche fare riferimento a funzioni.Nell'editor XML è disponibile una funzione denominata **LookupPrefix**.La funzione **LookupPrefix** cerca l'URI dello spazio dei nomi specificato dalla posizione nel documento XML dalla quale viene richiamato il frammento e restituisce il prefisso dello spazio dei nomi definito per quel determinato spazio dei nomi, se disponibile, e include i due punti \(:\) nel nome.Di seguito viene riportato un esempio di elemento `Literal` che utilizza la funzione **LookupPrefix**.  
  
```  
<Literal Editable="false">  
   <ID>prefix</ID>  
   <Function>LookupPrefix("namespaceURI")</Function>  
</Literal>  
```  
  
 La variabile $prefix$ può quindi essere utilizzata in altri punti all'interno del frammento di codice XML.  
  
## Vedere anche  
 [Frammenti di codice XML](../xml-tools/xml-snippets.md)   
 [Procedura: utilizzare frammenti XML](../xml-tools/how-to-use-xml-snippets.md)   
 [Procedura: generare un frammento XML da XML Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)