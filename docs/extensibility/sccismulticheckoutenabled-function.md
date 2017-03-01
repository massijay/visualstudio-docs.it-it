---
title: Funzione SccIsMultiCheckoutEnabled | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: 13
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
ms.openlocfilehash: 3d767767f3e2d8d3b67971dceda49c8309c549bb
ms.lasthandoff: 02/22/2017

---
# <a name="sccismulticheckoutenabled-function"></a>Funzione SccIsMultiCheckoutEnabled
Questa funzione controlla se il plug-in del controllo del codice sorgente consente più estrazioni su un file.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] La struttura di contesto plug-in del controllo di origine.  
  
 pbMultiCheckout  
 [out] Specifica se sono abilitate più estrazioni per questo progetto (diverso da zero indica che sono supportate più estrazioni).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Il controllo è riuscito.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specificato.|  
  
## <a name="remarks"></a>Note  
 L'IDE consente di eseguire due controlli per determinare se i file possono essere estratti contemporaneamente da più di un utente. In primo luogo, il controllo del codice sorgente deve supportare più estrazioni. Il plug-in del controllo del codice sorgente può specificare questa funzionalità durante l'inizializzazione di `SCC_CAP_MULTICHECKOUT`. Successivamente, come un secondo controllo, l'IDE chiama questa funzione per determinare se il progetto corrente supporta le estrazioni multiple. Se più estrazioni sono supportate per il progetto selezionato, i plug-in restituisce un esito positivo del codice e imposta `pbMultiCheckout` diverso da zero a (`TRUE`) o `FALSE`.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)
