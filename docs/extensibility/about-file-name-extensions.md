---
title: "Sulle estensioni di File | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "estensioni file"
  - "estensioni di file"
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Sulle estensioni di File
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

When you register a file extension of a VSPackage, you associate it with a version of [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Ciò è importante se più versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene installata in un computer.  
  
 Le estensioni di file per Vspackage vengono registrate nella chiave della chiave HKEY\_CLASSES\_ROOT con un valore predefinito che indica il ProgID associato \(ProgID\).  
  
 Di seguito viene riportato un esempio delle informazioni di registrazione per l'estensione vcproj:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 I file associati a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] devono avere un ProgID con versione, come `VisualStudio.vcproj.8.0`, per consentire alle installazioni contemporanee del prodotto di gestire le associazioni dell'estensione di file tra le diverse versioni del prodotto.  Un ProgID versione consente anche ai verbi standard di utilizzo, come aperto, modifica, e così via, senza la problematica di sovrascrivere o che viene sovrascritta da altre applicazioni o versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 In alcuni casi, il ProgID associato a un'estensione di file non deve essere modificato.  Ad esempio, il ProgID per l'estensione di file .htm \(progid \= htmlfile\) viene codificato complessa in una serie di punti del sistema operativo e ampiamente è noto e utilizzato in collaborazione con .htm e i file .html.  
  
## Vedere anche  
 [Registrazione di estensioni di File per le distribuzioni Side\-By\-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Specifica i gestori di File per le estensioni di File](../extensibility/specifying-file-handlers-for-file-name-extensions.md)