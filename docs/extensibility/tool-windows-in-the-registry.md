---
title: Strumento Windows nel Registro di sistema | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 12
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
ms.openlocfilehash: dc99605a367bb3584f9766b50aa2a4ff382656c4
ms.lasthandoff: 02/22/2017

---
# <a name="tool-windows-in-the-registry"></a>Finestre degli strumenti nel Registro di sistema
Package VS che forniscono le finestre degli strumenti è necessario registrare con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] come strumento di provider di finestra. Finestre degli strumenti create utilizzando il modello di pacchetto di Visual Studio per eseguire questa operazione predefinita. I provider di finestra strumento hanno chiavi di registro di sistema che specificano gli attributi di visibilità, ad esempio dimensione predefinita della finestra dello strumento e la posizione, il GUID della finestra che viene utilizzato come il riquadro della finestra dello strumento e lo stile di ancoraggio.  
  
 Durante lo sviluppo, il provider di finestra degli strumenti gestita registra finestre degli strumenti aggiungendo gli attributi per il codice sorgente e quindi eseguendo l'utilità RegPkg.exe sull'assembly risultante. Per ulteriori informazioni, vedere [la registrazione di una finestra degli strumenti](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Registrazione provider finestra dello strumento non gestito  
 Provider di finestra dello strumento non gestito è necessario registrare con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nella sezione ToolWindows del Registro di sistema. Nel seguente frammento di file con estensione reg viene illustrato come una finestra degli strumenti dinamica potrebbe essere registrata:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 La prima chiave nell'esempio precedente, il numero di versione è la versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ad esempio 7.1 o 8.0, la sottochiave {f0e1e9a1-9860-484d-ad5d-367d79aabf55} è il GUID del riquadro strumenti della finestra (DynamicWindowPane) e il valore predefinito {01069cdd-95ce-4620-ac21-ddff6c57f012} è il GUID del VSPackage fornendo la finestra degli strumenti. Per una spiegazione delle sottochiavi Float e DontForceCreate, vedere [finestra strumento di configurazione](../extensibility/tool-window-display-configuration.md).  
  
 La seconda chiave facoltativa, ToolWindows\Visibility, specifica il GUID di comandi che richiedono la finestra degli strumenti deve essere reso visibile. Sono non disponibili in questo caso, nessun comando specificato. Per ulteriori informazioni, vedere [finestra strumento di configurazione](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti di base sui VSPackage](../misc/vspackage-essentials.md)
