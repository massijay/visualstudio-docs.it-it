---
title: Uso dei controlli HTML5 nei test codificati dell'interfaccia utente | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2000b214-ae92-4334-b549-aa0eb4f45fe1
caps.latest.revision: "17"
ms.author: douge
manager: douge
ms.openlocfilehash: 3e2e14748e27d965762b3245908382b278e6e132
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Uso dei controlli HTML5 nei test codificati dell'interfaccia utente
I test codificati dell'interfaccia utente includono il supporto per alcuni dei controlli HTML5 inclusi in Internet Explorer 9 e Internet Explorer 10.  
  
 **Requisiti**  
  
-   Visual Studio Enterprise  
  
> [!WARNING]
>  Nelle versioni precedenti a Internet Explorer 10, è possibile eseguire test codificati dell'interfaccia utente con un livello di privilegi più alto rispetto a quello del processo di Internet Explorer. Quando si eseguono test codificati dell'interfaccia utente in Internet Explorer 10, sia il test codificato dell'interfaccia utente che il processo di Internet Explorer devono avere lo stesso livello di privilegi. Infatti le funzionalità di AppContainer sono più sicure in Internet Explorer 10.  
  
> [!WARNING]
>  Un test codificato dell'interfaccia utente creato in Internet Explorer 10 potrebbe non funzionare in Internet Explorer 9 o Internet Explorer 8. Questo perché Internet Explorer 10 include controlli HTML5 come audio, video, ProgressBar e dispositivo di scorrimento. Questi controlli HTML5 non sono riconosciuti da Internet Explorer 9 o da Internet Explorer 8. Analogamente, il test codificato dell'interfaccia utente creato in Internet Explorer 9 potrebbe includere alcuni controlli HTML5 non riconosciuti in Internet Explorer 8.  
  
## <a name="supported-html5-controls"></a>Controlli HTML5 supportati  
 I test codificati dell'interfaccia utente includono il supporto per registrazione, riproduzione e convalida dei controlli HTML5 seguenti:  
  
-   [Controllo Audio](#UsingHTML5ControlsCodedUITestsAudio)  
  
-   [Controllo Video](#UsingHTML5ControlsCodedUITestsVideo)  
  
-   [Controllo Slider](#UsingHTML5ControlsCodedUITestsSlider)  
  
-   [Controllo ProgressBar](#UsingHTML5ControlsCodedUITestsProgressBar)  
  
###  <a name="UsingHTML5ControlsCodedUITestsAudio"></a> Controllo Audio  
 **Controllo Audio**: le azioni nel controllo Audio HTML5 vengono registrate e riprodotte correttamente.  
  
 ![Controllo Audio HTML5](../test/media/codedui_html5_audio.png "CodedUI_HTML5_Audio")  
  
|Azione|Registrazione|Codice generato|  
|------------|---------------|--------------------|  
|**Riprodurre audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Riprodurre audio \<nome> a partire dalla posizione 00:00:00|HtmlAudio.Play(TimeSpan)|  
|**Ricercare un punto specifico dell'audio**|Ricercare nell'audio \<nome> la posizione 00:01:48|HtmlAudio.Seek(TimeSpan)|  
|**Sospendere la riproduzione dell'audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Sospendere la riproduzione dell'audio \<nome> alla posizione 00:01:53|HtmlAudio.Pause(TimeSpan)|  
|**Disattivare il volume dell'audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Disattivare il volume dell'audio \<nome>|HtmlAudio.Mute()|  
|**Riattivare il volume dell'audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Riattivare il volume dell'audio \<nome>|HtmlAudio.Unmute()|  
|**Modificare il volume dell'audio**|Impostare il volume dell'audio \<nome> sul 79%|HtmlAudio.SetVolume(float)|  
  
 Le seguenti proprietà sono disponibili per HtmlAudio ed è possibile aggiungere un'asserzione in tutte:  
  
```  
string AutoPlay  
string Controls  
string CurrentSrc  
string CurrentTime  
string CurrentTimeAsString  
string Duration  
string DurationAsString  
string Ended  
string Loop  
string Muted  
string Paused  
string PlaybackRate  
string ReadyState  
string Seeking  
string Src  
string Volume  
  
```  
  
 **Proprietà di ricerca:** le proprietà di ricerca per `HtmlAudio` sono `Id`, `Name` e `Title`.  
  
 **Proprietà di filtro:** le proprietà di filtro per `HtmlAudio` sono `Src`, `Class`, `ControlDefinition` e `TagInstance`.  
  
> [!NOTE]
>  L'intervallo di tempo per la ricerca e la sospensione può essere significativo. Durante la riproduzione, il test codificato dell'interfaccia utente attenderà fino all'ora specificata in `(TimeSpan)` prima di sospendere l'audio. Se, in alcune circostanze speciali, l'ora specificata passa prima di fare clic sul comando Sospendi, verrà generata un'eccezione.  
  
###  <a name="UsingHTML5ControlsCodedUITestsVideo"></a> Controllo Video  
 **Controllo Video**: le azioni nel controllo Video HTML5 vengono registrate e riprodotte correttamente.  
  
 ![Controllo Video HTML5](../test/media/codedui_html5_video.png "CodedUI_HTML5_Video")  
  
|Azione|Registrazione|Codice generato|  
|------------|---------------|--------------------|  
|**Riprodurre video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Riprodurre il video \<nome> a partire dalla posizione 00:00:00|HtmlVideo.Play(TimeSpan)|  
|**Ricercare un punto specifico nel video**|Ricercare nel video \<nome> la posizione 00:01:48|HtmlVideo.Seek(TimeSpan)|  
|**Sospendere la riproduzione del video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Sospendere la riproduzione del video \<nome> alla posizione 00:01:53|HtmlVideo.Pause(TimeSpan)|  
|**Disattivare il volume del video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Disattivare il volume del video \<nome>|HtmlVideo.Mute()|  
|**Riattivare il volume del video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Riattivare il volume del video \<nome>|HtmlVideo.Unmute()|  
|**Modificare il volume del video**|Impostare il volume del video \<nome> sul 79%||  
  
 Tutte le proprietà di HtmlAudio sono disponibili per HtmlVideo. Inoltre, sono disponibili le seguenti tre proprietà. È possibile aggiungere un'asserzione in tutte.  
  
```  
string Poster  
string VideoHeight  
string VideoWidth  
  
```  
  
 **Proprietà di ricerca:** le proprietà di ricerca per `HtmlVideo` sono `Id`, `Name` e `Title`.  
  
 **Proprietà di filtro:** le proprietà di filtro per `HtmlVideo` sono `Src`, `Poster`, `Class`, `ControlDefinition` e `TagInstance`.  
  
> [!NOTE]
>  Se si riavvolge o si fa avanzare rapidamente il video usando le etichette -30s o +30s, il video verrà aggregato in modo da passare all'ora appropriata.  
  
###  <a name="UsingHTML5ControlsCodedUITestsSlider"></a> Controllo Slider  
 **Controllo Slider**: le azioni nel controllo Slider HTML5 vengono registrate e riprodotte correttamente.  
  
 ![Controllo Slider HTML5](../test/media/codedui_html5_slider.png "CodedUI_HTML5_Slider")  
  
|Azione|Registrazione|Codice generato|  
|------------|---------------|--------------------|  
|**Impostare una posizione nel dispositivo di scorrimento**|Impostare la posizione su \<x> nel dispositivo di scorrimento \<nome>|HtmlSlider.ValueAsNumber=\<x>|  
  
 Le seguenti proprietà sono disponibili per HtmlSlider ed è possibile aggiungere un'asserzione in tutte:  
  
```  
string Disabled  
string Max  
string Min  
string Required  
string Step  
string ValueAsNumber  
```  
  
###  <a name="UsingHTML5ControlsCodedUITestsProgressbar"></a> Controllo ProgressBar  
 **Controllo ProgressBar**:si tratta di un controllo con cui non si può interagire. È possibile aggiungere asserzioni nelle proprietà `Value` e `Max` di questo controllo.  
  
 ![Controllo ProgressBar HTML5](../test/media/codedui_html5_progressbar.png "CodedUI_HTML5_ProgressBar")  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi HTML](http://go.microsoft.com/fwlink/?LinkID=232441)   
 [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)   
 [Creazione di test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Personalizzazione del test codificato dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeCUITModify)   
 [Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
