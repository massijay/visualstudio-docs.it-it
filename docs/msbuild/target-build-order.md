---
title: "Ordine di compilazione delle destinazioni | Microsoft Docs"
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
  - "MSBuild, ordine di compilazione"
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Ordine di compilazione delle destinazioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se l'input di una destinazione dipende dall'output di un'altra destinazione, le destinazioni devono essere ordinate.  È possibile utilizzare questi attributi per specificare l'ordine in cui le destinazioni vengono eseguiti:  
  
-   `InitialTargets`.  Questo attributo di `Project` specifica le destinazioni che verranno eseguite in primo luogo, anche se le destinazioni vengono specificate nella riga di comando o nell'attributo di `DefaultTargets`.  
  
-   `DefaultTargets`.  Questo atttribute di `Project` specifica che le destinazioni vengono eseguiti se una destinazione non viene specificato in modo esplicito la riga di comando.  
  
-   `DependsOnTargets`.  Questo attributo di `Target` specifica i database di destinazione da eseguire prima che questa destinazione possa funzionare.  
  
-   `BeforeTargets` e `AfterTargets`.  Questi attributi di `Target` specificano che tale destinazione deve eseguire prima o dopo le destinazioni specificate \(MSBuild 4,0\).  
  
 Una destinazione non viene mai eseguita due volte durante una compilazione, anche se una destinazione successiva nella build dipende da essa.  Quando una destinazione viene eseguita, il contributo di quest'ultima alla build è completo.  
  
 Le destinazioni possono presentare un attributo `Condition`.  Se la condizione specificata risulta a `false`, la destinazione non viene eseguita e non influisce sulla build.  Per ulteriori informazioni sulle condizioni, vedere [Conditions](../msbuild/msbuild-conditions.md).  
  
## Destinazioni iniziali  
 L'attributo di `InitialTargets` di elemento di [Progetto](../msbuild/project-element-msbuild.md) specifica le destinazioni che verranno eseguite in primo luogo, anche se le destinazioni vengono specificate nella riga di comando o nell'attributo di `DefaultTargets`.  In genere le destinazioni iniziali vengono utilizzate per il controllo degli errori.  
  
 Il valore dell'attributo di `InitialTargets` può essere un delimitato da punti e virgola, elenco ordinato di destinazioni.  Nell'esempio seguente viene specificato che la destinazione di `Warm` esegue e quindi la destinazione di `Eject` esecuzione.  
  
```  
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 I progetti importati possono presentare attributi `InitialTargets` propri.  Tutte le destinazioni iniziali vengono aggregate insieme e vengono eseguite in ordine.  
  
 Per ulteriori informazioni, vedere [How to: Specify Which Target to Build First](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## Destinazioni predefinite  
 L'attributo di `DefaultTargets` di elemento di [Progetto](../msbuild/project-element-msbuild.md) specifica quali destinazioni vengono compilate se una destinazione non viene specificato in modo esplicito in una riga di comando.  
  
 Il valore dell'attributo di `DefaultTargets` può essere un delimitato da punti e virgola, elenco ordinato di destinazioni predefinite.  Nell'esempio seguente viene specificato che la destinazione di `Clean` esegue e quindi la destinazione di `Build` esecuzione.  
  
```  
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 È possibile eseguire l'override delle destinazioni predefinite utilizzando l'opzione di **\/target** la riga di comando.  Nell'esempio seguente viene specificato che la destinazione di `Build` esegue e quindi la destinazione di `Report` esecuzione.  Quando si specificano le destinazioni in questo modo, tutte le destinazioni predefinite vengono ignorate.  
  
 `msbuild /target:Build;Report`  
  
 Se entrambe le destinazioni e destinazioni predefinite iniziali vengono specificati e se nessuna destinazione della riga di comando, MSBuild esegue le destinazioni iniziali innanzitutto e quindi le destinazioni predefinite.  
  
 I progetti importati possono presentare attributi `DefaultTargets` propri.  Il primo attributo `DefaultTargets` trovato determina quali destinazioni predefinite verranno eseguite.  
  
 Per ulteriori informazioni, vedere [How to: Specify Which Target to Build First](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## Prima destinazione  
 Se non vi sono destinazioni iniziali, predefinite o della riga di comando, MSBuild esegue la prima destinazione che trova nel file di progetto o in qualsiasi file di progetto importato.  
  
## Dipendenze fra destinazioni  
 Le destinazioni possono descrivere relazioni di dipendenza con altre destinazioni.  L'attributo `DependsOnTargets` indica che una destinazione dipende da altre destinazioni.  Di seguito è riportato un esempio:  
  
```  
<Target Name="Serve" DependsOnTargets="Chop;Cook" />  
```  
  
 indica a MSBuild che la destinazione di `Serve` dipende dalla destinazione di `Chop` e dal database di destinazione di `Cook`.  MSBuild esegue la destinazione di `Chop` quindi esegue la destinazione di `Cook` prima di eseguire la destinazione di `Serve`.  
  
## Prima di destinazione e dopo le destinazioni  
 In MSBuild 4.0 è possibile specificare l'ordine delle destinazioni tramite gli attributi `BeforeTargets` e `AfterTargets`.  
  
 Si consideri lo script seguente.  
  
```  
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Compile">  
        <Message Text="Compiling" />  
    </Target>  
    <Target Name="Link">  
        <Message Text="Linking" />  
    </Target>  
</Project>  
```  
  
 Per creare `Optimize` di destinazione intermedio che viene eseguita dopo la destinazione di `Compile`, ma prima della destinazione di `Link`, aggiungere la destinazione seguente in qualsiasi punto dell'elemento di `Project`.  
  
```  
<Target Name="Optimize"   
    AfterTargets="Compile" BeforeTargets="Link">  
    <Message Text="Optimizing" />  
</Target>  
```  
  
## Determinazione dell'ordine di compilazione delle destinazioni  
 MSBuild determina l'ordine di compilazione delle destinazioni come segue:  
  
1.  le destinazioni di`InitialTargets` vengono eseguiti.  
  
2.  Le destinazioni specificate nella riga di comando dall'opzione **\/target** vengono eseguite.  Se non si specifica il database di destinazione nella riga di comando, quindi le destinazioni di `DefaultTargets` vengono eseguiti.  Se non è presente, il primo database di destinazione initialtargets o viene eseguito.  
  
3.  L'attributo `Condition` della destinazione viene valutato.  Se l'attributo di `Condition` è presente e risulta a `false`, la destinazione non viene eseguita e non ha più alcun effetto sulla compilazione.  
  
4.  Prima che una destinazione venga eseguita, ne vengono eseguite le destinazioni `DependsOnTargets`.  
  
5.  Prima che una destinazione venga eseguita, vengono eseguite tutte le destinazioni che la indicano nel proprio attributo `BeforeTargets`.  
  
6.  Prima che una destinazione venga eseguita, viene eseguito un confronto fra i relativi attributi `Inputs` e `Outputs`.  Se MSBuild determina che i file di output sono non aggiornati rispetto a o ai file di input corrispondenti, MSBuild esegue la destinazione.  In caso contrario, MSBuild ignora la destinazione.  
  
7.  Dopo che una destinazione viene eseguita o ignorata, vengono eseguite tutte le destinazioni che la indicano nel proprio attributo `AfterTargets`.  
  
## Vedere anche  
 [Targets](../msbuild/msbuild-targets.md)