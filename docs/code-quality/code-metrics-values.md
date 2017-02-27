---
title: "Valori della metrica del codice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "metrica del codice"
  - "analisi codice"
  - "misura di qualità del codice"
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 20
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
caps.handback.revision: 20
---
# Valori della metrica del codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La metrica del codice è un insieme di misure del software in grado di fornire agli sviluppatori una migliore comprensione del codice che stanno sviluppando.  Sfruttando la metrica del codice, è possibile capire quali tipi e\/o metodi rielaborare o testare in modo più approfondito.  I team di sviluppo possono così identificare rischi potenziali, comprendere lo stato corrente di un progetto e tenere traccia dei progressi durante lo sviluppo del software.  
  
## Misurazioni del software  
 Nell'elenco riportato di seguito vengono illustrati i risultati della metrica codice calcolati da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   **Indice di gestibilità** \- Calcola un valore di indice tra 0 e 100 che rappresenta la relativa semplicità di gestione del codice.  Un valore alto indica una migliore gestibilità.  È possibile utilizzare le classificazioni codificate con colori differenti per identificare rapidamente i punti critici del codice.  Una classificazione verde è compresa tra 20 e 100 e indica che il codice ha una buona manutenibilità.  Una classificazione gialla è compresa tra 10 e 19 e indica che il codice ha una discreta manutenibilità.  Una classificazione rossa è compresa tra 0 e 9 e indica una bassa manutenibilità.  
  
-   **Complessità ciclomatica** \- Misura la complessità strutturale del codice.  Viene creata calcolando il numero di percorsi di codice diversi nel flusso del programma.  Un programma con un flusso di controllo complesso richiederà più test per raggiungere un buon code coverage e sarà meno gestibile.  
  
    > [!NOTE]
    >  In alcuni casi, il calcolo della complessità ciclomatica per un metodo in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] differisce dalle versioni precedenti.  Per ulteriori informazioni, vedere la sezione "Modifiche nei calcoli di complessità del codice di Visual Studio 2010" di [Risoluzione dei problemi relativi alla metrica codice](../code-quality/troubleshooting-code-metrics-issues.md).  
  
-   **Profondità dell'Ereditarietà** \- Indica il numero di definizioni della classe che estendono alla radice della gerarchia di classi.  Più la gerarchia è profonda e più potrebbe diventare difficile capire dove i particolari metodi e campi siano definiti o\/e ridefiniti.  
  
-   **Accoppiamento di classi** \- Misura l'accoppiamento di classi univoche tramite parametri, variabili locali, tipi restituiti, chiamate al metodo, creazioni di istanze generiche o sulla base di modelli, classi di base, implementazioni dell'interfaccia, campi definiti in base a tipologie esterne e decorazione dell'attributo.  Secondo i canoni della progettazione di software,tipologie e metodi devono avere coesione alta e accoppiamento basso.  Un alto indice di accoppiamento è indice di una progettazione difficile da riutilizzare e gestire, a causa delle molte interdipendenze con altre tipologie.  
  
-   **Righe di Codice** \- Indica il numero approssimativo di righe nel codice.  Il conteggio è basato sul codice IL e non corrisponde perciò al numero esatto di righe nel file di codice sorgente.  Un conteggio molto alto potrebbe indicare che un tipo o metodo sta tentando di fare troppo lavoro e deve essere suddiviso.  Potrebbe anche indicare che il tipo o il metodo potrebbe essere di difficile gestione.  
  
## Metodi anonimi  
 Un *metodo anonimo* è semplicemente un metodo privo di nome.  I metodi anonimi vengono usati il più delle volte per passare un blocco di codice come parametro di delegato.  I risultati delle metriche per un metodo anonimo dichiarato in un membro specifico,come ad esempio un metodo o una funzione di accesso, vengono associati al membro che dichiara il metodo.  Non vengono quindi associati al membro che chiama il metodo.  
  
 Per ulteriori informazioni sulle modalità con cui la metrica del codice tratta i metodi anonimi, vedere [Metodi anonimi e analisi del codice](../code-quality/anonymous-methods-and-code-analysis.md).  
  
## Codice generato  
 Tramite alcuni strumenti di software e compilatori, viene generato del codice aggiuntivo per i progetti che lo sviluppatore del progetto non vede o non deve modificare.  In genere, la metrica del codice ignora il codice generato durante il calcolo dei valori delle metriche.  In questo modo, consente ai valori delle metriche di riflettere ciò che lo sviluppatore può vedere e modificare.  
  
 Il codice generato per le Windows Form non viene ignorato, perché è codice che lo sviluppatore può vedere e modificare.  
  
## Vedere anche  
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)