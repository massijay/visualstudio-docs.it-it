---
title: "Procedura: Installare una versione specifica di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installare una versione specifica, Visual Studio"
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
caps.handback.revision: 11
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Procedura: Installare una versione specifica di Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il programma di installazione di Visual Studio viene aggiornato spesso in modo da offrire la versione più recente e ottimizzata delle funzionalità facoltative.  Tuttavia, se si vuole installare una versione precedente di Visual Studio 2015, ad esempio una versione di Visual Studio precedente a Update 1 con supporto per iOS, è necessario forzare il programma di installazione di Visual Studio in modo che usi una versione precedente dei file manifesto delle funzionalità. Questo articolo illustra la procedura specifica.  
  
## Installazione della versione corrente  
 Dopo la versione iniziale di Visual Studio 2015, il motore di installazione è stato aggiornato una volta e i file manifesto sono stati aggiornati più di cinque volte.  Se si vuole [scaricare ed eseguire oggi il programma di installazione di Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs) in un computer pulito e connesso a Internet, verrà installato Visual Studio 2015 Update 1, che include i miglioramenti più recenti per il prodotto e versioni più recenti delle funzionalità e degli strumenti facoltativi.  
  
## Installazione di versioni precedenti  
 È possibile creare e montare un'immagine ISO oppure scaricare e avviare direttamente il programma di installazione Web e quindi aggiungere al file EXE altri parametri della riga di comando, ad esempio \/CustomInstallPath, \/Full, \/InstallSelectableItems, \/NoRestart e così via per controllare il modo in cui viene installato Visual Studio.  
  
 La tabella seguente contiene alcuni scenari correlati a versioni precedenti specifiche e i parametri della riga di comando da passare al programma di installazione Web dell'edizione Enterprise. Gli stessi parametri possono essere usati anche con i programmi di installazione Web delle edizioni Community e Professional.  
  
|Edizione Visual Studio 2015|Versione da eseguire|Riga di comando da usare|Comportamento dell'installazione|  
|---------------------------------|--------------------------|------------------------------|--------------------------------------|  
|Visual Studio Enterprise \(versione pubblica più recente\)|Visual Studio Enterprise con Update 1 \(disponibile in [VisualStudio.com](https://www.visualstudio.com/en-us/products/vs-2015-product-editions.aspx)\)|`vs_enterprise.exe` **Note:**  Il comportamento predefinito dell'installazione offre le funzionalità facoltative più recenti e quindi non richiede alcun parametro della riga di comando.|L'installazione di Visual Studio userà il file feed.xml più recente e installerà i file più recenti.|  
|Visual Studio Enterprise \(RTM originale, ma con aggiornamenti precedenti a Update 1\)|Visual Studio Enterprise RTM \(disponibile nella [pagina di download per i titolari di abbonamenti MSDN](https://msdn.microsoft.com/en-us/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|L'installazione di Visual Studio userà il file feed.xml corrente prima del rilascio di Update 1.|  
|Visual Studio Enterprise Update 1 \(Update 1 originale senza aggiornamenti aggiuntivi relativi a Update 1\)|Visual Studio Enterprise con Update 1 \(disponibile nella [pagina di download per i titolari di abbonamenti MSDN](https://msdn.microsoft.com/en-us/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|L'installazione di Visual Studio userà il file feed.xml disponibile in corrispondenza dell'Update 1.|  
|Visual Studio Enterprise \(RTM originale, senza aggiornamenti\)|Visual Studio Enterprise RTM \(disponibile nella [pagina di download per i titolari di abbonamenti MSDN](https://msdn.microsoft.com/en-us/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|L'installazione di Visual Studio userà il file feed.xml disponibile con RTM.|  
  
> [!IMPORTANT]
>  In base alla lingua da usare, sostituire "enu" \(per inglese\) con uno dei valori seguenti:  
>   
>  -   chs \(per cinese \(semplificato\)\)  
> -   cht \(per cinese \(tradizionale\)\)  
> -   csy \(per ceco\)  
> -   deu \(per tedesco\)  
> -   esn \(per spagnolo\)  
> -   fra \(per francese\)  
> -   ita \(per italiano\)  
> -   jpa \(per giapponese\)  
> -   kor \(per coreano\)  
> -   plk \(per polacco\)  
> -   ptb \(per portoghese\)  
> -   rus \(per russo\)  
> -   trk \(per turco\)  
  
## Vedere anche  
 [Installazione di Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)