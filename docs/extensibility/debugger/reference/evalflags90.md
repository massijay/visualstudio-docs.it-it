---
title: "EVALFLAGS90 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Enumerazione EVALFLAGS90"
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# EVALFLAGS90
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Enumera i valori validi per i flag che controllano la valutazione di espressioni.  questa enumerazione estende [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) l'enumerazione.  
  
## Sintassi  
  
```cpp#  
enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
typedef DWORD EVALFLAGS90;  
```  
  
```c#  
public enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
```  
  
#### Parametri  
 EVAL90\_RETURNVALUE  
 Specifica che il valore restituito, se presente, viene valutato.  
  
 EVAL90\_NOSIDEEFFECTS  
 Specifica gli effetti collaterali per non perché.  
  
 EVAL90\_ALLOWBPS  
 specifica arrestare sui punti di interruzione.  
  
 EVAL90\_ALLOWERRORREPORT  
 Specifica la segnalazione errori all'host perché le sia.  Principalmente utilizzato per la valutazione di espressioni in script in Internet Explorer.  
  
 EVAL90\_FUNCTION\_AS\_ADDRESS  
 Impone l'esecuzione per essere valutata come indirizzi, anziché chiamare la funzione.  
  
 EVAL90\_NOFUNCEVAL  
 Impedisce la funzione dalla valutazione.  Ad esempio, si consideri il token di `int` nell'espressione `myExpression(int) + 10`.  Questa funzione può essere correttamente valutata come indirizzo, ma non come valore.  
  
 EVAL90\_NOEVENTS  
 Flag per indicare che gli eventi che si verificano durante la valutazione di espressioni non devono essere inviati al gestore di debug della sessione \(SDM\) o all'IDE.  
  
 EVAL90\_DESIGN\_TIME\_EXPR\_EVAL  
 Effettuare la valutazione di espressioni in fase di progettazione.  
  
 EVAL90\_ALLOW\_IMPLICIT\_VARS  
 Consente la creazione variabile implicita.  
  
 EVAL90\_FORCE\_EVALUATION\_NOW  
 Forza la valutazione per verificare immediatamente.  Ciò si rivela utile quando a una richiesta, ad esempio una richiesta dell'utente.  
  
## Requisiti  
 intestazione: Msdbg90.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)