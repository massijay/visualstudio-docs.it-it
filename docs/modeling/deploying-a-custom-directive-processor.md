---
title: "Deploying a Custom Directive Processor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, custom directive processors"
ms.assetid: 80c28722-a630-47b5-923b-024dc3f2c940
caps.latest.revision: 18
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 18
---
# Deploying a Custom Directive Processor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per utilizzare un processore di direttiva personalizzato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in un computer qualsiasi, è necessario registrarlo da uno dei metodi descritti in questo argomento.  
  
 I metodi alternativi sono i seguenti:  
  
-   [Visual Studio Extension \(VSIX\)](http://msdn.microsoft.com/it-it/64ff1452-f7d5-42d9-98b8-76f769f76832).  Fornisce un modo per installare e disinstallare il processore di direttiva sia in un proprio computer che in altri computer.  In genere, è possibile comprimere altre funzionalità nello stesso VSIX.  
  
-   [Package VS](../extensibility/internals/vspackages.md).  Se si definisce un package VS che contiene altre funzionalità oltre al processore di direttiva, esiste un metodo comodo per registrare il processore di direttiva.  
  
-   Impostare una chiave del Registro di sistema.  In questo metodo, si aggiunge una voce del Registro di sistema per il processore di direttiva.  
  
 È necessario utilizzare uno di questi metodi solo se si desidera trasformare il modello di testo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Se si utilizza un host personalizzato nella propria applicazione, l'host personalizzato è responsabile dell'individuazione dei processori di direttive per ciascuna direttiva.  
  
## Distribuzione di un processore di direttiva in un pacchetto VSIX  
 È possibile aggiungere un processore di direttiva personalizzato a un pacchetto [Visual Studio Extension \(VSIX\)](http://msdn.microsoft.com/it-it/64ff1452-f7d5-42d9-98b8-76f769f76832).  
  
 È necessario assicurarsi che i due elementi seguenti siano contenuti nel file .vsix:  
  
-   L'assembly \(.dll\) che contiene la classe del processore di direttiva personalizzata.  
  
-   Un file .pkgdef che registra il processore di direttiva.  Il nome radice del file deve essere uguale all'assembly.  Ad esempio, i file potrebbero essere denominati CDP.dll e CDP.pkgdef.  
  
 Per esaminare o modificare il contenuto di un file .vsix, cambiare l'estensione del file in .zip, quindi aprirlo.  Dopo avere modificato il contenuto, reimpostare l'estensione del file su .vsix.  
  
 Esistono diversi modi di creare un file .vsix.  Nella procedura seguente ne viene descritto uno.  
  
#### Per sviluppare un processore di direttiva personalizzato in un progetto VSIX  
  
1.  Creare un progetto VSIX in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    -   Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Visual Basic** o **Visual C\#**, quindi espandere **Extensibility**.  Fare clic su **Progetto VSIX**.  
  
2.  In **source.extension.vsixmanifest** impostare il tipo di contenuto e le edizioni supportate.  
  
    1.  Nell'editor di manifesto VSIX, su **Asset**, scegliere **Nuovo** e impostare le proprietà del nuovo elemento:  
  
         **Tipo di contenuto** \= **Package VS**  
  
         **Progetto di origine** \= \<*the current project*\>  
  
    2.  Fare clic su **Edizioni selezionate** e controllare i tipi di installazione nei quali si desidera che il processore di direttiva sia utilizzabile.  
  
3.  Aggiungere un file .pkgdef e impostarne le proprietà da includere in VSIX.  
  
    1.  Creare un file di testo e chiamarlo \<*assemblyName*\>.pkgdef.  
  
         \<*assemblyName*\> corrisponde in genere allo stesso nome del progetto.  
  
    2.  Selezionarlo in Esplora soluzioni e impostarne le proprietà come segue:  
  
         **Operazione di compilazione** \= **Contenuto**  
  
         **Copia nella directory di output** \= **Copia sempre**  
  
         **Includi in VSIX** \= **True**  
  
    3.  Impostare il nome del pacchetto VSIX e assicurarsi che l'ID sia univoco.  
  
4.  Aggiungere il seguente testo al file .pkgdef.  
  
    ```  
    [$RootKey$\TextTemplating]  
    [$RootKey$\TextTemplating\DirectiveProcessors]  
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]  
    @="Custom Directive Processor description"  
    "Class"="NamespaceName.ClassName"  
    "CodeBase"="$PackageFolder$\AssemblyName.dll"  
    ```  
  
     Sostituire i nomi seguenti con i propri nomi: `CustomDirectiveProcessorName`, `NamespaceName`, `ClassName`, `AssemblyName`.  
  
5.  Aggiungere i riferimenti seguenti al progetto:  
  
    -   **Microsoft.VisualStudio.TextTemplating.\*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.VSHost.\*.0**  
  
6.  Aggiungere la classe del processore di direttiva personalizzato al progetto.  
  
     Si tratta di una classe pubblica che deve implementare <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
#### Per installare il processore di direttiva personalizzato  
  
1.  In Esplora risorse, aprire la directory di compilazione \(in genere è bin\\Debug o bin\\Release\).  
  
2.  Se si desidera installare il processore di direttiva in un altro computer, copiare il file .vsix nell'altro computer.  
  
3.  Fare doppio clic sul file .vsix.  Verrà visualizzato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Extension Installer.  
  
4.  Riavviare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Si sarà ora in grado di eseguire modelli di testo che contengono direttive che si riferiscono al processore di direttiva personalizzato.  Ogni direttiva è nel seguente formato:  
  
     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" … #>`  
  
#### Per disinstallare o disabilitare temporaneamente il processore di direttiva personalizzato  
  
1.  In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], nel menu **Strumenti** fare clic su **Gestione estensioni**.  
  
2.  Selezionare il pacchetto VSIX che contiene il processore di direttiva, quindi fare clic su **Disinstalla** o **Disabilita**.  
  
### Risoluzione dei problemi relativi a un processore di direttiva in un pacchetto VSIX  
 Se il processore di direttiva non funziona, è possibile seguire i suggerimenti indicati di seguito:  
  
-   Il nome del processore che si specifica nella direttiva personalizzata deve corrispondere al `CustomDirectiveProcessorName` specificato nel file .pkgdef.  
  
-   Il metodo `IsDirectiveSupported` deve restituire `true` quando viene passato il nome di `CustomDirective`.  
  
-   Se l'estensione non è visibile in Gestione estensioni, ma il sistema non consente di installarla, eliminare l'estensione da **%localappdata%\\Microsoft\\VisualStudio\\\*.0\\Extensions\\**.  
  
-   Aprire il file .vsix ed esaminarne il contenuto.  Per aprirlo, impostare l'estensione del file su .zip.  Verificare che contenga i file .dll, .pkgdef ed extension.vsixmanifest.  Il file extension.vsixmanifest deve contenere l'elenco adatto nel nodo SupportedProducts e deve contenere anche un nodo Package VS sotto il nodo Contenuto:  
  
     `<Content>`  
  
     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`  
  
     `</Content>`  
  
## Distribuzione di un processore di direttiva in un package VS  
 Se il processore di direttiva fa parte di un package VS che sarà installato nella GAC, è possibile fare in modo che sia il sistema a generare il file .pkgdef.  
  
 Posizionare l'attributo seguente sulla classe del package:  
  
```  
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]  
```  
  
> [!NOTE]
>  Questo attributo viene posizionato sulla classe del package, non sulla classe del processore di direttiva.  
  
 Il file .pkgdef sarà generato quando si compila il progetto.  Quando si installa il package VS, nel file .pkgdef verrà registrato il processore di direttiva.  
  
 Verificare che il file .pkgdef venga visualizzato nella cartella di compilazione, che in genere è bin\\Debug o bin\\Release.  Se non è visualizzato, aprire il file .csproj in un editor di testo e rimuovere il nodo seguente: `<GeneratePkgDefFile>false</GeneratePkgDefFile>`.  
  
 Per ulteriori informazioni, vedere [Package VS](../extensibility/internals/vspackages.md).  
  
## Impostazione di una chiave di Registro di sistema  
 Questo metodo per installare un processore di direttiva personalizzato è il meno preferito.  Non fornisce un modo comodo per abilitare e disabilitare il processore di direttiva e non fornisce un metodo per distribuire il processore di direttiva ad altri utenti.  
  
> [!CAUTION]
>  Una modifica errata del Registro di sistema può provocare gravi danni al sistema.  Prima di apportare modifiche al Registro di sistema, eseguire il backup dei dati importanti sul computer.  
  
#### Per registrare un processore di direttiva impostando una chiave del Registro di sistema  
  
1.  Esecuzione `regedit`.  
  
2.  In regedit passare a  
  
     **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\\*.0\\TextTemplating\\DirectiveProcessors**  
  
     Se si desidera installare il processore di direttiva nella versione sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], inserire "Exp" dopo "11.0".  
  
3.  Aggiungere una chiave del Registro di sistema che abbia lo stesso nome della classe del processore di direttiva.  
  
    -   Nella struttura ad albero del Registro di sistema, fare clic con il pulsante destro del mouse nel nodo **DirectiveProcessors**, selezionare **Nuovo**, quindi fare clic su **Chiave**.  
  
4.  Nel nuovo nodo, aggiungere valori stringa per Class e CodeBase o Assembly, sulla base delle tabelle seguenti.  
  
    1.  Fare clic con il pulsante destro del mouse nel nodo creato, selezionare **Nuovo**, quindi fare clic su **Valore stringa**.  
  
    2.  Modificare il nome del valore.  
  
    3.  Fare doppio clic sul nome e modificare i dati.  
  
 Se il processore di direttiva personalizzato non è presente nella GAC, le sottochiavi del Registro di sistema appariranno come indicato nella tabella seguente:  
  
|Nome|Tipo|Dati|  
|----------|----------|----------|  
|\(Predefinito\)|REG\_SZ|\(valore non impostato\)|  
|Classe|REG\_SZ|\<Nome spazio dei nomi\>.\<Nome classe\>|  
|CodeBase|REG\_SZ|\<Percorso\>\\\<Nome assembly\>|  
  
 Se l'assembly è presente nella GAC, le sottochiavi del Registro di sistema appariranno come indicato nella tabella seguente:  
  
|Nome|Tipo|Dati|  
|----------|----------|----------|  
|\(Predefinito\)|REG\_SZ|\(valore non impostato\)|  
|Classe|REG\_SZ|\<Nome classe completo\>|  
|Assembly|REG\_SZ|\<Nome assembly nella GAC\>|  
  
## Vedere anche  
 [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md)