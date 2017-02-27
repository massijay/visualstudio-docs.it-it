---
title: "Creazione di istanze di progetto tramite le factory di progetto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "factory di progetto"
  - "progetti factory progetto [Visual Studio SDK]"
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Creazione di istanze di progetto tramite le factory di progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

I tipi di progetto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzano *una factory di progetto* per creare istanze di oggetti del progetto.  Una factory di progetto è analoga a una class factory standard per gli oggetti COM cocreatable e.  Tuttavia, gli oggetti del progetto non vengono cocreatable e: possono essere creati solo tramite una factory del progetto.  
  
 L'ide di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chiama la factory di progetto implementata nel package VS a carichi utente un progetto esistente oppure creare un nuovo progetto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Il nuovo oggetto del progetto fornisce IDE con informazioni sufficienti per popolare Esplora soluzioni.  Il nuovo oggetto del progetto fornisce inoltre le interfacce obbligatorie per il supporto di tutte le azioni importanti dell'interfaccia utente avviate dall'IDE.  
  
 È possibile implementare l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> nella classe nel progetto.  In genere, si trova nel proprio modulo.  
  
 For an example of an implementation of the `IVsProjectFactory` interface, see PrjFac.cpp that is contained in the [Basic Project](http://msdn.microsoft.com/it-it/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) sample directory.  
  
 I progetti che supportano essere aggregatoe da un proprietario è necessario salvare in modo permanente un proprietario nel file di progetto.  Quando il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> viene chiamato a un progetto con una chiave del proprietario, il progetto di proprietà converte la chiave del proprietario per una factory GUID del progetto quindi chiama il metodo di `CreateProject` sulla factory di progetto per rendere effettiva creazione.  
  
## creare un progetto di proprietà  
 un proprietario crea un progetto di proprietà in due fasi:  
  
1.  Mediante la chiamata del metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A>.  Ciò fornisce al progetto di proprietà una probabilità creare un oggetto del progetto aggregato basato sull'input che controlla `IUnknown`.  Il progetto di proprietà trascorre `IUnknown` interno e l'oggetto aggregato di nuovo al progetto proprietario.  Ciò fornisce al progetto di proprietà una probabilità archiviare `IUnknown`interno.  
  
2.  Mediante la chiamata del metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>.  Il progetto di proprietà fa tutta la sua creazione di istanze quando questo metodo viene chiamato anziché chiamare `IVsProjectFactory::CreateProject` come essere l'argomento per i progetti che non sono proprietà.  L'enumerazione di `VSOWNEDPROJECTOBJECT` di input corrisponde in genere al progetto di proprietà aggregato.  Il progetto di proprietà può utilizzare questa variabile per determinare se il relativo oggetto del progetto è già stato creato \(cookie non equivale a NULL\) oppure deve essere creato \(NULL equals cookie\).  
  
 I tipi di progetto sono identificati da un GUID del progetto univoco, simile al CLSID di un oggetto COM cocreatable e.  In genere, una factory di progetto gestisce creare istanze di un tipo di progetto, benché sia possibile avere una handle della factory di progetto più di un tipo di progetto GUID.  
  
 I tipi di progetto sono associati a un'estensione di file.  Quando un utente tenta di aprire un file di progetto esistente o tenta di creare un nuovo progetto duplicando un modello, l'ide utilizza l'estensione del file per determinare il GUID del progetto corrispondente.  
  
 Non appena l'ide determina se necessario creare un nuovo progetto o aprire un progetto esistente di un particolare tipo, l'ide utilizza le informazioni nel Registro di sistema in \[HKEY\_LOCAL\_MACHINE \\Software\\Microsoft\\VisualStudio\\8.0\\Projects\] to find which VSPackage implementa la factory richiesta di progetto.  L'ide carica il pacchetto VS.  Nel pacchetto gestito Framework queste informazioni vengono ottenute tramite reflection dalla classe che implementa l'interfaccia <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> con un oggetto <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> applicato a esso.  
  
 Il metodo principale dell'interfaccia di `IVsProjectFactory` è <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> che devono gestire due scenari: apertura di un progetto esistente e creare un nuovo progetto.  La maggior parte dei progetti vengono archiviate nello stato del progetto in un file di progetto.  In genere, i nuovi progetti vengono creati utilizzando una copia del file modello passato al metodo di `CreateProject` quindi aprire la copia.  I progetti esistenti vengono create direttamente l'apertura del file di progetto passato al metodo di `CreateProject` .  Il metodo di `CreateProject` possibile visualizzare in base alle esigenze funzionalità di interfaccia utente.  
  
 Un progetto può inoltre non utilizzare file e, invece, per archiviare lo stato del progetto in un meccanismo di archiviazione diverso dal file system, ad esempio un database o un server Web.  In questo caso, il parametro del nome file passato al metodo di `CreateProject` non è in realtà un percorso di file system ma una stringa\-un univoca URL\-a identifica i dati del progetto.  Non è necessario copiare i file di modello che vengono passati a `CreateProject` per attivare la sequenza corretta di costruzione da eseguire.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)