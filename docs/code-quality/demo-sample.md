---
title: "Esempio dimostrativo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analisi codice, esempi"
  - "esempio dimostrativo [Visual Studio ALM]"
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Esempio dimostrativo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nelle routine seguenti sono indicate le modalità di creazione dell'esempio per [Procedura guidata: analisi del codice C\/C\+\+ per l'identificazione degli errori](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md).  Con le routine vengono creati gli elementi seguenti:  
  
-   Una soluzione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] denominata CppDemo.  
  
-   Un progetto di libreria statica denominato CodeDefects.  
  
-   Un progetto di libreria statica denominato Annotations.  
  
 Le routine forniscono inoltre il codice per l'intestazione e file .cpp per le librerie statiche.  
  
### Creare la soluzione CppDemo e il progetto CodeDefects  
  
1.  Scegliere **Nuovo** dal menu **File** e quindi **Nuovo progetto**.  
  
2.  Neil'elenco struttura ad albero **Tipi progetto**, se Visual C\+\+ non è il linguaggio predefinito in Visual Studio espandere **Altri linguaggi**.  
  
3.  Espandere **Visual C\+\+** e quindi fare clic su **Generale**.  
  
4.  In **Modelli** fare clic su **Progetto vuoto**.  
  
5.  Nella casella di testo **Nome** digitare **CodeDefects**.  
  
6.  Selezionare la casella di controllo **Crea directory per soluzione**.  
  
7.  Nella casella di testo **Nome soluzione** digitare **CppDemo**.  
  
### Configurare il progetto CodeDefects come libreria statica  
  
1.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **CodeDefects**, quindi scegliere **Proprietà**.  
  
2.  Espandere **Proprietà di configurazione** e fare clic su **Generale**.  
  
3.  Nell'elenco **Generale** selezionare il testo nella colonna accanto a **Estensione di destinazione**, quindi digitare **.lib**.  
  
4.  In **Impostazioni predefinite progetto** fare clic sulla colonna accanto a **Tipo configurazione**, quindi fare clic su **Libreria statica \(.lib\)**.  
  
### Aggiungere il file di intestazione e il file sorgente al progetto CodeDefects.  
  
1.  In Esplora soluzioni espandere **CodeDefects**, fare clic con il pulsante destro del mouse su **File di intestazione**, scegliere **Aggiungi**, quindi fare clic su **Nuovo elemento**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento** fare clic su **Codice**, quindi su **File di intestazione \(.h\)**.  
  
3.  Nella casella **Nome** digitare **Bug.cpp**, quindi fare clic su **Aggiungi**.  
  
4.  Copiare il codice riportato di seguito e incollarlo nel file **Bug.cpp** all'interno dell'editor di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **File di origine**, quindi scegliere **Nuovo** e fare clic su **Nuovo elemento**.  
  
6.  Nella finestra di dialogo **Aggiungi nuovo elemento** fare clic su **File di C\+\+ \(.cpp\)**  
  
7.  Nella casella **Nome** digitare **Bug.cpp**, quindi fare clic su **Aggiungi**.  
  
8.  Copiare il codice riportato di seguito e incollarlo nel file Bug.h all'interno dell'editor [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. Scegliere **Salva tutto** dal menu **File**.  
  
### Aggiungere il progetto Annotations e configurarlo come libreria statica  
  
1.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **CppDemo**, scegliere **Aggiungi**, quindi fare clic su **Nuovo progetto**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo progetto** espandere Visual C\+\+, fare clic su **Generale**, quindi su **Progetto vuoto**.  
  
3.  Nella casella di testo **Nome** digitare **Annotations**, quindi fare clic su **Aggiungi**.  
  
4.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **Annotazioni**, quindi scegliere **Proprietà**.  
  
5.  Espandere **Proprietà di configurazione** e fare clic su **Generale**.  
  
6.  Nell'elenco **Generale** selezionare il testo nella colonna accanto a **Estensione di destinazione**, quindi digitare **.lib**.  
  
7.  In **Impostazioni predefinite progetto** fare clic sulla colonna accanto a **Tipo configurazione**, quindi fare clic su **Libreria statica \(.lib\)**.  
  
### Aggiungere il file di intestazione e il file sorgente al progetto Annotations.  
  
1.  In Esplora soluzioni espandere **Annotazioni**, fare clic con il pulsante destro del mouse su **File di intestazione**, scegliere **Aggiungi**, quindi fare clic su **Nuovo elemento**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento** fare clic su **File di intestazione \(.h\)**.  
  
3.  Nella casella **Nome** digitare **annotations.h**, quindi fare clic su **Aggiungi**.  
  
4.  Copiare il codice riportato di seguito e incollarlo nel file **annotations.h** all'interno dell'editor [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **File di origine**, quindi scegliere **Nuovo** e fare clic su **Nuovo elemento**.  
  
6.  Nella finestra di dialogo **Aggiungi nuovo elemento** fare clic su **Codice**, quindi su **File C\+\+ \(.cpp\)**.  
  
7.  Digitare **annotations.cpp** nella casella **Nome**, quindi scegliere **Aggiungi**.  
  
8.  Copiare il codice riportato di seguito e incollarlo nel file **annotations.cpp** all'interno dell'editor [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Scegliere **Salva tutto** dal menu **File**.