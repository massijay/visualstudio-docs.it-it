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
ms.openlocfilehash: 2d82fc0eb60b2680be9ed2bdb7de13313593da0d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
1. Se si prevede di distribuire le applicazioni con distribuzione Web in Visual Studio, installare la versione più recente di distribuzione Web nel server.

    Per installare distribuzione Web, utilizzare il [installazione guidata piattaforma Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx) o ottenere direttamente da un programma di installazione di [Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc). Trovare distribuzione Web nella scheda applicazioni. 

2. Verificare che la distribuzione Web è in esecuzione correttamente aprendo **Pannello di controllo > sistema e sicurezza > Strumenti di amministrazione > servizi** e verificare che **servizio agente distribuzione Web** è in esecuzione (la nome del servizio è diverso nelle versioni precedenti).

    Se il servizio dell'agente non è in esecuzione, avviarlo. Se non è presente in tutti, passare a **Pannello di controllo > programmi > Disinstalla un programma**, trovare **Microsoft Web Deploy <version>** . Scegliere di **modifica** l'installazione e assicurarsi di scegliere **verrà installata sul disco rigido locale** per i componenti di distribuzione Web. Completare i passaggi di installazione di modifica.