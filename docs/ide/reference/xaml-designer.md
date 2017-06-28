---
title: Pagina delle opzioni della finestra di progettazione XAML | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.XAMLDesigner
ms.assetid: ad3820b2-0d95-4807-a75c-c3467ed973a3
caps.latest.revision: 1
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: d23a47b708754248cd5c3fb8d86510a0c96491fa
ms.lasthandoff: 03/07/2017

---
# <a name="xaml-designer-options-page"></a>Pagina delle opzioni della finestra di progettazione XAML
Usare la pagina delle opzioni della **finestra di progettazione XAML** per specificare le modalità di formattazione di elementi e attributi nei documenti XAML. Per aprire questa pagina, scegliere **Opzioni** dal menu **Strumenti**. Per accedere alla pagina delle proprietà della **finestra di progettazione XAML**, scegliere il nodo **Finestra di progettazione XAML**. Le impostazioni della finestra di progettazione XAML vengono applicate quando si apre il documento. Quindi, se si apportano modifiche alle impostazioni, è necessario chiudere e riaprire Visual Studio per visualizzare le modifiche.

> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  

## <a name="enable-xaml-designer"></a>Abilita finestra di progettazione XAML
Se selezionata, questa impostazione consente di abilitare la finestra di progettazione XAML. La finestra di progettazione XAML offre un'area di lavoro visiva in cui è possibile modificare i documenti XAML. Alcune funzionalità di Visual Studio, ad esempio IntelliSense per le risorse e il data binding, richiedono l'abilitazione della finestra di progettazione XAML.

Le impostazioni seguenti sono valide solo se è abilitata la finestra di progettazione XAML. Se si modifica questa opzione, sarà necessario riavviare Visual Studio affinché l'impostazione abbia effetto.

## <a name="default-document-view"></a>Visualizzazione documento predefinita
Usare questa impostazione per verificare se la visualizzazione Progettazione appare quando vengono caricati documenti XAML.

|||  
|-|-|  
|**Visualizzazione Origine**|Specifica se viene visualizzata solo l'origine XAML nella visualizzazione XAML. L'impostazione è utile quando si caricano documenti di grandi dimensioni.|  
|**Visualizzazione Progettazione**|Specifica se deve apparire solo una finestra di progettazione XAML visiva nella visualizzazione XAML.|  
|**Doppia visualizzazione**|Specifica se sia la finestra di progettazione XAML visiva che l'origine XAML devono apparire l'una accanto all'altra nella visualizzazione XAML (percorso basato sull'impostazione **Orientamento divisione**).|  

## <a name="split-orientation"></a>Orientamento divisione
Usare questa impostazione per stabilire come e quando viene visualizzata la finestra di progettazione XAML quando si modifica un documento XAML. Queste impostazioni si applicano solo quando **Visualizzazione documento predefinita** è impostata su **Doppia visualizzazione**.

|||  
|-|-|  
|**Verticale**|L'origine XAML viene visualizzata sul lato sinistro della visualizzazione XAML e la finestra di progettazione XAML viene visualizzata sull'altro lato.|  
|**Orizzontale**|La finestra di progettazione XAML viene visualizzata nella parte superiore della visualizzazione XAML e l'origine XAML viene visualizzata sotto di essa.|  
|**Default**|Il documento XAML usa l'orientamento di divisione consigliato per la piattaforma di destinazione dal progetto del documento. Per la maggior parte delle piattaforme equivale a **Orizzontale**.|  

## <a name="zoom-by-using"></a>Zoom mediante
Usare questa impostazione per determinare il funzionamento dello zoom quando si modifica un documento XAML.

|||  
|-|-|  
|**Rotellina del mouse**|Fare zoom avanti nella finestra di progettazione XAML usando lo scorrimento della rotellina del mouse.|  
|**CTRL + rotellina del mouse**|Fare zoom avanti nella finestra di progettazione XAML premendo il tasto CTRL mentre si fa scorrere la rotellina del mouse.|  
|**ALT + rotellina del mouse**|Fare zoom avanti nella finestra di progettazione XAML premendo il tasto ALT mentre si fa scorrere la rotellina del mouse.|  

Queste impostazioni determinano il comportamento della finestra di progettazione quando si modifica un documento XAML.

|||  
|-|-|  
|**Assegna automaticamente un nome agli elementi interattivi durante la creazione**|Specifica se viene indicato un nome predefinito per un nuovo elemento interattivo quando se ne aggiunge uno alla finestra di progettazione.|  
|**Inserisci automaticamente le proprietà del layout durante la creazione degli elementi**|Specifica se vengono indicate le proprietà del layout per un nuovo elemento quando se ne aggiunge uno alla finestra di progettazione.|  
|**Usa layout basato su quadranti**|Specifica se il controllo attualmente selezionato deve essere allineato ai bordi più vicini del contenitore padre. Se questa casella di controllo è deselezionata, gli allineamenti dei controlli non cambiano durante un'operazione di spostamento o creazione.|  
|**Inserisci automaticamente elementi della casella degli strumenti**|Specifica se i controlli utente e i controlli personalizzati della soluzione corrente vengono visualizzati automaticamente nella casella degli strumenti.|  

## <a name="settings-blend-only"></a>Impostazioni (solo Blend)
Usare queste opzioni per determinare le impostazioni quando si modificano i file XAML con Blend.

|||  
|-|-|  
|**Zoom mediante**|Fare zoom avanti nella finestra di progettazione XAML scorrendo la rotellina del mouse o premendo il tasto CTRL o ALT mentre si fa scorrere la rotellina del mouse.|  
|**Digitare unità**|Specifica se le misurazioni nella finestra di progettazione sono basate su punti o pixel. Poiché le app di Windows universale non supportano i punti, le unità vengono automaticamente convertite in pixel se **Punti** è selezionata.|  

## <a name="artboard-blend-only"></a>Tavola da disegno (solo Blend)
Usare queste impostazioni per determinare il comportamento della finestra di progettazione XAML durante la modifica di documenti XAML in Blend.

### <a name="snapping"></a>Snapping

|||  
|-|-|  
|**Mostra griglia di allineamento**|Quando questa opzione è selezionata, le linee della griglia vengono visualizzate nella finestra di progettazione per consentire l'allineamento dei controlli. I controlli aggiunti alla finestra di progettazione vengono bloccati sulle linee della griglia se l'opzione **Blocca sulla griglia** è selezionata.|  
|**Blocca sulla griglia**|Quando i controlli vengono aggiunti o spostati nella finestra di progettazione vengono bloccati sulla griglia.|  
|**Spaziatura griglia**|Specifica la spaziatura tra le linee della griglia in pixel o punti (in base all'impostazione **Digitare unità**).|  
|**Blocca sulle guide di allineamento**|Specifica se i controlli vengono bloccati sulle guide di allineamento.|  
|**Margine predefinito**|Quando l'opzione **Blocca sulle guide di allineamento** è abilitata, specifica la spaziatura tra il controllo e le guide di allineamento in pixel o punti (in base all'impostazione **Digitare unità**).|  
|**Spaziatura interna predefinita**|Quando l'opzione **Blocca sulle guide di allineamento** è abilitata, specifica la spaziatura aggiuntiva tra il controllo e le guide di allineamento in pixel o punti (in base all'impostazione **Digitare unità**).|  

### <a name="animation"></a>Animazione
Usare questa impostazione per determinare se viene visualizzato un avviso quando vengono abilitate animazioni dipendenti (non accelerate) in Blend.

### <a name="effects"></a>Effetti
Usare queste impostazioni per determinare se viene eseguito il rendering degli effetti quando si modificano i file XAML nella finestra di progettazione XAML usando Blend.

|||  
|-|-|  
|**Rendering effetti**|Specifica se viene eseguito il rendering degli effetti quando si modificano i file XAML nella finestra di progettazione XAML usando Blend.|  
|**Soglia zoom**|Specifica la percentuale di zoom con cui viene eseguito il rendering degli effetti quando la casella di controllo **Rendering effetti** è selezionata. Se si ingrandisce oltre questa impostazione, non viene più eseguito il rendering degli effetti nella finestra di progettazione XAML.|  

## <a name="see-also"></a>Vedere anche  
 [XAML in WPF](http://msdn.microsoft.com/Library/5d858575-a83b-42df-ad3f-047ed2d6e3c8)   
 [Procedura: Modificare le impostazioni di visualizzazione XAML](http://msdn.microsoft.com/en-us/aee87c79-ca01-4f84-8fb7-a9e47048ee47)   
 [Procedure dettagliate relative all'uso di XAML e del codice](http://msdn.microsoft.com/en-us/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)
