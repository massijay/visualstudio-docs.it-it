---
title: "Comando Alias | Microsoft Docs"
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
  - "tools.alias"
helpviewer_keywords: 
  - "alias (comando)"
  - "alias, comandi di Visual Studio"
  - "alias di comandi"
  - "comandi, alias"
  - "Tools.Alias (comando)"
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Alias
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Crea un nuovo alias per un comando completo, per un comando completo con i relativi argomenti oppure per un altro alias.  
  
> [!TIP]
>  Se si digita `>alias` senza specificare alcun argomento, verrà visualizzato l'elenco corrente degli alias e delle relative definizioni.  
  
## Sintassi  
  
```  
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]  
```  
  
## Argomenti  
 `aliasname`  
 Parametro facoltativo.  Il nome del nuovo alias.  Se per `aliasname` non viene specificato alcun valore, verrà visualizzato un elenco degli alias correnti e delle relative definizioni.  
  
 `aliasstring`  
 Parametro facoltativo.  Il nome completo del comando o l'alias esistente, nonché qualsiasi parametro per cui si desidera creare un alias.  Se per `aliasstring` non viene specificato alcun valore, verranno visualizzati il nome e la stringa dell'alias specificato.  
  
## Opzioni  
 \/delete o \/del o \/d  
 Parametro facoltativo.  Elimina l'alias specificato, che viene rimosso dal completamento automatico.  
  
 \/reset  
 Parametro facoltativo.  Ripristina le impostazioni originali dell'elenco di alias predefiniti.  In altre parole, ripristina tutti gli alias predefiniti e rimuove quelli definiti dall'utente.  
  
## Note  
 Poiché rappresentano comandi, gli alias devono essere immessi all'inizio della riga di comando.  
  
 Quando si esegue questo comando, le opzioni devono essere collocate immediatamente dopo il comando e non dopo gli alias, altrimenti l'opzione stessa diventa parte integrante della stringa dell'alias.  
  
 Prima del ripristino degli alias con l'opzione `/reset`, viene chiesto di confermare l'operazione.  Non esiste una forma abbreviata di `/reset`.  
  
## Esempi  
 Nell'esempio che segue viene creato un nuovo alias, `upper`, per il comando completo Edit.MakeUpperCase.  
  
```  
>Tools.Alias upper Edit.MakeUpperCase  
```  
  
 Nell'esempio seguente viene eliminato l'alias `upper`.  
  
```  
>Tools.alias /delete upper  
```  
  
 In quest'ultimo esempio viene visualizzato un elenco degli alias correnti e delle relative definizioni.  
  
```  
>Tools.Alias  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)