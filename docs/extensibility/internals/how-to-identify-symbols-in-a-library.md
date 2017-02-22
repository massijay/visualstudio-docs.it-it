---
title: "Procedura: identificare i simboli in una libreria | Microsoft Docs"
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
  - "Chiamare lo strumento del Browser, che identifica i simboli nella libreria"
  - "Strumento Visualizzatore chiamate"
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: identificare i simboli in una libreria
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

gli strumenti di Simbolo\-esplorazione visualizzare le visualizzazioni gerarchiche dei simboli.  I simboli rappresentano spazi dei nomi, gli oggetti, le classi, i membri della classe e altri elementi del linguaggio.  
  
 Ciascun simbolo nella gerarchia può essere identificato dalle informazioni di navigazione passate dalla libreria di simboli gestione dell'oggetto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] attraverso le seguenti interfacce:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 La posizione del simbolo nella gerarchia distingue un simbolo.  Consente agli strumenti di simbolo\-esplorazione navigare a un simbolo specifico.  L'univoco, percorso completo del simbolo determina la posizione.  Ogni elemento del percorso è un nodo.  Il percorso inizia con il nodo di primo livello e termina con il simbolo specifico.  Ad esempio, se il metodo M1 è un membro della classe di C1 e C1 è disponibile nello spazio dei nomi N1, il percorso completo del metodo M1 è N1. C1. M1.  questo percorso contiene tre nodi: N1, C1 e M1.  
  
 Le informazioni di navigazione consentono di gestione dell'oggetto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] individuare, selezionare e mantenere seleziona i simboli nella gerarchia.  Consente di passare da uno strumento esplorante a un altro.  Quando si utilizza **Visualizzatore oggetti** per esaminare i simboli in [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] progetto, è possibile fare clic con il pulsante destro del mouse su un metodo e avviare lo strumento di **Visualizzatore chiamate** per visualizzare il metodo in un grafico delle chiamate.  
  
 Due form viene illustrata la posizione del simbolo.  Il formato canonico è basato sul percorso completo del simbolo.  Soddisfa il riferimento di file di progetto nel file EmptyWeb.vstemplate.  È indipendente dallo strumento di simbolo\-esplorazione.  Per ottenere le informazioni del form canonico, l'amministratore dell'oggetto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chiama il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> .  Il form di presentazione specifica la posizione del simbolo all'interno di uno strumento specifico di simbolo\-esplorazione.  La posizione del simbolo è relativo alla posizione di altri simboli nel hierarchicy.  Un simbolo specificato può contenere diversi percorsi di presentazione, ma solo un percorso canonico.  Ad esempio, se la classe di C1 viene ereditata dalla classe di C2 ed entrambe le classi nello spazio dei nomi N1, **Visualizzatore oggetti** visualizzato il seguente struttura ad albero gerarchica:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 Il percorso canonico della classe di C2, in questo esempio, è N1 \+ C2.  Il percorso di presentazione di C2 include i nodi di C1 e “di base e interfacce„: N1 \+ C1 \+ “basi e interfacce„ \+ C2.  
  
 Per ottenere il modulo informazioni di presentazione, l'amministratore dell'oggetto chiama il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> .  
  
## Identificazione dei simboli nella gerarchia  
  
#### Per ottenere modulo informazioni di presentazione e canonico  
  
1.  Implementare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.  
  
     L'amministratore dell'oggetto chiamato questo metodo per ottenere l'elenco dei nodi contenuti nel percorso canonico del simbolo.  
  
    ```vb#  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```c#  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  Implementare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>.  
  
     L'amministratore dell'oggetto chiamato questo metodo per ottenere l'elenco dei nodi contenuti nel percorso di presentazione del simbolo.  
  
## Vedere anche  
 [Supporto di strumenti di esplorazione di simbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Procedura: registrare una libreria con il gestore oggetti](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Procedura: esporre elenchi dei simboli forniti dalla libreria di gestione degli oggetti](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)