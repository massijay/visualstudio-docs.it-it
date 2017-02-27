---
title: "Rendere persistenti i dati nel File di progetto MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "file di progetto, il mantenimento dati"
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Rendere persistenti i dati nel File di progetto MSBuild
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un sottotipo di progetto può avere l'esigenza di rendere persistenti i dati sottotipo\-specifici nel file di progetto per un utilizzo successivo.  Un sottotipo del progetto utilizza la persistenza del file di progetto per soddisfare i requisiti seguenti:  
  
1.  Rendere persistenti i dati utilizzati come parte della compilazione del progetto.  \(Per ulteriori informazioni su Microsoft Build Engine, vedere [MSBuild](http://msdn.microsoft.com/it-it/7c49aba1-ee6c-47d8-9de1-6f29a906e20b).\) le informazioni relative possono uno:  
  
    1.  dati dell'Configurazione\-indipendente.  Ovvero dati memorizzati in elementi MSBuild con condizioni vuote o mancanti.  
  
    2.  dati dipendenti dalla configurazione.  Ovvero dati memorizzati in elementi MSBuild che sono condizionali per una configurazione di progetto specifico.  Di seguito è riportato un esempio:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Rendere persistenti i dati che non sono rilevanti da compilare.  Questi dati possono essere espressi in formato libero XML che non viene convalidato rispetto a uno Schema XML.  
  
    1.  dati dell'Configurazione\-indipendente.  
  
    2.  dati dipendenti dalla configurazione.  
  
## Mantenere informazioni correlate alla compilazione  
 La persistenza dei dati utili per compilare un progetto viene gestita da MSBuild.  Il sistema MSBuild gestisce una tabella master di informazioni relative.  I sottotipi di progetto sono responsabili di accedere a questi dati per ottenere e impostare valori di proprietà.  I sottotipi di progetto è possibile aumentare la tabella dati build\-correlata aggiungendo le proprietà aggiuntive da salvare in modo permanente e rimuovendo proprietà in modo da non vengono mantenuti.  
  
 Per modificare i dati di MSBuild, un sottotipo di progetto è responsabile di recuperare l'oggetto della proprietà MSBuild dal sistema di progetto di base con <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> è un'interfaccia implementata nel sistema del progetto principale e sulle query di aggregazione sottotipo di progetto per l'esecuzione `QueryInterface`.  
  
 La procedura riportata di seguito vengono descritti i passaggi per rimuovere una proprietà utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  
  
#### Per rimuovere una proprietà da un file di progetto MSBuild  
  
1.  Chiamare `QueryInterface` su <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> del sottotipo di progetto.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> e fornirgli l'oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>.  
  
### Mantenere informazioni correlate Non di Compilazione  
 La persistenza dei dati nel file di progetto che non importano per compilare viene gestita da <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.  
  
 È possibile distribuire <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> sull'obiettivo principale di `project subtype aggregator` , nell'oggetto `project subtype project configuration` , o in entrambi.  
  
 I punti seguenti vengono descritti i concetti principali relativi alla persistenza di informazioni correlate non compilazione.  
  
-   Le chiamate di progetto base sull'obiettivo di aggregazione principale del sottotipo di progetto \(ovvero il sottotipo più esterno del progetto\) per caricare e salvare i dati correlati di configurazione e chiama sugli oggetti di configurazione del progetto sottotipo di progetto per caricare o salvare i dati del dipendente di configurazione.  
  
-   Il progetto di base chiama i metodi di più volte <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> per ogni livello di aggregazione sottotipo di progetto e passa il GUID per ogni livello.  
  
-   Il progetto di base passa o riceve un frammento XML che è dedicato a un tipo specifico di progetto e utilizza questo meccanismo come modalità di mantenere lo stato tra i livelli di aggregazione.  
  
-   Il progetto di base chiama l'implementazione più esterna di <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>del sottotipo di progetto che passa un GUID.  Se il GUID appartiene al sottotipo più esterno di progetto, gestire la chiamata stessa; in caso contrario delega la chiamata un sottotipo interno del progetto, e così via, fino a trovare il sottotipo di progetto che il GUID corrisponde a.  
  
-   Un sottotipo di progetto può anche modificare il frammento XML prima o dopo delega la chiamata un sottotipo interno del progetto.  Nell'esempio seguente viene illustrato un estratto da un file di progetto, in cui un nome di un file che contiene le proprietà specifiche di un sottotipo di progetto, viene passato al sottotipo di progetto.  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## Vedere anche  
 [Progetto \(sottotipi\)](../../extensibility/internals/project-subtypes.md)