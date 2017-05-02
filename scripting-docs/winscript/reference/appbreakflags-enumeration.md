---
title: "Enumerazione APPBREAKFLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: APPBREAKFLAGS
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Costanti APPBREAKFLAGS"
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Enumerazione APPBREAKFLAGS
Scegliere lo stato corrente di debug delle applicazioni e i thread.  
  
## Sintassi  
  
```cpp  
enum enum_APPBREAKFLAGS  
{  
APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,  
APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,  
APPBREAKFLAG_STEP= 0x00010000,  
APPBREAKFLAG_NESTED= 0x00020000,  
APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,  
APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,  
APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,  
APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,  
APPBREAKFLAG_IN_BREAKPOINT= 0x80000000  
};  
  
```  
  
## Membri  
  
|Membro|Valore|Descrizione|  
|------------|------------|-----------------|  
|APPBREAKFLAG\_DEBUGGER\_BLOCK|0x00000001|Il motore di linguaggio deve arrestare immediatamente in tutti i thread con BREAKREASON\_DEBUGGER\_BLOCK.|  
|APPBREAKFLAG\_DEBUGGER\_HALT|0x00000002|Il motore di linguaggio deve arrestare immediatamente con BREAKREASON\_DEBUGGER\_HALT.|  
|APPBREAKFLAG\_STEP|0x00010000|Il motore di linguaggio deve arrestare immediatamente nel thread di esecuzione di istruzioni con BREAKREASON\_STEP.|  
|APPBREAKFLAG\_NESTED|0x00020000|L'applicazione è in esecuzione annidata in un punto di interruzione.|  
|APPBREAKFLAG\_STEPTYPE\_SOURCE|0x00000000|Il debugger è l'uscita a livello di origine.|  
|APPBREAKFLAG\_STEPTYPE\_BYTECODE|0x00100000|Il debugger è l'uscita a livello di codice di byte.|  
|APPBREAKFLAG\_STEPTYPE\_MACHINE|0x00200000|Il debugger è l'uscita a livello di computer.|  
|APPBREAKFLAG\_STEPTYPE\_MASK|0x00F00000|Maschera per scomporre i tipi di passaggio in fattori.|  
|APPBREAKFLAG\_IN\_BREAKPOINT|0x80000000|Un punto di interruzione è in corso.|  
  
## Note  
 I flag che specificano i motori di linguaggio devono interrompere la possibilità di seguito, mentre altri flag specificano la modalità l'esecuzione del debugger.  
  
## Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [Enumerazione BREAKREASON](../../winscript/reference/breakreason-enumeration.md)