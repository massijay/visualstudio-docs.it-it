---
title: "Utilizzo di risorse tridimensionali per giochi e app | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.graphics"
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
caps.latest.revision: 24
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 24
---
# Utilizzo di risorse tridimensionali per giochi e app
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo documento vengono descritti gli strumenti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che è possibile utilizzare per creare o modificare modelli 3D, trame e shader per i giochi e le app basati su DirectX.  
  
## Sviluppo dell'applicazione DirectX in Visual Studio  
 Un'applicazione DirectX in genere combina la logica di programma, l'API DirectX e i programmi HLSL insieme agli asset audio e visivi tridimensionali per presentare un'esperienza multimediale interattiva e complessa.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] include gli strumenti da utilizzare con immagini e trame, modelli 3D e shader senza lasciare che venga utilizzato un altro strumento dall'IDE.  Gli strumenti di Visual Studio sono particolarmente adatti per creare risorse *segnaposto*, che possono essere utilizzate per eseguire i test sul codice o sui prototipi di build prima di incaricare le risorse pronte alla produzione e per verificare e modificare le risorse pronte alla produzione durante il debug dell'app.  
  
 Di seguito vengono riportate maggiori informazioni sui tipi di asset che è possibile utilizzare in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### Immagini e trame  
 Immagini e trame forniscono il colore e il dettaglio visivo in giochi e app.  Nella grafica tridimensionale, le trame sono disponibili in diversi formati, tipi e geometrie per supportare utilizzi diversi.  Ad esempio, i mapping normali forniscono normali alla superficie per pixel per un'illuminazione più dettagliata dei modelli tridimensionali e i mapping del cubo forniscono la trama in tutte le direzioni per utilizzi come lo sky\-boxing, la reflection e il mapping a trama sferica.  Le trame possono produrre mappe MIP per supportare il rendering efficiente a livelli di dettaglio diversi e può supportare canali di colore e ordinamenti di colore diversi.  Le trame possono essere archiviate in diversi formati compressi che occupano meno memoria grafica dedicata e consentono alle GPU di accedere alle trame in modo più efficiente.  
  
 È possibile utilizzare l'editor di immagini [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizzare le immagini e le trame in molti tipi e formati comuni.  
  
### Modelli 3D  
 I modelli tridimensionali creano lo spazio e la forma nei giochi e nelle applicazioni.  Come minimo, nei modelli viene codificata la posizione dei punti nello spazio 3D, noti come *vertici*, insieme ai dati di indicizzazione per definire le righe o i triangoli che rappresentano la forma del modello.  È possibile associare i dati aggiuntivi a tali vertici \(ad esempio le informazioni sui colori, i vettori delle normali, o gli attributi specifici dell'applicazione\).  Ogni modello può inoltre definire gli attributi a livello di oggetto \(ad esempio, quale shader viene utilizzato per calcolare l'aspetto della superficie dell'oggetto, o che trama è applicata\).  
  
 È possibile utilizzare l'editor di modelli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per utilizzare i modelli 3D in diversi formati comuni.  
  
### Shader  
 Gli shader sono piccoli programmi specifici di dominio eseguiti nella GPU.  Gli shader determinano quali modelli tridimensionali vengono trasformati nelle forme sullo schermo e come ogni pixel in quelli forme è colorato.  Creando uno shader e applicandolo a un oggetto nel gioco o nell'applicazione, è possibile assegnare all'oggetto un aspetto univoco.  
  
 È possibile utilizzare la finestra di progettazione di shader [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], che è uno strumento di progettazione basato su grafico di shader, per creare effetti visivi personalizzati senza conoscere la programmazione di HLSL.  
  
> [!NOTE]
>  Per ulteriori informazioni su come iniziare a programmare con le DirectX, vedere [DirectX](http://go.microsoft.com/fwlink/p/?LinkId=224633).  Per ulteriori informazioni sul debug di un'applicazione basata su DirectX, vedere [Diagnostica grafica \(Debug grafica DirectX\)](../debugger/visual-studio-graphics-diagnostics.md).  
  
## Compatibilità tra versioni DirectX  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizza DirectX per eseguire il rendering delle risorse 2D e 3D.  È possibile selezionare il renderer di DirectX 11 o il renderer di software WARP.  Il renderer di DirectX 11 offre un rendering a elevate prestazioni e con accelerazione hardware nelle GPU DirectX 11 e DirectX 10.  Il renderer WARP consente di assicurarsi che le risorse funzionino con un'ampia gamma di computer, inclusi quelli che non sono dotati di hardware moderno per la grafica e quelli che sono dotati di hardware per la grafica integrato.  Per ulteriori informazioni su WARP, vedere la pagina relativa alla [Guida per la piattaforma avanzata \(WARP\) di Rasterizzazione](http://go.microsoft.com/fwlink/p/?LinkId=224634).  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Uso di trame e immagini](../designers/working-with-textures-and-images.md)|Viene descritto come utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per utilizzare le immagini e le trame.|  
|[Utilizzo dei modelli tridimensionali](../designers/working-with-3-d-models.md)|Viene descritto come utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per utilizzare i modelli tridimensionali.|  
|[Utilizzo degli shader](../designers/working-with-shaders.md)|Viene descritto come utilizzare la finestra di Progettazione shader di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per la creazione e la modifica degli effetto dello shader personalizzati.|  
|[Utilizzo delle risorse tridimensionali nel gioco o nell'app](../designers/using-3-d-assets-in-your-game-or-app.md)|Viene descritto come utilizzare le risorse create tramite l'editor immagini, l'editor di modello, o la finestra di progettazione shader nel gioco o nell'applicazione.|