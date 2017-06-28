---
title: "Opzioni, Editor di testo, Tutti i linguaggi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.JavaScript.General"
  - "VS.ToolsOptionsPages.Text_Editor.ResJSON.General"
  - "vs.toolsoptionspages.text_editor.all_languages.scrollbars"
helpviewer_keywords: 
  - "Editor di testo (finestra di dialogo Opzioni)"
  - "completamento delle istruzioni"
  - "a capo automatico"
  - "Generale (finestra di dialogo)"
  - "numeri di riga"
  - "spazio virtuale"
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Opzioni, Editor di testo, Tutti i linguaggi
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Questa finestra di dialogo consente di modificare il comportamento predefinito dell'editor di codice.  Queste impostazioni si applicano anche ad altri editor basati sull'editor di codice, ad esempio la visualizzazione Origine della finestra di progettazione HTML.  Per aprire questa finestra di dialogo, scegliere **Opzioni** dal menu **Strumenti**.  Nella cartella **Editor di testo** espandere la sottocartella **Tutti i linguaggi** e quindi scegliere **Generale**.  
  
> [!CAUTION]
>  In questa pagina è possibile impostare le opzioni predefinite di tutti i linguaggi di sviluppo.  La reimpostazione di un'opzione in questa finestra di dialogo determina la reimpostazione delle opzioni Generale in tutti i linguaggi in base alle selezioni effettuate in questo contesto.  Per modificare le opzioni dell'editor di testo per un solo linguaggio, espandere la sottocartella di tale linguaggio e selezionare le relative pagine di opzioni.  
  
 Quando nelle pagine di opzioni Generale è stata selezionata un'opzione per alcuni linguaggi di programmazione, ma non per altri, viene visualizzato un segno di spunta di colore grigio.  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Completamento istruzioni  
 Elenco membri automatico  
 Quando questa opzione è selezionata, IntelliSense visualizzerà elenchi popup dei membri, delle proprietà, dei valori e dei metodi disponibili durante la digitazione nell'editor.  Scegliere qualsiasi elemento dall'elenco popup per inserirlo nel codice.  Selezionando questa opzione viene attivata l'opzione **Nascondi membri avanzati**.  
  
 Nascondi membri avanzati  
 Se selezionata, gli elenchi popup di completamento delle istruzioni vengono ridotti e vengono visualizzati solo gli elementi di uso più comune.  Agli altri elementi viene applicato un filtro che non ne consente la visualizzazione nell'elenco.  
  
 Informazioni parametri  
 Quando questa opzione è selezionata, la sintassi completa della dichiarazione o della routine corrente viene visualizzata sotto il punto di inserimento nell'editor, con tutti i relativi parametri disponibili.  Il parametro successivo che è possibile assegnare viene visualizzato in grassetto.  
  
## Impostazioni  
 Attiva spazio virtuale  
 Quando questa opzione è selezionata e l'opzione **A capo automatico** è deselezionata, è possibile fare clic in qualsiasi punto oltre la fine della riga nell'editor di codice e digitare.  È possibile utilizzare questa funzionalità per inserire commenti relativi al codice sempre nello stesso punto.  
  
 A capo automatico  
 Se questa opzione è selezionata, la parte di una riga che si estende in senso orizzontale oltre la parte visibile dell'editor viene automaticamente visualizzata nella riga successiva.  Se si seleziona questa opzione, l'opzione **Mostra icone per ritorno a capo automatico** viene attivata.  
  
> [!NOTE]
>  Mentre l'opzione **A capo automatico** è attivata, la funzionalità **Spazio virtuale** viene disattivata.  
  
 Mostra icone per ritorno a capo automatico  
 Quando questa opzione è selezionata, viene visualizzato un indicatore a forma di freccia rivolta indietro in caso di ritorno a capo automatico di una riga lunga su una seconda riga.  
  
 Deselezionare questa opzione per non visualizzare tali indicatori.  
  
> [!NOTE]
>  Tali frecce di promemoria non vengono aggiunte al codice né stampate,  ma vengono visualizzati solo a scopo di riferimento.  
  
 Applica comandi Taglia o Copia a righe vuote in assenza di selezione  
 Questa opzione consente di impostare il comportamento dell'editor quando si posiziona il punto di inserimento su una riga vuota, non si seleziona alcun elemento, quindi si utilizza il comando Copia o Taglia.  
  
-   Se questa opzione è selezionata, la riga vuota viene copiata o tagliata.  Se quindi si utilizza il comando Incolla, viene inserita una nuova riga vuota.  
  
-   Se questa opzione è deselezionata, il comando Taglia rimuove le righe vuote.  Tuttavia, i dati negli Appunti vengono mantenuti.  Quindi, se si utilizza il comando Incolla, viene inserito il contenuto copiato più di recente negli Appunti.  Se non è stata effettuata alcuna copia precedente, non viene incollato nulla.  
  
 Questa impostazione non ha alcun effetto sul comando Copia o Taglia se una riga non è vuota.  Se non si seleziona alcun elemento, viene copiata o tagliata l'intera riga.  Se quindi si applica il comando Incolla, viene inserito il testo dell'intera riga, incluso il carattere di fine riga.  
  
> [!TIP]
>  Per visualizzare gli indicatori per spazi, tabulazioni e fine riga e distinguere pertanto le righe rientrate da quelle completamente vuote, selezionare **Avanzate** dal menu **Modifica**, quindi scegliere **Mostra\/Nascondi spazi**.  
  
## Visualizzazione  
 Numeri di riga  
 Quando questa opzione è selezionata, accanto a ciascuna riga di codice viene visualizzato un numero di riga.  
  
> [!NOTE]
>  Tali numeri di riga non vengono aggiunti al codice né stampati,  ma vengono visualizzati solo a scopo di riferimento.  
  
 Consenti apertura URL con clic singolo  
 Quando questa opzione è selezionata, il cursore del mouse assume la forma di una mano quando viene posizionato su un URL nell'editor.  È possibile fare clic sull'URL per visualizzare la pagina indicata nel browser Web.  
  
 Barra di navigazione  
 Quando questa opzione è selezionata, nella parte superiore dell'editor di codice viene visualizzata la **barra di navigazione**,  i cui elenchi a discesa **Oggetti** e **Membri** consentono di scegliere un determinato oggetto nel codice, selezionarne i membri e passare alla dichiarazione del membro selezionato nell'editor di codice.  
  
## Vedere anche  
 [Opzioni, Editor di testo, Tutti i linguaggi, Schede](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md)   
 [Utilizzo di IntelliSense](../../ide/using-intellisense.md)