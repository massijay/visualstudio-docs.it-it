---
title: "Distribuzione di applicazioni Shell isolata | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Distribuzione di applicazioni Shell isolata
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È necessario installare Visual Studio e Visual Studio SDK per creare un'applicazione shell isolata. Per distribuire l'applicazione per le macchine di altri utenti o clienti, è necessario includere un pacchetto ridistribuibile speciale per la shell isolata.  
  
## Prerequisiti per la distribuzione di applicazioni Shell isolata  
  
|Nome|Descrizione|  
|----------|-----------------|  
|Visual Studio SDK|il SDK è necessario per sviluppare e testare le estensioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Inoltre, è possibile utilizzare il SDK per creare un'istanza personalizzata della shell di Visual Studio isolato.<br /><br /> Visual Studio è un prerequisito per il SDK.|  
|Microsoft Visual Studio isolato Shell Redistributable|Il pacchetto ridistribuibile di includere nel programma di installazione quando si compila un ambiente con strumenti di Visual Studio isolati shell. Il pacchetto ridistribuibile di Shell isolato include .NET Framework 4.5.|  
  
## Creazione di un programma di installazione per l'applicazione  
 È necessario creare un programma di installazione speciali per l'applicazione di shell integrata o isolato. Per altre informazioni, vedere [Installazione di un'applicazione Shell isolata](../extensibility/installing-an-isolated-shell-application.md).  
  
## Che consente gli aggiornamenti dell'applicazione  
 Il programma di installazione è necessario considerare la possibilità che l'applicazione verrà aggiornata per gli aggiornamenti di Microsoft o per gli aggiornamenti della società. Per ulteriori informazioni sugli aggiornamenti, vedere [Linee guida per la manutenzione per applicazioni Shell isolata](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).