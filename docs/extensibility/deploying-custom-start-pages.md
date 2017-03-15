---
title: Distribuzione di pagine iniziali personalizzate | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 21
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
ms.openlocfilehash: 9e99f022f1dec71b82c2261cae1d45705fe8dc7f
ms.lasthandoff: 02/22/2017

---
# <a name="deploying-custom-start-pages"></a>Distribuzione di pagine iniziali personalizzate
È possibile distribuire pagine iniziali personalizzate tramite la distribuzione VSIX o copiando i file nelle posizioni corrette nel computer di destinazione.  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Distribuzione VSIX tramite il modello di progetto pagina iniziale  
 Quando si crea una pagina iniziale utilizzando il modello di progetto pagina iniziale e quindi compilare il progetto, Visual Studio crea un file con estensione VSIX che è possibile distribuire. Assemblaggio di una pagina di avvio in un file con estensione VSIX offre le seguenti opzioni per la distribuzione, a seconda del gruppo di destinatari previsto:  
  
-   È possibile inserire il file con estensione VSIX in una condivisione di rete o in un sito Web pubblico. Quando un utente apre il file, viene installata automaticamente la pagina iniziale.  
  
-   È possibile caricare il file con estensione VSIX per la [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) del sito Web in modo che gli utenti possono installarla utilizzando **Gestione estensioni**.  
  
 Il modello di progetto pagina iniziale Crea una copia del valore predefinito la pagina iniziale di Visual Studio in modo che è possibile modificare la copia e conservare l'originale.  
  
 È possibile ottenere il modello di progetto pagina iniziale utilizzando **Gestione estensioni** o scaricandolo dal sito Web.  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Distribuzione VSIX senza utilizzare il modello di progetto pagina iniziale  
 Una corretta distribuzione VSIX richiede un'estensione per essere installati in cartelle che sono riconosciute dal processo di registrazione del pacchetto VSIX e da **Gestione estensioni**. Poiché il modello di progetto della pagina di avvio specifica già nelle cartelle corrette, è consigliabile utilizzarlo ogni volta che si desidera creare un pacchetto di un'estensione per la distribuzione VSIX. Tuttavia, se si dispone di un caso in cui non è possibile utilizzare il modello, è possibile creare una distribuzione VSIX senza utilizzarlo.  
  
 Per creare una distribuzione VSIX senza utilizzare il modello di progetto pagina iniziale, è necessario innanzitutto creare un file con estensione VSIX per la pagina iniziale in uno dei due modi:  
  
-   Aggiungendo i file della pagina iniziale personalizzati a un progetto VSIX vuoto. Per ulteriori informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).  
  
-   Creando manualmente un file con estensione VSIX. Per ulteriori informazioni, vedere [procedura: creare manualmente i pacchetti (distribuzione VSIX) un'estensione](../misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
 Per Visual Studio di riconoscere una pagina iniziale di `Content Element` del manifesto VSIX deve contenere un `CustomExtension Element` che ha il `Type` attributo impostato su `"StartPage"`. Viene visualizzata un'estensione di pagina di avvio che è stata installata utilizzando la distribuzione VSIX nel **Personalizza pagina iniziale** elenco il **avvio** opzioni pagina come **[estensione installato]** *estensione*.  
  
 Se il pacchetto di pagina iniziale include gli assembly, è necessario aggiungere la registrazione di percorso di associazione in modo che siano disponibili quando si avvia Visual Studio. A tale scopo, assicurarsi che il pacchetto include un file. pkgdef che contiene le seguenti informazioni.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>Distribuzione VSIX per tutti gli utenti  
 Per impostazione predefinita, le estensioni distribuite nei pacchetti VSIX installare solo per l'utente corrente. Effettuare un'installazione di pagina iniziale per tutti gli utenti del computer di destinazione mediante la creazione di una distribuzione di tutti gli utenti.  
  
##### <a name="to-create-an-all-users-deployment"></a>Per creare una distribuzione di tutti gli utenti  
  
1.  Aprire il file Extension. vsixmanifest nella visualizzazione codice.  
  
2.  Nel `Identifier` elemento del manifesto vsix, aggiungere un `AllUsers` elemento che presenta un valore `true`.  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     In questo modo il programma di installazione di vsix richiedere le autorizzazioni di amministratore e quindi installare i file \Common7\IDE\Extensions.  
  
3.  Aprire il file. pkgdef.  
  
4.  Modificare pkgdef per impostare la pagina iniziale predefinita in HKLM aggiungendo il codice seguente, dove *MyStartPage.xaml* è il nome del file con estensione XAML contenente la pagina iniziale.  
  
     [$RootKey$ \StartPage\Default]  
  
     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"  
  
     In questo modo Visual superato per la ricerca nella nuova posizione pagina iniziale.  
  
## <a name="file-copy-deployment"></a>Distribuzione tramite Copia file  
 Non è necessario creare un file con estensione VSIX per distribuire una pagina iniziale personalizzata. In alternativa, è possibile copiare il markup e i file di supporto direttamente nella cartella \StartPages\ dell'utente. Il **Personalizza pagina iniziale** elenco il **avvio** opzioni pagina sono elencati tutti i file con estensione XAML nella cartella indicata, con il percorso, ad esempio, %USERPROFILE%\My Documents\Visual Studio *versione*\StartPages\\*nome File*con estensione XAML. Se la pagina iniziale include i riferimenti agli assembly privato, è necessario copiarli e incollarli nella cartella \PrivateAssemblies\.  
  
 Per distribuire una pagina iniziale creato senza imballaggio in un file con estensione VSIX, si consiglia di utilizzare una strategia di copia di file di base, ad esempio, uno script batch, o qualsiasi altra tecnologia di distribuzione che consente di collocare i file nella directory obbligatorie.  
  
#### <a name="to-manually-install-a-custom-start-page"></a>Per installare manualmente una pagina iniziale personalizzata  
  
1.  Copiare il file con estensione XAML contenente il markup della pagina iniziale, insieme a eventuali file di supporto diverso da assembly e incollarli nella cartella \StartPages\ dell'utente.  
  
2.  Se la pagina iniziale richiede l'assembly, copiarli e incollarli in... \\ *Cartella di installazione di visual Studio*\Common7\IDE\PrivateAssemblies.\\.  
  
3.  Nel **Personalizza pagina iniziale** elenco il **avvio** opzioni pagina, selezionare la nuova pagina di avvio. Per ulteriori informazioni, vedere [personalizzazione della pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione della pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Aggiunta controllo utente alla pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)
