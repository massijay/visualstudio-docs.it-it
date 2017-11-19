---
title: "Errore: La condivisione di file di Windows è stata configurata... | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.remote_credentials_prohibited
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: c45a1b74-61ec-4c64-9e2c-13051a4f50a5
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: afda40aea2340f85d27218b5a9cd7c4f09f64201
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Errore: la condivisione di file di Windows è stata configurata...
La condivisione di file di Windows è stata configurata in modo da connettersi al computer remoto utilizzando un nome utente diverso. Ciò è incompatibile con il debug remoto.  
  
 La condivisione di file è attualmente configurata per la connessione al computer remoto con un nome utente diverso. Il debug remoto non è possibile in uno scenario di questo tipo.  
  
 Per correggere l'errore, accedere al computer utilizzando un altro nome account oppure modificare la configurazione della condivisione di file in base al nome account utilizzato per il debug.  
  
 Prima di connettersi al computer remoto utilizzando questo nome utente, è necessario disconnettersi dal computer.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Accedere al computer locale, ossia il computer da cui viene eseguito il debug, utilizzando l'altro nome account.  
  
     -oppure-  
  
     . Disconnettersi dal computer remoto, quindi riconfigurare la condivisione file per connettersi a un altro computer con il proprio nome account:  
  
    1.  Nel **avviare** dal menu **Accessori**, quindi fare clic su **prompt dei comandi**.  
  
    2.  Al prompt dei comandi di Windows digitare:  
  
         `net use /delete computer_name`  
  
    3.  Modificare le impostazioni di condivisione file utilizzando uno dei metodi illustrati nella Guida di windows.