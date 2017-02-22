---
title: "Creazione di tipi di progetto | Microsoft Docs"
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
  - "condizioni per la creazione di tipi di progetto"
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Creazione di tipi di progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

creare un nuovo tipo di progetto fornisce una base per personalizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per gli utenti.  tuttavia, creare un nuovo tipo di progetto non è obbligatorio per tutte le personalizzazioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Le linee guida seguenti devono aiutare a determinare se un nuovo tipo di progetto è obbligatorio per lo scenario.  
  
## creare un nuovo tipo di progetto  
 You must create a project type if you want to customize [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] to act in one or more of the following ways:  
  
-   Partecipare alla compilazione, la distribuzione, le configurazioni e il controllo del codice sorgente.  
  
-   Supporto di debug offrono.  
  
-   elementi di progetto visualizzati in **Esplora soluzioni**.  
  
-   utilizzare la finestra di dialogo di **nuovo progetto** o di **aprire il progetto** .  
  
-   Annidamento di progetto di supporto.  
  
## estendere un tipo di progetto esistente  
 È possibile creare un nuovo tipo di progetto che può utilizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nei seguenti modi per modificare o estendere il comportamento di un tipo di progetto esistente, ad esempio, modificando il processo di compilazione per i progetti [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] :  
  
-   Utilizzare i file più come una singola unità.  
  
-   Visualizzare un singolo file come gerarchia di sottomarino\-elementi.  
  
-   Visualizzare un contesto del comando intorno agli editor.  
  
-   Visualizzare un contesto del servizio per gli editor.  
  
## utilizzare un tipo di progetto esistente  
 Creare un nuovo progetto non è necessario talvolta.  Nella tabella seguente vengono illustrate le attività che non è necessario creare un tipo di progetto di.  
  
|Task|Descrizione|  
|----------|-----------------|  
|comandi di gestione|Tutto il package VS possibile gestire i comandi.|  
|compilare un editor|Editor personalizzati possono essere registrati.  Per ulteriori informazioni, vedere [Document Windows and Editors](http://msdn.microsoft.com/it-it/603625e1-62b6-413a-bc44-089346e166bc).|  
|finestre proprietarie|È possibile creare sia lo strumento che le finestre di documento senza aggiungere un nuovo tipo di progetto.|  
|Esporre le proprietà nella Finestra Proprietà|Tutti gli oggetti possono esporre le proprietà.|  
  
## creare un sottotipo di progetto  
 È possibile utilizzare i sottotipi di progetto per estendere un tipo di progetto gestito senza dover creare un nuovo tipo di progetto.  I sottotipi di progetto utilizzano l'aggregazione COM per estendere i progetti gestiti scritti in Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o in[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  Con aggregazione COM, è possibile riutilizzare gran parte dell'implementazione gestita del sistema di progetto e di personalizzazione per uno scenario specifico con aggregazione e l'utilizzo di supporto delle interfacce.  per ulteriori informazioni sui sottotipi di progetto, vedere [Progetto \(sottotipi\)](../../extensibility/internals/project-subtypes.md).  
  
## Vedere anche  
 [Document Windows and Editors](http://msdn.microsoft.com/it-it/603625e1-62b6-413a-bc44-089346e166bc)   
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)