---
redirect_url: /visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio
ms.openlocfilehash: 5ba8ada294275a99aab27ff9c249d6c3d8e17da3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
titolo: "controlli Windows Form di associazione a dati | Ms.custom Microsoft Docs":" "ms. date: Reviewer" 11/04/2016":" "ms.suite:" "ms. tgt_pltfrm:" "ms. topic: helpviewer_keywords" articolo": 
  - "la visualizzazione dei dati, controlli Windows Form"
  - "Windows Form, visualizzazione di dati"
  - "origini dati, la visualizzazione"
  - ms. AssetID "dati [Windows Form], visualizzazione": 0163a34a-38cb-40b9-8f38-3058a90caf21 caps.latest.revision: autore 28: author "gewarren": "gewarren" manager: ms. Technology ghogen: "strumenti di dati Visual Studio"
---
# <a name="bind-windows-forms-controls-to-data"></a>Associare controlli Windows Form ai dati
È possibile associare le origini dati ai controlli trascinando gli oggetti dal **origini dati** finestra in un Windows Form o in un controllo esistente in un form. Prima di trascinare elementi, è possibile impostare il tipo di controllo che si desidera associare. Valori diversi visualizzati a seconda se si scelga la tabella stessa, o una singola colonna.  È inoltre possibile impostare valori personalizzati. Per una tabella, "Dettagli" significa che ogni colonna è associato a un controllo separato.  

![Associare l'origine dati a DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata origine dati di associazione di DataGridView")  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>Associazione a dati in un controllo DataGridView  
Per DataGridView, l'intera tabella è associato a tale controllo singolo. Quando si trascina un controllo DataGridView al form, uno strumento striscia per l'esplorazione dei record (<xref:System.Windows.Forms.BindingNavigator>) viene inoltre visualizzato. Oggetto [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti. Nella figura seguente, viene inoltre aggiunto un TableAdapterManager perché la tabella Customers è una relazione con la tabella Orders. Queste variabili sono tutti dichiarate nel codice generato automaticamente come membri privati nella classe del modulo. Il codice generato automaticamente per la compilazione di DataGridView si trova nel gestore eventi form_load. Il codice per il salvataggio dei dati per aggiornare il database si trova nel gestore dell'evento Save di BindingNavigator. È possibile spostare o modificare il codice in base alle esigenze.  
  
 ![GridView con BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView con BindingNavigator")  
  
 È possibile personalizzare il comportamento di DataGridView e BindingNavigator facendo clic sullo smart tag nell'angolo superiore destro di ogni:  
  
 ![DataGridView e associazione Navigator smart tag](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView e associazione Navigator smart tag")  
  
 Se i controlli dell'applicazione è necessario non è disponibile dall'interno di **origini dati** finestra, è possibile aggiungere controlli. Per ulteriori informazioni, vedere [aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 È anche possibile trascinare elementi dal **origini dati** finestra controlli già presenti in un form per associare il controllo ai dati. Un controllo che è già associato a dati con i dati di binding reimpostati sull'elemento trascinato più di recente. Per essere destinazioni di rilascio valide, i controlli devono essere in grado di visualizzare il tipo di dati sottostante dell'elemento trascinato su di esso dal **origini dati** finestra. Ad esempio, non è a trascinare un elemento che ha un tipo di dati <xref:System.DateTime> su un <xref:System.Windows.Forms.CheckBox>, in quanto il <xref:System.Windows.Forms.CheckBox> non è in grado di visualizzare una data.  
  
## <a name="bind-to--data-in-individual-controls"></a>Associazione a dati in singoli controlli  
 Quando si associa un'origine dati per "Dettagli", ogni colonna nel set di dati è associato a un controllo separato.  
  
 ![Associare l'origine dati per i dettagli](../data-tools/media/raddata-bind-data-source-to-details.png "raddata origine dati di associazione per i dettagli")  
  
> [!IMPORTANT]
>  Si noti che nella figura precedente, si trascina dalla proprietà ordini della tabella Customers, non dalla tabella Orders. Tramite l'associazione alla proprietà Orders, i comandi di spostamento apportati in DataGridView vengono riflesse immediatamente nei controlli di dettagli. Se è stata trascinata dalla tabella Orders, i controlli sarebbero comunque essere associati al set di dati, ma non potrebbe non essere sincronizzati con il controllo DataGridView.  
  
 La figura seguente mostra l'impostazione predefinita i controlli con associazione a dati che vengono aggiunti al modulo dopo che la proprietà di ordini nella tabella Customers è associata a "Dettagli" nel **origini dati** finestra.  
  
 ![Tabella Orders associata ai dettagli](../data-tools/media/raddata-orders-table-bound-to-details.png "tabella Orders raddata associata ai dettagli")  
  
 Si noti inoltre che ogni controllo dispone di uno smart tag. Questo tag consente personalizzazioni che si applicano a solo a tale controllo.  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)