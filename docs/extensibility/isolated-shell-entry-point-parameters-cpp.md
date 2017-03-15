---
title: Isolamento parametri punto di ingresso Shell (C++) | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode, Start entry point
- Visual Studio shell, isolated mode, Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 10
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
ms.openlocfilehash: 13f05a147f0d9ab36d49b93cc91bcbaa7b002c70
ms.lasthandoff: 02/22/2017

---
# <a name="isolated-shell-entry-point-parameters-c"></a>Parametri punto di ingresso Shell isolata (C++)
Quando viene avviata un'applicazione basata su shell di Visual Studio, viene chiamato il punto di ingresso di avvio della shell di Visual Studio. Le seguenti impostazioni possono essere sostituite nella chiamata al punto di ingresso di avvio della shell. Per una descrizione di ciascuna impostazione, vedere [. Il file pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
-   AddinsAllowed  
  
-   AllowsDroppedFilesOnMainWindow  
  
-   AppName  
  
-   CommandLineLogo  
  
-   DefaultHomePage  
  
-   DefaultProjectsLocation  
  
-   DefaultSearchPage  
  
-   DefaultUserFilesFolderRoot  
  
-   DisableOutputWindow  
  
-   HideMiscellaneousFilesByDefault  
  
-   HideSolutionConcept  
  
-   NewProjDlgInstalledTemplatesHdr  
  
-   NewProjDlgSlnTreeNodeTitle  
  
-   SolutionFileCreatorIdentifier  
  
-   SolutionFileExt  
  
-   UserFilesSubFolderName  
  
-   UserOptsFileExt  
  
 Il modello di Visual Studio Shell isolata crea un file di origine, *solutionName*. cpp, in cui *solutionName* è il nome della soluzione per l'applicazione. Questo file definisce il punto di ingresso principale per l'applicazione, la funzione tWinMain. Questa funzione richiama il punto di ingresso di avvio della shell.  
  
 È possibile modificare il comportamento dell'applicazione modificando queste impostazioni all'avvio dell'applicazione.  
  
## <a name="parameters"></a>Parametri  
 Il punto di ingresso di avvio della shell di Visual Studio definisce cinque parametri. Non modificare i primi quattro parametri. Il quinto parametro accetta un elenco di override delle impostazioni. Il punto di ingresso di avvio della shell viene chiamato dal punto di ingresso principale di un'applicazione.  
  
 Il punto di ingresso di avvio della shell ha la firma seguente.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Se non si desidera eseguire l'override di eventuali impostazioni dell'applicazione, lasciare il valore delle impostazioni di sostituzione parametro come un puntatore null.  
  
 Per eseguire l'override di una o più impostazioni, passare una stringa Unicode che contiene le impostazioni da sottoporre a override. La stringa è un elenco separato da punto e virgola di coppie nome-valore. Ogni coppia contiene il nome dell'impostazione di override, seguito da un segno di uguale (=), seguito dal valore di applicare l'impostazione.  
  
> [!NOTE]
>  Non includere spazi nelle stringhe Unicode.  
  
 Per le impostazioni booleane, le stringhe seguenti rappresentano il valore true; tutte le altre stringhe che rappresentano il valore false. Queste stringhe di maiuscole e minuscole.  
  
-   \+  
  
-   1  
  
-   -1  
  
-   attivo  
  
-   true  
  
-   sì  
  
## <a name="example"></a>Esempio  
 Per disabilitare i componenti aggiuntivi e modificare il percorso di progetti predefinito per l'applicazione, è possibile impostare l'ultimo parametro per "AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp".  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione Shell isolata](../extensibility/customizing-the-isolated-shell.md)   
 [. File pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
