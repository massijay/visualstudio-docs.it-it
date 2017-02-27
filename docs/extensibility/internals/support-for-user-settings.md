---
title: "Supporto per le impostazioni utente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "I punti di impostazioni personalizzato"
  - "impostazioni utente [Visual Studio SDK], supporto della persistenza di registrazione"
  - "persistenza, le impostazioni di registrazione"
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Supporto per le impostazioni utente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un VSPackage può definire uno o più categorie di impostazioni, che sono gruppi di variabili di stato che rendono persistenti quando un utente sceglie il **le impostazioni di importazione\/esportazione** comando il **strumenti** menu. Per abilitare la persistenza, utilizzare le impostazioni API nel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 Una voce del Registro di sistema che viene considerata come un punto di impostazioni personalizzato e un GUID definisce la categoria di impostazioni del VSPackage. Un pacchetto in grado di supportare più categorie di impostazioni, ognuno definito da un punto di impostazioni personalizzato.  
  
-   Le implementazioni di impostazioni che si basano sugli assembly di interoperabilità \(utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interface\) deve creare il punto di impostazioni personalizzato al Registro di sistema o utilizzando uno script di registrazione \(file con estensione RGS\). Per altre informazioni, vedere [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts).  
  
-   Il codice che utilizza il Framework di pacchetto gestito \(MPF\) deve creare punti di impostazioni personalizzato allegando un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> a VSPackage per ogni punto di impostazioni personalizzato.  
  
     Se un singolo VSPackage supporta diversi punti di impostazioni personalizzato, ciascun punto di impostazioni personalizzato viene implementato da una classe distinta e ciascuno viene registrato in un'istanza univoca della <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe. Di conseguenza, le impostazioni di implementazione di classe possono supportare più di una categoria di impostazioni.  
  
## Dettagli delle voci del Registro di sistema punto le impostazioni personalizzate  
 Punti di impostazioni personalizzate vengono creati in una voce del Registro di sistema nel percorso seguente: HKLM\\Software\\Microsoft\\VisualStudio\\*\< versione \>*\\UserSettings\\`<CSPName>`, dove `<CSPName>` è il nome del punto di impostazioni personalizzate supportate dal VSPackage e *\< versione \>* è la versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ad esempio 8.0.  
  
> [!NOTE]
>  Il percorso radice dell'HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\< versione \>* può essere sottoposto a override con un'alternativa principale quando il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene inizializzato l'ambiente di sviluppo integrato \(IDE\). Per altre informazioni, vedere [Opzioni della riga di comando](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 La struttura della voce del Registro di sistema è illustrata di seguito:  
  
 HKLM\\Software\\Microsoft\\VisualStudio\\*\< versione \>*\\UserSettings\\  
  
 `<CSPName`\> \= '\#12345' s  
  
 Pacchetto \= '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 Categoria \= '{aaaa YYYYYY verrà TRASMESSA aaaa aaaa YYYYYYYYY}'  
  
 ResourcePackage \= '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'  
  
 AlternateParent \= CategoryName  
  
|Nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|\(Predefinito\)|REG\_SZ|Nome del punto di impostazioni personalizzato|Il nome della chiave, `<CSPName`\>, è il nome non localizzato del punto di impostazioni personalizzato.<br /><br /> Per implementazioni basate su MPF, il nome della chiave viene ottenuto combinando il `categoryName` e `objectName` gli argomenti del <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> costruttore in `categoryName_objectName`.<br /><br /> La chiave può essere vuota o può contenere l'ID di riferimento per la stringa localizzata in una DLL satellite. Questo valore viene ottenuto dal `objectNameResourceID` argomento per il <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> costruttore.|  
|Pacchetto|REG\_SZ|GUID|Il GUID del package VS che implementa il punto di impostazioni personalizzato.<br /><br /> Implementazioni basata sull'utilizzo di MPF di <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> utilizzare il costruttore `objectType` argomento che contiene il package VS <xref:System.Type> e reflection per ottenere questo valore.|  
|Categoria|REG\_SZ|GUID|GUID che identifica la categoria di impostazioni.<br /><br /> Per implementazioni basate sugli assembly di interoperabilità, questo valore può essere un scelto arbitrariamente GUID, che il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE passa a di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> metodi. Tutte le implementazioni di questi due metodi è necessario verificare i relativi argomenti di GUID.<br /><br /> Per implementazioni basate su MPF, questo GUID è ottenuto il <xref:System.Type> della classe che implementa il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] meccanismo di impostazioni.|  
|ResourcePackage|REG\_SZ|GUID|Facoltativo.<br /><br /> Percorso satellite DLL contenente stringhe localizzate se non fornisce l'implementazione VSPackage.<br /><br /> MPF utilizza la reflection per ottenere la risorsa corretta VSPackage, pertanto la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe non viene impostato questo argomento.|  
|AlternateParent|REG\_SZ|Nome della cartella nella pagina Opzioni degli strumenti contenente il punto di impostazioni personalizzato.|Facoltativo.<br /><br /> È necessario impostare questo valore solo se l'implementazione delle impostazioni supporta **ToolsOptions** le pagine che utilizzano il meccanismo di persistenza nel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] anziché il meccanismo del modello di automazione per salvare lo stato.<br /><br /> In questi casi, il valore della chiave AlternateParent è il `topic` sezione il `topic.sub-topic` stringa utilizzata per identificare la particolare **strumentiOpzioni** pagina. Ad esempio, per il **strumentiOpzioni** pagina `"TextEditor.Basic"` il valore di AlternateParent `"TextEditor"`.<br /><br /> Quando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Genera il punto di impostazioni personalizzato, è identico al nome di categoria.|