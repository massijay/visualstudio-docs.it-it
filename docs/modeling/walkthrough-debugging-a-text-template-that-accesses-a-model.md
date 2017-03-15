---
title: 'Procedura dettagliata: Debug di un modello di testo che accede a un modello | Documenti di Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af46a7fe-6b98-4d3d-b816-0bbf8e81e220
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 7bbe2b592dc315bc0885e1f1ca4c890e4e66255d
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Procedura dettagliata: debug di un modello di testo che accede a un modello
Quando si modificano o si aggiungono modelli di testo in una soluzione di linguaggio specifico di dominio, è possibile ricevere errori quando il motore trasforma il modello di codice sorgente o durante la compilazione del codice generato. La seguente procedura dettagliata vengono illustrate alcune delle operazioni che è possibile eseguire per eseguire il debug di un modello di testo.  
  
> [!NOTE]
>  Per ulteriori informazioni sul testo in generale, vedere Modelli [la generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md). Per ulteriori informazioni sul debug di modelli di testo, vedere [procedura dettagliata: debug di un modello di testo](http://msdn.microsoft.com/Library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).  
  
## <a name="creating-a-domain-specific-language-solution"></a>Creazione di una soluzione di linguaggio specifico di dominio  
 In questa procedura, si crea una soluzione di linguaggio specifico di dominio che ha le caratteristiche seguenti:  
  
-   Nome: DebuggingTestLanguage  
  
-   Modello di soluzione: linguaggio minimo  
  
-   Estensione del file:. ddd  
  
-   Nome della società: Fabrikam  
  
 Per ulteriori informazioni sulla creazione di una soluzione di linguaggio specifico di dominio, vedere [procedura: creare una soluzione di linguaggio specifico di dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="creating-a-text-template"></a>Creazione di un modello di testo  
 Aggiungere un modello di testo alla soluzione.  
  
#### <a name="to-create-a-text-template"></a>Per creare un modello di testo  
  
1.  Compilare la soluzione e avviarne l'esecuzione nel debugger. (Nel **compilare** menu, fare clic su **Ricompila soluzione**e quindi sul **Debug** dal menu fare clic su **Avvia debug**.) Una nuova istanza di Visual Studio apre il progetto di debug.  
  
2.  Aggiungere un file di testo denominato `DebugTest.tt` al progetto di debug.  
  
3.  Assicurarsi che il **strumento personalizzato** di DebugTest.tt è impostata su `TextTemplatingFileGenerator`.  
  
## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Debug di direttive di accedere a un modello da un modello di testo  
 Prima di accedere a un modello dalle istruzioni e le espressioni in un modello di testo, è prima necessario chiamare un processore di direttiva generato. Chiamare il processore di direttiva generato rende le classi nel modello disponibile per il codice del modello di testo come proprietà. Per ulteriori informazioni, vedere [l'accesso a modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md).  
  
 Nelle procedure seguenti, si eseguirà il debug di un nome di direttiva non corretto e un nome di proprietà errata.  
  
#### <a name="to-debug-an-incorrect-directive-name"></a>Per eseguire il debug di un nome di direttiva non corretto  
  
1.  Sostituire il codice in DebugTest.tt con il codice seguente:  
  
    > [!NOTE]
    >  Il codice contiene un errore. È stato introdotto per eseguirne il debug.  
  
    ```c#  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb#  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2.  In **Esplora**, fare doppio clic su DebugTest.tt e quindi fare clic su **Esegui strumento personalizzato**.  
  
     Il **elenco errori** finestra viene visualizzato questo errore:  
  
     **Il processore denominato 'DebuggingTestLanguageDirectiveProcessor' non supporta la direttiva denominata 'modelRoot'. La trasformazione non verrà eseguita.**  
  
     In questo caso, la direttiva chiamata contiene un nome di direttiva non corretto. È stato specificato `modelRoot` come il nome della direttiva, ma il nome corretto della direttiva `DebuggingTestLanguage`.  
  
3.  Fare doppio clic su errore nel **elenco errori** finestra per passare al codice.  
  
4.  Per correggere il codice, modificare il nome della direttiva di `DebuggingTestLanguage`.  
  
     La modifica viene evidenziata.  
  
    ```c#  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
    ```vb#  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
5.  In **Esplora**, fare doppio clic su DebugTest.tt e quindi fare clic su **Esegui strumento personalizzato**.  
  
     A questo punto il sistema trasforma il modello di testo e genera il file di output corrispondente. Non può visualizzare eventuali errori durante il **elenco errori** finestra.  
  
#### <a name="to-debug-an-incorrect-property-name"></a>Per eseguire il debug di un nome di proprietà non corretto  
  
1.  Sostituire il codice in DebugTest.tt con il codice seguente:  
  
    > [!NOTE]
    >  Il codice contiene un errore. È stato introdotto per eseguirne il debug.  
  
    ```c#  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb#  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2.  Nel **Esplora**, fare doppio clic su DebugTest.tt e quindi fare clic su **Esegui strumento personalizzato**.  
  
     Il **elenco errori** finestra viene visualizzato uno di questi errori:  
  
     (C#)  
  
     **Compilazione trasformazione: Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation' non contiene una definizione per 'ExampleModel'**  
  
     (Visual Basic)  
  
     **Compilazione trasformazione: 'ExampleModel' non è un membro di ' Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation'.**  
  
     In questo caso, il codice del modello di testo contiene un nome di proprietà errata. È stato specificato `ExampleModel` come il nome della proprietà, ma la proprietà corretta è nome `LibraryModel`. È possibile trovare il nome corretto della proprietà di fornisce parametro, come illustrato nel codice seguente:  
  
    ```  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
    ```  
  
3.  Fare doppio clic nella finestra Elenco errori per passare al codice di errore.  
  
4.  Per correggere il codice, modificare il nome di proprietà in `LibraryModel` nel codice del modello di testo.  
  
     Le modifiche sono evidenziate.  
  
    ```c#  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.LibraryModel #>  
    <#  
    foreach (ExampleElement element in this.LibraryModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb#  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.LibraryModel #>  
    <#  
    For Each element as ExampleElement in Me.LibraryModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
5.  In **Esplora**, fare doppio clic su DebugTest.tt e quindi fare clic su **Esegui strumento personalizzato**.  
  
     A questo punto il sistema trasforma il modello di testo e genera il file di output corrispondente. Non può visualizzare eventuali errori durante il **elenco errori** finestra.
