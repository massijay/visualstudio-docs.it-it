---
title: "Progetto Web Essentials | Microsoft Docs"
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
  - "progetti Web, essentials"
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Progetto Web Essentials
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Progetti Web di creare applicazioni Web. È possibile utilizzare un progetto Web per creare un'applicazione Web che contiene pagine Web smart. Una pagina Web smart contiene codice lato server che esegue il rendering della pagina Web richiesta.  
  
 Utilizzando i linguaggi di programmazione tradizionali, ad esempio [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], è possibile creare pagine Web intelligente per raccogliere ed elaborare informazioni da un utente, archiviarlo in un database e così via.  
  
-   Il modello code-behind Associa file di codice sorgente dipendenti a pagine Web con il file estensione aspx o asmx. In Hello, ad esempio, potrebbe essere il hello.aspx.cs di file di codice sorgente dipendente.  
  
-   Il codice lato server associato a una pagina Web intelligente viene compilato in un file eseguibile che si trova nella cartella /bin del sito Web.  
  
-   File di codice di origine aggiuntivi, ad esempio classi helper che non sono associati a una pagina Web specifica, si trovano nella cartella /App_Code sito Web.  
  
    -   Un progetto di sito Web (WSP) genera un file eseguibile per ogni pagina Web smart. File eseguibile aggiuntivi vengono generati da qualsiasi file di codice sorgente nella cartella /App_Code.  
  
    -   Un progetto di applicazione Web (WAP) genera un singolo file eseguibile che combina il codice per tutte le pagine Web smart, nonché tutti i file di origine nella cartella /App_Code.  
  
-   Trova il file di soluzione per un progetto Web separatamente dal sito Web stesso. Per impostazione predefinita, i file della soluzione si trovano in \Documents and Settings\\*AccountUtente*documenti \My\\*\< Visual Studio # # # >*\Projects\\*sito Web personale*.  
  
    > [!NOTE]
    >  Se si desidera mantenere il file di soluzione con il sito Web, è sufficiente spostare esiste e riaprirlo.  
  
-   Se si apre un sito Web che non dispone di alcun file di soluzione in Visual Studio, viene generato automaticamente un nuovo file di soluzione per esso.  
  
-   Progetti Web non dispongono di alcun file di progetto. Informazioni di progetto vengono archiviate nel file di soluzione, il file Web. config e così via.  
  
-   Aggiunta automatica di proprietà globali per un progetto Web crea un file di archiviazione nella cartella della soluzione di progetto Web.  
  
-   Una pagina Web intelligente può essere associata a un linguaggio di programmazione sul lato server tramite la direttiva di pagina o \< script runat = "server"> tag.  
  
-   Inoltre, le pagine Web possono avere qualsiasi numero di blocchi di script sul lato client scritti in qualsiasi linguaggio di scripting.  
  
-   Un sistema di progetto del sito Web viene implementato mediante l'aggiunta di modelli di progetto e di elemento e della registrazione di [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] progetto.  
  
-   Un sistema WAP viene implementato come un sottotipo di progetto, denominato anche una versione del progetto. Il [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] progetto è tipo generico per il sottotipo WAP per creare il sistema WAP. Per ulteriori informazioni sul progetto (sottotipi), vedere [sottotipi progetto](../../extensibility/internals/project-subtypes.md).  
  
-   Una pagina Web smart combina HTML con un linguaggio di programmazione sul lato server. Il linguaggio sul lato server è denominato linguaggio indipendente. Per supportare un linguaggio indipendente, è necessario implementare il sistema del progetto Web di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> famiglia di interfacce.  
  
    -   Per supportare il linguaggio contenuto in un editor, il servizio di linguaggio HTML deve rinviare la visualizzazione codice lingua indipendente a un servizio di linguaggio contenute.  
  
    -   Marcatori di errore (smettono) devono essere sempre creati in buffer principale dell'editor di codice.  
  
## <a name="see-also"></a>Vedere anche  
 [Progetti Web](../../extensibility/internals/web-projects.md)