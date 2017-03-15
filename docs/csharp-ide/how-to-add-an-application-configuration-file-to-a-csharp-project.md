---
title: "How to: Add an Application Configuration File to a C# Project | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "app.config files, adding to C# projects"
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# How to: Add an Application Configuration File to a C# Project
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aggiunta di un file di configurazione dell'applicazione \(file app.config\) a un progetto c, è possibile personalizzare il modo in cui Common Language Runtime individua e carica i file assembly.  Per ulteriori informazioni sui file di configurazione dell'applicazione, vedere [Come il runtime individua gli assembly](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md).  
  
> [!NOTE]
>  L'archivio di Windows non supporta <xref:System.Configuration>.  Di conseguenza, le applicazioni di archiviazione non contengono un modello di app.config.  
  
 Quando si compila il progetto, l'ambiente di sviluppo vengono copiati automaticamente nel file app.config, modificare il nome file della copia da corrispondere al file eseguibile quindi sposta la copia nella directory bin.  
  
### Per aggiungere un file di configurazione dell'applicazione al progetto C\#  
  
1.  Sulla barra dei menu, scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.  
  
2.  Espandere **Installato**, espandere **Elementi di Visual C**e quindi scegliere il modello **File di configurazione dell'applicazione** dell'applicazione.  
  
3.  Nella casella di testo **Nome** un nome, quindi scegliere il pulsante **Aggiungi**.  
  
     Un file denominato app.config verrà aggiunto al progetto.  
  
## Vedere anche  
 [Gestione delle impostazioni di un'applicazione \(.NET\)](../ide/managing-application-settings-dotnet.md)   
 [Schema dei file di configurazione](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)   
 [Configurazione di app](../Topic/Configuring%20Apps%20by%20using%20Configuration%20Files.md)   
 [How to: Configure an App to Target a .NET Framework Version](http://msdn.microsoft.com/it-it/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Using the Visual C\# Development Environment](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)