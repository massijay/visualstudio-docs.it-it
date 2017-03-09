---
title: "Attivit&#224; XSD | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.xsd"
  - "VC.Project.VCXMLDataGeneratorTool.Namespace"
  - "VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "XSD (attività MSBuild) (Visual C++)"
  - "MSBuild (Visual C++), XSD (attività)"
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Attivit&#224; XSD
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esegue il wrapping dello strumento XML Schema Definition (xsd.exe), che genera file di classe o dello schema da un'origine.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella seguente vengono descritti i parametri del **XSD** attività.  
  
-   **AdditionalOptions**  
  
     Facoltativo **stringa** parametro.  
  
     Un elenco di opzioni come specificato sulla riga di comando. Ad esempio, "*/option1 /option2 /opzione #*". Utilizzare questo parametro per specificare le opzioni che non sono rappresentate da qualsiasi altro **XSD** parametro dell'attività.  
  
-   **GenerateFromSchema**  
  
     Facoltativo **stringa** parametro.  
  
     Specifica i tipi generati dallo schema specificato.  
  
     Specificare uno dei seguenti valori, ognuno dei quali corrisponde a un'opzione di XSD.  
  
    -   **classi** - **/classi**  
  
    -   **set di dati** - **/dataset**  
  
-   **Lingua**  
  
     Facoltativo **stringa** parametro.  
  
     Specifica il linguaggio di programmazione da utilizzare per il codice generato.  
  
     Scegliere **CS** (c#, ovvero l'impostazione predefinita), **VB** (Visual Basic), o **JS** (JScript). È anche possibile specificare un nome completo per una classe che implementa `System.CodeDom.Compiler.CodeDomProvider Class`.  
  
-   **Spazio dei nomi**  
  
     Facoltativo **stringa** parametro.  
  
     Specifica lo spazio dei nomi del runtime per i tipi generati.  
  
-   **Origini**  
  
     Parametro `ITaskItem[]` obbligatorio.  
  
     Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.  
  
-   **SuppressStartupBanner**  
  
     Facoltativo **booleano** parametro.  
  
     Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.  
  
-   **TrackerLogDirectory**  
  
     Facoltativo **stringa** parametro.  
  
     Specifica la directory per il log di Tracker.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento di attività](../msbuild/msbuild-task-reference.md)