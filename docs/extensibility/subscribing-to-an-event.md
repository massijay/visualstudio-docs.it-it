---
title: Sottoscrizione a un evento | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6bd1dd320ad5366ef494a8db958614d837529320
ms.lasthandoff: 02/22/2017

---
# <a name="subscribing-to-an-event"></a>Sottoscrizione a un evento
Questa procedura dettagliata viene illustrato come creare una finestra degli strumenti che risponde agli eventi in una tabella di documento (RDT) in esecuzione. Una finestra degli strumenti contiene un controllo utente che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>metodo connette l'interfaccia per gli eventi.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="subscribing-to-rdt-events"></a>La sottoscrizione di eventi RDT  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>Per creare un'estensione con una finestra degli strumenti  
  
1.  Creare un progetto denominato **RDTExplorer** utilizzando il modello di progetto VSIX e aggiungere un modello di elemento della finestra degli strumenti personalizzata denominato **RDTExplorerWindow**.  
  
     Per ulteriori informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
#### <a name="to-subscribe-to-rdt-events"></a>Per sottoscrivere eventi RDT  
  
1.  Aprire il file RDTExplorerWindowControl.xaml ed eliminare il pulsante denominato `button1`. Aggiungere un <xref:System.Windows.Forms.ListBox>controllare e accettare il nome predefinito.</xref:System.Windows.Forms.ListBox> L'elemento Grid dovrebbe essere simile al seguente:  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  Aprire il file RDTExplorerWindow.cs nella visualizzazione codice. Aggiungere le seguenti istruzioni using all'inizio del file.  
  
    ```c#  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Modificare il `RDTExplorerWindow` classe, che, oltre che derivano dalla <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>classe che implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> </xref:Microsoft.VisualStudio.Shell.ToolWindowPane>  
  
    ```c#  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>  
  
    -   Implementare l'interfaccia. Posizionare il cursore sul nome IVsRunningDocTableEvents. Verrà visualizzata una lampadina nel margine sinistro. Fare clic sulla freccia a destra della lampadina e selezionare **implementa interfaccia**.  
  
5.  In ogni metodo nell'interfaccia, sostituire la riga `throw new NotImplementedException();` con questo:  
  
    ```c#  
    return VSConstants.S_OK;  
    ```  
  
6.  Aggiungere un campo di cookie per la classe RDTExplorerWindow.  
  
    ```c#  
    private uint rdtCookie;   
    ```  
  
     Questo file contiene il cookie viene restituito per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>  
  
7.  Eseguire l'override di metodo Initialize () del RDTExplorerWindow per registrare gli eventi RDT. È necessario ottenere servizi sempre nel metodo Initialize () del ToolWindowPane, non nel costruttore.  
  
    ```c#  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     Il <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>servizio viene chiamato per ottenere un <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> </xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>metodo connette RDT eventi a un oggetto che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, in questo caso, un oggetto RDTExplorer.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>  
  
8.  Aggiornamento metodo Dispose (del RDTExplorerWindow).  
  
    ```c#  
    protected override void Dispose(bool disposing)  
    {  
        // Release the RDT cookie.  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));  
        rdt.UnadviseRunningDocTableEvents(rdtCookie);  
  
        base.Dispose(disposing);  
    }  
    ```  
  
     Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>metodo consente di eliminare la connessione tra `RDTExplorer` e notifica degli eventi RDT.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>  
  
9. Aggiungere la riga seguente al corpo del <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>gestore, immediatamente prima di `return` istruzione.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>  
  
    ```c#  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. Aggiungere una riga simile al corpo del <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>gestore e ad altri eventi che si desidera visualizzare nella casella di riepilogo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>  
  
    ```c#  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale di Visual Studio.  
  
12. Aprire il **RDTExplorerWindow** (**vista o altre finestre / RDTExplorerWindow**).  
  
     Il **RDTExplorerWindow** verrà visualizzata la finestra con un elenco di eventi vuoto.  
  
13. Aprire o creare una soluzione.  
  
     Come `OnBeforeLastDocument` e `OnAfterFirstDocument` gli eventi vengono attivati, notifica di ogni evento eventi viene visualizzato nell'elenco.
