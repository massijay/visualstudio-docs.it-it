---
title: "Comando Trova | Microsoft Docs"
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
  - "edit.find"
helpviewer_keywords: 
  - "Edit.Find (comando)"
  - "Trova (comando)"
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Trova
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

File di ricerche utilizzando un sottoinsieme delle opzioni disponibili nella scheda di **Cerca nei file** della finestra di **Trova e sostituisci** .  
  
## Sintassi  
  
```  
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]   
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]  
```  
  
## Argomenti  
 `findwhat`  
 Obbligatorio.  Il testo da ricercare.  
  
## Opzioni  
 \/case o \/c  
 Parametro facoltativo.  Le corrispondenze vengono rilevate solo se i caratteri in maiuscolo e minuscolo coincidono esattamente con quelli specificati nell'argomento `findwhat`.  
  
 \/doc o \/d  
 Parametro facoltativo.  Effettua la ricerca soltanto nel documento corrente.  Specificare uno solo degli ambiti di ricerca disponibili:`/doc`, `/proc`, `/open` o `/sel`.  
  
 \/markall o \/m  
 Parametro facoltativo.  Viene inserito un elemento grafico su ciascuna riga in cui è stata trovata un'occorrenza all'interno del documento corrente.  
  
 \/open o \/o  
 Parametro facoltativo.  Esegue la ricerca in tutti i documenti aperti come se costituissero un unico documento.  Specificare uno solo degli ambiti di ricerca disponibili:`/doc`, `/proc`, `/open` o `/sel`.  
  
 \/options o \/t  
 Parametro facoltativo.  Visualizza un elenco delle impostazioni correnti delle opzioni di ricerca e non effettua alcuna ricerca.  
  
 \/proc o \/p  
 Parametro facoltativo.  Effettua la ricerca soltanto nella routine corrente.  Specificare uno solo degli ambiti di ricerca disponibili:`/doc`, `/proc`, `/open` o `/sel`.  
  
 \/reset o \/e  
 Parametro facoltativo.  Ripristina le impostazioni predefinite delle opzioni di ricerca e non effettua alcuna ricerca.  
  
 \/sel o \/s  
 Parametro facoltativo.  Effettua la ricerca soltanto nella selezione corrente.  Specificare uno solo degli ambiti di ricerca disponibili:`/doc`, `/proc`, `/open` o `/sel`.  
  
 \/up o \/u  
 Parametro facoltativo.  Effettua la ricerca verso l'inizio del file, a partire dalla posizione corrente all'interno del file stesso.  Per impostazione predefinita, le ricerche vengono invece effettuate a partire dalla posizione corrente verso la fine del file.  
  
 \/regex o \/r  
 Parametro facoltativo.  Utilizza caratteri speciali predefiniti nell'argomento `findwhat` come notazioni rappresentative di determinati criteri testuali anziché di caratteri effettivi.  Per un elenco completo dei caratteri delle espressioni regolari, vedere [Espressioni regolari](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 \/wild o \/l  
 Parametro facoltativo.  Utilizza caratteri speciali predefiniti nell'argomento `findwhat` come notazioni rappresentative di un carattere o di una sequenza di caratteri.  
  
 \/word o \/w  
 Parametro facoltativo.  Cerca solo parole intere.  
  
## Esempio  
 Nell'esempio seguente viene cercata la parola "somestring", con distinzione di maiuscole e minuscole, all'interno della sezione di codice selezionata.  
  
```  
>Edit.Find somestring /sel /case  
```  
  
## Vedere anche  
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)