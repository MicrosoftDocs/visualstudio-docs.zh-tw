---
title: 全域 Windows Form 和 Web Form 的文化特性特定類別
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- globalization [Windows Forms], classes
- Web applications [.NET Framework], globalization
- culture, culture-specific classes
- numbers, international
- localization [Windows Forms], classes
- globalization [Visual Studio], culture-specific classes
- Windows Forms, localization
- international applications [Visual Studio], data formats
- time [Visual Studio], international
- dates [Visual Studio], international
- culture
- international characters
- currency formats
- ASP.NET, globalization
- classes [Visual Studio], culture-specific
- localization [Visual Studio], culture-specific classes
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3fdb46f79d6b300280c6743a368953bac5c5b02d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933895"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>全域 Windows Form 和 Web Form 的文化特性 (Culture) 特定類別

每個文化特性對於顯示日期、時間、數字、貨幣及其他資訊都有不同的慣例。 <xref:System.Globalization> 命名空間所包含的類別可用來修改文化特性 (Culture) 特定值的顯示方式，例如：
- <xref:System.Globalization.DateTimeFormatInfo>
- **Calendar**
- <xref:System.Globalization.NumberFormatInfo>

## <a name="using-the-culture-setting"></a>使用文化特性 (Culture) 設定

使用文化特性 (Culture) 設定 (儲存於應用程式或控制台的 [地區選項] 中)，在執行階段判斷文化特性 (Culture) 慣例並據以格式化資訊。 如需如何設定文化特性 (Culture) 的詳細資訊，請參閱 [How to:Set the culture and UI culture for ASP.NET web page globalization](https://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0) (如何：設定文化特性 (Culture) 及 UI 文化特性，使您的 ASP.NET 網頁全球化)。 根據文化特性 (Culture) 設定自動格式化資訊的類別，稱為「文化特性 (Culture) 特定」。 一部分文化特性 (Culture) 特定方法為
- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>

一些文化特性函式 (在 Visual Basic 語言中) 如 `MonthName` 和 `WeekDayName`。

例如，下列程式碼示範如何使用 <xref:System.IFormattable.ToString%2A> 方法來針對目前的文化特性 (Culture) 對貨幣進行格式化：

```vb
' Put the Imports statements at the beginning of the code module
Imports System.Threading
Imports System.Globalization
' Display a number with the culture-specific currency formatting
Dim MyInt As Integer = 100
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))
```

```csharp
// Put the using statements at the beginning of the code module
using System.Threading;
using System.Globalization;
// Display a number with the culture-specific currency formatting
int myInt = 100;
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));
```

如果文化特性 (Culture) 設定為 "fr-FR"，您會在輸出視窗中看到下列內容：

`100,00`

如果文化特性 (Culture) 設定為 "en-US"，您會在輸出視窗中看到下列內容：

`$100.00`

## <a name="see-also"></a>另請參閱

- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Globalization.DateTimeFormatInfo>
- <xref:System.Globalization.NumberFormatInfo>
- <xref:System.Globalization.Calendar>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>
- [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)