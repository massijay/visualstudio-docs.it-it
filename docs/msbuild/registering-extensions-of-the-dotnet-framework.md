---
title: "Registrazione di estensioni di .NET Framework | Microsoft Docs"
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
  - "Aggiungi riferimenti (finestra di dialogo), registrazione di estensioni di .NET Framework"
  - "MSBuild, registrazione di estensioni in .NET Framework"
  - ".NET Framework (estensioni), registrazione"
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Registrazione di estensioni di .NET Framework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile sviluppare un assembly che estende una versione specifica di .NET Framework.  Per consentire all'assembly di venire visualizzato nella finestra di dialogo **Aggiungi riferimenti** di Visual Studio, è necessario aggiungere la cartella che lo contiene al Registro di sistema.  
  
 Ad esempio, si supponga che la società Trey Research abbia sviluppato una libreria che estende .NET Framework 4 e desidera che gli assembly della libreria vengano visualizzati nella finestra di dialogo **Aggiungi riferimenti** quando un progetto è destinato a .NET Framework 4.  Si supponga inoltre che si tratti di assembly a 32 bit che vengono eseguiti su un computer a 32 bit o assembly a 64 bit che vengono eseguiti su un computer di 64 bit e che saranno installati nella cartella C:\\TreyResearch\\Extensions4\\.  
  
 Registrare la cartella utilizzando questa chiave: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\v4.0.21006\\AssemblyFoldersEx\\TreyResearch\\.  Assegnare alla chiave questo valore predefinito: C:\\TreyResearch\\Extensions4.  
  
> [!NOTE]
>  È possibile che il numero di build della versione di .NET Framework sia diverso.  
  
 Per registrare un assembly a 32 bit su un computer a 64 bit, utilizzare il nodo Wow6432, ad esempio: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\v4.0.21006\\AssemblyFoldersEx\\TreyResearch\\.  
  
## Vedere anche  
 [Integrazione con Visual Studio](../msbuild/visual-studio-integration-msbuild.md)