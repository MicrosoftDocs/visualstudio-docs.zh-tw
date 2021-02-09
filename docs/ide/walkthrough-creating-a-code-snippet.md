---
title: 逐步解說：建立程式碼片段
description: 瞭解如何在三個步驟中建立程式碼片段：建立 XML 檔案、填入適當的專案，以及將您的程式碼新增至其中。
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: how-to
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 39565b95b93e489a739c2da3a0f88fb9f683a2bc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873797"
---
# <a name="walkthrough-create-a-code-snippet"></a>逐步解說：建立程式碼片段

只需要幾個步驟就能建立程式碼片段。 您只需要建立 XML 檔案、填入適當的項目，並在其中新增您的程式碼。 您可以選擇性地運用取代參數和專案參考。 使用 [程式碼片段管理員] ([工具] > [程式碼片段管理員]) 上的 [匯入] 按鈕，將程式碼片段匯入至您的 Visual Studio 安裝。

## <a name="snippet-template"></a>程式碼片段範本

以下 XML 是基本程式碼片段範本：

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title></Title>
        </Header>
        <Snippet>
            <Code Language="">
                <![CDATA[]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="create-a-code-snippet"></a>建立程式碼片段

1. 在 Visual Studio 中建立新的 XML 檔案，並新增上面所示的範本。

2. 在 **Title** 元素中填入程式碼片段標題。 請使用 **Square Root** 作為標題。

3. 在 **Code** 元素的 **Languages** 屬性中，填入程式碼片段的語言。 若是 c #，請使用 **CSharp**、針對 Visual Basic、使用 **VB**，以及針對 c + + 使用 **CPP**。

   > [!TIP]
   > 若要查看所有可用的語言值，請瀏覽[程式碼片段結構描述參考](code-snippets-schema-reference.md)頁面上的[程式碼元素屬性區段](code-snippets-schema-reference.md#attributes)。

4. 在 **Code** 元素的 **CDATA** 區段中新增程式碼片段。

   若為 C#：

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   或者，若為 Visual Basic：

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

   > [!NOTE]
   > 您無法指定程式碼片段之 **CDATA** 區段中程式碼的縮排或格式化方式。 插入時，語言服務會自動對插入的程式碼進行格式化。

5. 將程式碼片段儲存為 *SquareRoot.snippet* (您可以將它儲存在任何位置)。

## <a name="import-a-code-snippet"></a>匯入程式碼片段

1. 您可以使用 [程式碼片段管理員]，將程式碼片段匯入至您的 Visual Studio 安裝。 選擇 [**工具**  >  **程式碼片段管理員**] 以開啟它。

2. 按一下 [匯入] 按鈕。

3. 移至您在先前程序中儲存程式碼片段的位置，並選取它，然後按一下 [開啟]。

4. [匯入程式碼片段] 對話方塊隨即開啟，要求您從右窗格的選項中選擇要新增程式碼片段的位置。 其中一個選項應該是 [我的程式碼片段]。 選取它，然後依序按一下 [完成] 和 [確定]。

5. 視程式碼語言而定，該程式碼片段會被複製到下列其中一個位置：

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual Studio 2017 \ Code Snippets\Visual c # \My 程式碼片段*  
   *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual Studio 2019 \ Code Snippets\Visual c # \My 程式碼片段*  
   *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

6. 開啟 C# 或 Visual Basic 專案來測試程式碼片段。 在編輯器中開啟程式碼檔案之後，從滑鼠右鍵功能表中選擇 [代碼 **段**  >  **插入代碼** 段]，然後 **My Code 程式碼片段**]。 您應該會看見名為 **Square Root** 的程式碼片段。 對它按兩下。

   系統會將程式碼片段插入程式碼檔案中。

## <a name="description-and-shortcut-fields"></a>描述和捷徑欄位

::: moniker range="vs-2017"

1. 描述欄位會提供您的程式碼片段在 [程式碼片段管理員] 中檢視時的詳細資訊。 捷徑是使用者可鍵入以插入程式碼片段的標記。 開啟 *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\\[Visual C# 或 Visual Basic]\My Code Snippet\SquareRoot.snippet* 檔案，來編輯您所加入的程式碼片段。

::: moniker-end

::: moniker range=">=vs-2019"

1. 描述欄位會提供您的程式碼片段在 [程式碼片段管理員] 中檢視時的詳細資訊。 捷徑是使用者可鍵入以插入程式碼片段的標記。 開啟 *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\\[Visual C# 或 Visual Basic]\My Code Snippet\SquareRoot.snippet* 檔案，來編輯您所加入的程式碼片段。

::: moniker-end

   > [!TIP]
   > 由於您正在 Visual Studio 放置該檔案的目錄中編輯它，您並不需要將它重新匯入至 Visual Studio。

2. 將 **Author** 和 **Description** 專案加入至 **Header** 專案中，並將其填入。

3. **標頭** 元素看起來應該像這樣：

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. 開啟 [ **程式碼片段管理員** ]，然後選取您的程式碼片段。 在右窗格中，您應該會看到 [描述] 和 [作者] 欄位現在已被填入。

   ![[程式碼片段管理員] 中的程式碼片段描述](media/code-snippet-description-author.png)

5. 若要加入捷徑，請在 **Header** 元素內加入 **Shortcut** 元素：

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. 重新儲存程式碼片段檔案。

7. 若要測試捷徑，請開啟您先前所使用的專案，在編輯器中輸入 **sqrt**，然後按 **Tab** (針對 Visual Basic 按一下，針對 C# 按兩下)。

   會插入程式碼片段程式碼。

## <a name="replacement-parameters"></a>取代參數

您可能會想要讓使用者取代部分的程式碼片段。 例如，您可能會想要讓使用者以其目前專案中的變數名稱，來取代現有的變數名稱。 您可以提供兩種類型的取代：常值和物件。 使用 [Literal 元素](code-snippets-schema-reference.md#literal-element)來識別整個包含在程式碼片段中，但可能會在插入程式碼後加以自訂之一小段程式碼的取代項目 (例如字串或數字值)。 使用 [Object 元素](code-snippets-schema-reference.md#object-element)來識別程式碼片段所需，但很可能是在程式碼片段本身之外定義的項目 (例如物件執行個體或控制項)。

1. 若要讓使用者輕鬆取代數字以計算平方根，請修改 *SquareRoot.snippet* 檔案的 **Snippet** 元素，如下所示：

   ```xml
   <Snippet>
     <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt($Number$);]]>
     </Code>
     <Declarations>
       <Literal>
         <ID>Number</ID>
         <ToolTip>Choose the number you want the square root of.</ToolTip>
         <Default>16</Default>
       </Literal>
     </Declarations>
   </Snippet>
   ```

   請注意，常值取代項目會被賦與識別碼 (`Number`)。 在程式碼片段中，會以將該識別碼包含在 `$` 字元內的形式來參考它：

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. 儲存程式碼片段檔案。

3. 開啟專案並插入程式碼片段。

   系統會插入程式碼片段，且會醒目提示可編輯的常值以進行取代。 暫留在取代參數上以查看該值的工具提示。

   ![Visual Studio 中的程式碼片段取代參數工具提示](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > 如果程式碼片段中有多個可取代的參數，您可以按 **Tab** 在這些參數之間瀏覽以變更其值。

## <a name="import-a-namespace"></a>匯入命名空間

您可以透過包含 [Imports 元素](code-snippets-schema-reference.md#imports-element)來使用程式碼片段加入 `using` 指示詞 (C#) 或 `Imports` 陳述式 (Visual Basic)。 針對 .NET Framework 專案，您也可以使用 [References 元素](code-snippets-schema-reference.md#references-element)來將參考加入專案。

下列 XML 顯示的程式碼片段會使用 System.IO 命名空間中的 `File.Exists` 方法，因此會定義 **Imports** 元素來匯入 System.IO 命名空間。

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>File Exists</Title>
      <Shortcut>exists</Shortcut>
    </Header>
    <Snippet>
      <Code Language="CSharp">
        <![CDATA[var exists = File.Exists("C:\\Temp\\Notes.txt");]]>
      </Code>
      <Imports>
        <Import>
          <Namespace>System.IO</Namespace>
        </Import>
      </Imports>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>另請參閱

- [程式碼片段結構描述參考](../ide/code-snippets-schema-reference.md)
