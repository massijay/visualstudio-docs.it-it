---
title: "Flag della riga di comando del compilatore VSCT | Microsoft Docs"
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
  - "File VSCT, la compilazione"
  - "compilazione di un file di comando-table (file VSCT)"
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Flag della riga di comando del compilatore VSCT
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il compilatore di Visual Studio comando tabella (VSCT) fornisce le opzioni della riga di comando per garantire una corretta compilazione del file. vsct.  
  
## <a name="command-line-parameters"></a>Parametri della riga di comando  
 Per visualizzare la Guida VSCT base da un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **comando** finestra, passare al *il percorso di installazione di Visual Studio SDK*\VisualStudioIntegration\Tools\Bin\ cartella e digitare:  
  
```  
vsct /?  
```  
  
 Restituisce:  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indcate what additional include paths to send to the preprocessor  
  -L    Specify the langauge to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        folowed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependancy checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  I caratteri - (trattino) e / (barra) sono entrambi accettati notazione per indicare i parametri della riga di comando.  
  
 Di seguito sono riportati i flag consentiti e il relativo significato.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|-D|Specificare i simboli definiti aggiuntivi.|  
|-I|Indicare che percorsi che devono essere utilizzati per la risoluzione dei riferimenti ai file di inclusione aggiuntive.|  
|-L|Specificare il <xref:System.Globalization.CultureInfo> nome delle impostazioni cultura, ad esempio "en-US".|  
|-E|Creare oggetti c# nello spazio dei nomi specificato per gli elementi di comando, seguito da [C &#124; C &#124; N]:*filename*dove C = in c#, H = intestazione di C++, N = spazio dei nomi. Lo spazio dei nomi è necessaria per c#.|  
|-v|Output dettagliato.|  
  
 L'opzione -L indica al compilatore di selezionare un gruppo di stringhe per generare il file binario .cto corrispondente per lo specificato <xref:System.Globalization.CultureInfo> nome delle impostazioni cultura. Il nome specificato deve corrispondere all'attributo di linguaggio di uno o più [stringhe elemento](../../extensibility/strings-element.md) nel file vsct. Se un elemento stringhe disponga di alcun attributo di linguaggio, viene ereditata dalla [CommandTable elemento](../../extensibility/commandtable-element.md).  
  
 Un file. vsct può disporre di più elementi di stringhe, e ognuno può avere un attributo di linguaggio diverso. Globalizzazione avviene eseguendo più volte il compilatore VSCT e modificando l'opzione -L per ogni nome di impostazioni cultura.  
  
 Se il nome delle impostazioni cultura specificato dall'opzione -L non corrisponde all'attributo di linguaggio di qualsiasi elemento di stringhe, il compilatore tenterà in modo che corrisponda alla lingua e non l'area. Ad esempio, se non trovato "en-US", il compilatore tenterà "en" invece. In caso contrario, verrà effettuato un tentativo di impostazioni cultura correnti del sistema operativo. In caso contrario, la compilazione del primo elemento di stringhe che viene trovato.  
  
 L'opzione -E può essere utilizzata per generare un file di intestazione di tipo C che contiene i simboli utilizzati per la tabella di comando o per generare un file c# contenente gli oggetti per i simboli di comando.  
  
 -D e -I parametri presentano la sintassi dei flag per il preprocessore C Cl.exe che hanno lo stesso nome. – D le definizioni che presentano il formato X = Y vengono utilizzate per l'espansione del basato su XML \< definiti> i test in `Condition` attributi. : Includere i percorsi utilizzati per risolvere \< Includi>, \< Extern> e \< Bitmap> i riferimenti di file. Per ulteriori informazioni, vedere il [riferimento allo Schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
 Il compilatore VSCT inoltre in grado di decompilare un file binario compilato in precedenza. A tale scopo, specificare un file binario per il \< infile>.   Se il file binario è stato generato dal compilatore VSCT, avranno i simboli già incorporati e viene prodotto un output con i nomi simbolici in un \< simboli> sezione dell'output. Se il file binario è stato generato dal compilatore CTC, l'output conterrà i GUID e ID effettivo. Se il file *.ctsym derivante dalle versioni correnti di Ctc.exe è nella stessa cartella del file di input binario, i simboli verranno caricati da tale file e utilizzati per l'output.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabella di comandi di Visual Studio (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Riferimento allo Schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)   
 [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)