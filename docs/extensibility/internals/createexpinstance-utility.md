---
title: "Utilit&#224; CreateExpInstance | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "compilazioni sperimentale"
  - "hive sperimentale"
  - "istanza sperimentale"
  - "createexpinstance"
  - "createexpinst"
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Utilit&#224; CreateExpInstance
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilizzare l'utilità CreateExpInstance per creare, reimpostare, o eliminare un'istanza sperimentale di Visual Studio. È possibile utilizzare l'istanza sperimentale di debug e test di estensioni di Visual Studio senza modificare il prodotto sottostante.  
  
## Sintassi  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### Parametri  
 \/ Creare  
 Crea l'istanza sperimentale.  
  
 \/ Reset  
 Elimina l'istanza sperimentale e quindi viene creato uno nuovo.  
  
 \/Clean  
 Elimina l'istanza sperimentale.  
  
 \/ VSInstance  
 Il nome della directory che contiene l'istanza di Visual Studio base da copiare.  
  
 \/ \/Rootsuffix  
 Il suffisso da aggiungere al nome della directory istanza sperimentale.  
  
## Note  
 Quando si lavora in un'estensione di Visual Studio, è possibile premere F5 per aprire l'istanza sperimentale predefinita e installare l'estensione corrente. Se non è disponibile alcuna istanza sperimentale, Visual Studio crea una che include le impostazioni predefinite.  
  
 Il percorso predefinito dell'istanza sperimentale dipende dal numero di versione di Visual Studio. Ad esempio, per Visual Studio 2015, il percorso è %localappdata%\\Microsoft\\VisualStudio\\14.0Exp\\ tutti i file nel percorso della directory sono considerati parte dell'istanza. Qualsiasi istanza sperimentale aggiuntiva non verrà caricato da Visual Studio a meno che non viene modificato il nome della directory nel percorso predefinito.  
  
 Visual Studio non accede al Registro di sistema quando si apre l'istanza sperimentale. Questo comportamento è diverso da versioni precedenti di Visual Studio, che utilizzata una versione sperimentale dell'hive del Registro di sistema.  
  
 L'utilità CreateExpInstance sostituisce l'utilità VsRegEx.  
  
 Nell'esempio seguente Reimposta istanza sperimentale predefinito di Visual Studio.  
  
 **\/VSInstance CreateExpInstance.exe \/Reset \= 14.0 \/RootSuffix Exp \=**  
  
## Vedere anche  
 [Rilascio di un prodotto](../../misc/releasing-a-visual-studio-integration-product.md)