---
title: "Procedura: creare Atom Feed per una raccolta privata | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Feed Atom, le raccolte private VSIX"
  - "Raccolte private VSIX, feed Atom"
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Procedura: creare Atom Feed per una raccolta privata
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile creare un Atom feed RSS in un percorso intranet che contiene le estensioni e aggiunta il feed in **estensioni e aggiornamenti** come una raccolta privata. Per altre informazioni, vedere [Raccolte private](../extensibility/private-galleries.md).  
  
## Creazione di un Atom Feed  
 Per creare un feed come una raccolta privata Atom, innanzitutto è necessario raccogliere le estensioni \(file con estensione VSIX\) in una cartella. Se si desidera, è possibile organizzarle nelle sottocartelle. È necessario anche le risorse seguenti:  
  
-   Un file atom.xml che rende disponibili le estensioni come una raccolta privata. Per informazioni su come connettere il file atom.xml **estensioni e aggiornamenti**, vedere [Raccolte private](../extensibility/private-galleries.md).  
  
-   Una cartella che contiene i file di immagine che sono stati estratti dalle estensioni \(ad esempio schermate\). Il file atom.xml contiene collegamenti relativi a queste immagini in modo che siano disponibili in **estensioni e aggiornamenti**.  
  
 Si supponga, ad esempio, che sono state raccolte le seguenti estensioni in una cartella:  
  
-   Template\_Wizard\_239.VSIX, ovvero un modello di progetto VSIX vuoto.  
  
-   SelectionHighlight.vsix, uno strumento per evidenziare tutte le istanze di una parola selezionata.  
  
 Il contenuto del file atom.xml sarebbe simile all'esempio seguente:  
  
```  
  <?xml version="1.0" encoding="utf-8" ?> - <feed xmlns="http://www.w3.org/2005/Atom"> <title type="text" /> <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id> <updated>2011-04-14T21:25:48Z</updated> - <entry> <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id> <title type="text">Highlight all occurrences of selected word</title> <summary type="text">This extends the editor to highlight ….</summary> <published>2011-04-14T14:24:51-07:00</published> <updated>2011-04-14T14:24:22-07:00</updated> - <author> <name>Microsoft</name> </author> <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" /> <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" /> <content type="application/octet-stream" src="SelectionHighlight.vsix" /> - <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010"> <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id> <Version>1.31</Version> <References /> <Rating xsi:nil="true" /> <RatingCount xsi:nil="true" /> <DownloadCount xsi:nil="true" /> </Vsix> </entry> - <entry> <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id> … </entry> </feed>  
  
```  
  
 Si noti che i tag di collegamento di due riferiscano alle schermate nella cartella delle immagini generata.  
  
## Vedere anche  
 [Raccolte private](../extensibility/private-galleries.md)