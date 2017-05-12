---
title: "IDebugExpressionContext::ParseLanguageText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionContext.ParseLanguageText
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpressionContext::ParseLanguageText"
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionContext::ParseLanguageText
Crea un'espressione di debug per il testo specificato.  
  
## Sintassi  
  
```  
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### Parametri  
 `pstrCode`  
 \[in\] fornisce il testo dell'espressione le istruzioni o.  
  
 `nRadix`  
 \[in\] base da utilizzare.  
  
 `pstrDelimiter`  
 \[in\] il delimitatore di entità finale\-de\-script\- blocco.  Quando `pstrCode` viene analizzato da un flusso di testo, l'host utilizza in genere un delimitatore, ad esempio due virgolette singole \('\), per individuare la fine del blocco di script.  Questo parametro specifica il delimitatore che l'host utilizzato, consentendo al motore di scripting fornire la pre\-elaborazione condizionale \(ad esempio, sostituendo una virgoletta \['\] con due virgolette semplici da utilizzare come delimitatore\).  Normalmente \(e\) se il motore di scripting utilizza queste informazioni dipendono dal motore di scripting.  Impostare questo parametro su `NULL` se l'host non utilizzi un delimitatore per contrassegnare la fine del blocco di script.  
  
 `dwFlags`  
 \[in\] la combinazione di testo riportato di debug diminuisce:  
  
|Costante|Valore|Descrizione|  
|--------------|------------|-----------------|  
|DEBUG\_TEXT\_ISEXPRESSION|0x00000001|Indica che il testo è un'espressione rispetto a un'istruzione.  Questo flag può influire sulla modalità in cui il testo è trattato in alcuni linguaggi.|  
|DEBUG\_TEXT\_RETURNVALUE|0x00000002|Se il valore restituito è disponibile, verrà utilizzato dal chiamante.|  
|DEBUG\_TEXT\_NOSIDEEFFECTS|0x00000004|Non consentire gli effetti collaterali.  Se questo flag è impostato, la valutazione di un'espressione non deve modificare lo stato di runtime.|  
|DEBUG\_TEXT\_ALLOWBREAKPOINTS|0x00000008|Consente i punti di interruzione durante la valutazione del testo.  Se questo flag quindi non è impostato i punti di interruzione vengono ignorati durante la valutazione del testo.|  
|DEBUG\_TEXT\_ALLOWERRORREPORT|0x00000010|Consente i report di errore durante la valutazione del testo.  Se questo flag quindi non è impostato errori non vengono segnalati all'host durante la valutazione.|  
|DEBUG\_TEXT\_EVALUATETOCODECONTEXT|0x00000020|Indica che deve essere valutata l'espressione in un contesto di codice anziché mediante l'espressione stessa|  
  
 `ppe`  
 \[out\] restituisce l'espressione di debug per il testo specificato.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo crea un'espressione di debug per il testo specificato.  
  
## Vedere anche  
 [Interfaccia IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)