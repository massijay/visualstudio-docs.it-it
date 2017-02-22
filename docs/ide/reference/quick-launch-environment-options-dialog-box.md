---
title: "Avvio veloce, Ambiente, finestra di dialogo Opzioni | Microsoft Docs"
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
  - "VS.ToolsOptionsPages.Environment.QuickLaunch"
  - "vs.quicklaunch"
helpviewer_keywords: 
  - "ricerca di IDE"
  - "IDE, ricerca"
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Avvio veloce, Ambiente, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

È possibile usare la casella **Avvio veloce** per cercare ed eseguire rapidamente azioni per risorse IDE come opzioni, modelli e menu.  Non è possibile usare la casella **Avvio veloce** per cercare codice e simboli.  La casella di ricerca **Avvio veloce** si trova nell'angolo superiore destro della barra dei menu ed è possibile accedervi premendo CTRL\+Q.  È sufficiente immettere la stringa di ricerca nella casella.  Per cercare stringhe contenenti @, usare "@@".  
  
 La casella **Avvio veloce** è abilitata per impostazione predefinita quando si installa Visual Studio.  Sulla barra dei menu è possibile mostrare o nascondere la casella **Avvio veloce** scegliendo **Strumenti**, **Opzioni**.  Espandere il nodo **Ambienti** e quindi scegliere **Avvio veloce**.  Selezionare o deselezionare la casella di controllo **Abilita avvio veloce**.  In questa pagina è anche possibile abilitare o disabilitare le categorie di ricerca.  
  
## Elenco di categorie  
 I risultati delle ricerche effettuate in Avvio veloce vengono visualizzati in quattro categorie: **Usati di recente**, **Menu**, **Opzioni** e **Documenti aperti**, con un'indicazione del numero di elementi in ogni categoria.  Per scorrere i risultati della ricerca per categoria, premere CTRL\+Q per mostrare tutti i risultati della categoria successiva.  Dopo che viene visualizzata l'ultima categoria, premendo CTRL\+Q è possibile visualizzare alcuni risultati di ogni categoria.  È possibile usare CTRL\+MAIUSC\+Q per spostarsi tra le categorie in ordine inverso.  Per visualizzare tutti i risultati della ricerca in una categoria, scegliere il nome della categoria.  
  
 È possibile usare i metodi rapidi seguenti per limitare la ricerca a categorie specifiche.  
  
|Categoria|Metodo rapido|Descrizione metodo rapido|  
|---------------|-------------------|-------------------------------|  
|Usati di recente|@mru<br /><br /> Ad esempio, `@mru carattere`|Mostra fino a cinque elementi **Usati di recente**.|  
|Menu|@menu<br /><br /> Ad esempio, `@menu carattere`|Limita la ricerca alle voci di menu.|  
|Opzioni|@opt<br /><br /> Ad esempio, `@opt carattere`|Limita la ricerca alle impostazioni nella finestra di dialogo **Opzioni**.|  
|Documenti|@doc<br /><br /> Ad esempio, `@doc carattere`|Limita la ricerca ai percorsi e ai nomi di file dei documenti aperti per i criteri di ricerca, ma non esegue la ricerca nel testo all'interno dei file.|  
  
> [!NOTE]
>  È possibile modificare i tasti di scelta rapida nella pagina **Generale**, **Tastiera** nella finestra di dialogo **Opzioni**.  
  
## Visualizzare i risultati precedenti  
 Per impostazione predefinita, il termine di ricerca immesso non viene mantenuto tra sessioni di ricerca.  La stringa di ricerca viene cancellata se si cerca un termine, si sposta il cursore all'esterno dell'area **Avvio veloce** e quindi si torna nell'area.  Per mantenere i risultati della ricerca, passare alla finestra di dialogo **Opzioni**, scegliere **Avvio veloce** e quindi selezionare la casella di controllo **Mostra risultati della ricerca precedente quando viene attivato Avvio veloce**.  In seguito, se si esegue una ricerca, si esce dall'area Avvio veloce e si torna nell'aera, verrà mantenuto il termine di ricerca usato per ultimo e verranno inoltre visualizzati i risultati della ricerca.  
  
 Per i più recenti suggerimenti e consigli in relazione all'uso della casella **Avvio veloce**, vedere il [blog di Visual Studio](http://go.microsoft.com/fwlink/?LinkId=236054).  
  
## Vedere anche  
 [Elementi generali dell'interfaccia utente \(Visual Studio\)](../../ide/reference/general-user-interface-elements-visual-studio.md)   
 [Finestra di dialogo Opzioni ambiente](../../ide/reference/environment-options-dialog-box.md)