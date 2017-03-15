---
title: Pagina iniziale di creazione di un oggetto personalizzato | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 18
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
ms.sourcegitcommit: c358bf79945b4f4eef5b19c60cad0bd866c175b3
ms.openlocfilehash: 2902ac3b5cd4fd038bdaf277a8390d5eb9e96b28
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-custom-start-page"></a>Creazione di una pagina iniziale personalizzata
È possibile creare una pagina iniziale personalizzata seguendo i passaggi descritti in questo documento.  
  
## <a name="creating-a-blank-start-page"></a>Creazione di una pagina iniziale vuota  
 Verificare innanzitutto una pagina vuota Start creando un file con estensione XAML che ha una struttura di tag che Visual Studio verrà riconosciuto. Aggiungere quindi il markup e code-behind per produrre l'aspetto e funzionalità che si desidera.  
  
#### <a name="to-create-a-blank-start-page"></a>Per creare una pagina vuota Start  
  
1.  Creare un nuovo progetto di tipo **applicazione WPF** (**Visual c# / Windows Desktop**.  
  
2.  Aggiungere un riferimento a `Microsoft.VisualStudio.Shell.14.0`.  
  
3.  Aprire il file XAML nell'editor XML e modificare il livello superiore \<finestra > elemento da un \<UserControl > elemento senza rimuovere le dichiarazioni dello spazio dei nomi.  
  
4.  Rimuovere il `x:Class` dichiarazione di elemento di primo livello. In questo modo il contenuto XAML compatibile con la finestra degli strumenti di Visual Studio che ospita la pagina iniziale.  
  
5.  Aggiungere le seguenti dichiarazioni dello spazio dei nomi di primo livello \<UserControl > elemento.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Questi spazi dei nomi consentono di accedere ai comandi di Visual Studio, controlli e impostazioni dell'interfaccia utente. Per ulteriori informazioni, vedere [aggiunta di comandi di Visual Studio a una pagina iniziale di](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     Nell'esempio seguente viene illustrato il markup nel file con estensione XAML per una pagina iniziale vuoto. Qualsiasi contenuto personalizzato deve andare nelle interna <xref:System.Windows.Controls.Grid>elemento.</xref:System.Windows.Controls.Grid>  
  
    ```vb  
    <UserControl  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
        xmlns:local="clr-namespace:StartPageHost"  
        mc:Ignorable="d"  
         Height="350" Width="525">  
        <Grid>  
        <!--Add content here.-->  
        </Grid>  
    </UserControl>  
    ```  
  
6.  Aggiungere controlli a vuota \<UserControl > elemento per riempire la pagina iniziale personalizzata. Per informazioni su come aggiungere funzionalità specifiche per Visual Studio, vedere [aggiunta di comandi di Visual Studio a una pagina iniziale di](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testing e applicazione della pagina iniziale personalizzata  
 Non impostare l'istanza principale di Visual Studio per eseguire la pagina iniziale personalizzata finché non viene verificato che arresti in modo anomalo Visual Studio. Al contrario, eseguirne il test nell'istanza sperimentale.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Per testare una pagina di avvio personalizzato creato manualmente  
  
1.  Copiare il file XAML e tutti i file di testo o markup supporto file, per il **%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\ ** cartella.  
  
2.  Se la pagina iniziale fa riferimento a tutti i controlli o i tipi negli assembly che non sono installati da Visual Studio, copiare gli assembly e incollarli in *cartella di installazione di Visual Studio***\Common7\IDE\PrivateAssemblies.\\**.  
  
3.  Al prompt dei comandi di Visual Studio, digitare **devenv /rootsuffix Exp** per aprire un'istanza sperimentale di Visual Studio.  
  
4.  Nell'istanza sperimentale, passare al **Strumenti / opzioni / ambiente / avvio** pagina e selezionare il file XAML dal **Personalizza pagina iniziale** nell'elenco a discesa.  
  
5.  Scegliere **Pagina iniziale** dal menu **Visualizza**.  
  
     La pagina iniziale personalizzata deve essere visualizzata. Se si desidera modificare i file, è necessario chiudere l'istanza sperimentale, apportare le modifiche, copiare e incollare i file modificati e quindi aprire nuovamente l'istanza sperimentale per visualizzare le modifiche.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Per applicare personalizzata pagina iniziale nell'istanza principale di Visual Studio  
  
-   Dopo aver testato la pagina iniziale e si è stabile, utilizzare il **Personalizza pagina iniziale** opzione il **opzioni** la finestra di dialogo per selezionarla come pagina iniziale nell'istanza principale di Visual Studio  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Aggiunta di XAML personalizzato nella pagina iniziale](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Aggiunta controllo utente alla pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)   
 [Aggiunta di comandi di Visual Studio a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Procedura dettagliata: Salvataggio delle impostazioni utente a una pagina iniziale](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Distribuzione di pagine iniziali personalizzate](../extensibility/deploying-custom-start-pages.md)
