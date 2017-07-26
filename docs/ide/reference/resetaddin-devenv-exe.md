---
title: -ResetAddin (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 826740ff2c56f50426d51e91fe9ccf8cdcb99081
ms.contentlocale: it-it
ms.lasthandoff: 05/24/2017

---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
Rimuove i comandi e l'interfaccia utente dei comandi associata al componente aggiuntivo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Argomenti  
 `AddIn`  
 Parametro facoltativo. Nome del comando del componente aggiuntivo.  
  
## <a name="remarks"></a>Note  
 Per impostazione predefinita, il nome del comando del componente aggiuntivo è uguale a *\<NomeSoluzioneComponenteAggiuntivo>*.Connect*.\<NomeSoluzioneComponenteAggiuntivo>* e viene visualizzato in Connect.cs come parametro `commandName` del metodo `Exec`. È anche possibile verificare il nome del comando digitando l'inizio del nome del componente aggiuntivo nella finestra dei comandi in Visual Studio e usando Intellisense per completarlo.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente avvia Visual Studio e impedisce l'esecuzione all'avvio del componente aggiuntivo `MyAddin`.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
