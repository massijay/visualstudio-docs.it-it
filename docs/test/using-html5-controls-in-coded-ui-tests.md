---
title: "Utilizzo dei controlli HTML5 nei test codificati dell&#39;interfaccia utente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2000b214-ae92-4334-b549-aa0eb4f45fe1
caps.latest.revision: 17
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 17
---
# Utilizzo dei controlli HTML5 nei test codificati dell&#39;interfaccia utente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I test codificati dell'interfaccia utente includono il supporto per alcuni dei controlli HTML5 inclusi in Internet Explorer 9 e Internet Explorer 10.  
  
 **Requisiti**  
  
-   Visual Studio Enterprise  
  
> [!WARNING]
>  Nelle versioni precedenti a Internet Explorer 10, è possibile eseguire test codificati dell'interfaccia utente con un livello di privilegi più alto rispetto a quello del processo di Internet Explorer.  Quando si eseguono test codificati dell'interfaccia utente in Internet Explorer 10, sia il test codificato dell'interfaccia utente che il processo di Internet Explorer devono avere lo stesso livello di privilegi.  Infatti le funzionalità di AppContainer sono più sicure in Internet Explorer 10.  
  
> [!WARNING]
>  Un test codificato dell'interfaccia utente creato in Internet Explorer 10 potrebbe non funzionare in Internet Explorer 9 o Internet Explorer 8.  Questo perché Internet Explorer 10 include controlli HTML5 come audio, video, ProgressBar e dispositivo di scorrimento.  Questi controlli HTML5 non sono riconosciuti da Internet Explorer 9 o da Internet Explorer 8.  Analogamente, il test codificato dell'interfaccia utente creato in Internet Explorer 9 potrebbe includere alcuni controlli HTML5 non riconosciuti in Internet Explorer 8.  
  
## Controlli HTML5 supportati  
 I test codificati dell'interfaccia utente includono il supporto per registrazione, riproduzione e convalida dei controlli HTML5 seguenti:  
  
-   [Controllo audio](#UsingHTML5ControlsCodedUITestsAudio)  
  
-   [Controllo video](#UsingHTML5ControlsCodedUITestsVideo)  
  
-   [Dispositivo di scorrimento](#UsingHTML5ControlsCodedUITestsSlider)  
  
-   [ProgressBar](#UsingHTML5ControlsCodedUITestsProgressBar)  
  
###  <a name="UsingHTML5ControlsCodedUITestsAudio"></a> Controllo audio  
 **Controllo audio:** le azioni nel controllo audio HTML5 vengono correttamente registrate e riprodotte.  
  
 ![Controllo audio HTML5](../test/media/codedui_html5_audio.png "CodedUI\_HTML5\_Audio")  
  
|Azione|Registrazione|Codice generato|  
|------------|-------------------|---------------------|  
|**Riproduzione audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Riproduci audio \<nome\> da 00.00.00|HtmlAudio.Play\(TimeSpan\)|  
|**Spostamento a un'ora specifica nel file audio**|Cerca audio \<nome\> a 00.01.48|HtmlAudio.Seek\(TimeSpan\)|  
|**Sospensione audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Metti in pausa audio \<nome\> a 00.01.53|HtmlAudio.Pause\(TimeSpan\)|  
|**Disattivazione audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Disattiva audio \<nome\>|HtmlAudio.Mute\(\)|  
|**Riattivazione audio**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Riattiva audio \<nome\>|HtmlAudio.Unmute\(\)|  
|**Modifica volume audio**|Imposta il volume di audio \<nome\> al 79%|HtmlAudio.SetVolume\(float\)|  
  
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
  
 **Proprietà filtro:** le proprietà filtro per `HtmlAudio` sono `Src`, `Class` `ControlDefinition` e `TagInstance`.  
  
> [!NOTE]
>  L'intervallo di tempo per la ricerca e la sospensione può essere significativo.  Durante la riproduzione, il test codificato dell'interfaccia utente attenderà fino all'ora specificata in `(TimeSpan)` prima di sospendere l'audio.  Se, in alcune circostanze speciali, l'ora specificata passa prima di fare clic sul comando Sospendi, verrà generata un'eccezione.  
  
###  <a name="UsingHTML5ControlsCodedUITestsVideo"></a> Controllo video  
 **Controllo video:** le azioni nel controllo video HTML5 vengono correttamente registrate e riprodotte.  
  
 ![Controllo video HTML5](../test/media/codedui_html5_video.png "CodedUI\_HTML5\_Video")  
  
|Azione|Registrazione|Codice generato|  
|------------|-------------------|---------------------|  
|**Riproduzione video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Riproduci video \<nome\> da 00.00.00|HtmlVideo.Play\(TimeSpan\)|  
|**Spostamento a un'ora specifica nel file video**|Cerca video \<nome\> a 00.01.48|HtmlVideo.Seek\(TimeSpan\)|  
|**Sospensione video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Metti in pausa video \<nome\> a 00.01.53|HtmlVideo.Pause\(TimeSpan\)|  
|**Disattivazione video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Disattiva l'audio del video \<nome\>|HtmlVideo.Mute\(\)|  
|**Riattivazione video**<br /><br /> Direttamente dal controllo o dal menu di scelta rapida dei controlli.|Riattiva l'audio del video \<nome\>|HtmlVideo.Unmute\(\)|  
|**Modifica volume video**|Imposta il volume del video \<nome\> su 79%||  
  
 Tutte le proprietà di HtmlAudio sono disponibili per HtmlVideo.  Inoltre, sono disponibili le seguenti tre proprietà.  È possibile aggiungere un'asserzione in tutte.  
  
```  
string Poster  
string VideoHeight  
string VideoWidth  
  
```  
  
 **Proprietà di ricerca:** le proprietà di ricerca per `HtmlVideo` sono `Id`, `Name` e `Title`.  
  
 **Proprietà filtro:** le proprietà filtro per `HtmlVideo` sono `Src`, `Poster` `Class`, `ControlDefinition` e `TagInstance`.  
  
> [!NOTE]
>  Se si riavvolge o si fa avanzare rapidamente il video usando le etichette \-30s o \+30s, il video verrà aggregato in modo da passare all'ora appropriata.  
  
###  <a name="UsingHTML5ControlsCodedUITestsSlider"></a> Dispositivo di scorrimento  
 **Dispositivo di scorrimento:** le azioni nel dispositivo di scorrimento HTML5 vengono correttamente registrate e riprodotte.  
  
 ![Controllo dispositivo di scorrimento HTML5](../test/media/codedui_html5_slider.png "CodedUI\_HTML5\_Slider")  
  
|Azione|Registrazione|Codice generato|  
|------------|-------------------|---------------------|  
|**Impostazione di una posizione sul dispositivo di scorrimento**|Imposta la posizione su \<x\> nel dispositivo di scorrimento \<nome\>|HtmlSlider.ValueAsNumber\=\<x\>|  
  
 Le seguenti proprietà sono disponibili per HtmlSlider ed è possibile aggiungere un'asserzione in tutte:  
  
```  
string Disabled  
string Max  
string Min  
string Required  
string Step  
string ValueAsNumber  
```  
  
###  <a name="UsingHTML5ControlsCodedUITestsProgressbar"></a> ProgressBar  
 **Controllo ProgreesBar:** ProgressBar è un controllo con cui non si può interagire.  È possibile aggiungere asserzioni nelle proprietà `Value` e `Max` di questo controllo.  
  
 ![Controllo ProgressBar HTML5](../test/media/codedui_html5_progressbar.png "CodedUI\_HTML5\_ProgressBar")  
  
## Vedere anche  
 [Elementi HTML](http://go.microsoft.com/fwlink/?LinkID=232441)   
 [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)   
 [Creazione di test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Personalizzazione del test codificato dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeCUITModify)   
 [Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)