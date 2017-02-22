---
title: "Procedura: utilizzare procedure guidate con modelli di progetto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfaccia IWizard"
  - "modelli di progetto [Visual Studio], procedure guidate"
  - "modelli [Visual Studio], procedure guidate"
  - "modelli di Visual Studio, procedure guidate"
  - "procedure guidate [Visual Studio], modelli di progetto"
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: 23
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: utilizzare procedure guidate con modelli di progetto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio fornisce l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> che, se implementata, consente di eseguire il codice personalizzato quando un utente crea un progetto da un modello.  
  
 La personalizzazione dei modelli di progetto può essere utilizzata per:  
  
-   Visualizzare l'interfaccia utente personalizzata che riceve l'input dell'utente per applicare parametri al modello.  
  
-   Aggiungere valori di parametro da utilizzare nel modello.  
  
-   Aggiungere al modello file aggiuntivi.  
  
-   Eseguire praticamente qualsiasi azione consentita dal modello a oggetti di automazione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in un progetto.  
  
 I metodi di interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> vengono chiamati in diversi momenti durante la creazione del progetto, a cominciare dal momento in cui l'utente sceglie **OK** nella finestra di dialogo **Nuovo progetto**.  Ogni metodo di interfaccia viene denominato per descrivere il punto in cui viene chiamato.  Ad esempio, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> viene chiamato non appena viene avviata la creazione del progetto e rappresenta quindi una buona posizione in cui scrivere il codice personalizzato per ricevere l'input dell'utente.  
  
 Gran parte del codice scritto per le creazioni guidate personalizzate utilizza l'oggetto <xref:EnvDTE.DTE>, che è l'oggetto principale del modello a oggetti di automazione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per la personalizzazione del progetto.  Per ulteriori informazioni sul modello a oggetti di automazione, vedere [Estensione dell'ambiente Visual Studio](../Topic/Extending%20the%20Visual%20Studio%20Environment.md) e [Riferimenti su Extensibility e automazione](../Topic/Automation%20and%20Extensibility%20Reference.md).  
  
## Creazione di una Creazione guidata modelli personalizzata  
 In questo argomento viene illustrato come creare una creazione guidata personalizzata che consente di aprire un Window Form prima della creazione del progetto.  Il form consente all'utente di aggiungere un valore di parametro personalizzato che verrà quindi aggiunto al codice sorgente durante la creazione del progetto.  Le fasi principali della procedura, con descrizioni dettagliate, sono riportate di seguito.  
  
#### Per creare una creazione guidata modelli personalizzata  
  
1.  Creare un assembly che implementi l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
2.  Installare l'assembly nella Global Assembly Cache.  
  
3.  Creare un progetto e utilizzare l'**Esportazione guidata modelli** per creare un modello per il progetto.  
  
4.  Modificare il modello aggiungendo un elemento `WizardExtension` nel file vstemplate, per collegare il modello all'assembly che implementa <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
5.  Creare un nuovo progetto utilizzando la creazione guidata personalizzata.  
  
## Implementazione dell'interfaccia IWizard  
 La prima fase del processo consiste nella creazione di un assembly che implementi l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  Questo assembly utilizza il metodo <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> per visualizzare un Windows Form che consente all'utente di aggiungere un valore di parametro personalizzato, che verrà quindi utilizzato durante la creazione del progetto.  
  
> [!NOTE]
>  Nell'esempio viene utilizzato [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] per implementare <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>, anche se è possibile utilizzare [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
#### Per implementare l'interfaccia IWizard  
  
1.  Creare un nuovo progetto di libreria di classi.  
  
2.  Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  Vedere il codice riportato di seguito per un esempio [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] di un'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> completamente implementata.  
  
 Nell'esempio sono contenuti due file di codice: `IWizardImplementation`, una classe che implementa l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> e `UserInputForm`, il Windows Form per l'input dell'utente.  
  
### Classe WizardImplementation  
 La classe `IWizardImplementation` contiene le implementazioni del metodo per ogni membro dell'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  Nell'esempio riportato di seguito solo il metodo <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> esegue un'attività.  Tutti gli altri metodi non eseguono alcunché o restituiscono `true`.  
  
 Il metodo <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> accetta quattro parametri:  
  
-   Un parametro <xref:System.Object> di cui è possibile eseguire sull'oggetto <xref:EnvDTE._DTE> di primo livello per consentire la personalizzazione del progetto.  
  
-   Parametro <xref:System.Collections.Generic.Dictionary%602> che contiene una raccolta di tutti i parametri definiti in precedenza nel modello.  Per ulteriori informazioni sui parametri dei modelli, vedere [Parametri di template](../ide/template-parameters.md).  
  
-   Parametro <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> che contiene informazioni sul tipo di modello che viene utilizzato.  
  
-   Array <xref:System.Object> che contiene un insieme di parametri passati alla procedura guidata da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Nell'esempio riportato di seguito viene aggiunto un valore di parametro dal form dell'input dell'utente al parametro <xref:System.Collections.Generic.Dictionary%602>.  Ogni istanza del parametro `$custommessage$` nel progetto verrà sostituita con il testo immesso dall'utente.  È necessario aggiungere al progetto gli assembly riportati di seguito.  
  
1.  EnvDTE.dll  
  
2.  Microsoft.VisualStudio.TemplateWizardInterface.dll  
  
3.  System.Windows.Forms.dll  
  
> [!IMPORTANT]
>  Lo UserInputForm utilizzato in questo esempio è definito nella sezione seguente.  
  
```c#  
using System;  
using System.Collections.Generic;  
using Microsoft.VisualStudio.TemplateWizard;  
using System.Windows.Forms;  
using EnvDTE;  
  
namespace CustomWizard  
{  
    public class IWizardImplementation:IWizard  
    {  
        private UserInputForm inputForm;  
        private string customMessage;  
  
        // This method is called before opening any item that   
        // has the OpenInEditor attribute.  
        public void BeforeOpeningFile(ProjectItem projectItem)  
        {  
        }  
  
        public void ProjectFinishedGenerating(Project project)  
        {  
        }  
  
        // This method is only called for item templates,  
        // not for project templates.  
        public void ProjectItemFinishedGenerating(ProjectItem   
            projectItem)  
        {  
        }  
  
        // This method is called after the project is created.  
        public void RunFinished()  
        {  
        }  
  
        public void RunStarted(object automationObject,  
            Dictionary<string, string> replacementsDictionary,  
            WizardRunKind runKind, object[] customParams)  
        {  
            try  
            {  
                // Display a form to the user. The form collects   
                // input for the custom message.  
                inputForm = new UserInputForm();  
                inputForm.ShowDialog();  
  
                customMessage = inputForm.get_CustomMessage();  
  
                // Add custom parameters.  
                replacementsDictionary.Add("$custommessage$",   
                    customMessage);  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.ToString());  
            }  
        }  
  
        // This method is only called for item templates,  
        // not for project templates.  
        public bool ShouldAddProjectItem(string filePath)  
        {  
            return true;  
        }          
    }  
}  
```  
  
### Form dell'input dell'utente  
 Il form dell'input dell'utente fornisce un semplice form per l'inserimento di un parametro personalizzato.  Nel form è contenuta una casella di testo chiamata `textBox1` e un pulsante chiamato `button1`.  Se si fa clic sul pulsante, il testo nella casella di testo viene archiviato nel parametro `customMessage`.  
  
##### Per aggiungere un Windows Form alla soluzione  
  
1.  Aggiungere il codice seguente al file contenente l'implementazione della procedura guidata.  
  
```c#  
public partial class UserInputForm : Form  
{  
    private string customMessage;  
    private TextBox textBox1;  
  
    public UserInputForm()  
    {   
        textBox1 = new TextBox();  
        this.Controls.Add(textBox1);  
    }  
  
    public string get_CustomMessage()  
    {  
        return customMessage;  
    }  
  
    private void textBox1_TextChanged(object sender, EventArgs e)  
    {  
        customMessage = textBox1.Text;  
        this.Dispose();  
    }  
}  
```  
  
## Installazione dell'assembly nella Global Assembly Cache  
 L'assembly che implementa <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> deve essere firmato con un nome sicuro e installato nella Global Assembly Cache.  
  
#### Per installare l'assembly nella Global Assembly Cache  
  
1.  Firmare l'assembly con un nome sicuro.  Per ulteriori informazioni, vedere [Procedura: firmare un assembly con un nome sicuro](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md) o [How to: Sign an Assembly \(Visual Studio\)](http://msdn.microsoft.com/it-it/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
2.  Installare un assembly con nome sicuro nella Global Assembly Cache.  Per ulteriori informazioni, vedere [Procedura: installare un assembly nella Global Assembly Cache](../Topic/How%20to:%20Install%20an%20Assembly%20into%20the%20Global%20Assembly%20Cache.md).  
  
## Creazione di un progetto da utilizzare come modello  
 In questo esempio il progetto utilizzato come modello è un'applicazione console in cui viene visualizzato il messaggio specificato nell'input dell'utente della creazione guidata personalizzata.  
  
#### Per creare il progetto di esempio  
  
1.  Creare una nuova applicazione console [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
2.  Nel metodo `Main` dell'applicazione aggiungere la riga di codice riportata di seguito.  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     Il parametro `$custommessage$` viene sostituito con il testo immesso nel form dell'input dell'utente quando viene creato un progetto dal modello.  
  
3.  Nel menu **File** scegliere **Esporta modello**.  
  
4.  Nell'**Esportazione guidata modelli** fare clic su **Modello di progetto**, selezionare il progetto corretto, quindi fare clic su **Avanti**.  
  
5.  Nell'**Esportazione guidata modelli** immettere informazioni descrittive sul modello, selezionare la casella di controllo **Importa automaticamente il modello in Visual Studio**, quindi fare clic su **Fine**.  
  
     Il modello appare ora nella finestra di dialogo **Nuovo progetto** ma non utilizza la creazione guidata personalizzata.  
  
 Nell'esempio riportato di seguito viene illustrato il file di codice completo prima dell'esportazione in un modello.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
namespace TemplateProject  
{  
    class WriteMessage  
    {  
        static void Main(string[] args)  
        {  
            Console.WriteLine("$custommessage$");  
        }  
    }  
}  
```  
  
## Modifica del modello  
 Una volta creato il modello, che appare nella finestra di dialogo **Nuovo progetto**, è necessario modificarlo in modo che utilizzi l'assembly creato nelle fasi precedenti.  
  
#### Per aggiungere la creazione guidata personalizzata al modello  
  
1.  Individuare il file .zip che contiene il modello.  
  
    1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
    2.  Fare clic su **Progetti e soluzioni**.  
  
    3.  Leggere la casella di testo **Percorso dei modelli di progetto utente di Visual Studio**.  
  
     Per impostazione predefinita, si tratta della directory Documenti\\Visual Studio *Version*\\Templates\\ProjectTemplates.  
  
2.  Estrarre il file con estensione zip.  
  
3.  Aprire il file .vstemplate in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Dopo l'elemento `TemplateContent`, aggiungere un elemento [Elemento WizardExtension \(modelli di Visual Studio\)](../extensibility/wizardextension-element-visual-studio-templates.md) con il nome sicuro dell'assembly della creazione guidata personalizzata.  Per ulteriori informazioni sull'individuazione del nome sicuro dell'assembly, vedere [Procedura: visualizzare il contenuto della Global Assembly Cache](../Topic/How%20to:%20View%20the%20Contents%20of%20the%20Global%20Assembly%20Cache.md) e [Procedura: aggiungere un riferimento a un assembly con nome sicuro](../Topic/How%20to:%20Reference%20a%20Strong-Named%20Assembly.md).  
  
     Nell'esempio riportato di seguito viene illustrato un elemento `WizardExtension`.  
  
    ```  
    <WizardExtension>  
        <Assembly>CustomWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=fa3902f409bb6a3b</Assembly>  
        <FullClassName>CustomWizard.IWizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
## Utilizzo della creazione guidata personalizzata  
 A questo punto è possibile creare un progetto dal modello e utilizzare la creazione guidata personalizzata.  
  
#### Per utilizzare la creazione guidata personalizzata  
  
1.  Scegliere **Nuovo progetto** dal menu **File**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** individuare il modello, digitare un nome e scegliere **OK**.  
  
     Verrà aperto il form dell'input dell'utente della procedura guidata.  
  
3.  Digitare un valore per il parametro personalizzato e fare clic sul pulsante.  
  
     Il form dell'input dell'utente della procedura guidata viene chiuso e viene creato un progetto dal modello.  
  
4.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file del codice sorgente, quindi scegliere **Visualizza codice**.  
  
     È importante sottolineare che `$custommessage$` è stato sostituito con il testo immesso nel form dell'input dell'utente della procedura guidata.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
 [Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)   
 [Elemento WizardExtension \(modelli di Visual Studio\)](../extensibility/wizardextension-element-visual-studio-templates.md)