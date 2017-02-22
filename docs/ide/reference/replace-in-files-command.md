---
title: "Comando Sostituisci nei file | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.replaceinfiles"
helpviewer_keywords: 
  - "Edit.ReplaceInFiles (comando)"
  - "Sostituisci nei file (comando)"
  - "ReplaceInFiles (comando)"
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Sostituisci nei file
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sostituisce il testo nei file utilizzando un sottoinsieme delle opzioni disponibili nella scheda **Sostituisci nei file** della finestra **Trova e sostituisci**.  
  
## Sintassi  
  
```  
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]  
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]  
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]  
```  
  
## Argomenti  
 `findwhat`  
 Obbligatorio.  Il testo da ricercare.  
  
 `replacewith`  
 Obbligatorio.  Il testo da immettere in sostituzione del testo ricercato.  
  
## Opzioni  
 \/all o \/a  
 Parametro facoltativo.  Sostituisce tutte le occorrenze del testo cercato con il testo sostitutivo.  
  
 \/case o \/c  
 Parametro facoltativo.  Vengono rilevate corrispondenze solo se i caratteri in maiuscolo e minuscolo coincidono esattamente con quelli specificati nell'argomento `findwhat`.  
  
 \/ext: `extensions`  
 Parametro facoltativo.  Specifica le estensioni di file in cui deve essere effettuata la ricerca.  
  
 \/keep o \/k  
 Parametro facoltativo.  Specifica che tutti i file modificati devono essere lasciati aperti.  
  
 \/lookin: `searchpath`  
 Parametro facoltativo.  La directory in cui deve essere effettuata la ricerca.  Se contiene degli spazi, l'intero percorso deve essere racchiuso tra virgolette.  
  
 \/options o \/t  
 Parametro facoltativo.  Visualizza un elenco delle impostazioni correnti delle opzioni di ricerca e non effettua alcuna ricerca.  
  
 \/regex o \/r  
 Parametro facoltativo.  Utilizza caratteri speciali predefiniti nell'argomento `findwhat` come notazioni rappresentative di determinati criteri testuali anziché di caratteri effettivi.  Per un elenco completo dei caratteri delle espressioni regolari, vedere [Espressioni regolari](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 \/reset o \/e  
 Parametro facoltativo.  Ripristina le impostazioni predefinite delle opzioni di ricerca e non effettua alcuna ricerca.  
  
 \/stop  
 Parametro facoltativo.  Interrompe l'operazione di ricerca corrente eventualmente in corso.  Quando viene specificato `/stop` , durante la sostituzione vengono ignorati tutti gli altri argomenti.  Se ad esempio si desidera interrompere la sostituzione corrente, immettere quanto segue:  
  
```  
>Edit.ReplaceinFiles /stop  
```  
  
 \/sub o \/s  
 Parametro facoltativo.  Effettua la ricerca nelle sottocartelle incluse nella directory specificata nell'argomento \/lookin:`searchpath`.  
  
 \/text2 o \/2  
 Parametro facoltativo.  Visualizza i risultati della sostituzione nella finestra **Risultati ricerca 2**.  
  
 \/wild o \/l  
 Parametro facoltativo.  Utilizza caratteri speciali predefiniti nell'argomento `findwhat` come notazioni rappresentative di un carattere o di una sequenza di caratteri.  
  
 \/word o \/w  
 Parametro facoltativo.  Cerca solo parole intere.  
  
## Esempio  
 Nell'esempio riportato di seguito viene cercato `btnCancel` e sostituito con `btnReset` in tutti i file CLS presenti nella cartella "My Visual Studio Projects", quindi le informazioni relative alla sostituzione vengono visualizzate nella finestra **Risultati ricerca 2**.  
  
```  
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2  
```  
  
## Vedere anche  
 [Ricerca e sostituzione di testo](../../ide/finding-and-replacing-text.md)   
 [Sostituisci nei file](../../ide/replace-in-files.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)