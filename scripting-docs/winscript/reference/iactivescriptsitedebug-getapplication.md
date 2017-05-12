---
title: "IActiveScriptSiteDebug::GetApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetApplication"
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetApplication
Restituisce l'oggetto applicazione di debug associato al sito dello script.  
  
## Sintassi  
  
```  
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### Parametri  
 `ppda`  
 \[out\] puntatore all'applicazione di debug associato al sito dello script.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|L'host non supporta direttamente il debug.|  
  
## Note  
 Il metodo `GetApplication` consente di definire uno SmartHost l'oggetto applicazione a cui appartiene ogni script.  I moduli di gestione di script devono tentare di chiamare questo metodo per ottenere la propria applicazione e località di soggiorno contenitore a `IProcessDebugManager::GetDefaultApplication` se questa operazione non riesce.  
  
## Vedere anche  
 [Interfaccia IActiveScriptSiteDebug Interface](../../winscript/reference/iactivescriptsitedebug-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)