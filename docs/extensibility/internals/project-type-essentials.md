---
title: Progetto di tipo Essentials | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 11
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
ms.openlocfilehash: 77ac7852a4fe42e69602edcd7e75354b404e315e
ms.lasthandoff: 02/22/2017

---
# <a name="project-type-essentials"></a>Essentials tipo di progetto
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]include diversi tipi di progetto per le lingue, ad esempio [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]consente inoltre di creare i propri tipi di progetto.  
  
 Se si desidera aggiungere comandi personalizzati, gli editor o finestre degli strumenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è possibile farlo senza creare un nuovo tipo di progetto. Per altre informazioni, vedere i seguenti argomenti:  
  
-   [I comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [Estensione e personalizzazione di finestre degli strumenti](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 Analogamente, se si desidera personalizzare il comportamento del parametro [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipi di progetto, è possibile eseguire utilizzando sottotipi di progetto. Per ulteriori informazioni, vedere [sottotipi progetto](../../extensibility/internals/project-subtypes.md).  
  
 È necessario creare un nuovo tipo di progetto per i progetti che si basano su una lingua diversa da [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] se si desidera supportare uno o più delle operazioni seguenti:  
  
-   Compilazione  
  
-   Distribuzione  
  
-   Configurazioni multiple  
  
-   Controllo del codice sorgente  
  
-   Debug  
  
-   Elementi del progetto in Esplora soluzioni  
  
-   Il **Apri progetto** o **nuovo progetto** le finestre di dialogo  
  
-   Nidificazione di progetto  
  
-   Per ulteriori informazioni sulle funzionalità dei tipi di progetto, vedere quanto segue:  
  
-   Tipi di progetto sono oggetti in un VSPackage che implementano il set di interfacce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prevista. Se si utilizza c# per sviluppare un tipo di progetto, le classi del progetto Managed Package Framework implementano le interfacce necessarie per l'utente e consentono di ereditano tale implementazione. Per ulteriori informazioni, vedere [utilizzando Managed Package Framework per implementare un tipo di progetto (c#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
-   Per gli sviluppatori in C++, le classi nella libreria HierUtil funzionano in modo simile. Per ulteriori informazioni, vedere [non incluso nella compilazione: utilizzo di classi di progetto HierUtil7 per implementare un tipo di progetto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
-   Tipi di progetto possono supportare dati diversi dai file di codice sorgente tipico che compila in un assembly .exe o DLL. Ad esempio, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetti di database contengono riferimenti a script e query file archiviati su disco e aggiungere comandi a **Esplora** per eseguire gli script e query su un database, ma i progetti non supportano il comportamento di compilazione. Per ulteriori informazioni, vedere [di apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
-   Un tipo di progetto non è necessario utilizzare tutti i file. Ad esempio, un tipo di progetto potrebbe memorizzare tutti i relativi dati in un database. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Fornisce tipi di progetto di controllo completo sulla modalità sono persistenti i dati per progetti ed elementi di progetto. Per ulteriori informazioni, vedere [decisioni di progettazione di tipo progetto](../../extensibility/internals/project-type-design-decisions.md).  
  
-   Tipi di progetto è necessario fornire un *factory del progetto*, ovvero un oggetto che crea un'istanza del progetto digitare ogni volta che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] detto aprire o creare un progetto basato su tale tipo di progetto. Per ulteriori informazioni, vedere [creazione progetto istanze da utilizzando progetto factory](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
-   I tipi di progetto devono fornire modelli per progetti ed elementi del progetto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilizza i modelli quando si creano nuovi progetti e aggiungere nuovi elementi ai progetti esistenti. Per ulteriori informazioni, vedere [aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
-   Tipi di progetto possono supportare più configurazioni, ad esempio Debug e rilascio. Gli utenti possono modificare le configurazioni diverse di un progetto utilizzando le pagine di proprietà fornito. Per ulteriori informazioni, vedere [la gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di progetto di distribuzione](../../extensibility/internals/deploying-project-types.md)
