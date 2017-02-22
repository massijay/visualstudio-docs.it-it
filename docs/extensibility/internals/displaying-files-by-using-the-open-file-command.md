---
title: "Visualizzazione di file utilizzando il comando Apri File | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tipi di progetto, il comando Apri File di supporto"
  - "Apri file (comando)"
  - "persistenza, il comando Apri File di supporto"
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Visualizzazione di file utilizzando il comando Apri File
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nei passaggi seguenti viene descritto come l'ide gestisce il comando di **file aperto** , disponibile nel menu File di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  I passaggi viene descritto inoltre come i progetti devono rispondere alle chiamate provenienti da questo comando.  
  
 Quando un utente sceglie il comando di **file aperto** il menu File e selezionare un file nella finestra di dialogo di **file aperto** , il seguente processo si verifica.  
  
1.  Utilizzando la tabella in esecuzione di documento, l'ide determina se il file è già aperto in un progetto.  
  
    -   Se il file è aperto, l'ide rifa la finestra.  
  
    -   If the file is not open, the IDE calls <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> to query each project to determine which project can open the file.  
  
        > [!NOTE]
        >  In your project implementation of <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, provide a priority value that indicates the level at which your project opens the file.  I valori di priorità sono forniti nell'enumerazione <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> .  
  
2.  Ogni progetto risponde a un livello di priorità che indica l'importanza che posiziona su come progetto aprire il file.  
  
3.  L'ide utilizza i criteri seguenti per determinare quale progetto viene aperto il file:  
  
    -   Il progetto che risponde alla priorità più alta DP\_Intrinsic\) viene aperto il file.  Se più di un progetto risponde alla priorità, il primo progetto rispondere viene aperto il file.  
  
    -   Se nessun progetto risponde con la priorità più alta DP\_Intrinsic\), ma tutti i progetti compatibili con lo stesso, la priorità più bassa, il progetto viene aperto il file.  Se non esiste alcun progetto, viene attivato il primo progetto rispondere viene aperto il file.  
  
    -   Se nessun progetto attesta la proprietà del file \(DP\_Unsupported\), il progetto file esterni viene aperto il file.  
  
         Se un'istanza di progetto file esterni viene creata, il progetto non sempre con il valore DP\_CanAddAsExternal.  questo valore indica che il progetto può aprire il file.  Questo progetto viene utilizzato ospitare i file aperti non presenti in qualsiasi altro progetto.  Elenco di elementi nel progetto non viene salvato in modo permanente; questo progetto è visibile in **Esplora soluzioni** solo quando viene utilizzato per aprire un file.  
  
         Se il progetto file esterni non indica che può aprire il file, un'istanza del progetto non è stata creata.  In questo caso, l'ide crea un'istanza di file esterni progetti e indica al progetto aprire il file.  
  
4.  Non appena l'ide determina il progetto viene aperto il file, chiama il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> per quel progetto.  
  
5.  Il progetto quindi con l'opzione di aprire il file utilizzando un editor specifico del progetto o un editor standard.  Per ulteriori informazioni, vedere rispettivamente [Procedura: aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md) e [Procedura: aprire gli editor Standard](../../extensibility/how-to-open-standard-editors.md).  
  
## Vedere anche  
 [Visualizzazione di file utilizzando l'aperto con il comando](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Procedura: aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Procedura: aprire gli editor Standard](../../extensibility/how-to-open-standard-editors.md)