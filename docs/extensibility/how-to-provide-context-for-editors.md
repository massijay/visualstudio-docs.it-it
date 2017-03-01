---
title: 'Procedura: fornire il contesto per gli editor | Documenti di Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 17
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 362cd554e0723b1137d033440c9844d6cf3e59dd
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-context-for-editors"></a>Procedura: fornire il contesto per gli editor
Per un editor, il contesto è attivo solo quando l'editor ha lo stato attivo o attivo immediatamente prima che lo stato attivo è stato spostato in una finestra degli strumenti. È possibile fornire contesto per un editor effettuando le operazioni seguenti:  
  
1.  Creare un contenitore del contesto.  
  
2.  Pubblicare il contenitore del contesto per l'identificatore dell'elemento di selezione (SEID).  
  
3.  Mantenere il contesto nell'elenco.  
  
 Queste attività rientrano le procedure seguenti. Per ulteriori informazioni su come fornire contesto, vedere **programmazione efficiente** più avanti in questo argomento.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Per creare un contenitore del contesto per un editor o una finestra di progettazione  
  
1.  Chiamare `QueryService` sul <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>interfaccia per il <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>service.</xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
     Un puntatore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>interfaccia viene restituito.</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>  
  
2.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>metodo per creare un nuovo contenitore di contesto o sottocontesto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>  
  
     Un puntatore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>interfaccia viene restituito.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>  
  
3.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>metodo per aggiungere gli attributi, parole chiave di ricerca o le parole chiave F1 all'elenco contesto o sottocontesto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>  
  
4.  Se si sta creando un contenitore sottocontesto, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>metodo a cui collegarsi contesti padre contenitore sottocontesto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>  
  
5.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>per ricevere una notifica quando il **Guida dinamica** finestra è effettuato l'aggiornamento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>  
  
     Con il **Guida dinamica** finestra chiamare editor quando è pronto per l'aggiornamento consente di ritardare la modifica del contesto fino a quando non si verifica l'aggiornamento. Questa operazione può migliorare le prestazioni poiché consente di ritardare l'esecuzione richiede molto tempo algoritmi fino a quando non è disponibile tempo di inattività del sistema.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Per pubblicare il contenitore del contesto di SEID  
  
1.  Chiamare `QueryService` sul <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>servizio di restituire un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> </xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>  
  
2.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, specificando un identificatore di elemento (`elementid` parametro) valore di SEID_UserContext per indicare che si sta passando contesto a livello globale.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>  
  
3.  Quando l'editor o la finestra di progettazione diventa attivo, i valori dei relativi <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>oggetto vengono propagate alla selezione globale.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> È sufficiente completare il processo una volta per sessione e quindi archiviare il puntatore per il contesto globale creato durante la chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>  
  
### <a name="to-maintain-the-context-bag"></a>Per mantenere il contenitore del contesto  
  
1.  Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>per garantire che il **Guida dinamica** chiamate nella finestra editor o nella finestra di progettazione prima viene aggiornato.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>  
  
     Per ogni contenitore del contesto che ha chiamato <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>dopo che il contenitore del contesto viene creato e ha implementato <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, le chiamate IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>per notificare al provider di contesto che verrà aggiornato il contenitore del contesto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> È possibile utilizzare questa chiamata per modificare gli attributi e parole chiave in contesti e in qualsiasi bagagli sottocontesto, prima di **Guida dinamica** si verifica di Windows update.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>in contesti per indicare che l'editor o la finestra di progettazione è nuovo contesto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>  
  
     Quando il **Guida dinamica** finestra chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>per indicare che l'aggiornamento, l'editor o la finestra di progettazione può aggiornare il contesto in modo appropriato per il contenitore del contesto padre e qualsiasi sacchi sottocontesto in quel momento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>  
  
    > [!NOTE]
    >  Il `SetDirty` flag viene impostato automaticamente su `true` ogni volta che contesto viene aggiunto o rimosso dall'elenco di contesto. Il **Guida dinamica** solo chiamate nella finestra <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>in contesti se il `SetDirty` flag è impostato su `true`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> Viene reimpostato su `false` dopo l'aggiornamento.  
  
3.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>per aggiungere contesto per la raccolta di contesto attivo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>rimuovere contesto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Se si sta scrivendo un editor personalizzato, è necessario completare tutte e tre le procedure descritte in questo argomento per fornire il contesto per l'editor.  
  
> [!NOTE]
>  Per attivare una finestra dell'editor o finestra di progettazione e assicurarsi che il routing di comandi è stato aggiornato correttamente, è necessario chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>sul componente per rendere tale finestra lo stato attivo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>  
  
 Il SEID è una raccolta di proprietà che cambiano in base alla selezione. Informazioni SEID sono disponibile tramite la selezione globale. La selezione globale è formare gli eventi generati dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>interfaccia, e ha un elenco di tutti gli elementi che è selezionato (editor corrente, finestra degli strumenti corrente, gerarchia corrente e così via).</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>  
  
 Per gli editor e finestre di progettazione, in cui il contesto può cambiare ogni volta che il cursore si sposta all'interno di una parola, non è efficiente aggiornare continuamente i contesti. Per facilitare l'aggiornamento più efficiente ogni volta che si rileva il cursore all'interno di editor o nella finestra di progettazione, è possibile chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> Questa operazione consente di mantenere le modifiche di contesto fino a quando non vi è tempo di inattività e il servizio di contesto dell'IDE invia la notifica per l'editor o la finestra di progettazione che il **Guida dinamica** finestra sta aggiornando. Questo approccio viene utilizzato nella procedura "per mantenere il contenitore del contesto" in questo argomento.  
  
 Dopo aver fornito contesto per le attività all'interno dell'editor o finestra di progettazione, è necessario fornire una parola chiave F1 specifica per consentire agli utenti di visualizzare la Guida per l'editor o la finestra di progettazione stessa.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>
