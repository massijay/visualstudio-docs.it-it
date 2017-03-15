---
title: "Comandi e menu che utilizzano gli assembly di interoperabilità | Documenti di Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 13
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
ms.openlocfilehash: c0d2cf9218743ec21121d849482e5a3086b36ab2
ms.lasthandoff: 02/22/2017

---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Comandi e menu che utilizzano gli assembly di interoperabilità
Un package VS che implementa i comandi di menu e barra degli strumenti utilizzando gli assembly di interoperabilità deve:  
  
-   Informare il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) sui comandi supportati e se sono attualmente abilitate.  
  
-   Rispettare le regole (contratto) per la gestione dei comandi.  
  
-   Implementare la gestione dei comandi in modo esplicito, utilizzando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
 Di seguito viene descritto come eseguire queste attività.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Determinazione dello stato del comando tramite gli assembly di interoperabilità](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Viene descritto come un VSPackage notifica all'IDE sui comandi supportati e se sono attualmente abilitate.  
  
 [Contratti di comando nell'assembly di interoperabilità](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Fornisce una definizione del contratto di comandi di base utilizzato da tutti i package VS che implementa i comandi tramite gli assembly di interoperabilità  
  
 [Implementazione](../../extensibility/internals/command-implementation.md)  
 Viene fornita una panoramica di come un VSPackage implementa un comando.  
  
 [Registrazione dei gestori di comando di Assembly di interoperabilità](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Descrive le voci del Registro di sistema necessarie per inviare una notifica dell'IDE che un pacchetto Visual Studio fornisce un gestore del comando.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Disponibilità](../../extensibility/internals/command-availability.md)  
 Descrive i criteri utilizzati per determinare quali comandi VSPackage sono disponibili e quali oggetti vengono gestiti dall'IDE.  
  
 [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Vengono fornite informazioni dettagliate su come creare un'interfaccia utente che utilizza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comando supporto.  
  
 [Routing dei comandi in VS](../../extensibility/internals/command-routing-in-vspackages.md)  
 Panoramica del processo utilizzato per correlare un oggetto con la richiesta corretta del comando.
