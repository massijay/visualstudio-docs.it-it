---
title: "Finestra Propriet&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proprietà [Visual Studio], finestra Proprietà"
  - "funzioni gestore, finestra Proprietà"
  - "gestori, finestra Proprietà"
  - "Windows (messaggi)"
  - "proprietà [Visual Studio], impostazione in fase di progettazione"
  - "proprietà [Visual Studio], modifica"
  - "Visualizzatore proprietà"
  - "Messaggi Windows, aggiunta di gestori messaggi"
  - "Finestra Proprietà, override"
  - "funzioni virtuali, finestra Proprietà"
  - "Finestra Proprietà"
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Finestra Propriet&#224;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilizzare questa finestra per visualizzare e modificare gli eventi e le proprietà della fase di progettazione degli oggetti selezionati situati negli editor e nelle finestre di progettazione.  È inoltre possibile utilizzare la finestra **Proprietà** per modificare e visualizzare le proprietà di file, progetti e soluzioni.  È possibile scegliere la finestra **Proprietà** dal menu **Visualizza**.  È inoltre possibile aprirlo premendo F4 o digitando proprietà nella finestra **Avvio veloce**.  
  
 Nella finestra **Proprietà** vengono visualizzati diversi tipi di campi di modifica, a seconda delle esigenze di una determinata proprietà.  Tali campi includono caselle di testo, caselle di riepilogo a discesa e collegamenti a finestre di dialogo di editor personalizzate.  Le proprietà in grigio sono di sola lettura.  
  
## Elenco UIElement  
 Nome oggetto  
 Elenca l'oggetto o gli oggetti correntemente selezionati.  Sono visibili solo gli oggetti dell'editor o della finestra di progettazione attiva.  Quando si selezionano più oggetti, vengono visualizzate soltanto le proprietà comuni a tutti gli oggetti selezionati.  
  
 Per categoria  
 Elenca tutte le proprietà e i relativi valori per l'oggetto selezionato, per categoria.  È possibile comprimere una categoria per ridurre il numero di proprietà visibili.  Quando si espande o si comprime una categoria, a sinistra del nome della categoria viene visualizzato rispettivamente il segno meno \(\-\) o più \(\+\).  Le categorie sono elencate in ordine alfabetico.  
  
 Alfabetico  
 Elenca in ordine alfabetico tutti gli eventi e le proprietà della fase di progettazione per gli oggetti selezionati.  Per modificare una proprietà attiva, fare clic nella cella a destra e immettere le modifiche.  
  
 Pagine delle proprietà  
 Consente di visualizzare la finestra di dialogo **Pagine delle proprietà** o **Progettazione progetti** per l'elemento selezionato.  Nella finestra di dialogo Pagine delle proprietà viene visualizzato un subset di proprietà, che corrisponde a quello delle proprietà disponibili nella finestra **Proprietà** o ne rappresenta un superset.  Utilizzare questo pulsante per visualizzare e modificare le proprietà relative alla configurazione attiva del progetto.  
  
 Proprietà  
 Consente di visualizzare le proprietà per un oggetto.  Molti oggetti dispongono inoltre di eventi che possono essere visualizzati utilizzando la finestra **Proprietà**.  
  
 Ordine per origine della proprietà.  
 Raggruppa le proprietà per origine, quale ereditarietà, stili applicati e associazioni.  Disponibile solo in caso di modifica di file XAML nella finestra di progettazione.  
  
 Eventi  
 Consente di visualizzare gli eventi relativi a un oggetto.  
  
> [!NOTE]
>  Questo controllo della barra degli strumenti della finestra **Proprietà** è disponibile solo quando è attiva una finestra di progettazione form o controlli nel contesto di un progetto [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  In caso di modifica di file XAML, gli eventi vengono visualizzati in una scheda separata della finestra delle proprietà.  
  
 Messaggi  
 Consente di elencare tutti i messaggi di Windows.  Consente di aggiungere o eliminare funzioni specifiche del gestore per i messaggi forniti per la classe selezionata.  
  
> [!NOTE]
>  Questo controllo della barra degli strumenti della finestra **Proprietà** è disponibile solo quando **Visualizzazione classi** è la finestra attiva nel contesto di un progetto [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 Overrides  
 Consente di elencare tutte le funzioni virtuali per la classe selezionata e di aggiungere o eliminare funzioni di override.  
  
> [!NOTE]
>  Questo controllo della barra degli strumenti della finestra **Proprietà** è disponibile solo quando **Visualizzazione classi** è la finestra attiva nel contesto di un progetto [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 Riquadro Descrizione  
 Consente di visualizzare il tipo e una breve descrizione della proprietà.  È possibile attivare e disattivare la descrizione della proprietà tramite il comando Descrizione del menu di scelta rapida.  
  
> [!NOTE]
>  Questo controllo della barra degli strumenti della finestra **Proprietà** non è disponibile in caso di modifica di file XAML nella finestra di progettazione.  
  
 Visualizzazione anteprima  
 Mostra una rappresentazione visiva dell'elemento attualmente selezionato in caso di modifica di file XAML nella finestra di progettazione.  
  
 Cerca  
 Fornisce una funzione di ricerca per proprietà ed eventi in caso di modifica di file XAML nella finestra di progettazione.  La casella di ricerca risponde alle ricerche di parola parziali e aggiorna risultati della ricerca mentre si digita.  
  
## Vedere anche  
 [Riferimenti alle proprietà di progetto](../../ide/reference/project-properties-reference.md)   
 [Personalizzazione del layout della finestra](../../ide/customizing-window-layouts-in-visual-studio.md)