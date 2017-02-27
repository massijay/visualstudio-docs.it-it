---
title: "Il motore di debug | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motori di debug"
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Il motore di debug
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Attività \(DE\) del modulo di debug tramite l'interprete o il sistema operativo per fornire servizi di debug quali il controllo di esecuzione, i punti di interruzione e la valutazione delle espressioni.  Il DE è responsabile di monitorare lo stato di un programma sottoposto a debug.  Per eseguire tale scopo, il DE utilizza i metodi sono disponibili nel runtime supportato, se alla CPU o da API forniti dal runtime.  
  
 Ad esempio, Common Language \(CLR\) Runtime fornisce i meccanismi per monitorare un programma in esecuzione tramite le interfacce di ICorDebugXXX.  Un DE che supporta CLR utilizza le interfacce appropriate di ICorDebugXXX per tenere traccia di un programma di codice gestito che viene eseguito il debug.  Quindi comunica tutte le modifiche dello stato all'amministratore di debug della sessione \(SDM\), che inoltra tali informazioni all'IDE di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  
  
> [!NOTE]
>  Il modulo di debug destinato al runtime specifico, ovvero, il sistema in cui il programma che viene eseguito durante il debug.  CLR rappresenta il runtime per il codice gestito e il runtime Win32 sono per le applicazioni Windows native.  Se il linguaggio che si può utilizzare una di queste due runtime, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] già fornisce i motori di debug necessari.  Tutto ciò che è necessario distribuire è un analizzatore di espressioni.  
  
## Passaggi del motore di debug  
 I servizi di monitoraggio vengono implementati tramite il DE interfaces e possono causare il pacchetto di debug per la transizione tra le modalità operative diversi.  Per ulteriori informazioni, vedere [Modalità operative](../../extensibility/debugger/operational-modes.md).  Esiste in genere un solo DE implementation per ambiente di runtime.  
  
> [!NOTE]
>  Mentre è DE implementations separato per Transact\-SQL e [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)], VBScript e [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] condividono un singolo DE.  
  
 eseguire il debug di[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]consente ai motori di debug per eseguire uno dei due modi seguenti: nello stesso processo shell di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], o nello stesso processo del programma oggetto sottoposto a debug.  La seconda forma si verifica in genere quando il processo sottoposto a debug è in realtà un funzionamento dello script in un interprete e il motore di debug deve avere una conoscenza approfondita interprete per monitorare lo script.  Si noti che in questo caso, l'interprete è effettivamente il runtime; i motori di debug sono per le implementazioni di runtime specifiche.  Inoltre, l'implementazione di un singolo DE può essere suddivisa oltre i limiti del computer e di processo, ad esempio debug remoto\).  
  
 Il DE espone le interfacce di debug di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Le comunicazioni è tramite COM.  Se il DE è in\-process caricato, out\-of\-process, o in un altro computer, non influisce sulla comunicazione componente.  
  
 Funzionamento di DE con un componente dell'analizzatore di espressioni per abilitare il DE per il runtime particolare comprendano la sintassi delle espressioni.  Il DE funziona anche con una parte del gestore dei simboli per accedere alle informazioni di debug sui simboli generati dal compilatore di linguaggio.  Per ulteriori informazioni, vedere [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md) e [Provider di simboli](../../extensibility/debugger/symbol-provider.md).  
  
## Vedere anche  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)   
 [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md)   
 [Provider di simboli](../../extensibility/debugger/symbol-provider.md)