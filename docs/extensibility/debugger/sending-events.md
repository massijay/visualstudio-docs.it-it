---
title: L&quot;invio di eventi | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: edd4abfa31b309290bdb07fd98c104a279d98fc7
ms.lasthandoff: 02/22/2017

---
# <a name="sending-events"></a>L'invio di eventi
Il meccanismo per la comunicazione tra il debugger e il motore di debug (DE) è un modello di evento basato su DCOM. Gli eventi vengono inviati come oggetti COM e ogni evento dispone di parametri che specificano le operazioni seguenti:  
  
-   DE che ha chiamato l'evento.  
  
-   Una descrizione di cosa è successo.  
  
-   Il processo, programma e informazioni sul thread che identifica il contesto di in cui si è verificato l'evento. Per gli eventi inviati da un DE non viene inviato il processo.  
  
-   Il tipo di evento che indica se l'evento è sincrono o asincrono.  
  
 Tutti gli eventi di debug vengono inviati utilizzando il metodo [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Origini eventi](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Vengono illustrati due origini di eventi: il motore di debug (DE) e la sessione di debug manager (SDM).  
  
 [Tipi di evento supportati](../../extensibility/debugger/supported-event-types.md)  
 Vengono descritti i tipi di eventi attualmente supportate: sincroni e asincroni.  
  
 [Descrizioni degli eventi](../../extensibility/debugger/event-descriptions.md)  
 Definisce gli eventi e i motivi per l'uso.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un motore di Debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Viene illustrato il funzionamento di un DE con sistema operativo o interprete per fornire servizi di debug.
