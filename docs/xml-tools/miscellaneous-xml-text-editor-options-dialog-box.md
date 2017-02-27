---
title: "Varie, XML, editor di testo, finestra di dialogo Opzioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Varie, XML, editor di testo, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa finestra di dialogo consente di modificare le impostazioni di completamento automatico e dello schema per l'editor XML.È possibile accedere alla finestra di dialogo **Opzioni** dal menu **Strumenti**.  
  
> [!NOTE]
>  Queste impostazioni sono disponibili quando si seleziona la cartella **Editor di testo**, la cartella **XML** e quindi l'opzione **Varie** nella finestra di dialogo **Opzioni**.  
  
## Inserimento automatico  
 **Tag di fine**  
 Se l'impostazione di completamento automatico è selezionata, l'editor aggiunge automaticamente un tag di fine quando si digita una parentesi uncinata chiusa \(\>\) per chiudere un tag di inizio, se il tag non è stato ancora chiuso.Questo è il funzionamento predefinito.  
  
 Il completamento di un elemento vuoto non dipende dall'impostazione di completamento automatico.È sempre possibile completare automaticamente un elemento vuoto digitando una barra rovesciata \(\/\).  
  
 **Virgolette attributo**  
 Quando si creano attributi XML, l'editor inserisce i caratteri `=" "` e posiziona l'accento circonflesso \(^\) all'interno delle virgolette.  
  
 Selezionato per impostazione predefinita.  
  
 **Dichiarazioni dello spazio dei nomi**  
 L'editor inserisce automaticamente le dichiarazioni dello spazio dei nomi ovunque siano necessarie.  
  
 Selezionato per impostazione predefinita.  
  
 **Altri markup \(commenti, CDATA\)**  
 Commenti, CDATA, DOCTYPE, istruzioni di elaborazione e altri markup vengono completati automaticamente.  
  
 Selezionato per impostazione predefinita.  
  
## Rete  
 **Scarica automaticamente le DTD e gli schemi**  
 Gli schemi e le DTD \(Document Type Definitions\) vengono scaricati automaticamente dalle posizioni HTTP.Questa funzionalità utilizza System.Net con il rilevamento automatico dei server proxy abilitato.  
  
 Selezionato per impostazione predefinita.  
  
## Struttura  
 **Attiva modalità struttura all'apertura del file**  
 Attiva la funzionalità struttura quando un file è aperto.  
  
 Selezionato per impostazione predefinita.  
  
## Memorizzazione nella cache  
 **Schemi**  
 Specifica il percorso della cache degli schemi.Il pulsante Sfoglia \(**...**\) consente di aprire la finestra di dialogo **Directory** nella posizione corrente della cache dello schema.È possibile selezionare una directory diversa o selezionare una cartella nella finestra di dialogo, fare clic con il pulsante destro del mouse, quindi scegliere **Apri** per visualizzare il contenuto della directory.  
  
## Vedere anche  
 [Proprietà dei documenti XML, finestra Proprietà](../xml-tools/xml-document-properties-properties-window.md)   
 [Componenti dell'editor XML](../xml-tools/xml-editor-components.md)