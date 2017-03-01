---
title: Utilizzare e fornire servizi | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 41
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
ms.openlocfilehash: fb380330420d6256190ade75e0afe89f8cbda303
ms.lasthandoff: 02/22/2017

---
# <a name="using-and-providing-services"></a>Utilizzo e servizi
Un servizio è un contratto tra due VSPackage. Un pacchetto Visual Studio offre un set specifico di interfacce per un altro VSPackage da utilizzare. Ad esempio, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] offre il <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>mantenerlo a qualsiasi pacchetto carichi.</xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> Questo servizio fornisce l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>interfaccia, che consente di scrivere nel registro attività.</xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Per ulteriori informazioni, vedere [procedura: utilizzare il registro attività](../extensibility/how-to-use-the-activity-log.md).  
  
 Package VS può offrire i propri servizi tramite l' <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>  
  
 Visual Studio offre servizi importanti, ad esempio le operazioni seguenti:  
  
|Servizio IDE|Descrizione|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Fornisce la gestione di servizi di accesso all'IDE con funzionalità di base, VSPackage e nel Registro di sistema.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornisce funzionalità legate all'interfaccia utente nell'IDE, ad esempio la possibilità di creare strumenti e finestre di documento e finestre di base.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution></xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornisce funzionalità base associate alla soluzione, ad esempio la possibilità di enumerare i progetti, creare nuovi progetti e monitorare le modifiche del progetto.|  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Funzionalità fondamentali del servizio](../extensibility/internals/service-essentials.md)  
 Visualizza gli elementi importanti di un servizio di Visual Studio.  
  
 [Procedura: ottenere un servizio](../extensibility/how-to-get-a-service.md)  
 Viene illustrato come richiedere (utilizzare) un servizio.  
  
 [Procedura: fornire un servizio](../extensibility/how-to-provide-a-service.md)  
 Viene descritto come fornire un servizio.  
  
 [Procedura: fornire un servizio asincrono Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Viene descritto come fornire un servizio asincrono.  
  
 [Procedura: risolvere i problemi relativi a servizi](../extensibility/how-to-troubleshoot-services.md)  
 Vengono descritti i problemi comuni e vengono fornite soluzioni a essi.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
