---
title: Codifiche e interruzioni di riga | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 8
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
ms.openlocfilehash: 34c400c280096acb7e0ce272fa717cbc2f8f0d8a
ms.contentlocale: it-it
ms.lasthandoff: 05/24/2017

---
# <a name="encodings-and-line-breaks"></a>Codifiche e interruzioni di riga
In Visual Studio è possibile usare le impostazioni **File/Opzioni di salvataggio avanzate** per determinare il tipo di caratteri dell'interruzione di riga. Con le stesse impostazioni è anche possibile modificare la codifica di un file.  
  
> [!NOTE]
>  Se si usano determinati tipi di impostazioni di sviluppo (Visual Basic, F #, sviluppo Web), l'impostazione **Opzioni di salvataggio avanzate** potrebbe non essere visualizzata nel menu. Per modificare le impostazioni (ad esempio in Generale), aprire **Strumenti / Importa ed Esporta impostazioni**. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 In Visual Studio i caratteri seguenti vengono interpretati come interruzioni di riga:  
  
-   CRLF: ritorno a capo + avanzamento riga, caratteri Unicode 000D + 000A  
  
-   LF: avanzamento riga, carattere Unicode 000A  
  
-   NEL:rRiga successiva, carattere Unicode 0085  
  
-   LF: separatore di riga, carattere Unicode 2028  
  
-   PS: separatore di paragrafo, carattere Unicode 2029  
  
 Il testo che viene copiato da altre applicazioni mantiene la codifica e i caratteri originali dell'interruzione di riga. Ad esempio, quando il testo viene copiato da Blocco note e incollato in un file di testo in Visual Studio, il testo mantiene le stesse impostazioni che aveva in Blocco note.  
  
 Quando si apre un file con caratteri diversi dell'interruzione di riga, è possibile che venga visualizzata una finestra di dialogo in cui si chiede se normalizzare i caratteri dell'interruzione di riga incoerenti e quale tipo di interruzione di riga scegliere.
