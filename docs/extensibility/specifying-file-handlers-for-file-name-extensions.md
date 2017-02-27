---
title: "Specifica i gestori di File per le estensioni di File | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "estensioni di file, specificando i gestori di file"
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Specifica i gestori di File per le estensioni di File
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esistono diversi modi per determinare l'applicazione che gestisce un file con un'estensione particolare. I verbi OpenWithList e OpenWithProgids sono due modi per specificare i gestori di file nella voce del Registro di sistema per l'estensione del file.  
  
## Verbo OpenWithList  
 Facendo clic su un file in Esplora risorse, vedere il **aprire** comando. Se più di un prodotto è associato a un'estensione, verrà visualizzato un **Apri con** sottomenu.  
  
 È possibile registrare applicazioni diverse da aprire un'estensione per l'impostazione della chiave OpenWithList per l'estensione del file in HKEY\_CLASSES\_ROOT. Le applicazioni elencate in questa chiave per un'estensione di file vengono visualizzati sotto il **applicazioni consigliate** intestazione nel **Apri con** la finestra di dialogo. Nell'esempio seguente mostra le applicazioni registrate per aprire l'estensione di file VCPROJ.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  Le chiavi che specifica le applicazioni sono nell'elenco in HKEY\_CLASSES\_ROOT\\Applications.  
  
 Aggiunta di una chiave OpenWithList, si dichiara che l'applicazione supporta un'estensione di file anche se un'altra applicazione assume la proprietà dell'estensione. Potrebbe trattarsi di una versione futura dell'applicazione o un'altra applicazione.  
  
## OpenWithProgIDs  
 Identificatore programmatico \(ProgID\) sono versioni descrittive ClassID che identificano una versione di un'applicazione o un oggetto COM. Ogni oggetto generabile condiviso deve avere il proprio ProgID. Ad esempio, VisualStudio.DTE.7.1 avvia Visual Studio .NET 2003 durante l'avvio di VisualStudio.DTE.10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Come proprietario di un tipo di progetto o un tipo di elemento di progetto, è necessario creare un ProgID in base alla versione per l'estensione di file. Questi ProgID può essere ridondante in più di un ProgID può avviare l'applicazione stessa. Per altre informazioni, vedere [La registrazione di verbi di estensioni di File](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Utilizzare la seguente convenzione di denominazione per il file con controllo delle versioni ProgID per evitare la duplicazione con la registrazione di altri fornitori:  
  
|Estensione di file|Con controllo delle versioni ProgID|  
|------------------------|-----------------------------------------|  
|.Extension|ProductName. extension.versionMajor.versionMinor|  
  
 È possibile registrare diverse applicazioni che sono in grado di aprire una determinata estensione di file mediante l'aggiunta di ProgID con controllo delle versioni come valori per il HKEY\_CLASSES\_ROOT\\*\< estensione \>*\\OpenWithProgids chiave. Questa chiave del Registro di sistema contiene un elenco di ProgID alternativo associato all'estensione di file. Le applicazioni associate ai ProgID elencati vengono visualizzati nel **Apri con***nome prodotto* sottomenu. Se la stessa applicazione viene specificata in entrambe le `OpenWithList` e `OpenWithProgids` chiavi, il sistema operativo unisce i duplicati.  
  
> [!NOTE]
>  Il `OpenWithProgids` chiave è supportata solo in Windows XP. Poiché altri sistemi operativi non supportano questa chiave, non utilizzarlo come la registrazione sola per i gestori di file. Utilizzare questa chiave per fornire una migliore esperienza utente in Windows XP.  
  
 Aggiungere i ProgID desiderati come valori di tipo REG\_NONE. Il codice seguente viene fornito un esempio di registrazione di ProgID per un'estensione di file \(.*ext*\).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 Il valore ProgID specificato, come il valore predefinito per l'estensione del file è il gestore di file predefinito. Se si modifica il ProgID per un'estensione di file forniti con una versione precedente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o che possono essere eseguite da altre applicazioni, quindi è necessario registrare il `OpenWithProgids` chiave per l'estensione di file e specificare il nuovo ProgID nell'elenco con i ProgID precedenti è supportata. Ad esempio:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Se il vecchio ProgID dispone di verbi associati, quindi tali verbi verranno visualizzati anche in **Apri con** *nome prodotto* nel menu di scelta rapida.  
  
## Vedere anche  
 [Sulle estensioni di File](../extensibility/about-file-name-extensions.md)   
 [La registrazione di verbi di estensioni di File](../extensibility/registering-verbs-for-file-name-extensions.md)