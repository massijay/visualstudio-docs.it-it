---
title: Funzione SccGetCommandOptions | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
caps.latest.revision: 14
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
ms.openlocfilehash: 86f8b896581d4238e1328bd0fe086987145c9fb5
ms.lasthandoff: 02/22/2017

---
# <a name="sccgetcommandoptions-function"></a>Funzione SccGetCommandOptions
Questa funzione richiede all'utente per le opzioni avanzate per un determinato comando.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccGetCommandOptions(  
   LPVOID pvContext,  
   HWND hWnd,  
   enum SCCCOMMAND iCommand,  
   LPCMDOPTS* ppvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in del controllo di origine.  
  
 hWnd  
 [in] Handle di finestra IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 iCommand  
 [in] Il comando per il quale vengono richieste le opzioni avanzate (vedere [comando codice](../extensibility/command-code-enumerator.md) per i valori possibili).  
  
 ppvOptions  
 [in] La struttura di opzione (può anche essere `NULL`).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Operazione completata.|  
|SCC_I_ADV_SUPPORT|Il controllo del codice sorgente del plug-in supporta le opzioni avanzate per il comando.|  
|SCC_I_OPERATIONCANCELED|L'utente ha annullato l'origine controllo del plug-in **opzioni** la finestra di dialogo.|  
|SCC_E_OPTNOTSUPPORTED|Il plug-in del controllo del codice sorgente non supporta questa operazione.|  
|SCC_E_ISCHECKEDOUT|Impossibile eseguire questa operazione in un file che è attualmente estratto.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NONSPECIFICERROR|Errore non specificato.|  
  
## <a name="remarks"></a>Note  
 Questa funzione viene chiamata l'IDE per la prima volta con `ppvOptions` = `NULL` per determinare se il controllo del codice sorgente del plug-in supporta la funzionalità delle opzioni avanzate per il comando specificato. Se il plug-in supporta la funzionalità per il comando, l'IDE di questa funzione viene chiamata nuovamente quando l'utente richiede le opzioni avanzate (in genere implementato come un **avanzate** pulsante in una finestra di dialogo) e fornisce un puntatore non NULL per `ppvOptions` che punta a un `NULL` puntatore. Il plug-in vengono archiviate tutte le opzioni avanzate specificate dall'utente in una struttura private e restituisce un puntatore alla struttura in `ppvOptions`. Questa struttura viene quindi passata a tutte le altre funzioni API plug-in controllo di origine che occorre conoscere, tra cui le chiamate successive al `SccGetCommandOptions` (funzione).  
  
 Un esempio può aiutare a chiarire questa situazione.  
  
 Un utente sceglie il **ottenere** comando e l'IDE visualizza un **ottenere** la finestra di dialogo. Le chiamate IDE il `SccGetCommandOptions` funzione `iCommand` impostato su `SCC_COMMAND_GET` e `ppvOptions` impostato su `NULL`. Questo numero viene interpretato dal plug-in come il punto di controllo del codice sorgente, "Hai le opzioni avanzate per questo comando?" Se il plug-in restituisce `SCC_I_ADV_SUPPORT`, l'IDE visualizza un **avanzate** pulsante relativo **ottenere** la finestra di dialogo.  
  
 La prima volta che l'utente fa clic il **avanzate** pulsante, l'IDE chiama nuovamente la `SccGetCommandOptions` funzione, questa volta con un`NULL``ppvOptions` che punta a un `NULL` puntatore. I plug-in consente di visualizzare il proprio **opzioni Leggi** nella finestra di dialogo richiede all'utente informazioni aggiuntive, inserire tali informazioni nella propria struttura e restituisce un puntatore a tale struttura in `ppvOptions`.  
  
 Se l'utente fa clic **avanzate** nuovamente nella stessa finestra di dialogo, l'IDE chiama il `SccGetCommandOptions` funzione nuovamente senza modificare `ppvOptions`, in modo che la struttura viene passata per il plug-in. In questo modo il plug-in reinizializzare la finestra di dialogo per i valori che l'utente ha impostato in precedenza. Il plug-in modifica la struttura sul posto prima della restituzione.  
  
 Infine, quando l'utente fa clic **OK** dell'IDE **ottenere** la finestra di dialogo, le chiamate a IDE il [SccGet](../extensibility/sccget-function.md), passando la struttura restituita in `ppvOptions` che contiene le opzioni avanzate.  
  
> [!NOTE]
>  Il comando `SCC_COMMAND_OPTIONS` viene utilizzato quando l'IDE visualizza un **opzioni** la finestra di dialogo che consente all'utente di imposta le preferenze che controllano il funzionamento dell'integrazione. Se il controllo del codice sorgente del plug-in fornire una finestra di dialogo Preferenze, può visualizzare da un **avanzate** pulsante nella finestra di dialogo Preferenze dell'IDE. Il plug-in è esclusivamente responsabile per il recupero e il mantenimento di queste informazioni. l'IDE non utilizzarlo o modificarlo.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [Codice di comando](../extensibility/command-code-enumerator.md)
