---
title: Aggiunta di comandi di Visual Studio a una pagina iniziale | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 20
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c75d9b41d0e51d6db2e78d0afa0e1ddf37e87b8a
ms.lasthandoff: 02/22/2017

---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Aggiunta di comandi di Visual Studio a una pagina iniziale
Quando si crea una pagina iniziale personalizzata, è possibile aggiungervi comandi di Visual Studio. Questo documento vengono illustrate le diverse modalità per associare i comandi di Visual Studio a oggetti XAML in una pagina iniziale.  
  
 Per ulteriori informazioni sui comandi in XAML, vedere [panoramica dei comandi](http://msdn.microsoft.com/Library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>Aggiunta di comandi anche dal comando  
 La pagina iniziale creato in [la creazione di una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md) aggiunto il <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>e <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName>gli spazi dei nomi, come indicato di seguito.</xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> </xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Aggiungere un altro spazio dei nomi per Microsoft.VisualStudio.Shell Microsoft.VisualStudio.Shell.Immutable.11.0.dll dell'assembly. (Potrebbe essere necessario aggiungere un riferimento all'assembly del progetto)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 È possibile utilizzare il `vscom:` alias per associare i comandi di Visual Studio a XAML controlla nella pagina impostando la <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A>proprietà del controllo da `vscom:VSCommands.ExecuteCommand`.</xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> È quindi possibile impostare il <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>proprietà sul nome del comando da eseguire, come illustrato nell'esempio seguente.</xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  Il `x:` alias, che fa riferimento allo schema XAML, è necessario all'inizio di tutti i comandi.  
  
 È possibile impostare il valore di `Command` proprietà a qualsiasi comando che è possibile accedere dal **comando** finestra. Per un elenco di comandi disponibili, vedere [alias di comandi di Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
 Se il comando per aggiungere richiede un parametro aggiuntivo, è possibile aggiungere il valore di `CommandParameter` proprietà. Parametri separati da comandi utilizzando spazi, come illustrato nell'esempio seguente.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Chiamata anche le estensioni del comando  
 È possibile chiamare i comandi da VS registrato utilizzando la stessa sintassi utilizzata per chiamare altri comandi di Visual Studio. Ad esempio, se un VSPackage installato aggiunge un **Home Page** comando per il **visualizzazione** menu, è possibile chiamare il comando impostando `CommandParameter` a `View.HomePage`.  
  
> [!NOTE]
>  Se si chiama un comando che è associato a un pacchetto Visual Studio, è necessario caricare il pacchetto quando viene richiamato il comando.  
  
## <a name="adding-commands-from-assemblies"></a>Aggiunta di comandi dagli assembly  
 Per chiamare un comando da un assembly o accedere al codice in un VSPackage che non è associato a un comando di menu, è necessario creare un alias per l'assembly e quindi chiamare l'alias.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Per chiamare un comando da un assembly  
  
1.  Nella soluzione, aggiungere un riferimento all'assembly.  
  
2.  Nella parte superiore del file StartPage, aggiungere una direttiva dello spazio dei nomi per l'assembly, come illustrato nell'esempio seguente.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Richiamare il comando impostando la `Command` proprietà di un oggetto XAML, come illustrato nell'esempio seguente.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  È necessario copiare l'assembly e quindi incollarlo in... \\ *Cartella di installazione di visual Studio*\common7\ide\privateassemblies\. per assicurarsi che il caricamento prima che venga chiamato.  
  
## <a name="adding-commands-with-the-dte-object"></a>Aggiunta di comandi con l'oggetto DTE  
 È possibile accedere all'oggetto DTE da una pagina iniziale nel markup e nel codice.  
  
 Nel markup, è possibile accedervi tramite il [estensione di Markup Binding](http://msdn.microsoft.com/Library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) sintassi per chiamare il <xref:EnvDTE.DTE>oggetto.</xref:EnvDTE.DTE> È possibile utilizzare questo approccio da associare alla proprietà semplici, ad esempio quelli che restituiscono raccolte, ma non è possibile associare ai metodi o servizi. Nell'esempio seguente un <xref:System.Windows.Controls.TextBlock>controllo associato al <xref:EnvDTE._DTE.Name%2A>proprietà e un <xref:System.Windows.Controls.ListBox>controllo che enumera il <xref:EnvDTE.Window.Caption%2A>le proprietà della raccolta restituito dal <xref:EnvDTE._DTE.Windows%2A>proprietà.</xref:EnvDTE._DTE.Windows%2A> </xref:EnvDTE.Window.Caption%2A> </xref:System.Windows.Controls.ListBox> </xref:EnvDTE._DTE.Name%2A> </xref:System.Windows.Controls.TextBlock>  
  
```xml  
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>  
<ListBox ItemsSource="{Binding Path=DTE.Windows}">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <TextBlock Text="{Binding Path=Caption}"/>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
</ListBox  
```  
  
 Per un esempio, vedere [procedura dettagliata: salvataggio delle impostazioni utente in una pagina iniziale di](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta controllo utente alla pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)
