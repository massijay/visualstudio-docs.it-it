---
title: "Procedura: compilare destinazioni specifiche all&#39;interno di soluzioni tramite MSBuild.exe | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, compilazione di destinazioni specifiche in una soluzione"
  - "MSBuild.exe, compilazione di destinazioni specifiche in una soluzione"
  - "MSBuild, msbuild.exe"
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: compilare destinazioni specifiche all&#39;interno di soluzioni tramite MSBuild.exe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile utilizzare MSBuild.exe per compilare destinazioni specifiche di progetti specifici in una soluzione.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Per compilare una destinazione specifica di un progetto specifico in una soluzione  
  
1.  Nella riga di comando, digitare `MSBuild.exe <SolutionName>.sln`, dove `<SolutionName>` corrisponde al nome del file della soluzione che contiene la destinazione che si desidera eseguire.  
  
2.  Specificare la destinazione dopo il **/t** passare nel formato *NomeProgetto*:*TargetName*.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene eseguita la `Rebuild` destinazione del `NotInSlnFolder` del progetto, quindi viene eseguita la `Clean` destinazione del `InSolutionFolder` progetto che si trova nel `NewFolder` cartella della soluzione.  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento della riga di comando](../msbuild/msbuild-command-line-reference.md)   
 [Riferimenti di MSBuild](../msbuild/msbuild-reference.md)   
 [ MSBuild](../msbuild/msbuild1.md)  
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)