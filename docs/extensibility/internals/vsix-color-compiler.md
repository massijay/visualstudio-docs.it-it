---
title: "Compilatore colore VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Compilatore colore VSIX
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lo strumento Colore compilatore estensione di Visual Studio è un'applicazione console che accetta un file XML che rappresenta i colori per i temi di Visual Studio esistenti e vengono convertiti in un. pkgdef file in modo che i colori da utilizzare in Visual Studio. Poiché è facile confrontare le differenze tra file con estensione XML, questo strumento è utile per la gestione dei colori personalizzati nel controllo del codice sorgente. Inoltre possibile eseguire l'hook negli ambienti di compilazione in modo che l'output della compilazione è un file. pkgdef valido.  
  
 **Schema XML del tema**  
  
 Un file con estensione XML tema completo è simile al seguente:  
  
```xml  
<Themes>  
      <!—one or Theme elements -->  
      <Theme>  
        <!-- one or more Category elements -->  
        <Category>  
          <!-- one or more Color elements -->  
          <Color>  
            <!-- zero or one Background element -->  
            <Background />  
            <!-- zero or one Foreground element -->  
            <Foreground />  
          </Color>  
        </Category>  
      </Theme>  
</Themes>  
```  
  
 **Tema**  
  
 Il \< tema> elemento definisce un tema completo. Deve contenere almeno un tema \< categoria> elemento. Elementi definiti simile al seguente:  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|Nome|[Obbligatorio] Il nome del tema|  
|GUID|[Obbligatorio] GUID del tema (devono corrispondere GUID formattazione)|  
  
 Durante la creazione di colori personalizzati per Visual Studio, i colori devono essere definiti per i seguenti temi. Se non esistono alcun colore per un tema specifico, Visual Studio tenta di caricare i colori mancanti dal tema chiaro.  
  
|||  
|-|-|  
|**Nome del tema**|**Tema GUID**|  
|Chiaro|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Scuro|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|Blu|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Contrasto elevato|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Categoria**  
  
 Il \< categoria> elemento definisce una raccolta di colori in un tema. I nomi di categoria contengono raggruppamenti logici e devono essere definiti come ristretto possibile. Deve contenere almeno una categoria \< colore> elemento. Elementi delle categorie vengono definiti simile al seguente:  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|Nome|[Obbligatorio] Il nome della categoria|  
|GUID|[Obbligatorio] GUID della categoria (devono corrispondere GUID formattazione)|  
  
 **Colore**  
  
 Il \< colore> elemento definisce un colore per un componente o lo stato dell'interfaccia Utente. Lo schema di denominazione preferito per un colore è [tipo di interfaccia Utente] [stato]. Non utilizzare la parola "colore", come è ridondante. Un colore deve indicare chiaramente il tipo di elemento e le situazioni o "stato", per cui verrà applicato il colore. Un colore non deve essere vuoto e deve contenere uno o entrambi un \< Background> e \< in primo piano> elemento. Gli elementi di colore sono definiti nel modo seguente:  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|Nome|[Obbligatorio] Il nome del colore|  
  
 **Sfondo e/o in primo piano**  
  
 Il \< Background> e \< in primo piano> elementi che definiscono un colore valore e tipo di primo piano di un elemento dell'interfaccia Utente o di sfondo. Questi elementi non avere figli.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|Tipo|[Obbligatorio] Il tipo del colore. Può essere uno dei seguenti:<br /><br /> *CT_INVALID:* il colore non è valido o non impostato.<br /><br /> *CT_RAW:* un valore ARGB non elaborato.<br /><br /> *CT_COLORINDEX:* NON UTILIZZARE.<br /><br /> *CT_SYSCOLOR:* un colore di sistema di Windows da SysColor.<br /><br /> *CT_VSCOLOR:* un colore di Visual Studio da __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* il colore automatico.<br /><br /> *CT_TRACK_FOREGROUND:* NON UTILIZZARE.<br /><br /> *CT_TRACK_BACKGROUND:* NON UTILIZZARE.|  
|Origine|[Obbligatorio] Il valore del colore rappresentato in formato esadecimale|  
  
 Tutti i valori supportati dall'enumerazione __VSCOLORTYPE supportati dallo schema dell'attributo di tipo. Tuttavia, è consigliabile utilizzare solo CT_RAW e CT_SYSCOLOR.  
  
 **Tutti insieme**  
  
 Questo è un esempio semplice di un file XML di tema valido:  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">  
      <Color Name="MyActiveBorder">  
        <Background Type="CT_RAW" Source="FFCCCEDB" />  
      </Color>  
    </Category>  
  </Theme>  
</Themes>  
```  
  
## <a name="how-to-use-the-tool"></a>Procedura: utilizzare lo strumento  
 **Sintassi**  
  
 VsixColorCompiler \< file XML> \< file PkgDef> \< argomenti facoltativi>  
  
 **Argomenti**  
  
||||  
|-|-|-|  
|**Nome del commutatore**|**Note**|**Obbligatorio o facoltativo**|  
|Senza nome (file con estensione XML)|Questo è il primo parametro senza nome e percorso del file XML da convertire.|Obbligatorio|  
|Senza nome (file. pkgdef)|Questo è il secondo parametro senza nome e il percorso di output per il file. pkgdef generato.<br /><br /> Valore predefinito: \< nome file XML>. pkgdef|Facoltativo|  
|/noLogo|L'impostazione di questo flag interrompe prodotto e informazioni sul copyright di stampare le informazioni.|Facoltativo|  
|/?|Stampare le informazioni della Guida.|Facoltativo|  
|/help|Stampare le informazioni della Guida.|Facoltativo|  
  
 **Esempi**  
  
-   VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
-   /NoLogo VsixColorCompiler D:\xml\colors.xml  
  
## <a name="notes"></a>Note  
  
-   Questo strumento è necessario che la versione più recente del runtime di VC + + sia installato.  
  
-   Sono supportati solo i file singoli. Conversione in blocco tramite i percorsi delle cartelle non è supportata.  
  
## <a name="sample-output"></a>Esempio di output  
 Il file. pkgdef generato dallo strumento sarà simile di sotto le chiavi:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```