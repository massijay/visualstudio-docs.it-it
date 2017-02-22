---
title: "Procedura dettagliata: debug in fase di progettazione | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "punti di interruzione, debug in fase di progettazione"
  - "debug [Visual Studio], fase di progettazione"
  - "debug in fase di progettazione"
  - "Controllo immediato (finestra), debug in fase di progettazione"
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura dettagliata: debug in fase di progettazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile utilizzare la finestra di **controllo immediato** di Visual Studio per eseguire una funzione o una subroutine quando l'applicazione non è in esecuzione.  Se la funzione o la subroutine contiene un punto di interruzione, l'esecuzione verrà interrotta nel punto appropriato.  È quindi possibile utilizzare le finestre del debugger per esaminare lo stato del programma.  Questa funzionalità è denominata debug in fase di progettazione.  
  
 Nella procedura riportata di seguito viene descritto come utilizzare questa funzionalità.  
  
### Per raggiungere punti di interruzione dalla finestra di controllo immediato  
  
1.  Incollare il seguente codice in un'applicazione console Visual Basic:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  Impostare un punto di interruzione nella riga `s="Add BreakPoint Here"`.  
  
3.  Nella finestra **Controllo immediato** digitare quanto segue: `?<enter>`  
  
4.  Verificare che il punto di interruzione sia stato raggiunto e che lo stack di chiamate sia corretto.  
  
5.  Scegliere **Continua** dal menu **Debug** e verificare che sia ancora attivata la modalità di progettazione.  
  
6.  Nella finestra **Controllo immediato** digitare quanto segue: `?<enter>`  
  
7.  Nella finestra **Controllo immediato** digitare quanto segue: `?MySub<enter>`  
  
8.  Verificare che il punto di interruzione sia stato raggiunto e controllare il valore della variabile statica `i` nella finestra **Variabili locali**.  Il valore dovrebbe essere 3.  
  
9. Verificare che lo stack di chiamate sia corretto.  
  
10. Scegliere **Continua** dal menu **Debug** e verificare che sia ancora attivata la modalità di progettazione.  
  
## Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)