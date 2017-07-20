---
title: Autorizzazione del proxy richiesta | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 63aad78bdc7df685ca3a73ec16a9cbc87b78151f
ms.openlocfilehash: 537928b9ce99cbda9873500780719353d34fcbe1
ms.contentlocale: it-it
ms.lasthandoff: 07/14/2017

---
# <a name="proxy-authorization-required"></a>Autorizzazione del proxy richiesta
Generalmente questo errore si verifica quando gli utenti sono connessi a Visual Studio Online tramite un server proxy e il server proxy blocca le chiamate. Visual Studio Online viene usato per mantenere l'utente connesso all'IDE.  
  
## <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Riavviare Visual Studio. Verrà visualizzata una finestra di dialogo di autenticazione del proxy. Immettere le credenziali nella finestra di dialogo.  
  
-   Se il passaggio precedente non risolve il problema, è possibile che il server proxy usato richieda le credenziali per gli indirizzi http://go.microsoft.com, ma non per gli indirizzi *.visualStudio.com. Per questi server, è necessario aggiungere l'elenco seguente nell'elenco degli elementi consentiti per sbloccare tutti gli scenari di accesso in Visual Studio:  
  
    -   *.windows.net  
  
    -   *.microsoftonline.com  
  
    -   *.visualstudio.com  
  
    -   *.microsoft.com  
  
    -   *.live.com  
  
-   In caso contrario, è possibile rimuovere l'indirizzo http://go.microsoft.com dall'elenco degli elementi consentiti in modo che al riavvio di Visual Studio venga visualizzata la finestra di dialogo di autenticazione del proxy per l'indirizzo http://go.microsoft.com e gli endpoint server.  
  
-   OR  
  
-   Se si desidera usare le credenziali predefinite con il proxy, è possibile eseguire le operazioni seguenti:  
  
    1.  Trovare devenv.exe.config (file di configurazione devenv.exe) in: **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (o **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).  
  
    2.  Nel file di configurazione trovare il blocco `<system.net>` e aggiungere il codice seguente:  
  
        ```xml  
        <defaultProxy enabled="true" useDefaultCredentials="true">  
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>  
        </defaultProxy>  
  
        ```  
  
         È necessario inserire l'indirizzo del proxy corretto per la rete in `proxyaddress="<http://<yourproxy:port#>`.  
  
-   OR  
  
-   Si possono anche seguire le istruzioni in [questo post](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) per aggiungere il codice che consente di usare il proxy.
