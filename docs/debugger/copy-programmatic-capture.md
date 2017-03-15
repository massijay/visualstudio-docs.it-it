---
title: "Copia (acquisizione a livello di codice) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Copia (acquisizione a livello di codice)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Copiare il contenuto del log degli elementi grafici \(.vsglog\) in un nuovo file.  
  
## Sintassi  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### Parametri  
 `szNewVSGLog`  
 Il nome del nuovo file di log degli elementi grafici.  
  
## Note  
 Per copiare le informazioni grafiche in un nuovo file, è necessario avere già acquisito alcune informazioni grafiche; in caso contrario, non viene eseguito nulla.