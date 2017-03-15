---
title: Funzione SccGetProjPath | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: 15
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
ms.openlocfilehash: 551fe26fe20da62d6892a8c7e807cf6c22600fc8
ms.lasthandoff: 02/22/2017

---
# <a name="sccgetprojpath-function"></a>Funzione SccGetProjPath
Questa funzione richiede all'utente per un percorso di progetto, è una stringa che è significativa solo per il plug-in del controllo del codice sorgente. Viene chiamato quando l'utente è:  
  
-   Crea un nuovo progetto  
  
-   Aggiunta di un progetto esistente al controllo della versione  
  
-   Tentativo di trovare un progetto di controllo di versione esistente  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccGetProjPath (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPSTR  lpProjName,  
   LPSTR  lpLocalPath,  
   LPSTR  lpAuxProjPath,  
   BOOL   bAllowChangePath,  
   LPBOOL pbNew  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in del controllo di origine.  
  
 hWnd  
 [in] Handle di finestra IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 lpUser  
 [in, out] Il nome utente (che non devono superare SCC_USER_SIZE, compreso il terminatore NULL)  
  
 lpProjName  
 [in, out] Il nome del progetto IDE, area di lavoro progetto o makefile (che non devono superare SCC_PRJPATH_SIZE, compreso il terminatore NULL).  
  
 lpLocalPath  
 [in, out] Percorso di lavoro del progetto. Se `bAllowChangePath` è `TRUE`, il plug-in del controllo del codice sorgente è possibile modificare questa stringa (che non devono superare MAX_PATH, compreso il terminatore null).  
  
 lpAuxProjPath  
 [in, out] Un buffer per il percorso del progetto restituiti (che non devono superare SCC_PRJPATH_SIZE, compreso il terminatore NULL).  
  
 bAllowChangePath  
 [in] Se si tratta di `TRUE`, il plug-in del controllo del codice sorgente è possibile richiedere e modificare il `lpLocalPath` stringa.  
  
 pbNew  
 [in, out] Valore in entrata indica se creare un nuovo progetto. Valore restituito indica l'esito positivo della creazione di un progetto:  
  
|In ingresso|Interpretazione|  
|--------------|--------------------|  
|TRUE|L'utente può creare un nuovo progetto.|  
|FALSE|L'utente non può creare un nuovo progetto.|  
  
|In uscita|Interpretazione|  
|--------------|--------------------|  
|TRUE|È stato creato un nuovo progetto.|  
|FALSE|È stato selezionato un progetto esistente.|  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Il progetto è stata correttamente creato o recuperato.|  
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete.|  
|SCC_E_CONNECTIONFAILURE|Si è verificato un problema durante la connessione al sistema di controllo di origine.|  
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato.|  
  
## <a name="remarks"></a>Note  
 Lo scopo di questa funzione è per l'IDE di acquisire i parametri `lpProjName` e `lpAuxProjPath`. Dopo che il plug-in del controllo del codice sorgente richiede all'utente di questa informazione, passa questi due stringhe tornare all'IDE. L'IDE mantiene queste stringhe nel file di soluzione e li passa a di [SccOpenProject](../extensibility/sccopenproject-function.md) ogni volta che l'utente apre il progetto. Queste stringhe di abilitare il plug-in tenere traccia delle informazioni associate a un progetto.  
  
 Quando viene chiamata la funzione, `lpAuxProjPath` è impostato su una stringa vuota. `lProjName`può anche essere vuota o contenere il nome del progetto IDE, che può utilizzare o ignorare il controllo del codice sorgente del plug-in. Quando la funzione restituisce correttamente, il plug-in restituisce le due stringhe corrispondenti. L'IDE non fa alcuna ipotesi su queste stringhe, non verrà utilizzati e non consente all'utente di modificarli. Se l'utente desidera modificare le impostazioni, l'IDE chiamerà `SccGetProjPath` nuovamente, passando gli stessi valori ha ricevuto l'ora precedente. In questo modo il plug-in controllo completo su questi due stringhe.  
  
 Per `lpUser`, l'IDE può passare un nome utente o semplicemente possibile passare un puntatore a una stringa vuota. Se è presente un nome utente, il plug-in del controllo del codice sorgente necessario utilizzarlo come valore predefinito. Tuttavia, se è stato passato alcun nome o l'account di accesso non riuscito con il nome specificato, il plug-in deve richiedere all'utente per un account di accesso e passa il nome del nuovo `lpUser` quando riceve un account di accesso valido. Perché il plug-in possono modificare questa stringa, l'IDE verrà sempre allocare un buffer di dimensione (`SCC_USER_LEN`+&1;).  
  
> [!NOTE]
>  La prima azione che esegue l'IDE può essere una chiamata al metodo di `SccOpenProject` funzione o `SccGetProjPath` (funzione). Di conseguenza, essi dispongono di identica `lpUser` parametro, che consente il plug-in per effettuare l'accesso in fase di controllo del codice sorgente. Anche se il valore restituito dalla funzione indica un errore, il plug-in deve riempire questa stringa con un nome di account di accesso valido.  
  
 `lpLocalPath`è la directory in cui l'utente mantiene il progetto. Può trattarsi di una stringa vuota. Se è presente alcuna directory attualmente definiti (come nel caso di un utente che tenta di scaricare un progetto dal sistema di controllo di origine) e se `bAllowChangePath` è `TRUE`, il plug-in del controllo del codice sorgente può richiedere l'input dell'utente o utilizzare un altro metodo per inserire una stringa in `lpLocalPath`. Se `bAllowChangePath` è `FALSE`, il plug-in necessario non modificare la stringa, perché l'utente sta già lavorando nella directory specificata.  
  
 Se l'utente crea un nuovo progetto di controllo del codice sorgente, il plug-in del controllo del codice sorgente potrebbe non effettivamente crearlo nel sistema di controllo di origine al momento `SccGetProjPath` viene chiamato. Al contrario, passa nuovamente la stringa con un valore diverso da zero per `pbNew`, che indica che il progetto verrà creato nel sistema di controllo di origine.  
  
 Ad esempio, se un utente di **nuovo progetto** procedura guidata in Visual Studio aggiunge il proprio progetto al controllo del codice sorgente, Visual Studio chiama questa funzione e il plug-in determina se è possibile creare un nuovo progetto nel sistema di controllo di origine contenga il progetto di Visual Studio. Se l'utente fa clic **Annulla** prima di completare la procedura guidata, il progetto non viene mai creato. Se l'utente fa clic **OK**, Visual Studio chiama `SccOpenProject`, passando `SCC_OPT_CREATEIFNEW`, e viene creato il progetto di controllo del codice sorgente in quel momento.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
