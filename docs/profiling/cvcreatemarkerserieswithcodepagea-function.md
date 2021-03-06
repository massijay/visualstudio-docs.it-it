---
title: Funzione CvCreateMarkerSeriesWithCodePageA | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords: CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc266ff4a96fa96f89e1eaafe2eaa8377ef601fa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>Funzione CvCreateMarkerSeriesWithCodePageA
Crea una serie di marcatori per un provider e una tabella codice specifici. Questa funzione può essere usata per specificare la tabella codici in modo esplicito per il testo scritto da funzioni ANSI dell'API dei marcatori. L'impostazione della tabella codici può risultare utile nel caso in cui la traccia venga acquisita e quindi analizzata in computer diversi con impostazioni locali/linguaggi diversi. Per impostazione predefinita viene usata la tabella codici restituita dalla funzione GetACP().  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pProvider`  
 Oggetto provider preinizializzato tramite CvInitProvider. Non può essere NULL.  
  
 `pSeriesName`  
 Nome della serie di marcatori. Non può essere NULL, ma le stringhe vuote sono consentite.  
  
 `nTextCodePage`  
 Tabella codici valida.  
  
 `ppMarkerSeries`  
 Indirizzo di una variabile di output in cui viene memorizzato il contesto della serie di marcatori. Non può essere NULL.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK quando la serie di marcatori viene creata correttamente oppure codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** cvmarkers.h  
  
## <a name="see-also"></a>Vedere anche  
 [C++ Library Reference](../profiling/cpp-library-reference.md) (Riferimento alla libreria C++)