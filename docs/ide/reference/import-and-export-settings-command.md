---
title: "Comando Importa/Esporta impostazioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Tools.ImportandExportSettings"
helpviewer_keywords: 
  - "Tools.ImportandExportSettings"
  - "Importa/Esporta impostazioni (comando)"
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# Comando Importa/Esporta impostazioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Importa, esporta o ripristina le impostazioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Sintassi  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## Opzioni  
 \/export:`filename`  
 Parametro facoltativo.  Esporta le impostazioni correnti nel file specificato.  
  
 \/import:`filename`  
 Parametro facoltativo.  Importa le impostazioni nel file specificato.  
  
 \/reset  
 Parametro facoltativo.  Reimposta le impostazioni correnti.  
  
## Note  
 Se questo comando viene eseguito senza le opzioni, apre la **Importazione\/Esportazione guidata delle impostazioni**.  Per ulteriori informazioni, vedere [How to: Share Settings Between Computers or Visual Studio Versions](http://msdn.microsoft.com/it-it/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## Esempio  
 Il seguente comando consente di esportare le impostazioni correnti nel file `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## Vedere anche  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)