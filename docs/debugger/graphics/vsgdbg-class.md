---
title: Classe VsgDbg | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0ee36596521f26ff4dd948e697640d0c82d796f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="vsgdbg-class"></a>Classe VsgDbg
Rappresenta un'interfaccia per il controllo a livello di codice del componente in-app di diagnostica della grafica.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
class VsgDbg;  
```  
  
## <a name="members"></a>Membri  
 La `VsgDbg` classe supporta i seguenti membri.  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (Costruttore)](vsgdbg-vsgdbg-constructor.md)|Costruisce un'istanza di `VsgDbg` classe e facoltativamente Prepara il componente in-app di diagnostica della grafica per acquisire e registrare le informazioni grafiche attivamente.|  
|[VsgDbg::~VsgDbg (distruttore)](vsgdbg-tilde-vsgdbg-destructor.md)|Elimina un'istanza di `VsgDbg` classe.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[AddMessage](addmessage.md)|Aggiunge un messaggio personalizzato alla diagnostica della grafica HUD (Head-Up Display).|  
|[BeginCapture](begincapture.md)|Inizia un intervallo di acquisizione che termina con `EndCapture`.|  
|[CaptureCurrentFrame](capturecurrentframe.md)|Acquisisce il resto del frame corrente nel file di log di grafica.|  
|[Copia (acquisizione a livello di codice)](copy-programmatic-capture.md)|Copiare il contenuto del log di grafica (.vsglog) attivo in un nuovo file.|  
|[EndCapture](endcapture.md)|Termina un intervallo di acquisizione avviato con `BeginCapture`.|  
|[Init](init.md)|Prepara il componente in-app di diagnostica della grafica per acquisire e registrare le informazioni grafiche attivamente.|  
|[ToggleHUD](togglehud.md)|Attiva o disattiva la sovrapposizione di diagnostica HUD grafica o disattivare.|  
|[UnInit](uninit.md)|Finalizza il file di log di grafica, lo chiude e libera le risorse utilizzate durante la registrazione attiva delle informazioni grafiche da parte dell'applicazione.|  
  
## <a name="remarks"></a>Note  
 La `VsgDbg` classe rappresenta un'interfaccia che consente di controllare a livello di programmazione di funzionalità di diagnostica grafica. È possibile utilizzare alcune funzionalità, anche quando si ha non attivamente acquisizione e la registrazione di informazioni grafiche; Ciò include la `AddMessage` funzione membro e `ToggleHUD` funzione membro. Le altre funzioni membro preparare il componente in-app di diagnostica della grafica per avviare o arrestare l'acquisizione di informazioni grafiche attivo oppure devono essere chiamate mentre l'app è attivamente acquisire e registrare le informazioni grafiche in un file di log di grafica.