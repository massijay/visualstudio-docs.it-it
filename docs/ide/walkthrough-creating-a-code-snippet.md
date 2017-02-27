---
title: "Procedura dettagliata: creazione di un frammento di codice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "frammenti di codice, creazione"
  - "frammenti di codice, importazioni"
  - "frammenti di codice, riferimenti"
  - "frammenti di codice, sostituzioni"
  - "frammenti di codice, collegamento"
  - "frammenti di codice, modello"
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Procedura dettagliata: creazione di un frammento di codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile creare un frammento di codice con solo alcuni passaggi.  È sufficiente creare un file XML, compilare gli elementi appropriati e aggiungere il codice.  È inoltre possibile aggiungere riferimenti e i parametri sostitutivi al codice.  È possibile aggiungere il frammento all'installazione di Visual Studio tramite il pulsante di importazione in Gestione frammenti di codice \(**Strumenti\/Gestione frammenti di codice**\).  
  
> [!TIP]
>  Per informazioni su come scrivere frammenti di codice più facilmente, cercare nel sito Web CodePlex strumenti della community quali [Snippet Editor](http://go.microsoft.com/fwlink/?LinkId=251033).  
  
## Modello del frammento  
 Di seguito è riportato il modello di frammento di base:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CodeSnippets  
    xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title></Title>  
        </Header>  
        <Snippet>  
            <Code Language="">  
                <![CDATA[]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
  
```  
  
### Per creare un frammento di codice  
  
1.  Creare un nuovo file XML in Visual Studio e aggiungere il modello visualizzato sopra.  
  
2.  Compilare il titolo del frammento di codice, ad esempio "Hello World VB", nell'elemento Title.  
  
3.  Compilare il linguaggio del frammento di codice nell'attributo Languages dell'elemento Code.  Per questo esempio, utilizzare "VB".  
  
4.  Aggiungere codice nella sezione CDATA nell'elemento di codice, ad esempio:  
  
    ```  
    <Code Language="VB">  
        <![CDATA[Console.WriteLine("Hello, World!")]]>  
    </Code>  
  
    ```  
  
5.  Salvare il frammento di codice come VBCodeSnippet.snippet.  
  
### Per aggiungere un frammento di codice a Visual Studio  
  
1.  È possibile aggiungere frammenti all'installazione di Visual Studio tramite Gestione frammenti di codice.  Aprire Gestione frammenti di codice \(**Strumenti\/Gestione frammenti di codice**\).  
  
2.  Fare clic sul pulsante **Importa**.  
  
3.  Andare al percorso in cui è stato salvato il frammento di codice nella procedura precedente, selezionarlo e fare clic su **Apri**.  
  
4.  La finestra di dialogo **Importa frammento di codice** viene aperta, richiedendo di specificare dove aggiungere il frammento dalle opzioni nel riquadro di destra.  È consigliabile che una delle opzioni sia **Frammenti di codice**.  Selezionarlo, quindi fare clic su **Fine**, quindi **OK**.  
  
5.  Il frammento viene copiato nel percorso seguente:  
  
     `%USERPROFILE%\Documenti\Visual Studio 2013\Frammenti di codice\Visual Basic\Frammenti di codice`  
  
6.  Testare il frammento aprendo un progetto di Visual Basic e un file di codice.  Nel file fare clic su **Inserisci frammento di codice** nel menu di scelta rapida, quindi **Frammenti di codice**.  Dovrebbe comparire un frammento denominato **Frammento di codice Visual Basic**.  Doppio clic su di esso.  
  
7.  Si dovrebbe visualizzare `Console.WriteLine("Hello, World!")` inserito nel codice.  
  
### Aggiunta di descrizione e campi collegamento  
  
1.  I campi di descrizione forniscono ulteriori informazioni sul frammento di codice una volta visualizzato in Gestione frammenti di codice.  Il collegamento è un tag che gli utenti possono digitare per inserire il frammento.  Modificare il frammento di codice aggiunto aprendo il file `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet`.  
  
2.  Aggiungere gli elementi Author e Description all'elemento Intestazione e riempirli.  
  
3.  L'elemento di intestazione dovrebbe avere il seguente aspetto:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
    </Header>  
  
    ```  
  
4.  Aprire Gestione frammenti di codice e selezionare il frammento di codice in uso.  Nel riquadro di destra si vedrà che i campi Descrizione e Autore sono ora popolati.  
  
5.  Per aggiungere un collegamento, aggiungere un elemento di collegamento accanto all'elemento descrizione e autore:  
  
    ```  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
        <Shortcut>hello</Shortcut>  
    </Header>  
  
    ```  
  
6.  Salvare il file frammento nuovamente.  
  
7.  Per testare il collegamento, aprire un progetto Visual Basic. e aprire un file di codice.  Digitare `hello` nel file e premere TAB.  Il codice dei frammenti deve essere inserito.  
  
### Per aggiungere riferimenti e importazioni  
  
1.  Con i frammenti mancanti di Visual Basic è possibile aggiungere un riferimento a un progetto utilizzando l'elemento Riferimenti e aggiungere una dichiarazione Importazioni tramite l'elemento Importazioni. I frammenti di codice in altri linguaggi non dispongono di questa funzionalità. Ad esempio, se `Console.WriteLine` nell'esempio di codice viene impostato su `MessageBox.Show`, potrebbe essere necessario aggiungere l'assembly System.Windows.Forms.dll al progetto.  
  
2.  Aprire il frammento di codice in uso.  
  
3.  Aggiungere l'elemento References sotto l'elemento del frammento:  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Windows.Forms.dll</Assembly>  
        </Reference>  
    </References>  
  
    ```  
  
4.  Aggiungere l'elemento Imports sotto l'elemento del frammento:  
  
    ```  
    <Imports>  
        <Import>  
           <Namespace>System.Windows.Forms</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
5.  Modificare la sezione CDATA come indicato di seguito:  
  
    ```  
    <![CDATA[MessageBox.Show("Hello, World!")]]>  
    ```  
  
6.  Salvare il frammento di codice.  
  
7.  Aprire un progetto Visual Basic e aggiungere il frammento di codice.  
  
8.  Verrà visualizzata un'istruzione Imports all'inizio del file di codice:  
  
    ```  
    Imports System.Windows.Forms  
  
    ```  
  
9. Verificare le proprietà del progetto.  La scheda Riferimenti include un riferimento a System.Windows.Forms.dll.  
  
### Aggiunta di sostituzioni  
  
1.  È possibile desiderate parti dei frammenti di codice da sostituire dall'utente, ad esempio se si aggiunge una variabile e si desidera che l'utente sostituisca la variabile con una nel progetto corrente.  È possibile fornire due tipi di sostituzioni: valori letterali e oggetti.  I valori letterali sono stringhe di un certo tipo \(stringhe letterali, nomi di variabili o rappresentazioni di stringa di valori numerici\).  Gli oggetti sono istanze di alcuni tipi diversi da una stringa.  In questa procedura verrà dichiarata una sostituzione di valore letterale e una sostituzione di oggetto e il codice verrà modificato in modo da fare riferimento a queste sostituzioni.  
  
2.  Aprire il frammento di codice in uso.  
  
3.  In questo esempio viene utilizzata una stringa di connessione SQL, pertanto è necessario modificare gli elementi di Importazioni e riferimenti per aggiungere i riferimenti appropriati:  
  
    ```  
    <References>  
        <Reference>  
            <Assembly>System.Data.dll</Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>System.Xml.dll</Assembly>  
        </Reference>  
    </References>  
    <Imports>  
        <Import>  
            <Namespace>System.Data</Namespace>  
        </Import>  
        <Import>  
            <Namespace>System.Data.SqlClient</Namespace>  
        </Import>  
    </Imports>  
  
    ```  
  
4.  Per dichiarare una sostituzione di valore letterale per la stringa di connessione SQL, aggiungere un elemento delle dichiarazioni sotto l'elemento del frammento e in esso aggiungere un elemento letterale con i sottoelementi per l'ID, la descrizione comando e il valore predefinito per la sostituzione:  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
    </Declarations>  
  
    ```  
  
5.  Per dichiarare una sostituzione di oggetto per la connessione SQL, aggiungere un elemento oggetto nell'elemento di dichiarazioni e aggiungere i sottoelementi per l'ID, il tipo di oggetto, la descrizione comando e il valore predefinito.  L'elemento di dichiarazioni risultante dovrebbe avere il seguente aspetto:  
  
    ```  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
        <Object>  
            <ID>SqlConnection</ID>  
            <Type>System.Data.SqlClient.SqlConnection</Type>  
            <ToolTip>Replace with a connection object in your application.</ToolTip>  
            <Default>dcConnection</Default>  
        </Object>  
    </Declarations>  
    ```  
  
6.  Nella sezione del codice fare riferimento alle sostituzioni con segni $ circostanti, ad esempio `$sostituzione$`:  
  
    ```  
    <Code Language="VB" Kind="method body">  
        <![CDATA[Dim daCustomers As SqlDataAdapter  
            Dim selectCommand As SqlCommand  
  
            daCustomers = New SqlClient.SqlDataAdapter()  
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)  
            daCustomers.SelectCommand = selectCommand  
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>  
    </Code>  
    ```  
  
7.  Salvare il frammento di codice.  
  
8.  Aprire un progetto Visual Basic e aggiungere il frammento di codice.  
  
9. Il codice dovrebbe essere analogo al seguente, dove le sostituzioni `SQL connection string` e `dcConnection` sono evidenziate in arancione chiaro.  Premere TAB per passare da una all'altra.  
  
    ```  
    Dim daCustomers As SqlDataAdapter  
    Dim selectCommand As SqlCommand  
  
    daCustomers = New SqlClient.SqlDataAdapter()  
    selectCommand = New SqlClient.SqlCommand("SQL connection string")  
    daCustomers.SelectCommand = selectCommand  
    daCustomers.SelectCommand.Connection = dcConnection  
  
    ```  
  
## Vedere anche  
 [Riferimento dello schema dei frammenti di codice](../ide/code-snippets-schema-reference.md)