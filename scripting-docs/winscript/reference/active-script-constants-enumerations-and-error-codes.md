---
title: "Costanti, enumerazioni e codici di errore dello script ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Costanti, enumerazioni e codici di errore dello script ActiveX
Questa sezione descrive le enumerazioni e i codici di errore utilizzati nei moduli di gestione di script windows.  
  
## Costanti  
  
|Costante|Descrizione|  
|--------------|-----------------|  
|[Costanti SCRIPTTHREADID](../../winscript/reference/scriptthreadid-constants.md)|Specifica il tipo di thread.|  
  
## Proprietà  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[Proprietà SCRIPTPROP\_HOSTKEEPALIVE](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Utilizzata per specificare se il motore di scripting deve essere mantenuto completamente funzionale se sono presenti riferimenti costanti.|  
  
## Enumerazioni  
  
|Enumerazione|Descrizione|  
|------------------|-----------------|  
|[Enumerazione SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md)|Il tipo di operazione da eseguire.|  
|[Enumerazione SCRIPTLANGUAGEVERSION](../../winscript/reference/scriptlanguageversion-enumeration.md)|Specifica le versioni possibili di script.|  
|[Enumerazione SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md)|Specifica lo stato di un motore di scripting.|  
|||  
|[Enumerazione SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md)|Specifica lo stato di un thread nel motore di scripting.|  
|[Enumerazione SCRIPTTRACEINFO](../../winscript/reference/scripttraceinfo-enumeration.md)|Rappresenta l'evento di script che sta analizzando.  Utilizzato in [Metodo IActiveScriptSiteTraceInfo::SendScriptTraceInfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[Enumerazione SCRIPTUICHANDLING](../../winscript/reference/scriptuichandling-enumeration.md)|Rappresenta il modo in cui il controllo dell'interfaccia utente deve essere gestito.|  
|[Enumerazione SCRIPTUICITEM](../../winscript/reference/scriptuicitem-enumeration.md)|Rappresenta il tipo di elemento dell'interfaccia utente.  Utilizzato in [Metodo IActiveScriptSiteUIControl::GetUIBehavior](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## Codici di errore  
  
|Codice di errore|Descrizione|  
|----------------------|-----------------|  
|[Codice di errore SCRIPT\_E\_PROPAGATE](../../winscript/reference/script-e-propagate-error-code.md)|Un errore di script sta propagando al chiamante, che potrebbe trovarsi in un altro thread.|  
|[Codice di errore SCRIPT\_E\_RECORDED](../../winscript/reference/script-e-recorded-error-code.md)|Un errore è stato passato tra il modulo di gestione di script e l'host.|  
|[Codice di errore SCRIPT\_E\_REPORTED](../../winscript/reference/script-e-reported-error-code.md)|Il motore di scripting ha generato un'eccezione non gestita all'host.|  
  
## Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)