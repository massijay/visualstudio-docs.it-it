---
title: "Funzione SccSetOption | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccSetOption"
helpviewer_keywords: 
  - "Funzione SccSetOption"
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzione SccSetOption
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La funzione imposta le opzioni che controllano il comportamento del plug\-in del controllo del codice sorgente.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### Parametri  
 pvContext  
 \[in\] La struttura di contesto plug\-in del controllo di origine.  
  
 nOption  
 \[in\] L'opzione da impostare.  
  
 dwVal  
 \[in\] Impostazioni per l'opzione.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|L'opzione è stata impostata.|  
|SCC\_I\_SHARESUBPROJOK|Restituito se `nOption` è stato `SCC_OPT_SHARESUBPROJ` e il plug\-in del controllo del codice sorgente consente l'IDE impostare la cartella di destinazione.|  
|SCC\_E\_OPNOTSUPPORTED|L'opzione non è stato impostato e non deve essere considerato affidabile.|  
  
## Note  
 L'IDE chiama questa funzione per controllare il comportamento del plug\-in del controllo del codice sorgente. Il primo parametro, `nOption`, indica il valore da impostare, mentre il secondo, `dwVal`, indica che cosa fare con tale valore. Il plug\-in archivia le informazioni associate un `pvContext``,` l'IDE è necessario chiamare questa funzione dopo la chiamata di [SccInitialize](../extensibility/sccinitialize-function.md) \(ma non necessariamente dopo ogni chiamata al [SccOpenProject](../extensibility/sccopenproject-function.md)\).  
  
 Riepilogo delle opzioni e i relativi valori:  
  
|`nOption`|`dwValue`|Descrizione|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Abilita\/Disabilita background Accodamento messaggi di evento.|  
|`SCC_OPT_USERDATA`|Valore arbitrario|Specifica un valore da passare all'utente il [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) funzione di callback.|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indica se l'IDE supporta attualmente l'annullamento di un'operazione.|  
|`SCC_OPT_NAMECHANGEPFN`|Puntatore al [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) funzione di callback|Imposta un puntatore a una funzione di callback modifica del nome.|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indica se l'IDE consente l'estrazione i file manualmente \(tramite interfaccia utente del controllo di origine\) o se è necessario estrarre solo tramite il plug\-in del controllo del codice sorgente.|  
|`SCC_OPT_SHARESUBPROJ`|N\/D|Se il plug\-in del controllo del codice sorgente consente l'IDE specificare la cartella di progetto locale, il plug\-in restituisce `SCC_I_SHARESUBPROJOK`.|  
  
## SCC\_OPT\_EVENTQUEUE  
 Se `nOption` è `SCC_OPT_EVENTQUEUE`, l'IDE è la disattivazione \(o la riabilitazione\) l'elaborazione in background. Ad esempio, durante una compilazione, l'IDE può indicare il plug\-in per arrestare l'elaborazione su inattivo di qualsiasi tipo di controllo del codice sorgente. Dopo la compilazione, abilitano nuovamente l'elaborazione in background per mantenere aggiornato coda eventi il plug\-in. Corrispondente per il `SCC_OPT_EVENTQUEUE` valore `nOption`, esistono due possibili valori per `dwVal`, vale a dire, `SCC_OPT_EQ_ENABLE` e `SCC_OPT_EQ_DISABLE`.  
  
## SCC\_OPT\_HASCANCELMODE  
 Se il valore per `nOption` è `SCC_OPT_HASCANCELMODE`, l'IDE consente agli utenti di annullare l'esecuzione di operazioni lunghe. L'impostazione `dwVal` per `SCC_OPT_HCM_NO` \(predefinito\) indica che l'IDE non possiede alcuna modalità di annullamento. Se desidera che l'utente sia in grado di annullare, il plug\-in del controllo del codice sorgente deve offrire un pulsante Annulla.`SCC_OPT_HCM_YES` indica che l'IDE fornisce la possibilità di annullare un'operazione, il plug\-in del controllo del codice sorgente è necessario visualizzare un pulsante Annulla. Se l'IDE imposta `dwVal` a `SCC_OPT_HCM_YES`, provvederà a rispondere a `SCC_MSG_STATUS` e `DOCANCEL` i messaggi inviati al `lpTextOutProc` funzione di callback \(vedere [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)\). Se l'IDE non impostare questa variabile, il plug\-in non devono inviare questi due messaggi.  
  
## SCC\_OPT\_NAMECHANGEPFN  
 Se nOption è impostato su `SCC_OPT_NAMECHANGEPFN`, sia l'origine e plug\-in controllo e l'IDE lo consentono, il plug\-in può effettivamente rinominare o spostare un file durante un'operazione di controllo di origine. Il `dwVal` verrà impostato su un puntatore a funzione di tipo [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Durante un'operazione di controllo di origine, il plug\-in può chiamare questa funzione, passando i tre parametri. Questi sono il nome esistente \(con il percorso completo\) di un file, il nuovo nome \(con il percorso completo\) del file e un puntatore alle informazioni che sono rilevante per l'IDE. Invia l'IDE in questo ultimo puntatore chiamando `SccSetOption` con `nOption` impostato su `SCC_OPT_USERDATA`, con `dwVal` che punta ai dati. Supporto per questa funzione è facoltativo. Un plug VSSCI\-che utilizza questa possibilità deve inizializzare le variabili di dati utente e puntatore funzione per `NULL`, e non deve chiamare una funzione rename a meno che non abbia ricevuto uno. Deve inoltre essere preparata per contenere il valore specificato o per modificarlo in risposta a una nuova chiamata a `SccSetOption`. Questa operazione non verrà eseguita all'interno di un'operazione di comando di controllo di origine, ma può avvenire tra i comandi.  
  
## SCC\_OPT\_SCCCHECKOUTONLY  
 Se nOption è impostato su `SCC_OPT_SCCCHECKOUTONLY`, l'IDE indica che i file nel progetto attualmente aperto non dovrebbero mai essere estratto manualmente tramite l'interfaccia utente del sistema di controllo di origine. Al contrario, i file devono essere estratti solo tramite il controllo del codice sorgente del plug\-nel controllo IDE. Se `dwValue` è impostato su `SCC_OPT_SCO_NO`, significa che i file devono essere trattati in genere per il plug\-in e possono essere estratto tramite il controllo del codice sorgente dell'interfaccia utente. Se `dwValue` è impostato su `SCC_OPT_SCO_YES`, quindi solo il plug\-in è possibile estrarre i file e dell'interfaccia utente del sistema di controllo di origine non deve essere richiamato. Ciò è utile nelle situazioni in cui l'IDE potrebbe essere "pseudo\-file" per estrarre solo tramite l'IDE ha senso.  
  
## SCC\_OPT\_SHARESUBPROJ  
 Se`nOption` è impostato su `SCC_OPT_SHARESUBPROJ`, l'IDE è verificare se il plug\-in del controllo del codice sorgente è possibile utilizzare una cartella locale specificata quando si aggiungono file dal controllo del codice sorgente. Il valore di `dwVal` parametro non è rilevante in questo caso. Se il plug\-in consente l'IDE specificare la cartella di destinazione locale dove verranno aggiunto i file di origine controllare quando il [SccAddFromScc](../extensibility/sccaddfromscc-function.md) viene chiamato, il plug\-in deve restituire `SCC_I_SHARESUBPROJOK` quando il `SccSetOption` viene chiamata la funzione. L'IDE utilizza quindi la `lplpFileNames` parametro il `SccAddFromScc` funzione passare nella cartella di destinazione. Il plug\-in utilizza la cartella di destinazione per inserire i file aggiunti dal controllo del codice sorgente. Se il plug\-in non restituisce `SCC_I_SHARESUBPROJOK` quando il `SCC_OPT_SHARESUBPROJ` opzione è impostata, l'IDE si presuppone che il plug\-in è in grado di aggiungere file solo nella cartella locale corrente.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)