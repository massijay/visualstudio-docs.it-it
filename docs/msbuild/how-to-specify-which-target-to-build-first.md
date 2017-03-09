---
title: "Procedura: specificare quale destinazione compilare per prima | Microsoft Docs"
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
  - "DefaultTargets (attributo) [MSBuild]"
  - "MSBuild, specifica della destinazione predefinita"
  - "MSBuild, DefaultTargets (attributo)"
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: specificare quale destinazione compilare per prima
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un file di progetto può contenere uno o più `Target` elementi che definiscono come viene compilato il progetto. Il [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) motore crea il primo proiettarlo trovato ed eventuali dipendenze, a meno che il file di progetto contiene un `DefaultTargets` attributo, un `InitialTargets` un attributo o una destinazione è specificato nella riga di comando mediante il **/destinazione** passare.  
  
## <a name="using-the-initialtargets-attribute"></a>Utilizzo dell'attributo InitialTargets  
 Il `InitialTargets` attributo il `Project` elemento specifica una destinazione che verrà eseguita in primo luogo, anche se le destinazioni vengono specificate nella riga di comando o nel `DefaultTargets` attributo.  
  
#### <a name="to-specify-one-initial-target"></a>Per specificare una destinazione iniziale  
  
-   Specificare la destinazione predefinita di `InitialTargets` attributo del `Project` elemento. Ad esempio:  
  
     `<Project InitialTargets="Clean">`  
  
 È possibile specificare più di una destinazione iniziale nel `InitialTargets` attributo elencando le destinazioni in ordine e con un punto e virgola per separare ogni destinazione. Le destinazioni nell'elenco verranno eseguite in sequenza.  
  
#### <a name="to-specify-more-than-one-initial-target"></a>Per specificare più di una destinazione iniziale  
  
-   Elencare le destinazioni iniziali, separate da punti e virgola, nel `InitialTargets` dell'attributo di `Project` elemento. Ad esempio, per eseguire il `Clean` destinazione e quindi la `Compile` di destinazione, digitare:  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="using-the-defaulttargets-attribute"></a>Utilizzo dell'attributo DefaultTargets  
 Il `DefaultTargets` dell'attributo di `Project` elemento specifica quali destinazioni vengono compilate se una destinazione non è specificata in modo esplicito nella riga di comando. Se le destinazioni vengono specificate in entrambi il `InitialTargets` e `DefaultTargets` gli attributi e destinazione non è specificato nella riga di comando, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] esegue le destinazioni specificate nel `InitialTargets` attributo seguita da quelle specificate nel `DefaultTargets` attributo.  
  
#### <a name="to-specify-one-default-target"></a>Per specificare una destinazione predefinita  
  
-   Specificare la destinazione predefinita di `DefaultTargets` attributo del `Project` elemento. Ad esempio:  
  
     `<Project DefaultTargets="Compile">`  
  
 È possibile specificare più di una destinazione predefinita nel `DefaultTargets` attributo elencando le destinazioni in ordine e con un punto e virgola per separare ogni destinazione. Le destinazioni nell'elenco verranno eseguite in sequenza.  
  
#### <a name="to-specify-more-than-one-default-target"></a>Per specificare più di una destinazione predefinita  
  
-   Elencare le destinazioni predefinite, separate da punti e virgola, nel `DefaultTargets` dell'attributo di `Project` elemento. Ad esempio, per eseguire il `Clean` destinazione e quindi la `Compile` di destinazione, digitare:  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="using-the-target-switch"></a>Utilizzo dell'opzione /target  
 Se una destinazione predefinita non è definita nel file di progetto o se non si desidera utilizzare tale destinazione predefinita, è possibile utilizzare l'opzione della riga di comando **/destinazione** per specificare una destinazione diversa. Le destinazioni specificate con il **/destinazione** switch vengono eseguite al posto destinazioni specificate dal `DefaultTargets` attributo. Le destinazioni specificate nel `InitialTargets` attributo sempre eseguito per primo.  
  
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Utilizzare innanzitutto una destinazione diversa da quella predefinita  
  
-   Specificare la destinazione come la prima destinazione utilizzando il **/destinazione** opzione della riga di comando. Ad esempio:  
  
     `msbuild file.proj /target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Per utilizzare diverse destinazioni diverse da quelle predefinite prima  
  
-   Elencare le destinazioni, separate da punti e virgola o da virgole, utilizzando il **/destinazione** opzione della riga di comando. Ad esempio:  
  
     `msbuild <file name>.proj /t:Clean;Compile`  
  
## <a name="see-also"></a>Vedere anche
  [MSBuild](../msbuild/msbuild1.md)  
 [Destinazioni](../msbuild/msbuild-targets.md)   
 [Procedura: pulire una compilazione](../msbuild/how-to-clean-a-build.md)