---
title: "Procedura: Ignorare gli errori nelle attivit&#224; | Microsoft Docs"
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
  - "MSBuild, ignorando gli errori"
  - "ContinueOnError (attributo) [MSBuild]"
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: Ignorare gli errori nelle attivit&#224;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Talvolta una compilazione per la tolleranza di errore di errori in determinate attività. Se tali attività non critici per l'esito negativo, si desidera che la compilazione continuare poiché è ancora possibile produrre l'output desiderato. Ad esempio, se un progetto utilizza un `SendMail` attività per inviare un messaggio di posta elettronica dopo ogni componente viene compilato, può essere ritenuto accettabile per la generazione proceda fino al completamento anche quando il server di posta elettronica non sono disponibili e non possono essere inviati i messaggi di stato. In alternativa, ad esempio, se i file intermedi vengono generalmente eliminati durante la compilazione, può essere ritenuto accettabile per la generazione proceda fino al completamento anche quando tali file non possono essere eliminati.  
  
## <a name="using-the-continueonerror-attribute"></a>Utilizzo dell'attributo ContinueOnError  
 Il `ContinueOnError` attributo il `Task` elemento controlla se una compilazione si interrompe o continua quando si verifica un errore in un'attività. Questo attributo controlla inoltre se gli errori vengono considerati come errori o avvisi durante la compilazione continua.  
  
 Il `ContinueOnError` attributo può contenere uno dei valori seguenti:  
  
-   **WarnAndContinue** o **true**. Quando un'attività non riesce, le successive attività di [destinazione](../msbuild/target-element-msbuild.md) elemento e la compilazione continua l'esecuzione, mentre tutti gli errori dall'attività vengono considerati come avvisi.  
  
-   **ErrorAndContinue**. Quando un'attività non riesce, le successive attività di `Target` elemento e la compilazione continua l'esecuzione, mentre tutti gli errori dall'attività vengono considerati come errori.  
  
-   **ErrorAndStop** o **false** (impostazione predefinita). Quando un'attività non riesce, le attività rimanenti di `Target` elemento e la compilazione non vengono eseguite e l'intero `Target` elemento e la compilazione è considerato non riuscito.  
  
 Versioni di .NET Framework precedenti alla 4.5 supportato solo il `true` e `false` valori.  
  
 Il valore predefinito di `ContinueOnError` è `ErrorAndStop`. Se si imposta l'attributo su `ErrorAndStop`, rendere esplicito il comportamento per chiunque legga il file di progetto.  
  
#### <a name="to-ignore-an-error-in-a-task"></a>Per ignorare un errore in un'attività  
  
-   Utilizzare il `ContinueOnError` attributo dell'attività. Ad esempio:  
  
     `<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>`  
  
## <a name="example"></a>Esempio  
 Esempio di codice riportato di seguito viene illustrato che il `Build` destinazione continui a essere eseguita e la compilazione viene considerata un esito positivo, anche se il `Delete` attività ha esito negativo.  
  
```  
<Project DefaultTargets="FakeBuild"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Files Include="*.obj"/>  
    </ItemGroup>  
    <Target Name="Clean">  
        <Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>  
    </Target>  
  
    <Target Name="FakeBuild" DependsOnTargets="Clean">  
        <Message Text="Building after cleaning..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche
[MSBuild](../msbuild/msbuild1.md)  
 [Riferimento di attività](../msbuild/msbuild-task-reference.md)   
 [Attività](../msbuild/msbuild-tasks.md)