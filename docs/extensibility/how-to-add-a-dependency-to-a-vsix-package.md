---
title: 'Procedura: aggiungere una dipendenza a un pacchetto VSIX | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3f3b54e19d8418f35a733b73ea0616b53bd42ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Procedura: aggiungere una dipendenza a un pacchetto VSIX
È possibile configurare una distribuzione di pacchetto VSIX che installa tutte le dipendenze che non sono già presenti nel computer di destinazione. A tale scopo, includere le dipendenze del progetto VSIX per il file vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Per aggiungere una dipendenza  
  
1.  Aprire il file vsixmanifest nel **progettazione** visualizzazione. Passare al **dipendenze** scheda e fare clic su **New**.  
  
2.  Per aggiungere un'estensione installata: nel **aggiungere nuove dipendenze** nella finestra di dialogo **estensione installata** e quindi, per il **nome**, selezionare un'estensione nell'elenco.  
  
3.  Per aggiungere un altro progetto VSIX che non è installato:: nel **aggiungere nuove dipendenze** nella finestra di dialogo **File nel file system** e quindi usare il **Sfoglia** per selezionare il progetto VSIX.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento dello Schema 1.0 dell'estensione VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Preparazione di estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)