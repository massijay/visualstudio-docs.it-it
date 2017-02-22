---
title: "Modifica di fogli di stile XSLT | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Modifica di fogli di stile XSLT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'editor XML consente anche di modificare i fogli di stile XSLT.È possibile utilizzare le funzionalità predefinite dell'editor, quali IntelliSense, struttura, frammenti XML e così via.Sono inoltre disponibili nuove funzionalità che semplificano lo sviluppo in XSLT.  
  
## Funzionalità XSLT  
 Nella tabella seguente vengono descritte le funzionalità specifiche per utilizzare i fogli di stile XSLT.  
  
 **Colorazione della sintassi**  
 Le parole chiave XSLT, quali `template`, `match` e così via, vengono visualizzate nel colore della parola chiave XSLT specificato nelle impostazioni **Tipi di carattere e colori**.  
  
 **Sottolineatura ondulata**  
 L'editor XML utilizza il file xslt.xsd installato per convalidare i fogli di stile XSLT.Gli errori di convalida vengono visualizzati con una sottolineatura ondulata di colore blu.L'editor XML compila inoltre il foglio di stile in background e segnala gli errori del compilatore o avvisi con le opportune sottolineature ondulate.  
  
 **Supporto per i blocchi di script**  
 Il codice nei blocchi di script è supportato dal debugger XSLT, consentendo di impostare punti di interruzione e di eseguire il codice del blocco di script.  
  
 **Visualizzazione dell'output XSLT**  
 È possibile eseguire una trasformazione XSL e visualizzare l'output dall'editor XML.Per ulteriori informazioni, vedere [Procedura: eseguire una trasformazione XSLT dall'editor XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).  
  
 **Debug XSLT**  
 È possibile avviare il debugger XSLT da un file XSLT nell'editor XML.Il debugger supporta l'impostazione dei punti di interruzione nel file XSLT, la visualizzazione dello stato di esecuzione di XSLT e così via.Se si passa con il mouse su una variabile XSLT, viene visualizzata una descrizione con il valore della matrice.Il debugger può essere utilizzato per eseguire il debug di un foglio di stile o di una trasformazione XSLT chiamata da un'altra applicazione.Per ulteriori informazioni, vedere [Debug di XSLT](../xml-tools/debugging-xslt.md).  
  
## Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)