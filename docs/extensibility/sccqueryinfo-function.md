---
title: Funzione SccQueryInfo | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: 18
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
ms.openlocfilehash: a178aada6303ed21f51a6be66ba02b2145dcd694
ms.lasthandoff: 02/22/2017

---
# <a name="sccqueryinfo-function"></a>Funzione SccQueryInfo
Questa funzione Ottiene informazioni sullo stato per un set di file selezionati nel controllo del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in del controllo di origine.  
  
 nFiles  
 [in] Numero di file specificato per il `lpFileNames` matrice e la lunghezza del `lpStatus` matrice.  
  
 lpFileNames  
 [in] Una matrice di nomi di file da recuperare.  
  
 lpStatus  
 [in, out] Matrice in cui il controllo del codice sorgente del plug-in restituisce i flag di stato per ogni file. Per ulteriori informazioni, vedere [codice di stato File](../extensibility/file-status-code-enumerator.md).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Query è stata completata.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema con accesso al sistema di controllo di origine, probabilmente causato da problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_PROJNOTOPEN|Il progetto non è aperto in controllo del codice sorgente.|  
|SCC_E_NONSPECIFICERROR|Errore non specificato.|  
  
## <a name="remarks"></a>Note  
 Se `lpFileName` è una stringa vuota, non sono attualmente disponibili informazioni di stato per aggiornare. In caso contrario, è il nome e percorso completo del file per cui le informazioni sullo stato sia stato modificato.  
  
 La matrice restituita può essere una maschera di bit di `SCC_STATUS_xxxx` bits. Per ulteriori informazioni, vedere [codice di stato File](../extensibility/file-status-code-enumerator.md). Un sistema di controllo potrebbe non supportare tutti i tipi di bit. Ad esempio, se `SCC_STATUS_OUTOFDATE` non è disponibile, ma non viene impostato il bit.  
  
 Quando si utilizza questa funzione per estrarre i file, tenere presente quanto segue `MSSCCI` requisiti di stato:  
  
-   `SCC_STATUS_OUTBYUSER`viene impostata quando l'utente corrente ha estratto il file.  
  
-   `SCC_STATUS_CHECKEDOUT`può essere impostata solo se `SCC_STATUS_OUTBYUSER` è impostata.  
  
-   `SCC_STATUS_CHECKEDOUT`viene impostata solo quando il file è stato estratto nella directory di lavoro designato.  
  
-   Se il file è stato estratto dall'utente corrente in una directory diversa dalla directory di lavoro, `SCC_STATUS_OUTBYUSER` è impostata ma `SCC_STATUS_CHECKEDOUT` non.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [Codice di stato file](../extensibility/file-status-code-enumerator.md)