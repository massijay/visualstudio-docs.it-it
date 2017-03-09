---
title: "Variante del formato di destinazione di rendering 16bpp | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Variante del formato di destinazione di rendering 16bpp
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Imposta il formato di pixel su DXGI\_FORMAT\_B5G6R5\_UNORM per tutte le destinazioni di rendering e i buffer nascosti.  
  
## Interpretazione  
 Una destinazione di rendering o un buffer nascosto usa in genere un formato a 32bpp \(32 bit per pixel\), come ad esempio B8G8R8A8\_UNORM.  I formati a 32bpp possono usare una larghezza di banda della memoria molto elevata.  Se si usa il formato B5G6R5\_UNORM, ovvero un formato a 16bpp che corrisponde alla metà delle dimensioni dei formati a 32bpp, è possibile alleggerire il carico sulla larghezza di banda della memoria, a fronte di una riduzione della fedeltà del colore.  
  
 Se questa variante mostra un miglioramento notevole delle prestazioni, ciò potrebbe indicare un consumo eccessivo della larghezza di banda della memoria.  I miglioramenti in termini di prestazioni possono risultare particolarmente significativi quando il fotogramma profilato presenta una quantità di caricamento significativa o una notevole fusione alfa.  
  
 Se il tipo di scene di cui l'app esegue il rendering non richiedono la riproduzione dei colori ad alta fedeltà, non richiedono che la destinazione di rendering disponga di un canale alfa e spesso non contengono sfumature che possono generare striature in caso di fedeltà dei colori ridotta, valutare l'uso di un formato di destinazione di rendering di 16bpp per ridurre l'utilizzo della larghezza di banda della memoria.  
  
 Se le scene di cui l'app esegue il rendering richiedono la riproduzione dei colori ad alta fedeltà o un canale alfa, se spesso contengono sfumature, è consigliabile valutare altre strategie per ridurre l'uso della larghezza di banda della memoria. È ad esempio possibile ridurre la quantità di caricamento o fusione alfa, ridurre le dimensioni del buffer di frame o modificare le risorse della trama affinché usino una quantità inferiore di larghezza di banda della memoria abilitando la compressione o riducendone le dimensioni.  Di norma, è necessario valutare i compromessi relativi alla qualità di immagine associati a ognuna di queste ottimizzazioni.  
  
 Se per l'app risulta vantaggioso passare a un buffer nascosto a 16bpp che però fa parte della catena di scambio, è necessario effettuare procedure aggiuntive perché il formato DXGI\_FORMAT\_B5G6R5\_UNORM non è un formato di buffer nascosto supportato per le catene di scambio create tramite `D3D11CreateDeviceAndSwapChain` o `IDXGIFactory::CreateSwapChain`.  In questo caso, è necessario creare una destinazione di rendering in formato B5G6R5\_UNORM usando `CreateTexture2D` ed eseguire il rendering in quel formato.  Successivamente, prima di chiamare Present sulla catena di scambio, copiare la destinazione di rendering nel buffer nascosto della catena di scambio disegnando una quaterna a schermo intero con la destinazione di rendering come trama di origine.  Sebbene si tratti di un passaggio aggiuntivo che richiede una certa quantità di larghezza di banda della memoria, la maggior parte delle operazioni di rendering userà una larghezza di banda inferiore, in quanto interessa la destinazione di rendering a 16bpp. Se questa operazione genera un risparmio di larghezza di banda superiore rispetto a quella usata dalla copia della destinazione di rendering nel buffer nascosto della catena di scambio, le prestazioni di rendering risultano migliorate.  
  
 Le architetture GPU che usano tecniche di rendering basate su riquadri registrano vantaggi significativi usando un formato di buffer di frame a 16bpp perché la cache del frame di buffer locale di ogni riquadro può ospitare una parte del buffer di frame più grande.  Le architetture di rendering basate su riquadri vengono spesso usate nelle GPU di telefoni cellulari e tablet; è raro trovarle in altri tipi di dispositivi.  
  
## Note  
 Il formato della destinazione di rendering viene reimpostato su DXGI\_FORMAT\_B5G6R5\_UNORM a ogni chiamata al metodo `ID3D11Device::CreateTexture2D` che crea una destinazione di rendering.  In particolare, il formato viene sovrascritto quando l'oggetto D3D11\_TEXTURE2D\_DESC passato a pDesc descrive una destinazione di rendering, ovvero:  
  
-   Il membro BindFlags presenta il flag D3D11\_BIND\_REDNER\_TARGET impostato.  
  
-   Il membro BindFlags presenta il flag D3D11\_BIND\_DEPTH\_STENCIL deselezionato.  
  
-   Il membro Usage è impostato su D3D11\_USAGE\_DEFAULT.  
  
## Limiti e restrizioni  
 Poiché il formato B5G6R5 non ha un canale alfa, il contenuto alfa non viene mantenuto da questa variante.  Se il rendering dell'app richiede un canale alfa nella destinazione di rendering, non è possibile passare semplicemente al formato B5G6R5.  
  
## Esempio  
 La variante del `formato di destinazione di rendering a 16bppCreateTexture2D può essere riprodotta per destinazioni di rendering create tramite  usando codice simile al seguente:`  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```