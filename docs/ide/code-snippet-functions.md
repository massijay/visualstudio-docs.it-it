---
title: "Funzioni dei frammenti di codice | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "frammenti di codice [Visual Studio], funzioni"
  - "frammenti di codice IntelliSense, funzioni"
  - "frammenti [Visual Studio], funzioni"
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Funzioni dei frammenti di codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le funzioni disponibili per l’utilizzo con i frammenti di codice [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] sono tre.  Le funzioni sono specificate nell'elemento [Function](http://msdn.microsoft.com/it-it/572c5549-5821-4e15-8ecd-0fa86c1c65df) del frammento di codice.  Per informazioni sulla creazione di frammenti di codice, vedere [Frammenti di codice](../ide/code-snippets.md).  
  
## Funzioni  
 Nella tabella seguente sono descritte le funzioni disponibili per l'utilizzo con l'elemento `Function` nei frammenti di codice.  
  
|Funzione|Descrizione|Linguaggio|  
|--------------|-----------------|----------------|  
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Genera un'istruzione switch e un insieme di istruzioni case per i membri dell'enumerazione specificata dal parametro `EnumerationLiteral`.  Il parametro `EnumerationLiteral` deve essere un riferimento a un valore letterale dell'enumerazione oppure a un tipo di enumerazione.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`ClassName()`|Restituisce il nome della classe contenente il frammento di codice inserito.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`SimpleTypeName(` `TypeName` `)`|Riduce il parametro *TypeName* alla forma più semplice nel contesto in cui è stato chiamato il frammento di codice.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato come utilizzare la funzione `GenerateSwitchCases`.  Quando viene inserito questo frammento di codice e un'enumerazione viene immessa nel valore letterale `$switch_on$`, il valore letterale `$cases$` genera un'istruzione `case` per ogni valore presente nell'enumerazione.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>switch</Title>   
            <Shortcut>switch</Shortcut>   
            <Description>Code snippet for switch statement</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>expression</ID>   
                    <ToolTip>Expression to switch on</ToolTip>   
                    <Default>switch_on</Default>   
                </Literal>  
                <Literal Editable="false">  
                    <ID>cases</ID>   
                    <Function>GenerateSwitchCases($expression$)</Function>   
                    <Default>default:</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[  
                    switch ($expression$)  
                    {  
                        $cases$  
                    }  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato come utilizzare la funzione `ClassName`.  Quando viene inserito questo frammento di codice, il valore letterale `$classname$` viene sostituito con il nome della classe che lo contiene in corrispondenza della medesima posizione nel file del codice.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Common constructor pattern</Title>   
            <Shortcut>ctor</Shortcut>   
            <Description>Code Snippet for a constructor</Description>  
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>  
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal>  
                    <ID>type</ID>   
                    <Default>int</Default>   
                </Literal>  
                <Literal>  
                    <ID>name</ID>   
                    <Default>field</Default>   
                </Literal>  
                <Literal default="true" Editable="false">  
                    <ID>classname</ID>   
                    <ToolTip>Class name</ToolTip>   
                    <Function>ClassName()</Function>   
                    <Default>ClassNamePlaceholder</Default>   
                </Literal>  
            </Declarations>  
            <Code Language="vjsharp" Format="CData">  
                <![CDATA[   
                    public $classname$ ($type$ $name$)  
                    {  
                        this._$name$ = $name$;  
                    }  
                    private $type$ _$name$;  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato come utilizzare la funzione `SimpleTypeName`.  Quando viene inserito questo frammento di codice in un file del codice, il valore letterale `$SystemConsole$` viene sostituito con la forma più semplice del tipo <xref:System.Console> nel contesto in cui è stato chiamato il frammento.  
  
```  
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <CodeSnippet Format="1.0.0">  
        <Header>  
            <Title>Console_WriteLine</Title>   
            <Shortcut>cw</Shortcut>   
            <Description>Code snippet for Console.WriteLine</Description>   
            <Author>Microsoft Corporation</Author>   
            <SnippetTypes>  
                <SnippetType>Expansion</SnippetType>   
            </SnippetTypes>  
        </Header>  
        <Snippet>  
            <Declarations>  
                <Literal Editable="false">  
                    <ID>SystemConsole</ID>   
                    <Function>SimpleTypeName(global::System.Console)</Function>   
                </Literal>  
            </Declarations>  
            <Code Language="csharp">  
                <![CDATA[   
                    $SystemConsole$.WriteLine();  
                ]]>  
            </Code>  
        </Snippet>  
    </CodeSnippet>  
</CodeSnippets>  
```  
  
## Vedere anche  
 [Function Element \(Intellisense Code Snippets\)](http://msdn.microsoft.com/it-it/572c5549-5821-4e15-8ecd-0fa86c1c65df)   
 [Riferimento dello schema dei frammenti di codice](../ide/code-snippets-schema-reference.md)