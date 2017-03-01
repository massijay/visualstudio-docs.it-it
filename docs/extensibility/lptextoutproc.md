---
title: LPTEXTOUTPROC | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7229d2681912663ad2cddcf95e140197495c0934
ms.lasthandoff: 02/22/2017

---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
Quando l'utente esegue un'operazione di controllo di origine all'interno dell'ambiente di sviluppo integrato (IDE), il controllo del codice sorgente del plug-in potrebbe essere necessario trasmettere i messaggi di errore o di stato relative all'operazione. Il plug-in possono visualizzate finestre di messaggio per questo scopo. Tuttavia, per una perfetta integrazione più, il plug-in può passare stringhe all'IDE, che li visualizza in modo nativo per la visualizzazione di informazioni sullo stato. Il meccanismo di questo è il `LPTEXTOUTPROC` puntatore a funzione. L'IDE implementa questa funzione (descritta in dettaglio più avanti) per la visualizzazione di errori e sullo stato.  
  
 L'IDE passa il controllo del codice sorgente del plug-in un puntatore a funzione a questa funzione, come il `lpTextOutProc` parametro, quando si chiama il [SccOpenProject](../extensibility/sccopenproject-function.md). Durante un'operazione di controllo del codice sorgente, ad esempio, all'interno di una chiamata al [SccGet](../extensibility/sccget-function.md) che coinvolgono molti file, può chiamare il plug-in di `LPTEXTOUTPROC` funzione periodicamente passando stringhe da visualizzare. L'IDE può visualizzare queste stringhe nella barra di stato, in una finestra di output o in una finestra separata, come appropriato. Facoltativamente, l'IDE potrebbe essere necessario visualizzare alcuni messaggi con un **Annulla** pulsante. Ciò consente all'utente di annullare l'operazione e consente l'IDE per passare queste informazioni per il plug-in.  
  
## <a name="signature"></a>Signature  
 L'IDE di output del funzione presenta la seguente firma:  
  
```cpp#  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>Parametri  
 display_string  
 Una stringa di testo da visualizzare. Questa stringa non deve essere terminata con un ritorno a capo restituito o un avanzamento riga.  
  
 mesg_type  
 Tipo di messaggio. Nella tabella seguente sono elencati i valori supportati per questo parametro.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|Il messaggio è considerato informazioni, avviso o errore.|  
|`SCC_MSG_STATUS`|Il messaggio Mostra lo stato e può essere visualizzato nella barra di stato.|  
|`SCC_MSG_DOCANCEL`|Con alcuna stringa di messaggio inviato.|  
|`SCC_MSG_STARTCANCEL`|Inizia la visualizzazione di un **Annulla** pulsante.|  
|`SCC_MSG_STOPCANCEL`|Non verrà più visualizzato una **Annulla** pulsante.|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Chiede IDE se l'operazione in background è possibile annullare: IDE restituisce `SCC_MSG_RTN_CANCEL` se l'operazione è stata annullata; in caso contrario, restituisce `SCC_MSG_RTN_OK`. Il `display_string` parametro viene eseguito il cast come un [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled) struttura, che viene fornito per il plug-in del controllo del codice sorgente.|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Indica all'IDE su un file prima che vengano recuperati dal controllo della versione. Il `display_string` parametro viene eseguito il cast come un [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile) struttura, che viene fornito per il plug-in del controllo del codice sorgente.|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Indica all'IDE su un file dopo che sono stati recuperati dal controllo della versione. Il `display_string` parametro viene eseguito il cast come un [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile) struttura, che viene fornito per il plug-in del controllo del codice sorgente.|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Indica all'IDE lo stato corrente di un'operazione in background. Il `display_string` parametro viene eseguito il cast come un [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage) struttura, che viene fornito per il plug-in del controllo del codice sorgente.|  
  
## <a name="return-value"></a>Valore restituito  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|La stringa è stata visualizzata o l'operazione è stata completata correttamente.|  
|SCC_MSG_RTN_CANCEL|L'utente desidera annullare l'operazione.|  
  
## <a name="example"></a>Esempio  
 Si supponga che le chiamate a IDE il [SccGet](../extensibility/sccget-function.md) con&20; nomi di file. Il plug-in del controllo del codice sorgente desidera impedire l'annullamento dell'operazione all'interno di un'operazione get file. Dopo l'acquisizione di ogni file, chiama il metodo `lpTextOutProc`, passando le informazioni sullo stato per ogni file e invia un `SCC_MSG_DOCANCEL` messaggio se nessuno stato al report. Se in qualsiasi momento il plug-in riceve un valore restituito di `SCC_MSG_RTN_CANCEL` dall'IDE, di annullare l'operazione get immediatamente, in modo che nessun altro file vengono recuperato.  
  
## <a name="structures"></a>Strutture  
  
###  <a name="a-namelinksccmsgdataiscancelleda-sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 Questa struttura viene inviata con il `SCC_MSG_BACKGROUND_IS_CANCELLED` messaggio. Utilizzato per comunicare l'ID dell'operazione in background che è stata annullata.  
  
###  <a name="a-namelinksccmsgdataonbeforegetfilea-sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 Questa struttura viene inviata con il `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` messaggio. Utilizzato per comunicare l'ID dell'operazione in background che esegue il recupero e il nome del file sta per essere recuperato.  
  
###  <a name="a-namelinksccmsgdataonaftergetfilea-sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile  
  
```cpp#  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 Questa struttura viene inviata con il `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` messaggio. Utilizzato per comunicare il risultato di recupero di file specificato, nonché l'ID dell'operazione in background che ha eseguito il recupero. Vedere i valori restituiti per il [SccGet](../extensibility/sccget-function.md) per ciò che è possibile assegnare di conseguenza.  
  
###  <a name="a-namelinksccmsgdataonmessagea-sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 Questa struttura viene inviata con il `SCC_MSG_BACKGROUND_ON_MESSAGE` messaggio. Utilizzato per comunicare lo stato corrente di un'operazione in background. Lo stato viene espresso sotto forma di stringa da visualizzare nell'IDE e `bIsError` indica la gravità del messaggio (`TRUE` per un messaggio di errore. `FALSE` per un avviso o per un messaggio informativo). L'ID dell'operazione in background inviare lo stato viene inoltre assegnato.  
  
## <a name="code-example"></a>Esempio di codice  
 Ecco un breve esempio di chiamata `LPTEXTOUTPROC` per inviare il `SCC_MSG_BACKGROUND_ON_MESSAGE` messaggio, che mostra come eseguire il cast della struttura per la chiamata.  
  
```cpp#  
LONG SendStatusMessage(  
    LPTEXTOUTPROC pTextOutProc,  
    DWORD         dwBackgroundID,  
    LPCTSTR       pStatusMsg,  
    BOOL          bIsError)  
{  
    SccMsgDataOnMessage msgData = { 0 };  
    LONG                result  = 0;  
  
    msgData.dwBackgroundOperationID = dwBackgroundID;  
    msgData.szMessage               = pStatusMsg;  
    msgData.bIsError                = bIsError;  
  
    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);  
    return result;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Plug-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)
