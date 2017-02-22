---
title: "ClickOnce Unmanaged API Reference | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "LaunchApplication [ClickOnce unmanaged]"
  - "ClickOnce, unmanaged APIs"
  - "CleanOnlineAppCache [ClickOnce unmanaged]"
  - "CleanOnlineAppCacheW interface [ClickOnce unmanaged]"
  - "GetDeploymentDataFromManifest [ClickOnce unmanaged]"
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce Unmanaged API Reference
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

API pubbliche non gestite [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] da dfshim.dll.  
  
## CleanOnlineAppCache  
 Pulisce o disinstalla tutte le applicazioni online dalla cache dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
### Valore restituito  
 Se eseguito correttamente restituisce S\_OK, in caso contrario restituisce un HRESULT che rappresenta l'errore.  Se si verifica un'eccezione gestita, restituisce 0x80020009 \(DISP\_E\_EXCEPTION\).  
  
### Note  
 La chiamata a CleanOnlineAppCache avvia il servizio [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se non è già in esecuzione.  
  
## GetDeploymentDataFromManifest  
 Recupera informazioni di distribuzione dall'URL di attivazione e del manifesto.  
  
### Parametri  
  
|Parametro|Descrizione|Type|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|Puntatore a `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Puntatore a `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Un puntatore a un buffer per ricevere una stringa a terminazione NULL che specifichi l'identità completa dell'applicazione restituita.|LPWSTR|  
|`pdwIdentityBufferLength`|Un puntatore ad un DWORD che costituisce la lunghezza del buffer `pwzApplicationIdentity`, in WCHAR.  Include lo spazio per il carattere di terminazione NULL.|LPDWORD|  
|`pwzProcessorArchitecture`|Un puntatore ad un buffer per ricevere una stringa a terminazione NULL che specifichi l'architettura del processore della distribuzione dell'applicazione, dal manifesto.|LPWSTR|  
|`pdwArchitectureBufferLength`|Un puntatore ad un DWORD che costituisce la lunghezza del buffer `pwzProcessorArchitecture`, in WCHAR.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Un puntatore ad un buffer per ricevere una stringa a terminazione NULL che specifichi la codebase del manifesto dell'applicazione, dal manifesto.|LPWSTR|  
|`pdwCodebaseBufferLength`|Un puntatore ad un DWORD che costituisce la lunghezza del buffer `pwzApplicationManifestCodebase`, in WCHAR.|LPDWORD|  
|`pwzDeploymentProvider`|Un puntatore ad un buffer per ricevere una stringa a terminazione NULL che specifichi il provider di distribuzione dal manifesto, se presente.  In caso contrario verrà restituita una stringa vuota.|LPWSTR|  
|`pdwProviderBufferLength`|Un puntatore ad un DWORD che costituisce la lunghezza di `pwzProviderBufferLength`.|LPDWORD|  
  
### Valore restituito  
 Se eseguito correttamente restituisce S\_OK, in caso contrario restituisce un HRESULT che rappresenta l'errore.  Restituisce HRESULTFROMWIN32 \(ERROR\_INSUFFICIENT\_BUFFER\) se un buffer è troppo piccolo.  
  
### Note  
 I puntatori non devono essere null.  `pcwzActivationUrl` e `pcwzPathToDeploymentManifest` non devono essere vuoti.  
  
 È responsabilità del chiamante pulire l'URL di attivazione,  ad esempio, aggiungendo caratteri di escape dove sono necessari o rimuovendo la stringa di query.  
  
 È responsabilità del chiamante limitare la lunghezza dell'input,  ad esempio, la lunghezza massima dell'URL è 2 KB.  
  
## LaunchApplication  
 Avvia o installa un'applicazione utilizzando un URL di distribuzione.  
  
### Parametri  
  
|Parametro|Descrizione|Type|  
|---------------|-----------------|----------|  
|`deploymentUrl`|Un puntatore a una stringa a terminazione NULL contenente l'URL del manifesto di distribuzione.|LPCWSTR|  
|`data`|Riservato per un utilizzo futuro.  Deve essere NULL.|LPVOID|  
|`flags`|Riservato per un utilizzo futuro.  Deve essere 0.|DWORD|  
  
### Valore restituito  
 Se eseguito correttamente restituisce S\_OK, in caso contrario restituisce un HRESULT che rappresenta l'errore.  Se si verifica un'eccezione gestita, restituisce 0x80020009 \(DISP\_E\_EXCEPTION\).  
  
## Vedere anche  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>