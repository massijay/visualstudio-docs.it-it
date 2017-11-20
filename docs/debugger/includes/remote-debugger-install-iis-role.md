---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 103cefa8573c8f44efff0b53b0c09a5ec26706e6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
Procedura mostra solo una configurazione di base di IIS. Per ulteriori informazioni o per installare in un computer Desktop Windows, vedere [la pubblicazione in IIS](https://docs.microsoft.com/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) o [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](https://docs.microsoft.com/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Per i sistemi operativi Windows Server, utilizzare il **Aggiungi ruoli e funzionalità** guidata tramite la **Gestisci** collegamento o **Dashboard** sul collegamento nella **diServerManager**. Nel passaggio **Ruoli del server** selezionare la casella per **Server Web (IIS)**.

![Il ruolo Server Web IIS viene selezionato nel passaggio dei ruoli del server Selezionare.](../media/remotedbg-server-roles-ws2012.png)

Nel passaggio **Servizi ruolo** selezionare i servizi ruolo IIS desiderato o accettare i servizi ruolo predefiniti forniti.

Procedere con la procedura di conferma per installare il ruolo server web e servizi. Un riavvio del server/IIS non è necessario dopo l'installazione del ruolo Server Web (IIS).