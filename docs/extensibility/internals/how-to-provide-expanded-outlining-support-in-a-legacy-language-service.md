---
title: Fornire la struttura di supporto in un servizio di linguaggio | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: 16
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
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: fc502e4430a49284cffe14386249999d82085f1c
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Procedura: fornire il supporto esteso della struttura in un servizio di linguaggio Legacy
Sono disponibili due opzioni per l'estensione della struttura di supporto per il linguaggio oltre, supportando il **Comprimi alle definizioni** comando. È possibile aggiungere aree della struttura di controllo editor e aggiungere aree della struttura gestito dal client.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Aggiunta di aree della struttura controllato Editor  
 Utilizzare questo approccio per creare un'area della struttura e quindi consentire all'editor di gestire se l'area viene espanso, compresso e così via. Delle due opzioni per fornire supporto della struttura, questa opzione è meno affidabile. Per questa opzione, si crea una nuova area di struttura in un intervallo specificato di testo utilizzando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> Dopo la creazione di quest'area, il relativo comportamento è controllato dall'editor. Utilizzare la procedura seguente per implementare aree della struttura controllato editor.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Per implementare un'area della struttura controllato editor  
  
1.  Chiamare `QueryService` per<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager></xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Restituisce un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando un puntatore per un buffer di testo specificato.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> Restituisce un puntatore per il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>oggetto per il buffer.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
3.  Chiamare <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>per un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> </xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>  
  
4.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>per aggiungere uno o più nuovi descrive le aree contemporaneamente.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>  
  
     Questo metodo consente di specificare l'intervallo di testo alla struttura, se esistente aree della struttura vengono rimossi o mantenute e se l'area della struttura è espansa o compressa per impostazione predefinita.  
  
## <a name="adding-client-controlled-outline-regions"></a>Aggiunta di aree della struttura di controllo Client  
 Utilizzare questo approccio alla struttura implementare gestito dal client (o smart) simile a quella utilizzata per la [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] servizi linguistici. Un servizio di linguaggio che gestisce la propria struttura consente di monitorare il contenuto del buffer di testo per eliminare aree della struttura precedente quando essi diventa non valido e creare nuove aree della struttura in base alle esigenze.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Per implementare un'area struttura gestito dal client  
  
1.  Chiamare `QueryService` per <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> Restituisce un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando un puntatore per un buffer di testo specificato.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> Questo parametro determina se esiste già una sessione di testo nascosto per il buffer.  
  
3.  Se esiste già una sessione di testo, quindi non è necessario creare uno e un puntatore a un esistente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>viene restituito l'oggetto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Utilizzare questo puntatore per enumerare e creare aree della struttura. In caso contrario, chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>per creare una sessione di testo nascosto per il buffer.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> Un puntatore per il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>viene restituito l'oggetto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
    > [!NOTE]
    >  Quando si chiama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, è possibile specificare un client di testo nascosto (vale a dire un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>oggetto).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> Il client invia una notifica quando un testo nascosto o area della struttura è espanso o compresso dall'utente.  
  
4.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>struttura) parametri: specificare un valore di <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE>nel `iType` membro del <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>struttura per indicare che si sta creando un'area della struttura, piuttosto che in un'area nascosta.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> </xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> Specificare se l'area è gestito dal client o editor controllate nel `dwBehavior` membro del <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>struttura.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> L'implementazione della struttura smart può contenere una combinazione di aree della struttura editor e gestito dal client. Specificare il testo dell'intestazione che viene visualizzato quando l'area della struttura è compressa, ad esempio "...", nel `pszBanner` membro del <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>struttura.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Testo dell'intestazione dell'editor predefinito per un'area nascosta è "...".
