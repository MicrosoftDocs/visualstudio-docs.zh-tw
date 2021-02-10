---
title: 格式、XAML、文字編輯器、選項
description: 瞭解如何在程式碼編輯器中使用 XAML 進行程式設計時，使用 [格式化選項] 頁面及其子頁面來設定格式化程式碼的選項。
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: f550499545fda3250f4d2449697513fbc8c09fa2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970786"
---
# <a name="options-text-editor-xaml-formatting"></a>格式、XAML、文字編輯器、選項

使用 [格式化] 屬性頁來指定如何格式化您 XAML 文件中的項目和屬性。 若要開啟 [選項] 對話方塊，請按一下 [工具] 功能表，然後按一下 [選項]。 若要存取 [格式化] 屬性頁，請展開 [文字編輯器] > [XAML] > [格式] 節點。

## <a name="auto-formatting-events"></a>自動格式化事件

偵測到下列任一事件時，可能會進行自動格式化。

- 結束標記或簡單標記完成。

- 開始標記完成。

- 從剪貼簿貼上。

- 格式化鍵盤命令。

您可以指定哪些事件會導致自動格式化。

**結束標記或簡單標記完成時**

完成鍵入結束標記或簡單標記時，會進行自動格式化。 簡單標記沒有屬性，例如 `<Button />`。

**開始標記完成時**

完成鍵入開始標記時，會進行自動格式化。

**從剪貼簿貼上**

將 XAML 從剪貼簿貼入 XAML 檢視時，會進行自動格式化。

## <a name="quotation-mark-style"></a>引號樣式

這個設定表示以單引號還是雙引號括住屬性值。 自動格式化程式和 IntelliSense 自動完成都會使用此設定。

設定此選項之後，只會影響使用設計工具所後續新增的屬性或在 XAML 檢視中手動新增的屬性。

**雙引號 (")**

屬性值會括在雙引號中。
`<Button Name="button1">Hello</Button>`

**單引號 (')**

屬性值會括在單引號中。
`<Button Name='button1'>Hello</Button>`

## <a name="tag-wrapping"></a>標記換行

您可以指定進行標記換行的行長度。 啟用標記換行時，使用設計工具所後續新增的任何 XAML 都會適當地換行。

**將超過指定長度的標記換行**

指定是否在 [長度] 所指定的行長度處換行。

**長度**

一行可以包含的字元數。 必要時，有些 XAML 行可能會超過指定的行長度。

## <a name="attribute-spacing"></a>屬性間距

使用此設定可控制 XAML 文件中的屬性排列方式

**保留屬性間的新行與空格**

自動格式化不會影響屬性間的新行與空格。

```xml
<Button Height="23"   Name="button1"
Width="75">Hello</Button>
```

**在屬性之間插入單一空格**

屬性會佔用一行，並以一個空格分隔相鄰的屬性。 套用標記換行設定。

```xml
<Button Height="23" Name="button1" Width="75">Hello</Button>
```

**將每個屬性置於不同行**

每個屬性都會佔用其自己的行，當存在許多屬性時非常有用。

```xml
<Button
Height="23"
Name="button1"
Width="75">Hello</Button>
```

**將第一個屬性置於開始標記的同一行**

核取時，第一個屬性會出現在項目之開始標記的同一行。

```xml
<Button Height="23"
Name="button1"
Width="75">Hello</Button>
```

## <a name="element-spacing"></a>項目間距

使用此設定可控制 XAML 文件中的項目排列方式。

**保留內容中的新行**

不會移除項目內容中的空白行。

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**將內容中的多個空白行摺疊成一行**

項目內容中的空白行會摺疊成一行。

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**移除內容中的空白行**

移除項目內容中的所有空白行。

```xml
<Grid>
<Button Name="button1">Hello</Button>
</Grid>
```

## <a name="see-also"></a>另請參閱

- [WPF 中的 XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
