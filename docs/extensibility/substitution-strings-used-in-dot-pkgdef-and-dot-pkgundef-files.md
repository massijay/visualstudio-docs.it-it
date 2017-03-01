---
title: Utilizzato stringhe di sostituzione. Pkgdef e. File Pkgundef | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 4
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: c64a760b821663ba488f6f9dab415bad13d6047d
ms.lasthandoff: 02/22/2017

---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Utilizzato stringhe di sostituzione. Pkgdef e. File Pkgundef
È possibile utilizzare le stringhe di sostituzione elencate sotto il. pkgdef e applicazione di shell isolata di file .pkgundef definite per Visual Studio.  
  
## <a name="substitution-strings"></a>Stringhe di sostituzione  
  
|Stringa|Descrizione|  
|------------|-----------------|  
|$=*Registro*$|Il valore di *registro* voce. Se la stringa della voce del Registro di sistema termina con una barra rovesciata (\\), quindi viene utilizzato il valore predefinito della sottochiave del Registro di sistema. Ad esempio, la sostituzione della stringa $= HKEY_CURRENT_USER\Environment\TEMP$ viene espanso nella cartella temporanea dell'utente corrente.|  
|$ $AppName|Il nome completo dell'applicazione che viene passato per i punti di ingresso AppEnv.dll. Il nome completo è costituito il nome dell'applicazione, un carattere di sottolineatura e l'identificatore di classe (CLSID) dell'oggetto di automazione dell'applicazione, è anche registrato come valore dell'impostazione ThisVersionDTECLSID nel file. pkgdef del progetto.|  
|$AppDataLocalFolder|La sottocartella % LOCALAPPDATA % per questa applicazione.|  
|$ $BaseInstallDir|Il percorso completo della posizione in cui è stato installato Visual Studio.|  
|$ $CommonFiles|Il valore della variabile di ambiente % CommonProgramFiles %.|  
|$ $MyDocuments|Il percorso completo della cartella documenti dell'utente corrente.|  
|$ $PackageFolder|Il percorso completo della directory che contiene i file di assembly di pacchetto per l'applicazione.|  
|$ $ProgramFiles|Il valore della variabile di ambiente % ProgramFiles %.|  
|$ $RootFolder|Il percorso completo della directory radice dell'applicazione.|  
|$ $RootKey|La chiave del Registro di sistema radice per l'applicazione. Per impostazione predefinita la radice è HKEY_CURRENT_USER\Software\\*CompanyName*\\*NomeProgetto*\\*VersionNumber* (quando l'applicazione è in esecuzione, _Config viene aggiunto a questa chiave). È impostato per il valore RegistryRoot il *SolutionName*file. pkgdef.<br /><br /> La stringa $ $RootKey può essere utilizzata per recuperare un valore del Registro di sistema nella sottochiave applicazione. Ad esempio, la stringa "$= $RootKey$ \AppIcon$" restituirà il valore della voce AppIcon nella sottochiave radice dell'applicazione.<br /><br /> Il parser elabora il file. pkgdef in modo sequenziale e può accedere a una voce del Registro di sistema nella sottochiave applicazione solo se la voce è stata definita in precedenza|  
|$ $ShellFolder|Il percorso completo della posizione in cui è stato installato Visual Studio.|  
|$ $System|La cartella Windows\system32.|  
|$ $WINDIR|La cartella Windows.|  
  
 Se il parser non riconosce la stringa di sostituzione o non è possibile determinare il valore di una voce del Registro di sistema o una variabile di ambiente, quindi non verrà eseguita su quella parte della stringa di sostituzione.
