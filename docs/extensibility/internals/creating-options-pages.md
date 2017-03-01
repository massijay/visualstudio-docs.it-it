---
title: Creare le pagine delle opzioni | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 56a51aa0a2232ff149e1959842fced1dc26e7c1b
ms.lasthandoff: 02/22/2017

---
# <a name="creating-options-pages"></a>Creazione di pagine di opzioni
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] framework pacchetto gestito, le classi derivate da <xref:Microsoft.VisualStudio.Shell.DialogPage>estendere il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE aggiungendo **opzioni** pagine sotto il **strumenti** menu.</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
 Un oggetto che implementa un determinato **opzione strumenti** pagina è associata a VSPackage specifico per il <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>oggetto.</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 Poiché l'ambiente di un'istanza dell'oggetto che implementa un particolare **ToolsOptions** pagina quando è visualizzata la pagina specifica dall'IDE:  
  
-   Oggetto **opzione strumenti** pagina deve essere implementata nel proprio oggetto e non per l'oggetto che implementa un VSPackage.  
  
-   Un oggetto non può implementare più **ToolsOptions** pagine.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Registrazione di un provider di pagina di opzioni strumenti  
 Una configurazione utente supporto VSPackage tramite **Strumenti opzioni** pagine indica gli oggetti che li fornisce **opzioni degli strumenti** pagine applicando le istanze di <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>applicato per il <xref:Microsoft.VisualStudio.Shell.Package>implementazione.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 Deve esistere un'istanza di <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>per ogni <xref:Microsoft.VisualStudio.Shell.DialogPage>-tipo che implementa derivato un **ToolsOptions** pagina.</xref:Microsoft.VisualStudio.Shell.DialogPage> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 Ogni istanza di <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>utilizza il tipo che implementa il **opzioni degli strumenti** pagina, le stringhe che contengono la categoria e sottocategoria utilizzato per identificare un **Strumenti opzioni** pagina e informazioni per registrare il tipo come fornire un **opzioni degli strumenti** pagina.</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
## <a name="persisting-tools-options-page-state"></a>Persistente lo stato di pagina di opzioni strumenti  
 Se un **Strumenti opzioni** di implementazione della pagina è registrato con il supporto di automazione abilitato, l'IDE mantiene lo stato della pagina insieme a tutti gli altri **ToolsOptions** pagine.  
  
 Un VSPackage è possibile gestire il proprio persistenza tramite <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Deve essere utilizzato solo uno o l'altro metodo di persistenza.  
  
## <a name="implementing-dialogpage-class"></a>Implementazione della classe DialogPage  
 Oggetto che fornisce l'implementazione di un pacchetto di un <xref:Microsoft.VisualStudio.Shell.DialogPage>-tipo derivato può sfruttare le funzionalità seguenti ereditate:</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
-   Una finestra dell'interfaccia utente predefinita.  
  
-   Oggetto predefinito disponibile il meccanismo di persistenza se <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>viene applicato alla classe, o se il <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A>è impostata su `true` per <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>cui viene applicato alla classe.</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> </xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>  
  
-   Supporto di automazione.  
  
 Il requisito minimo per un oggetto che implementa un **Strumenti opzioni** pagina utilizzando <xref:Microsoft.VisualStudio.Shell.DialogPage>è l'aggiunta di proprietà pubbliche.</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
 Se la classe registrata correttamente come un **Strumenti opzioni** pagina provider, quindi le proprietà pubbliche sono disponibili nel **opzioni** sezione il **strumenti** menu sotto forma di una griglia delle proprietà.  
  
 Tutte queste funzionalità predefinito possono essere sottoposto a override. Ad esempio, per creare più sofisticata interfaccia utente richiede solo l'override dell'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.</xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>  
  
## <a name="example"></a>Esempio  
 Di seguito è un'implementazione semplice "hello world" di una pagina di opzioni. Aggiungere il codice seguente a un progetto predefinito creato dal modello di pacchetto di Visual Studio con il **comando di Menu** opzione selezionata in modo adeguato illustra le funzionalità della pagina opzione.  
  
### <a name="description"></a>Descrizione  
 La classe seguente definisce una pagina di opzioni minimo "hello world". All'apertura, l'utente può impostare pubblico `HelloWorld` proprietà in una griglia delle proprietà.  
  
### <a name="code"></a>Codice  
 [!code-cs[UI_UserSettings_ToolsOptionPages&#11;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#11;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>Descrizione  
 Applicando l'attributo seguente alla classe del pacchetto rende disponibili le opzioni pagina quando viene caricato il pacchetto. I numeri sono arbitrari ID di risorsa per la categoria e la pagina e il valore booleano alla fine specifica se la pagina supporta l'automazione.  
  
### <a name="code"></a>Codice  
 [!code-cs[UI_UserSettings_ToolsOptionPages &#07;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#07;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>Descrizione  
 Il seguente gestore eventi visualizza un risultato in base al valore della proprietà impostata nella pagina Opzioni. Usa il <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>metodo con il risultato in modo esplicito il cast nel tipo di pagina opzione personalizzata per accedere alle proprietà esposte dalla pagina.</xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>  
  
 Nel caso di un progetto generato dal modello di pacchetto, chiamare questa funzione dal `MenuItemCallback` funzione di collegarlo al comando predefinito viene aggiunto il **strumenti** menu.  
  
### <a name="code"></a>Codice  
 [!code-cs[UI_UserSettings_ToolsOptionPages &#08;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages &#08;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni e impostazioni utente estensione](../../extensibility/extending-user-settings-and-options.md)   
 [Supporto di automazione per le pagine di opzioni](../../extensibility/internals/automation-support-for-options-pages.md)
