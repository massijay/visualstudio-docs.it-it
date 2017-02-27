---
title: "CV_CFL_LANG | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CV_CFL_LANG (enumerazione)"
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# CV_CFL_LANG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Specifica il linguaggio del codice sorgente dell'applicazione o del modulo collegato.  
  
## Sintassi  
  
```cpp#  
typedef enum CV_CFL_LANG {   
   CV_CFL_C       = 0x00,  
   CV_CFL_CXX     = 0x01,  
   CV_CFL_FORTRAN = 0x02,  
   CV_CFL_MASM    = 0x03,  
   CV_CFL_PASCAL  = 0x04,  
   CV_CFL_BASIC   = 0x05,  
   CV_CFL_COBOL   = 0x06,  
   CV_CFL_LINK    = 0x07,  
   CV_CFL_CVTRES  = 0x08,  
   CV_CFL_CVTPGD  = 0x09,  
   CV_CFL_CSHARP  = 0x0A,  
   CV_CFL_VB      = 0x0B,  
   CV_CFL_ILASM   = 0x0C,  
   CV_CFL_JAVA    = 0x0D,  
   CV_CFL_JSCRIPT = 0x0E,  
   CV_CFL_MSIL    = 0x0F,  
   CV_CFL_HLSL    = 0x10  
} CV_CFL_LANG;  
```  
  
## Elementi  
 CV\_CFL\_C  
 Il linguaggio di applicazione è C.  
  
 CV\_CFL\_CXX  
 Il linguaggio di applicazione è C\+\+.  
  
 CV\_CFL\_FORTRAN  
 Il linguaggio di applicazione è fortran.  
  
 CV\_CFL\_MASM  
 Il linguaggio di applicazione è Microsoft Macro Assembler.  
  
 CV\_CFL\_PASCAL  
 Il linguaggio di applicazione è Pascal.  
  
 CV\_CFL\_BASIC  
 Il linguaggio di applicazione è A BASE.  
  
 CV\_CFL\_COBOL  
 Il linguaggio di applicazione è COBOL.  
  
 CV\_CFL\_LINK  
 L'applicazione è un modulo di comando generato.  
  
 CV\_CFL\_CVTRES  
 L'applicazione è un modulo di risorse convertito mediante lo strumento di CVTRES.  
  
 CV\_CFL\_CVTPGD  
 L'applicazione è un modulo ottimizzato POGO generato dallo strumento di CVTPGD.  
  
 CV\_CFL\_CSHARP  
 Il linguaggio di applicazione è C\#.  
  
 CV\_CFL\_VB  
 Il linguaggio di applicazione è Visual Basic.  
  
 CV\_CFL\_ILASM  
 Il linguaggio dell'assembly Microsoft Intermediate Language \(ovvero assembly di Common Language Runtime \(CLR\)\).  
  
 CV\_CFL\_JAVA  
 Il linguaggio di applicazione è Java.  
  
 CV\_CFL\_JSCRIPT  
 Il linguaggio di applicazione è JScript.  
  
 CV\_CFL\_MSIL  
 Il linguaggio di applicazione è Microsoft Intermediate Language\) sconosciuta \(MSIL\), possibilmente un risultato di utilizzo dell'opzione di [\/LTCG \(Generazione di codice in fase di collegamento\)](/visual-cpp/build/reference/ltcg-link-time-code-generation) .  
  
 CV\_CFL\_HLSL  
 Il linguaggio di applicazione è linguaggio ad alto livello di shader.  
  
## Note  
 I valori in questa enumerazione restituiti da una chiamata al metodo di [IDiaSymbol::get\_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .  
  
## Requisiti  
 Intestazione: cvconst.h  
  
## Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)