---
title: "Condivisione di classi tra DSL utilizzando una libreria DSL | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 7
caps.handback.revision: 7
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Condivisione di classi tra DSL utilizzando una libreria DSL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] L'sdk di visualizzazione e modellazione di, è possibile creare una definizione completa DSL che è possibile includere in un altro linguaggio DSL.  Ciò consente di scomporre le parti in fattori comuni di simili modelli.  
  
## Creazione e utilizzo delle librerie DSL  
  
#### Per creare una raccolta DSL  
  
1.  Creare un nuovo progetto di modello DSL e scegliere il modello di soluzioni della raccolta DSL.  
  
     Un singolo progetto di modello DSL verrà creato con un modello vuoto.  
  
2.  È possibile aggiungere classi di dominio, relazioni, forme e così via.  
  
     Gli elementi della raccolta non è necessario formare una singola struttura ad albero che utilizza.  
  
     Per definire una relazione che le utilità di importazione possono utilizzare, creare due classi di dominio e creare la relazione tra esse.  
  
     Si consideri la possibilità di impostare **modificatore di ereditarietà** le classi di dominio a  `Abstract`.  
  
3.  È possibile aggiungere gli elementi definiti nel modello DSL Esplora Risorse, quali generatori della connessione.  
  
4.  È possibile aggiungere le personalizzazioni che richiedono ulteriore codice, come vincoli di convalida.  
  
5.  Fare clic su **Trasformazione di tutti i modelli**.  
  
6.  Compilare il progetto.  
  
7.  Quando si distribuisce il modello DSL per altri utenti da utilizzare, è necessario specificare sia l'assembly compilato \(DLL\) che il file `DslDefinition.dsl`.  È possibile trovare l'assembly compilato in una cartella a l `Dsl\bin\*`  
  
#### Per importare una libreria DSL  
  
1.  In un'altra definizione DSL, in **DSL Esplora Risorse**, fare clic con il pulsante destro del mouse sulla classe radice del modello DSL e quindi fare clic su  **aggiungere la nuova importazione di DslLibrary**.  
  
2.  Nella Finestra Proprietà, impostare **Percorso del file** la raccolta.  È possibile utilizzare un percorso relativo o assoluto.  
  
     La raccolta inclusa nel modello DSL Esplora Risorse, in modalità di sola lettura.  
  
3.  È possibile utilizzare le classi importate come classi base.  Creare una classe di dominio nel modello DSL di importazione, quindi nella Finestra Proprietà impostare **Classe base** in una classe inclusa.  
  
4.  Trasformazione di selezionare tutti i modelli.  
  
5.  Aggiungere al progetto di modello DSL un riferimento a un assembly \(DLL\) che è stato compilato dal progetto libreria DSL.  
  
6.  Compilare la soluzione.  
  
 Una raccolta DSL possibile importare altre raccolte.  Quando si importa una libreria, le importazioni inoltre visualizzate automaticamente nel modello DSL Esplora Risorse.  
  
## Vedere anche  
 [Procedura: definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)