---
title: Implementazione di colorazione della sintassi | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 67535bcc2c907978c24d764c617f8311dc51a444
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-syntax-coloring"></a>Implementazione di colorazione della sintassi
Quando il servizio di linguaggio fornisce la colorazione della sintassi, il parser converte una riga di testo in una matrice di colori e restituisce i tipi di token corrispondenti a questi elementi colorabili. Il parser deve restituire tipi di token che appartengono a un elenco di colori. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Visualizza ogni elemento colorabile predefinito nella finestra del codice in base agli attributi assegnati per l'oggetto di rappresentazione per il tipo di token appropriato.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]non specifica un'interfaccia, parser e implementazione del parser viene scelta dall'utente. Tuttavia, viene fornita un'implementazione di parser predefinita nel progetto di Visual Studio Language Pack. Per il codice gestito, il framework di pacchetto gestito (MPF) fornisce supporto completo per la colorazione del testo.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni sulla nuova modalità per implementare la colorazione della sintassi, vedere [procedura dettagliata: evidenziazione testo](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a utilizzare il nuovo editor API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Passaggi seguiti da un Editor per colorare il testo  
  
1.  L'editor Ottiene la rappresentazione mediante la chiamata di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>oggetto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>  
  
2.  Nell'editor viene chiamato il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>metodo per determinare se la rappresentazione richiede lo stato di ogni riga per essere gestite di fuori di rappresentazione.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>  
  
3.  Se la rappresentazione richiede lo stato per essere gestite di fuori di rappresentazione, l'editor chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>metodo per ottenere lo stato della prima riga.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>  
  
4.  Per ogni riga nel buffer, l'editor chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>metodo, che esegue i passaggi seguenti:</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>  
  
    1.  La riga di testo viene passata a uno scanner per convertire il testo in token. Ogni token specifica il testo del token e il tipo di token.  
  
    2.  Il tipo di token viene convertito in un indice in un elenco di colori.  
  
    3.  Le informazioni sul token viene utilizzati per compilare una matrice in modo che ogni elemento della matrice corrisponde a un carattere nella riga. I valori archiviati nella matrice sono gli indici nell'elenco di colori.  
  
    4.  Viene restituito lo stato alla fine della riga per ogni riga.  
  
5.  Se la rappresentazione richiede lo stato da mantenere, l'editor memorizza nella cache lo stato per la riga.  
  
6.  L'editor esegue il rendering della riga di testo utilizzando le informazioni restituite dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>(metodo).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> La procedura da adottare è la seguente:  
  
    1.  Per ogni carattere nella riga, ottenere l'indice dell'elemento colorabile.  
  
    2.  Se si utilizza gli elementi di colori predefiniti, accedere a elenco di colori dell'editor.  
  
    3.  In caso contrario, chiamare il servizio di linguaggio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>metodo per ottenere un elemento colorabile.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>  
  
    4.  Utilizzare le informazioni nell'elemento colorabile predefinito per il rendering del testo nella visualizzazione di.  
  
## <a name="managed-package-framework-colorizer"></a>Rappresentazione di Framework pacchetto gestito  
 Il framework di pacchetto gestito (MPF) fornisce tutte le classi necessarie per implementare una rappresentazione. La classe di servizio di linguaggio deve ereditare la <xref:Microsoft.VisualStudio.Package.LanguageService>classe e implementare i metodi richiesti.</xref:Microsoft.VisualStudio.Package.LanguageService> È necessario fornire un scanner e parser implementando il <xref:Microsoft.VisualStudio.Package.IScanner>interfaccia e restituire un'istanza di tale interfaccia dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>(metodo) (uno dei metodi che devono essere implementati nel <xref:Microsoft.VisualStudio.Package.LanguageService>(classe)).</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> </xref:Microsoft.VisualStudio.Package.IScanner> Per ulteriori informazioni, vedere [colorazione della sintassi in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: utilizzare gli elementi di colori predefiniti](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Elementi di colori personalizzati](../../extensibility/internals/custom-colorable-items.md)   
 [Sviluppo di un servizio di linguaggio Legacy](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Colorazione della sintassi in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
