---
title: Eseguire la migrazione di registrazione della classe COM debugger a 64 bit | Documenti di Microsoft
ms.custom: 
ms.date: 11/10/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
caps.latest.revision: 1
author: gregg-miskelly
ms.author: greggm
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
ms.openlocfilehash: e273f31cb1f43ff79fd9a4ade37d112351dea9b5
ms.lasthandoff: 02/22/2017

---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Eseguire la migrazione a 64 bit debugger registrazione della classe COM

>**Nota:** questa documentazione è preliminare e in base alla versione di Visual Studio 2017 RC.

Per le estensioni del debugger registrare le classi COM in HKEY_CLASSES_ROOT (da utilizzare regasm, regsvr32, o direttamente la scrittura nel Registro di sistema) e caricati in msvsmon.exe (il debugger remoto), è ora possibile fornire la registrazione a msvsmon senza la necessità di scrivere in HKEY_CLASSES_ROOT. Ciò influisce sul analizzatori di espressioni del debugger .NET legacy o motori di debug che sono configurati per il caricamento nel processo di msvsmon.exe.

## <a name="msvsmon-comclass-def"></a>definizione di comclass msvsmon

Per utilizzare questa tecnica, aggiungere un file *.msvsmon-comclass-def.json accanto msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64).

Ecco un esempio di file di definizione di comclass msvsmon che registra uno gestito e una classe nativa:

Nome file: MyCompany.MyExample.msvsmon-comclass-def.json

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```

