---
title: 格式、XAML、文字編輯器、選項 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Miscellaneous
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing
helpviewer_keywords:
- element spacing, XAML view settings
- attribute spacing, XAML view settings
- XAML view settings, auto-formatting events
- auto-formatting events, XAML view settings
- XAML view settings, tag wrapping
- XAML view settings, auto insert
- quotation mark style, XAML view settings
- XAML formatting, WPF Designer
- XAML view settings, Toolbox
- XAML view settings, element spacing
- default view, XAML view settings
- auto insert, XAML view settings
- XAML view settings, default view
- XAML view settings, quotation mark style
- tag wrapping, XAML view settings
- WPF Designer, XAML formatting
- XAML view settings, attribute spacing
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 537223aab878aee2fb00e9417d0415f0a17d2dd5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534130"
---
# <a name="options-text-editor-xaml-formatting"></a>格式、XAML、文字編輯器、選項
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用 [格式化]**** 屬性頁來指定如何格式化您 XAML 文件中的項目和屬性。 若要開啟 [選項]**** 對話方塊，請按一下 [工具]**** 功能表，然後按一下 [選項]****。 若要存取 [格式]**** 屬性頁，請展開 [文字編輯器]****、[XAML]****、[格式]**** 節點。

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具]**** 功能表上選擇 [匯入和匯出設定]****。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。

## <a name="auto-formatting-events"></a>自動格式化事件
偵測到下列任一事件時，可能會進行自動格式化。

- 結束標記或簡單標記完成。

- 開始標記完成。

- 從剪貼簿貼上。

- 格式化鍵盤命令。

  您可以指定哪些事件會導致自動格式化。

|名稱|描述|
|-|-|
|**結束標記或簡單標記完成時**|輸入結束標記或簡單標記完成時，會進行自動格式化。 簡單標記沒有屬性，例如 `<Button />`。|
|**開始標記完成時**|完成鍵入開始標記時，會進行自動格式化。|
|**從剪貼簿貼上**|將 XAML 從剪貼簿貼入 XAML 檢視時，會進行自動格式化。|

## <a name="quotation-mark-style"></a>引號樣式
這個設定表示以單引號還是雙引號括住屬性值。 自動格式器和 IntelliSense 自動完成都會使用此設定。

設定此選項之後，只會影響使用設計工具所後續新增的屬性或在 XAML 檢視中手動新增的屬性。

|名稱|描述|
|-|-|
|**雙引號 (")**|屬性值會括在雙引號中。<br /><br /> `<Button Name="button1">Hello</Button>`|
|**單引號 (')**|屬性值會括在單引號中。<br /><br /> `<Button Name='button1'>Hello</Button>`|

## <a name="tag-wrapping"></a>標記換行
您可以指定進行標記換行的行長度。 啟用標記換行時，使用設計工具所後續新增的任何 XAML 都會適當地換行。

|名稱|描述|
|-|-|
|**將超過指定長度的標記換行**|指定是否在 [長度]**** 所指定的行長度處換行。|
|**長度**|一行可以包含的字元數。 必要時，有些 XAML 行可能會超過指定的行長度。|

## <a name="attribute-spacing"></a>屬性間距
使用此設定可控制 XAML 文件中的屬性排列方式

|名稱|描述|
|-|-|
|**保留屬性間的新行與空格**|自動格式化不會影響屬性間的新行與空格。<br /><br /> `<Button Height="23" Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**在屬性之間插入單一空格**|屬性會佔用一行，並以一個空格分隔相鄰的屬性。 套用標記換行設定。<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|
|**將每個屬性置於不同行**|每個屬性都會佔用它自己的一行。 有許多屬性時，這非常有用。<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**將第一個屬性置於開始標記的同一行**|核取時，第一個屬性會出現在項目之開始標記的同一行。<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|

## <a name="element-spacing"></a>項目間距
使用此設定可控制 XAML 文件中的項目排列方式

|                                                               |                                                                                                                                                                                       |
|---------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **保留內容中的新行**                             | 不會移除項目內容中的空白行。<br /><br /> `<Grid>`<br /><br /><br /><br /><br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /><br /><br /> `</Grid>\`   |
| **將內容中的多個空白行摺疊成一行** | 項目內容中的空白行會摺疊成一行。<br /><br /> `<Grid>`<br /><br /><br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /><br /><br /> `</Grid>` |
| **移除內容中的空白行**                             | 移除項目內容中的所有空白行。<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`                                        |

## <a name="auto-insert"></a>自動插入
使用此設定可控制標記和引號的自動產生時機。

|名稱|描述|
|-|-|
|**結尾標記**|指定當您關閉具有大於字元 (>) 的開始標記時，是否自動產生項目的結尾標記。|
|**屬性引號**|指定從陳述式完成下拉式清單中選取屬性值時，是否產生封閉式引號。|
|**MarkupExtension 的右大括弧**|指定當您輸入左大括弧字元 ({) 時，是否自動產生標記延伸的右大括弧 (})。|
|**分隔 MarkupExtension 參數的逗號**|指定是否在您於標記延伸中輸入多個參數時產生逗號。|

## <a name="default-view"></a>預設檢視
使用此設定可控制載入 XAML 文件時是否出現設計檢視。

|名稱|描述|
|-|-|
|**一律以完整的 XAML 視圖開啟檔**|指定 XAML 檔是否只會出現在 XAML 視圖中，而不設計檢視。 適用于載入大型檔。|

## <a name="toolbox"></a>工具箱
使用此設定可指定是否要在 [工具箱] 中顯示使用者控制項和自訂控制項。

|名稱|描述|
|-|-|
|**自動填入工具箱項目**|指定目前方案中的使用者控制項和自訂控制項是否自動顯示在工具箱。|

## <a name="see-also"></a>另請參閱
WPF 中的[XAML](https://msdn.microsoft.com/library/5d858575-a83b-42df-ad3f-047ed2d6e3c8) 
[如何：變更 XAML 視圖設定](https://msdn.microsoft.com/aee87c79-ca01-4f84-8fb7-a9e47048ee47) 
[XAML 和程式碼](https://msdn.microsoft.com/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)逐步解說
