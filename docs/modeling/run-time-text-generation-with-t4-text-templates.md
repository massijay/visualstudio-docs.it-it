---
title: "Run-Time Text Generation with T4 Text Templates | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Preprocessed Text Template project item"
  - "TextTemplatingFilePreprocessor custom tool"
  - "text templates, TransformText() method"
  - "text templates, generating files at run time"
ms.assetid: 79b4b3c6-a9a7-4446-b6fd-e2388fc6b05f
caps.latest.revision: 22
caps.handback.revision: 22
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Run-Time Text Generation with T4 Text Templates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile generare stringhe di testo nell'applicazione in fase di esecuzione utilizzando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i modelli di testo di runtime.  Non è necessario che nel computer su cui viene eseguita l'applicazione sia installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  I modelli di runtime sono talvolta denominati "pre\-elaborato i modelli di testo" perché in fase di compilazione, il modello genera il codice che viene eseguito in fase di esecuzione.  
  
 Ogni modello è una combinazione tra il testo come verrà visualizzato nella stringa generata e i frammenti di codice programma.  I frammenti del programma forniscono i valori per le parti variabili della stringa e controllano le parti ripetute e condizionali.  
  
 Ad esempio, il modello seguente potrebbe essere utilizzato in un'applicazione in grado di creare un rapporto HTML.  
  
```  
<#@ template language="C#" #>  
<html><body>  
<h1>Sales for Previous Month</h2>  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
This report is Company Confidential.  
</body></html>  
```  
  
 Si noti che il modello è una pagina HTML in cui le parti variabili sono state sostituite con codice programma.  È possibile iniziare la progettazione di tale pagina scrivendo un prototipo statico della pagina HTML.  È quindi possibile sostituire la tabella e le altre parti variabili con codice programma che genera il contenuto che varia da una volta all'altra.  
  
 L'utilizzo di un modello dell'applicazione consente di vedere più facilmente il formato finale dell'output rispetto a quanto sarebbe possibile, ad esempio, in una lunga serie di istruzioni write.  Apportare modifiche al formato dell'output è più facile e sicuro.  
  
## Creazione di un modello di testo della fase di esecuzione in qualsiasi applicazione  
  
#### Per creare un modello di testo della fase di esecuzione  
  
1.  In Esplora soluzioni, nel menu di scelta rapida del progetto, scegliere  **Aggiungi**,  **Nuovo elemento**.  
  
2.  Nel  **Aggiungi nuovo elemento** la finestra di dialogo, seleziona  **Modello di testo di Runtime**.  \(In [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] cercare in **Elementi comuni\\Generale**\).  
  
3.  Digitare un nome per il file modello.  
  
    > [!NOTE]
    >  Il nome del file modello sarà utilizzato come un nome di classe nel codice generato,  pertanto non deve contenere spazi o segni di punteggiatura.  
  
4.  Scegliere  **aggiungere**.  
  
     Verrà creato un nuovo file con estensione **.tt**.  La relativa proprietà **Strumento personalizzato** viene impostata su **TextTemplatingFilePreprocessor**.  Contiene le seguenti righe:  
  
    ```  
    <#@ template language="C#" #>  
    <#@ assembly name="System.Core" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="System.Text" #>  
    <#@ import namespace="System.Collections.Generic" #>  
    ```  
  
## Conversione di un file esistente in un modello della fase di esecuzione  
 Un modo semplice e pratico per creare un modello consiste nel convertire un esempio esistente dell'output.  Ad esempio, se l'applicazione genererà file HTML, si può iniziare creando un file HTML semplice.  Verificare che funzioni correttamente e che l'aspetto sia corretto.  Includerlo quindi nel progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e convertirlo in un modello.  
  
#### Per convertire un file di testo esistente in un modello della fase di esecuzione  
  
1.  Includere il file nel progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  In Esplora soluzioni, nel menu di scelta rapida del progetto, scegliere  **Aggiungi**,  **Elemento esistente**.  
  
2.  Impostare la proprietà **Strumenti personalizzati** del file su **TextTemplatingFilePreprocessor**.  In Esplora soluzioni, nel menu di scelta rapida del file, scegliere  **le proprietà**.  
  
    > [!NOTE]
    >  Se la proprietà è già impostata, verificare che sia **TextTemplatingFilePreprocessor** e non **TextTemplatingFileGenerator**.  Questo può accadere se si include un file che già dispone di estensione **.tt**.  
  
3.  Modificare l'estensione di file in **.tt**.  Anche se il passaggio è facoltativo, consente di evitare di aprire il file in un editor errato.  
  
4.  Rimuovere qualsiasi spazio o punteggiatura dalla parte principale del nome file.  Ad esempio, "Pagina Web.tt" è errato, mentre "PaginaWeb.tt" è corretto.  Il nome del file sarà utilizzato come nome di classe nel codice generato.  
  
5.  Inserire la seguente riga all'inizio del file:  Se si lavora a un progetto Visual Basic, sostituire "C\#" con "VB".  
  
     `<#@ template language="C#" #>`  
  
## Contenuto del modello della fase di esecuzione  
  
### Direttiva del modello  
 Mantenere la prima riga del modello invariata rispetto a quella del momento della creazione del file:  
  
 `<#@ template language="C#" #>`  
  
 Il parametro del linguaggio dipenderà dal linguaggio del progetto.  
  
### Contenuto semplice  
 Modificare il file **.tt** per contenere il testo che si desidera generare tramite l'applicazione.  Di seguito è riportato un esempio:  
  
```  
<html><body>  
<h1>Sales for January</h2>  
<!-- table to be inserted here -->  
This report is Company Confidential.  
</body></html>  
```  
  
### Codice programma incorporato  
 È possibile inserire codice programma tra `<#` e `#>`.  Di seguito è riportato un esempio:  
  
```c#  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
```  
  
```vb#  
<table>  
<#  
    For i As Integer = 1 To 10  
#>  
    <tr><td>Test name <#= i #> </td>  
      <td>Test value <#= i*i #> </td></tr>  
<#  
    Next  
#>  
</table>  
  
```  
  
 Si noti che le istruzioni sono inserite tra `<# ... #>` e le espressioni sono inserite tra `<#= ... #>`.  Per ulteriori informazioni, vedere [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md).  
  
## Utilizzo del modello  
  
### Codice compilato dal modello  
 Ogni qualvolta si salva il file **.tt**, verrà generato un file sussidiario con estensione **.cs** o con estensione **.vb**.  Per visualizzare questo file in Esplora soluzioni, espandere il nodo del file **.tt**.  In un progetto Visual Basic, sarà possibile espandere il nodo dopo avere fatto clic su **Mostra tutti i file** sulla barra degli strumenti di Esplora soluzioni.  
  
 Si noti che questo file sussidiario contiene una classe parziale che contiene un metodo denominato `TransformText()`.  Questo metodo può essere chiamato dall'applicazione.  
  
### Generazione di testo in fase di esecuzione  
 Nel codice dell'applicazione è possibile generare il contenuto del modello utilizzando una chiamata come la seguente:  
  
```c#  
MyWebPage page = new MyWebPage();  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
  
```  
  
```vb#  
Dim page = New My.Templates.MyWebPage  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
 Per inserire la classe generata in un particolare spazio dei nomi, impostare la proprietà **Custom Tool Namespace** del file modello di testo.  
  
### I modelli di testo di Runtime di debug  
 Eseguire il debug e test di modelli di testo di runtime nello stesso modo come normale codice.  
  
 È possibile impostare un punto di interruzione in un modello di testo.  Se si avvia l'applicazione in modalità di debug da Visual Studio, è possibile eseguire il codice e valutare espressioni di controllo nel modo consueto.  
  
### Passaggio di parametri nel costruttore  
 In genere, un modello deve importare alcuni dati da altre parti dell'applicazione.  Per facilitare questa operazione, il codice compilato dal modello è una classe parziale.  È possibile creare un'altra parte della stessa classe in un altro file nel progetto.  Quel file può includere un costruttore con parametri, proprietà e funzioni ai quali si accede dal codice incorporato nel modello e dal resto dell'applicazione.  
  
 Ad esempio, è possibile creare un file **MyWebPageCode.cs** separato:  
  
```c#  
partial class MyWebPage  
{  
    private MyData m_data;  
    public MyWebPage(MyData data) { this.m_data = data; }}  
```  
  
 Nel file modello **MyWebPage.tt** è possibile scrivere:  
  
```c#  
<h2>Sales figures</h2>  
<table>  
<# foreach (MyDataItem item in m_data.Items)   
   // m_data is declared in MyWebPageCode.cs  
   { #>  
      <tr><td> <#= item.Name #> </td>  
          <td> <#= item.Value #> </td></tr>  
<# } // end of foreach  
#>  
</table>  
```  
  
 Per utilizzare questo modello nell'applicazione:  
  
```c#  
MyData data = ...;  
MyWebPage page = new MyWebPage(data);  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
```  
  
#### Parametri del costruttore in Visual Basic  
 In [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] il file separato **MyWebPageCode.vb** contiene:  
  
```vb#  
Namespace My.Templates  
  Partial Public Class MyWebPage  
    Private m_data As MyData  
    Public Sub New(ByVal data As MyData)  
      m_data = data  
    End Sub  
  End Class  
End Namespace  
```  
  
 Il file modello potrebbe contenere:  
  
```vb#  
<#@ template language="VB" #>  
<html><body>  
<h1>Sales for January</h2>  
<table>  
<#  
    For Each item In m_data.Items  
#>  
    <tr><td>Test name <#= item.Name #> </td>  
      <td>Test value <#= item.Value #> </td></tr>  
<#  
    Next  
#>  
</table>  
This report is Company Confidential.  
</body></html>  
  
```  
  
 Il modello viene richiamato passando il parametro nel costruttore:  
  
```vb#  
Dim data = New My.Templates.MyData  
    ' Add data values here ....  
Dim page = New My.Templates.MyWebPage(data)  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
#### Passaggio dei dati nelle proprietà del modello  
 Un metodo alternativo per passare i dati al modello consiste nell'aggiungere proprietà pubbliche alla classe del modello in una definizione di classe parziale.  L'applicazione può impostare le proprietà prima di richiamare `TransformText()`.  
  
 È inoltre possibile aggiungere campi alla classe del modello in una definizione parziale.  In tal modo è possibile passare i dati tra esecuzioni successive del modello.  
  
### Utilizzare classi parziali per il codice  
 Molti sviluppatori preferiscono evitare di scrivere grandi quantità di codice nei modelli.  Definire invece i metodi in una classe parziale con lo stesso nome del file modello.  Chiamare tali metodi dal modello.  In questo modo, il modello mostra più chiaramente l'aspetto della stringa di output di destinazione.  Le discussioni sull'aspetto del risultato possono essere separate dalla logica della creazione dei dati che vengono visualizzati.  
  
### Assembly e riferimenti  
 Se si desidera che il codice del modello faccia riferimento a un assembly .NET o a un altro assembly, quale **System.Xml.dll**, è necessario aggiungerlo alla sezione **Riferimenti** del progetto secondo la normale procedura.  
  
 Se si desidera importare uno spazio dei nomi nella stessa modalità di un'istruzione `using`, è possibile utilizzare la direttiva `import`:  
  
```  
<#@ import namespace="System.Xml" #>  
```  
  
 È necessario posizionare queste direttive all'inizio del file, immediatamente dopo la direttiva `<#@template`.  
  
### Contenuto condiviso  
 Se si dispone di testo condiviso tra diversi modelli, è possibile posizionarlo in un file separato e includerlo in ogni file nel quale deve essere visualizzato:  
  
```  
<#@include file="CommonHeader.txt" #>  
```  
  
 Il contenuto incluso può contenere qualsiasi combinazione di codice programma e testo normale, altre direttive include e altre direttive.  
  
 La direttiva include può essere utilizzata ovunque all'interno del testo di un file modello o di un file incluso.  
  
### Ereditarietà tra modelli di testo della fase di esecuzione  
 È possibile condividere il contenuto tra modelli della fase di esecuzione scrivendo un modello della classe di base che può essere astratto.  Utilizzo di `inherits` parametro del `<@#template#>` direttiva fare riferimento a un'altra classe di modello di runtime.  
  
#### Modello di ereditarietà: frammenti nei metodi di base  
 Nel modello utilizzato nell'esempio riportato di seguito, notare i punti seguenti:  
  
-   La classe di base `SharedFragments` definisce i metodi all'interno dei blocchi della funzionalità di classe `<#+ ... #>`.  
  
-   La classe di base non contiene testo libero.  Tutti i blocchi di testo di tale classe si verificano invece nei metodi della funzionalità di classe.  
  
-   La classe derivata richiama i metodi definiti in `SharedFragments`.  
  
-   L'applicazione chiama il metodo `TextTransform()` della classe derivata, ma non trasforma la classe di base `SharedFragments`.  
  
-   Le classi di base e derivate sono modelli di testo di runtime: vale a dire la  **Strumento personalizzato** è impostata su  **TextTemplatingFilePreprocessor**.  
  
 **SharedFragments.tt:**  
  
```c#  
<#@ template language="C#" #>  
<#+  
protected void SharedText(int n)  
{  
#>  
   Shared Text <#= n #>  
<#+  
}  
// Insert more methods here if required.  
#>  
  
```  
  
 **MyTextTemplate1.tt:**  
  
```c#  
<#@ template language="C#" inherits="SharedFragments" #>  
begin 1  
   <# SharedText(2); #>  
end 1  
  
```  
  
 **MyProgram.cs:**  
  
```c#  
...   
MyTextTemplate1 t1  = new MyTextTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **Output risultante:**  
  
```  
begin 1  
    Shared Text 2  
end 1  
```  
  
#### Modello di ereditarietà: testo nel corpo di base  
 In questa alternativa all'utilizzo dell'ereditarietà del modello, la maggior parte del testo viene definito nel modello di base.  I modelli derivati forniscono dati e frammenti di testo che si adattano al contenuto di base.  
  
 **AbstractBaseTemplate1.tt:**  
  
```c#  
<#@ template language="C#" #>  
  
Here is the description for this derived template:  
  <#= this.Description #>  
  
Here is the fragment specific to this derived template:  
<#   
  this.PushIndent("  ");  
  SpecificFragment(42);   
  this.PopIndent();  
#>  
End of common template.  
<#+   
  // State set by derived class before calling TextTransform:  
  protected string Description = "";  
  // 'abstract' method to be defined in derived classes:  
  protected virtual void SpecificFragment(int n) { }  
#>  
  
```  
  
 **DerivedTemplate1.tt:**  
  
```c#  
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>  
<#   
  // Set the base template properties:  
  base.Description = "Description for this derived class";   
  
  // Run the base template:  
  base.TransformText();  
  
#>  
End material for DerivedTemplate1.  
  
<#+  
// Provide a fragment specific to this derived template:  
  
protected override void SpecificFragment(int n)  
{  
#>  
   Specific to DerivedTemplate1 : <#= n #>  
<#+  
}  
#>  
  
```  
  
 **Codice dell'applicazione:**  
  
```c#  
...   
DerivedTemplate1 t1 = new DerivedTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **Output risultante:**  
  
```  
Here is the description for this derived template:  
  Description for this derived class  
  
Here is the fragment specific to this derived template:  
     Specific to DerivedTemplate1 : 42  
End of common template.  
End material for DerivedTemplate1.  
```  
  
## Argomenti correlati  
 Modelli della fase di progettazione: se si desidera utilizzare un modello per generare codice che diventi parte dell'applicazione, vedere [Design\-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Modelli di runtime possono essere utilizzati in qualsiasi applicazione in cui vengono determinati i modelli e il loro contenuto in fase di compilazione.  Se si desidera invece scrivere un'estensione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che genera testo dai modelli che cambiano in fase di esecuzione, vedere [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## Vedere anche  
 [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md)   
 [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md)   
 [Understanding T4: Pre\-elaborato i modelli di testo da Oleg Synch](http://www.olegsych.com/2009/09/t4-preprocessed-text-templates/)