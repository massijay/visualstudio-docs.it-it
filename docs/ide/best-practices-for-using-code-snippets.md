---
title: Procedure consigliate per l&quot;uso dei frammenti di codice | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
ms.assetid: a293ec17-4dd7-4a99-8eeb-99f44a822a8b
caps.latest.revision: 22
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 954bd5e0ba38d7a538700cba175933cc8303c863
ms.lasthandoff: 02/22/2017

---
# <a name="best-practices-for-using-code-snippets"></a>Procedure consigliate per l'utilizzo dei frammenti di codice
Il codice in un frammento illustra solo il modo più semplice per eseguire un'operazione. Per la maggior parte delle applicazioni, il codice deve essere modificato per essere adattato all'applicazione.  
  
## <a name="handling-exceptions"></a>Gestione delle eccezioni  
 In genere, i blocchi Try... Catch dei frammenti di codice raccolgono e rigenerano tutte le eccezioni. Questo comportamento potrebbe anche non essere idoneo al progetto in uso. Per ogni eccezione, esistono infatti modi diversi di rispondere. Vedere ad esempio [Procedura: Gestire un'eccezione usando Try/Catch (Guida per programmatori C#)](http://msdn.microsoft.com/Library/ca8e3773-980e-4767-8633-7408540e9818) e [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) (Istruzione Try...Catch...Finally).  
  
## <a name="file-locations"></a>Percorsi dei file  
 Quando i percorsi dei file vengono adattati all'applicazione, considerare quanto segue:  
  
-   Ricerca di una posizione accessibile. È possibile che gli utenti non accedano alla cartella Programmi del computer. Archiviare i file insieme ai file dell'applicazione potrebbe non essere la scelta corretta.  
  
-   Ricerca di una posizione sicura. Non è sicuro archiviare i il file nella cartella radice (C:\\). Per i dati dell'applicazione, è consigliabile scegliere la cartella \Dati applicazioni. Per i singoli dati utente, l'applicazione può creare un file per ogni utente nella cartella Documenti.  
  
-   Uso di un nome di file valido. È possibile usare i comandi <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> per ridurre la probabilità di usare nomi di file non validi. Tenere presente che tra il momento in cui l'utente seleziona un file e il momento in cui il codice lo modifica, il file potrebbe essere eliminato. Può anche succedere che l'utente non abbia le autorizzazioni per scrivere il file.  
  
## <a name="security"></a>Sicurezza  
 In base a dove un frammento viene usato nel codice sorgente e a come viene modificato all'interno del codice, il livello di protezione cambia. Di seguito sono elencati alcuni aspetti da considerare.  
  
-   Accesso a file e database  
  
-   Sicurezza dall'accesso di codice  
  
-   Protezione delle risorse, ad esempio dei registri eventi e del Registro di sistema  
  
-   Archiviazione dei segreti  
  
-   Verifica degli input  
  
-   Passaggio dei dati a tecnologie script  
  
 Per altre informazioni, vedere [Securing Applications](../ide/securing-applications.md) (Protezione delle applicazioni).  
  
## <a name="downloaded-code-snippets"></a>Frammenti di codice scaricati  
 I frammenti di codice IntelliSense installati da Visual Studio non rappresentano di per sé un pericolo. Possono tuttavia mettere a rischio la sicurezza dell'applicazione. È necessario trattare i frammenti di codice scaricati da Internet con estrema cautela, come si è soliti fare per qualsiasi altro contenuto scaricato.  
  
-   È consigliabile scaricare i frammenti di codice solo da siti attendibili e usare un software antivirus aggiornato.  
  
-   Aprire tutti i file di frammenti scaricati in Blocco note o nell'editor XML di Visual Studio e analizzarli con attenzione prima di installarli. Considerare le problematiche seguenti:  
  
    -   Se eseguito, il frammento di codice potrebbe danneggiare il sistema. Leggere attentamente il codice sorgente prima di eseguirlo.  
  
    -   Il blocco URL Guida del file di frammento può contenere URL che eseguono file di script dannosi o visualizzano un sito Web offensivo.  
  
    -   Il frammento di codice può contenere riferimenti che vengono automaticamente aggiunti al progetto e possono essere caricati da un punto qualsiasi nel sistema. Questi riferimenti possono essere stati scaricati nel computer dal punto in cui è stato scaricato il frammento di codice. Il frammento di codice può a questo punto chiamare un metodo nel riferimento che esegue codice dannoso. Per proteggersi da questo tipo di attacco, analizzare i blocchi delle importazioni e dei riferimenti del file di frammento.  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Basic IntelliSense Code Snippets](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)  (Frammenti di codice IntelliSense di Visual Basic)  
 [Securing Applications](../ide/securing-applications.md)  (Protezione delle applicazioni)  
 [Frammenti di codice](../ide/code-snippets.md)