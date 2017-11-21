---
title: Origine controllo Runtime dettagli | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9647f1f399b0d6516fe6475e6245c6834a0ea2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-runtime-details"></a>Dettagli dell'origine controllo Runtime
Quando l'utente aggiunge un file nel progetto di controllo del codice sorgente o tramite un controller di automazione, ad esempio una procedura guidata, viene aggiunto un progetto al controllo del codice sorgente. Un progetto non è specificato per se stesso che sia in controllo del codice sorgente; supporta controllo del codice sorgente, ma devono essere aggiunti manualmente a esso.  
  
## <a name="registering-with-a-source-control-package"></a>Registrazione con un pacchetto di controllo di origine  
 Quando un file nel progetto viene aggiunto al controllo del codice sorgente, l'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> per fornire quattro stringhe opache che vengono utilizzate come i cookie per il controllo del codice sorgente. Archiviare queste stringhe nel file di progetto. Queste stringhe devono essere passate allo stub del controllo origine (il componente di Visual Studio che gestisce i pacchetti di controllo di origine) all'avvio del tipo di progetto per la chiamata <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. Ciò a sua volta carica il pacchetto di controllo di origine appropriato e inoltra la chiamata alla relativa implementazione di `IVsSccManager2::RegisterSccProject`.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)