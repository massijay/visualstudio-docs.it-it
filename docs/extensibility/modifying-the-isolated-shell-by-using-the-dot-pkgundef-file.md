---
title: Modifica la Shell isolata utilizzando il. File Pkgundef | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 11
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: b49f3c5a39e82e0385aab12ef7042a6845b12664
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modifica la Shell isolata utilizzando il. File Pkgundef
È possibile modificare il file .pkgundef per escludere le voci del Registro di sistema specificato da un'applicazione shell isolata. In genere, al primo avvio di un'applicazione in un computer, la shell di Visual Studio copia le voci del Registro di sistema di Visual Studio esistenti per la chiave del Registro di sistema radice per l'applicazione. Sono inclusi tutti i riferimenti ai package VS attualmente installato.  
  
 Per escludere una voce del Registro di sistema da un'applicazione shell isolata, aggiungere la chiave del pacchetto aggiungendo la voce nel file di .pkgundef applicazione. Le chiavi e le voci sono rappresentate come file. pkgdef. vale a dire come [$$RootKey] o [$ $RootKey\\*sottochiave*] e "*voce*" =*valore*, dove *sottochiave* è la sottochiave da assegnare, *voce* è la voce da rimuovere, e *valore* è `""` o `dword:00000000`.  
  
 Per escludere più voci da una chiave del Registro di sistema, semplicemente elencare la chiave di una sola volta, seguito da una riga per ogni voce da escludere.  
  
 Per escludere una chiave del Registro di sistema tutto da un'applicazione shell isolata, aggiungere la chiave nel file .pkgundef applicazione ma non si specifica qualsiasi voce del Registro di sistema per la chiave.  
  
 È possibile aggiungere commenti al file .pkgundef. Un commento a riga singola deve avere due barre i primi due caratteri.  
  
 Ad esempio, per rimuovere il **Connetti al Database** e **Connetti al server r** comandi il **strumenti** menu, è possibile rimuovere il commento:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 e aggiungere la riga:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 file .pkgundef dell'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [GUID del pacchetto di funzionalità di Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Personalizzazione Shell isolata](../extensibility/customizing-the-isolated-shell.md)
