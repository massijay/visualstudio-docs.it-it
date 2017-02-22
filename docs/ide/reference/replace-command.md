---
title: "Comando Sostituisci | Microsoft Docs"
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
  - "edit.replace"
helpviewer_keywords: 
  - "Edit.Replace (comando)"
  - "Sostituisci (comando)"
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Sostituisci
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sostituisce il testo nei file utilizzando un sottoinsieme delle opzioni disponibili nella scheda **Sostituisci nei file** della finestra **Trova e sostituisci**.  
  
## Sintassi  
  
```  
Edit.Replace findwhat replacewith [/all] [/case]  
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]  
[/wild|/regex] [/word]  
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
  
 \/doc o \/d  
 Parametro facoltativo.  Effettua la ricerca soltanto nel documento corrente.  Specificare uno solo degli ambiti di ricerca disponibili:`/doc`, `/proc`, `/open` o `/sel`.  
  
 \/hidden o \/h  
 Parametro facoltativo.  Effettua la ricerca nel testo compresso e nascosto, ad esempio nei metadati di un controllo della fase di progettazione, in un'area nascosta di un documento strutturato oppure in classi o metodi compressi.  
  
 \/open o \/o  
 Parametro facoltativo.  Esegue la ricerca in tutti i documenti aperti come se costituissero un unico documento.  Specificare uno solo degli ambiti di ricerca disponibili:`/doc`, `/proc`, `/open` o `/sel`.  
  
 \/options o \/t  
 Parametro facoltativo.  Visualizza un elenco delle impostazioni correnti delle opzioni di ricerca e non effettua alcuna ricerca.  
  
 \/proc o \/p  
 Parametro facoltativo.  Effettua la ricerca soltanto nella routine corrente.  Specificare uno solo degli ambiti di ricerca disponibili:`/doc`, `/proc`, `/open` o `/sel`.  
  
 \/regex o \/r  
 Parametro facoltativo.  Utilizza caratteri speciali predefiniti nell'argomento `findwhat` come notazioni rappresentative di determinati criteri testuali anziché di caratteri effettivi.  Per un elenco completo dei caratteri delle espressioni regolari, vedere [Espressioni regolari](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 \/reset o \/e  
 Parametro facoltativo.  Ripristina le impostazioni predefinite delle opzioni di ricerca e non effettua alcuna ricerca.  
  
 \/sel o \/s  
 Parametro facoltativo.  Effettua la ricerca soltanto nella selezione corrente.  Specificare uno solo degli ambiti di ricerca disponibili:`/doc`, `/proc`, `/open` o `/sel`.  
  
 \/up o \/u  
 Parametro facoltativo.  Effettua la ricerca verso l'inizio del file, a partire dalla posizione corrente all'interno del file stesso.  Per impostazione predefinita, le ricerche vengono invece effettuate a partire dalla posizione corrente verso la fine del file.  
  
 \/wild o \/l  
 Parametro facoltativo.  Utilizza caratteri speciali predefiniti nell'argomento `findwhat` come notazioni rappresentative di un carattere o di una sequenza di caratteri.  
  
 \/word o \/w  
 Parametro facoltativo.  Cerca solo parole intere.  
  
## Esempio  
 Nell'esempio riportato di seguito `btnSend` viene sostituito con `btnSubmit` in tutti i documenti aperti.  
  
```  
>Edit.Replace btnSend btnSubmit /open  
```  
  
## Vedere anche  
 [Ricerca e sostituzione di testo](../../ide/finding-and-replacing-text.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)