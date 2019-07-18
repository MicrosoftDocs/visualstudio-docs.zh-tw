---
title: HOW TO：散發程式碼片段 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d1878fd1ce91842e8d03b6e78de244380df8eb2b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62430558"
---
# <a name="how-to-distribute-code-snippets"></a>HOW TO：散發程式碼片段
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用程式碼片段管理員，將您的程式碼片段提供給您的朋友，並讓他們在自己的電腦上安裝程式碼片段。 不過，如果您有數個程式碼片段要散發，或想要更廣泛地散發，請在 Visual Studio 使用者可以安裝的 Visual Studio 擴充功能中包含您的程式碼片段檔案。  
  
 若要建立 Visual Studio 擴充功能，您必須安裝 Visual Studio SDK。 尋找符合您 Visual Studio 安裝的 vssdk 版本[Visual Studio 2015 下載](http://www.visualstudio.com/downloads/visual-studio-2015-downloads-vs.aspx)。  
  
## <a name="setting-up-the-extension"></a>設定擴充功能  
 在此程序中，我們將使用同一個 Hello World 程式碼片段中建立[逐步解說：建立程式碼片段](../ide/walkthrough-creating-a-code-snippet.md)。 我們將提供 .snippet 文字，所以您不需返回再做一次。  
  
1. 建立新的 VSIX 專案，名為 **TestSnippet**。 ( [檔案] / [新增] / [專案] / [Visual C#] \(或 [Visual Basic] / [擴充性])  
  
2. 在 **TestSnippet** 專案中加入新的 XML 檔案，並將其命名為 **VBCodeSnippet.snippet**。 使用下列內容取代此內容：  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <CodeSnippets  
        xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
      <CodeSnippet Format="1.0.0">  
        <Header>  
          <Title>Hello World VB</Title>  
          <Shortcut>HelloWorld</Shortcut>  
          <Description>Inserts code</Description>  
          <Author>MSIT</Author>  
          <SnippetTypes>  
            <SnippetType>Expansion</SnippetType>  
            <SnippetType>SurroundsWith</SnippetType>  
          </SnippetTypes>  
        </Header>  
        <Snippet>  
          <Code Language="VB">  
            <![CDATA[Console.WriteLine("Hello, World!")]]>  
          </Code>  
        </Snippet>  
      </CodeSnippet>  
    </CodeSnippets>  
    ```  
  
#### <a name="setting-up-the-directory-structure"></a>設定目錄結構  
  
1. 在 [方案總管] 中，選取專案節點並加入資料夾，其名稱為在 [程式碼片段管理員] 中您要讓程式碼片段具有的名稱。 在此情況下，它應該是 **HelloWorldVB**。  
  
2. 將 .snippet 檔案移至 **HelloWorldVB** 資料夾。  
  
3. 在方案總管中選取此 .snippet 檔案，然後確認 [屬性] 視窗的 [建置動作] 已設為 [內容]、[複製到輸出目錄] 已設為 [一律複製]，且 [包含在 VSIX] 已設為 [true]。  
  
#### <a name="adding-the-pkgdef-file"></a>加入 .pkgdef 檔  
  
1. 將文字檔新增至 **HelloWorldVB** 資料夾，並將它命名為 **HelloWorldVB.pkgdef**。 這個檔案用來將特定機碼加入登錄。 在此情況下，它會將新的機碼加入   
  
     **HKCU\Software\Microsoft\VisualStudio\14.0\Languages\CodeExpansions\Basic**。  
  
2. 將下列各行加入檔案。  
  
    ```  
    // Visual Basic   
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]   
    "HelloWorldVB"="$PackageFolder$"  
    ```  
  
     如果您檢查此機碼，您可以了解如何指定不同的語言。  
  
3. 在方案總管中選取此 .pkgdef 檔案，然後確認 [屬性] 視窗的 [建置動作] 已設為 [內容]、[複製到輸出目錄] 已設為 [一律複製]，且 [包含在 VSIX] 已設為 [true]。  
  
4. 加入 .pkgdef 檔做為 VSIX 資訊清單中的資產。 在 source.extension.vsixmanifest 檔案中，移至 [資產] 索引標籤，然後按一下 [新增]。  
  
5. 在 [新增資產] 對話方塊中，將 [類型] 設為 [Microsoft.VisualStudio.VsPackage]、[類型] 設為 [檔案系統上的檔案]，並將 [路徑] 設為 [HelloWorldVB.pkgdef]\(這應該會出現在下拉式清單中)。  
  
### <a name="testing-the-snippet"></a>測試程式碼片段  
  
1. 現在您可以確定程式碼片段適用於 Visual Studio 的實驗性執行個體。 此實驗性執行個體是 Visual Studio 的第二個複本，這複本與您用來撰寫程式碼的不同。 它可讓您處理擴充功能，而不會影響您的開發環境。  
  
2. 建置此專案並開始偵錯。 Visual Studio 的第二個執行個體應該會出現。  
  
3. 在實驗性執行個體中，移至 [工具]/[程式碼片段管理員]，然後將 [語言] 設為 [基本]。 您應該會看到 HelloWorldVB 做為其中一個資料夾，而且您應該能夠展開此資料夾，以查看 HelloWorldVB 程式碼片段。  
  
4. 測試程式碼片段。 在實驗性執行個體中，開啟 Visual Basic 專案，並開啟其中一個程式碼檔案。 將游標放在程式碼中的某處，按一下滑鼠右鍵，然後在 [操作功能表] 上選取 [插入程式碼片段]。  
  
5. 您應該會看到 HelloWorldVB 做為其中一個資料夾。 對它按兩下。 您應該會看到快顯視窗 [插入程式碼片段：HelloWorldVB >]**HellowWorldVB >** ，這具有下拉式清單**HelloWorldVB**。 按一下這個 HelloWorldVB 下拉式清單。 您應該會看到下面這一行已加入此檔案：  
  
    ```vb  
    Console.WriteLine("Hello, World!")  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [程式碼片段](../ide/code-snippets.md)
