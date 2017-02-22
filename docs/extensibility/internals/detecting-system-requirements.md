---
title: "Rilevamento dei requisiti di sistema | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installazione, VSPackage"
  - "le condizioni di avvio"
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 50
caps.handback.revision: 50
ms.author: "gregvanl"
manager: "ghogen"
---
# Rilevamento dei requisiti di sistema
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un VSPackage non funzionerà a meno che non è installato Visual Studio. Quando si utilizza Microsoft Windows Installer per gestire l'installazione del pacchetto di Visual Studio, è possibile configurare il programma di installazione per verificare se è installato Visual Studio. È inoltre possibile configurare per controllare il sistema per altri requisiti, ad esempio, una particolare versione di Windows o una determinata quantità di RAM.  
  
## Il rilevamento delle edizioni di Visual Studio  
 Per determinare se un'edizione di Visual Studio è installata, verificare che il valore della chiave del Registro di sistema di installare sia \(REG\_DWORD\) 1 nella cartella appropriata, come elencato nella tabella seguente. Si noti che esiste una gerarchia di edizioni di Visual Studio:  
  
1.  Enterprise  
  
2.  Professionale  
  
3.  Community  
  
 Quando si installa un'edizione "superiore", vengono aggiunte le chiavi del Registro di sistema per questa edizione anche per le edizioni "lower". Ovvero, se è installata la versione Enterprise edition, la chiave di installazione è impostata su 1 per Enterprise, nonché per le edizioni Professional e Community. Pertanto è necessario controllare solo per l'edizione "massimo", che è necessario.  
  
> [!NOTE]
>  Nella versione a 64 bit dell'editor del Registro di sistema, chiavi a 32 bit vengono visualizzate in HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\. Le chiavi di Visual Studio sono in HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\DevDiv\\vs\\Servicing\\.  
  
|Prodotto|Chiave|  
|--------------|------------|  
|Visual Studio Enterprise 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\enterprise|  
|Visual Studio Professional 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\professional|  
|Visual Studio Community 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\community|  
|Visual Studio 2015 Shell \(integrato e isolata\)|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell|  
  
## Rilevare quando viene eseguito Visual Studio  
 Se Visual Studio è in esecuzione quando viene installato il pacchetto Visual Studio, il pacchetto Visual Studio non è registrato correttamente. Il programma di installazione deve rilevare quando è in esecuzione Visual Studio e quindi rifiutare l'installazione del programma. Windows Installer non è possibile utilizzare le voci della tabella per abilitare il rilevamento di questo tipo. In alternativa, è necessario creare un'azione personalizzata, come indicato di seguito: utilizzare il `EnumProcesses` funzione rilevare devenv.exe exe e quindi impostare una proprietà di programma di installazione che viene utilizzata in una condizione di avvio o in modo condizionale consente di visualizzare una finestra di dialogo che chiede all'utente di chiudere Visual Studio.  
  
## Vedere anche  
 [L'installazione di VS con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)