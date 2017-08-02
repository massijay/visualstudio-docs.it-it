---
title: "Raccolte private | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Raccolte VSIX, private"
  - "raccolte private, VSIX"
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Raccolte private
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile condividere i controlli, modelli e strumenti che si sviluppano inviando messaggi a un *raccolta privata* sulla rete intranet dell'organizzazione, come indicato di seguito:  
  
-   Creare un Atom feed RSS in una posizione centrale \(repository\) opportunamente configurata nella rete intranet. Per altre informazioni, vedere [Procedura: creare Atom Feed per una raccolta privata](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Distribuire un file. pkgdef che descrive la raccolta privata. Si consiglia questa configurazione per gli amministratori che desiderano connettersi a una raccolta privata a più computer contemporaneamente.  
  
## Aggiunta di una raccolta privata a estensioni e aggiornamenti in Visual Studio  
 Quando una raccolta privata è disponibile, è possibile aggiungerlo a **estensioni e aggiornamenti** in Visual Studio.  
  
 ![Finestra di dialogo Aggiungi di Gestione estensioni](~/extensibility/media/em_adddialog.png "EM\_AddDialog")  
  
#### Per aggiungere una raccolta privata estensioni e aggiornamenti  
  
1.  Nella barra dei menu scegliere **Strumenti**, **Opzioni**.  
  
2.  Nel **ambiente** nodo, selezionare **estensioni e aggiornamenti**.  
  
3.  Scegliere il pulsante **Aggiungi**.  
  
4.  Nel **nome** immettere un nome per la raccolta privata, ad esempio, `My Gallery`.  
  
5.  Nel **URL** immettere l'URL del feed Atom o sito di SharePoint che ospita la raccolta privata.  
  
    1.  Se l'host è un feed Atom che si connette a una raccolta privata, l'URL sarà simile a questo: http:\/\/www.mywebsite\/mygallery\/atom.xml.  Questo URL può fare riferimento a un file o un percorso di rete.  
  
    2.  Se l'host è un sito di SharePoint, l'URL sarà simile a questo: http:\/\/mysharepoint\/sites\/mygallery\/forms\/AllItems.aspx.  
  
### La gestione di raccolte Private  
 Un amministratore può renderla una raccolta privata disponibile per più computer nello stesso momento modificando il Registro di sistema in ogni computer. A tale scopo, creare un file. pkgdef che descrive le nuove chiavi del Registro di sistema e i relativi valori.  Il formato di questo file è come indicato di seguito.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Per altre informazioni, vedere [Procedura: gestire una raccolta privata utilizzando le impostazioni del Registro di sistema](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## L'installazione delle estensioni da una raccolta privata  
 È possibile cercare e installare le estensioni di Visual Studio da una raccolta privata in **estensioni e aggiornamenti**. La procedura seguente utilizza una raccolta privata denominata `My Gallery`.  
  
 ![Installazione della galleria privata di Gestione estensioni](~/extensibility/media/em_.png "EM\_")  
  
#### Per cercare e installare le estensioni da una raccolta privata  
  
1.  Nella barra dei menu scegliere **Strumenti**, **Estensioni e aggiornamenti**.  
  
2.  Nel riquadro a sinistra, selezionare **estensioni Online**, quindi selezionare **raccolta personale**.  
  
3.  Nel riquadro di destra, selezionare un'estensione e quindi scegliere il **scaricare** pulsante.  
  
## Aggiornamento delle estensioni da una raccolta privata  
 Come le nuove versioni delle estensioni di Visual Studio vengono registrate nella raccolta privata, è possibile aggiornare le estensioni installate. La procedura seguente utilizza una raccolta privata denominata `My Repository`.  
  
 ![Aggiornamento della galleria privata di Gestione estensioni](~/extensibility/media/em_update.png "EM\_Update")  
  
#### Per aggiornare un'estensione installata da una raccolta privata  
  
1.  Nella barra dei menu scegliere **Strumenti**, **Estensioni e aggiornamenti**.  
  
2.  Nel riquadro a sinistra, selezionare **aggiornamenti**, quindi selezionare **archivio My**.  
  
3.  Nel riquadro di destra, selezionare un'estensione e quindi scegliere il **aggiornamento** pulsante.  
  
## Vedere anche  
 [Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Distribuzione di estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)