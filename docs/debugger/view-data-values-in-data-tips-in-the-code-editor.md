---
title: "Visualizzare i valori di dati nei suggerimenti dati nell&#39;editor del codice | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DataTips (strumento)"
  - "debug [Visual Studio], DataTips"
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzare i valori di dati nei suggerimenti dati nell&#39;editor del codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I suggerimenti dati sono un modo pratico per visualizzare le informazioni sulle variabili nel programma durante il debug.  I suggerimenti dati funzionano solo in modalità di interruzione e solo con variabili che si trovano nell'ambito di esecuzione corrente.  
  
 In [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] i suggerimenti dati possono essere bloccati in un percorso specifico in un file di origine oppure possono scorrere nella parte superiore delle finestre di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### Per visualizzare un suggerimento dati \(solo in modalità di interruzione\)  
  
1.  In una finestra di origine, posizionare il puntatore del mouse su una qualsiasi variabile nell'ambito corrente.  
  
     Viene visualizzato un suggerimento dati.  
  
    > [!NOTE]
    >  I suggerimenti dati vengono sempre valutati nel contesto in cui l'esecuzione viene sospesa, non nel punto in cui passa il cursore.  Se si passa il puntatore su una variabile in un'altra funzione con lo stesso nome di una variabile presente nel contesto corrente, il valore della variabile nell'altra funzione viene visualizzato come valore della variabile nel contesto corrente.  
  
2.  Il suggerimento dati scompare quando si rimuove il puntatore del mouse.  Per bloccare il suggerimento dati in modo tale che rimanga aperto, fare clic sull'icona **Blocca a origine** oppure  
  
    -   Fare clic con il pulsante destro del mouse su una variabile, quindi fare clic su **Blocca a origine**.  
  
     Il suggerimento dati bloccato verrà chiuso al termine della sessione di debug.  
  
### Per sbloccare un suggerimento dati e far sì che scorra  
  
-   In un suggerimento dati bloccato fare clic sull'icona **Sblocca da origine**.  
  
     L'icona di blocco passa alla posizione sbloccata.  Il suggerimento dati scorre ora nella parte superiore delle finestre aperte.  Il suggerimento dati mobile verrà chiuso al termine della sessione di debug.  
  
### Per ribloccare un suggerimento dati mobile  
  
-   In un suggerimento dati fare clic sull'icona di blocco.  
  
     L'icona passa alla posizione bloccata.  Se il suggerimento dati è al di fuori di una finestra di origine, l'icona di blocco è disabilitata e il suggerimento dati non può essere bloccato.  
  
### Per chiudere un suggerimento dati  
  
-   Posizionare il puntatore del mouse su un suggerimento dati, quindi fare clic sull'icona **Chiudi**.  
  
### Per chiudere tutti i suggerimenti dati  
  
-   Scegliere **Cancella tutti i suggerimenti dati** dal menu **Debug**.  
  
### Per chiudere tutti i suggerimenti dati di un file specifico  
  
-   Nel menu **Debug** scegliere **Cancella tutti i suggerimenti dati bloccati a** *File*.  
  
## Espansione e modifica delle informazioni  
 È possibile utilizzare i suggerimenti dati per espandere una matrice, una struttura o un oggetto e visualizzarne i membri.  È anche possibile modificare il valore di una variabile da un suggerimento dati.  
  
#### Per espandere una variabile per visualizzarne gli elementi  
  
-   In un suggerimento dati posizionare il puntatore del mouse sul segno **\+** che precede il nome della variabile.  
  
     La variabile si espande per visualizzare i relativi elementi in formato struttura ad albero.  
  
     Quando la variabile è espansa, è possibile utilizzare i tasti di direzione sulla tastiera per spostarsi verso l'alto e verso il basso.  In alternativa, è possibile utilizzare il mouse.  
  
#### Per modificare il valore di una variabile utilizzando un suggerimento dati  
  
1.  In un suggerimento dati, fare clic sul valore.  Questa opzione non è disponibile per i valori di sola lettura.  
  
2.  Digitare un nuovo valore e premere INVIO.  
  
## Rendere trasparente un suggerimento dati  
 Per visualizzare il codice che sta dietro a un suggerimento dati, è possibile renderlo temporaneamente trasparente.  Ciò non si applica a suggerimenti dati bloccati o mobili.  
  
#### Per rendere trasparente un suggerimento dati  
  
-   In un suggerimento dati, premere CTRL.  
  
     Il suggerimento dati resterà trasparente finché si terrà premuto il tasto CTRL.  
  
## Visualizzazione di tipi di dati complessi  
 Se accanto a un nome di variabile in un suggerimento dati viene visualizzata un'icona a forma di lente di ingrandimento, sono disponibili uno o più [Visualizzatori](../debugger/create-custom-visualizers-of-data.md) per variabili di tale tipo di dati.  È possibile utilizzare un visualizzatore per visualizzare le informazioni in un formato più significativo, generalmente grafico.  
  
#### Per visualizzare il contenuto di una variabile utilizzando un visualizzatore  
  
-   Fare clic sull'icona a forma di lente di ingrandimento per selezionare il visualizzatore predefinito per il tipo di dati.  
  
     \-oppure\-  
  
     Fare clic sulla freccia popup accanto al visualizzatore per selezionare da un elenco di visualizzatori appropriati per il tipo di dati.  
  
     Un visualizzatore visualizzerà le informazioni.  
  
## Aggiunta di informazioni a una finestra Espressioni di controllo  
 Per continuare a controllare una variabile, è possibile aggiungerla alla finestra **Espressioni di controllo** da un suggerimento dati.  
  
#### Per aggiungere una variabile alla finestra Espressioni di controllo  
  
-   Fare clic con il pulsante destro del mouse su un suggerimento dati, quindi scegliere **Aggiungi espressione di controllo**.  
  
     La variabile verrà aggiunta alla finestra **Espressioni di controllo**.  In caso di utilizzo di un'edizione che supporta più finestre **Espressioni di controllo**, la variabile verrà aggiunta a **Espressioni di controllo 1**.  
  
## Importazione ed esportazione di suggerimenti dati  
 È possibile esportare suggerimenti dati in un file XML, per poi condividerlo con un collega o modificarlo mediante un editor di testo.  
  
#### Per esportare suggerimenti dati  
  
1.  Scegliere **Esporta suggerimenti dati** dal menu Debug.  
  
     Verrà visualizzata la finestra di dialogo **Esporta suggerimenti dati**.  
  
2.  Utilizzare tecniche di file standard per passare al percorso in cui si desidera salvare il file XML, digitare un nome per il file nella casella **Nome file**, quindi fare clic su **OK**.  
  
#### Per importare suggerimenti dati  
  
1.  Scegliere **Importa suggerimenti dati** dal menu Debug.  
  
     Verrà visualizzata la finestra di dialogo **Importa suggerimenti dati**.  
  
2.  Utilizzare la finestra di dialogo per trovare il file XML che si desidera aprire e fare clic su **OK**.  
  
## Vedere anche  
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Procedura: utilizzare la finestra di dialogo Controllo immediato](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Visualizzatori](../debugger/create-custom-visualizers-of-data.md)   
 [Procedura: modificare il formato numerico delle finestre del debugger](../Topic/How%20to:%20Change%20the%20Numeric%20Format%20of%20Debugger%20Windows.md)