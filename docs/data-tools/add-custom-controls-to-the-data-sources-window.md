---
title: "Aggiungere controlli personalizzati alla finestra Origini dati | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.howtoaddcustomcontrol"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Finestra Origini dati, aggiunta controlli"
  - "controlli [Visual Studio], aggiunta alla finestra Origini dati"
  - "Classe DefaultBindingPropertyAttribute, uso"
  - "Classe LookupBindingPropertiesAttribute, uso"
  - "Classe ComplexBindingPropertiesAttribute, uso"
  - "Finestra Origini dati, selezione controlli"
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: 42
caps.handback.revision: 39
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Aggiungere controlli personalizzati alla finestra Origini dati
Quando si trascina un elemento dalla finestra **Origini dati** in un'area di progettazione per creare un controllo con associazione a dati, è possibile selezionare il tipo di controllo da creare.  Per ogni elemento della finestra è presente un elenco a discesa in cui sono visualizzati i controlli tra cui è possibile scegliere.  Il set di controlli associati a ciascun elemento dipende dal tipo di dati dell'elemento.  Se il controllo che si desidera creare non è visualizzato nell'elenco, è possibile aggiungerlo seguendo le istruzioni fornite in questo argomento.  
  
 Per ulteriori informazioni sulla selezione di controlli associati a dati da creare per gli elementi nella finestra **Origini dati**, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, selezionare **Importa\/Esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="customizinglist"></a> Personalizzazione dell'elenco dei controlli associabili per un tipo di dati  
 Eseguire i passaggi seguenti per aggiungere o rimuovere i controlli dall'elenco dei controlli disponibili per gli elementi della finestra **Origini dati** che presentano un tipo di dati specifico.  
  
#### Per selezionare i controlli da elencare per un tipo di dati  
  
1.  Verificare che Progettazione WPF o Progettazione Windows Form sia aperto.  
  
2.  Nella finestra **Origini dati** fare clic su un elemento che fa parte di un'origine dati aggiunta alla finestra, quindi fare clic sul menu a discesa dell'elemento.  
  
3.  Nel menu a discesa fare clic su **Personalizza**.  Verrà visualizzata una delle finestre di dialogo seguenti:  
  
    -   Se Progettazione Windows Form è aperto, verrà visualizzata la pagina **Personalizzazione dell'interfaccia utente dati** della finestra di dialogo **Opzioni**.  
  
    -   Se Progettazione WPF è aperto, verrà visualizzata la finestra di dialogo **Personalizza associazione controlli**.  
  
4.  Nella finestra di dialogo selezionare un tipo di dati nell'elenco a discesa **Tipo di dati**.  
  
    -   Per personalizzare l'elenco dei controlli per una tabella o un oggetto, selezionare **\[Elenco\]**.  
  
    -   Per personalizzare l'elenco dei controlli per una colonna di una tabella o una proprietà di un oggetto, selezionare il tipo di dati della colonna o la proprietà nell'archivio dati sottostante.  
  
    -   Per personalizzare l'elenco dei controlli per visualizzare oggetti dati con forme definite dall'utente, selezionare **\[Altro\]**.  Selezionare **\[Altro\]** se ad esempio l'applicazione include un controllo personalizzato che visualizza i dati di più proprietà di un oggetto specifico.  
  
5.  Nella casella **Controlli associati** selezionare tutti i controlli che si desidera rendere disponibili per il tipo di dati scelto oppure annullare la selezione dei controlli che si desidera rimuovere dall'elenco.  
  
    > [!NOTE]
    >  Se il controllo che si intende selezionare non è presente nella casella **Controlli associati**, è necessario aggiungerlo all'elenco.  Per ulteriori informazioni, vedere [Aggiunta di controlli all'elenco di controlli associati a un tipo di dati](#addingcontrols).  
  
6.  Scegliere **OK**.  
  
7.  Nella finestra **Origini dati** fare clic su un elemento del tipo di dati cui sono stati appena associati uno o più controlli, quindi fare clic sul menu a discesa dell'elemento.  
  
     I controlli selezionati nella casella **Controlli associati** sono ora visualizzati nel menu a discesa dell'elemento.  
  
##  <a name="addingcontrols"></a> Aggiunta di controlli all'elenco di controlli associati a un tipo di dati  
 Se si desidera associare un controllo a un tipo di dati ma il controllo non è presente nella casella **Controlli associati**, è necessario aggiungerlo all'elenco.  Il controllo deve trovarsi nella soluzione corrente o in un assembly di riferimento, essere disponibile nella **Casella degli strumenti** e presentare un attributo che specifica il comportamento dell'associazione a dati del controllo.  
  
#### Per aggiungere controlli all'elenco di controlli associati  
  
1.  Aggiungere il controllo desiderato alla **Casella degli strumenti** facendo clic con il pulsante destro del mouse su **Casella degli strumenti** e scegliendo **Scegli elementi**.  
  
     Il controllo deve avere uno degli attributi seguenti.  
  
    |Attributo|Descrizione|  
    |---------------|-----------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implementare questo attributo su controlli semplici in cui viene visualizzata una singola colonna \(oppure una proprietà\) di dati, ad esempio <xref:System.Windows.Forms.TextBox>.|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implementare questo attributo su controlli in cui vengono visualizzati elenchi \(oppure tabelle\) di dati, ad esempio <xref:System.Windows.Forms.DataGridView>.|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implementare questo attributo sui controlli in cui vengono visualizzati elenchi \(oppure tabelle\) di dati, ma nei quali deve poter essere presentata anche una singola colonna o proprietà, ad esempio <xref:System.Windows.Forms.ComboBox>.|  
  
2.  Aprire la pagina **Personalizzazione dell'interfaccia utente dati** della finestra di dialogo **Opzioni** \(per Windows Form\) oppure aprire la finestra di dialogo  **Personalizza associazione controlli**  \(per WPF\).  Per ulteriori informazioni, vedere [Personalizzazione dell'elenco di controlli associabili per un tipo di dati](#customizinglist).  
  
3.  Il controllo aggiunto alla **Casella degli strumenti** dovrebbe essere visualizzato nella casella **Controlli associati**.  
  
    > [!NOTE]
    >  Possono essere aggiunti all'elenco dei controlli associati solo i controlli che si trovano nella soluzione corrente o in un assembly di riferimento e che implementano uno degli attributi di associazione a dati riportati nella tabella precedente.  Per associare i dati a un controllo personalizzato non disponibile nella finestra **Origini dati**, trascinare il controllo dalla **Casella degli strumenti** all'area di progettazione, quindi trascinare l'elemento da associare dalla finestra **Origini dati** al controllo.  
  
## Vedere anche  
 [Procedura dettagliata: visualizzazione di dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)   
 [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati complessa](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)   
 [Procedura dettagliata: creazione di un controllo utente Windows Form che supporta l'associazione dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)   
 [Finestra di dialogo Personalizza associazione controllo](../data-tools/customize-control-binding-dialog-box.md)