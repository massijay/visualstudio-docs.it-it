---
title: "DA0030: Raccogli misurazioni di interazione tra livelli per i progetti di database | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0030"
  - "vs.performance.rules.DA0030"
  - "vs.performance.30"
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0030: Raccogli misurazioni di interazione tra livelli per i progetti di database
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0030|  
|Category|Utilizzo di strumenti di profilatura|  
|Metodo di profilatura|Campionamento|  
|Messaggio|La raccolta di misurazioni per le applicazioni multilivello consente di comprendere i criteri di utilizzo del database e i ritardi di accesso ai dati di chiave.  Abilitare l'opzione Profilo interazione tra livelli e provare a eseguire di nuovo la profilatura dell'applicazione.|  
|Tipo regola|Informazioni|  
  
## Causa  
 Le chiamate ai metodi <xref:System.Data> costituiscono una percentuale significativa dei dati di profilatura e non sono stati raccolti dati di interazione tra livelli nell'esecuzione della profilatura.  Considerare la possibilità di ripetere la profilatura e di aggiungere dati di interazione tra livelli.  
  
## Descrizione della regola  
 Questa regola viene attivata ogni volta che viene rilevata un'attività significativa in funzioni che risiedono negli spazi dei nomi System.Data, ad esempio <xref:System.Data.Linq> <xref:System.Data.Linq>.  
  
 Le applicazioni multilivello utilizzano servizi sovrapposti per i livelli presentazione e dati.  Spesso il livello dati è un processo separato che esegue un sistema di gestione di database quale Microsoft SQL Server.  Il livello dati potrebbe anche essere eseguito su un computer separato dal resto dell'applicazione.  I profili di campionamento forniscono una quantità limitata di informazioni su funzioni e servizi eseguiti out\-of\-process o in modalità remota.  
  
 Gli strumenti di profilatura possono raccogliere informazioni sugli intervalli per applicazioni multilivello che interagiscono con il livello dati di Microsoft SQL Server utilizzando chiamate asincrone ai servizi ADO.NET.  È necessario abilitare in modo esplicito la profilatura dell'interazione tra livelli.  Non è attivata per impostazione predefinita.  
  
## Come correggere le violazioni  
 Questa regola è solo a scopo informativo e potrebbe non richiedere azione correttiva.  
  
 Per informazioni su come aggiungere dati di interazione tra livelli ai dati di profilo dall'IDE di Visual Studio, consultare [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md) .  Per informazioni sull'aggiunta di dati di interazione tra livelli dalla riga di comando, vedere [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md).