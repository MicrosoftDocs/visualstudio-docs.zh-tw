---
title: 全域 Windows Form 和 Web Form 的特定文化特性類別 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c2d048387e4e81763a63b5bf010c36c87beeacf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665913"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>全域 Windows Form 和 Web Form 的文化特性特定類別
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

每個文化特性對於顯示日期、時間、數字、貨幣及其他資訊都有不同的慣例。 <xref:System.Globalization> 命名空間包含的類別可用來修改文化特性 (Culture) 特定值的顯示方式，例如 <xref:System.Globalization.DateTimeFormatInfo>、**Calendar** 和 <xref:System.Globalization.NumberFormatInfo>。

## <a name="using-the-culture-setting"></a>使用文化特性設定
 但大部分的情況，您會使用文化特性設定 (儲存於應用程式或控制台的 [地區選項] 中) 自動在執行階段判斷慣例並據以格式化資訊。 如需設定文化特性的詳細資訊，請參閱[如何：設定 Windows Form 全球化的文化特性和 UI 文化特性](https://msdn.microsoft.com/694e049f-0b91-474a-9789-d35124f248f0)或[如何：為 ASP.NET 網頁全球化設定文化特性和 UI 文化特性](https://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0)。 根據文化特性設定自動格式化資訊的類別，稱為文化特性專用。 一部分的文化特性 (Culture) 特定方法為 <xref:System.IFormattable.ToString%2A?displayProperty=fullName>、<xref:System.Console.WriteLine%2A?displayProperty=fullName> 和 <xref:System.String.Format%2A?displayProperty=fullName>。 一些文化特性函式 (在 Visual Basic 語言中) 如 `MonthName` 和 `WeekDayName`。

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

 如果文化特性設定為 "fr-FR"，您會在輸出視窗中看到這個：

 `100,00`

 如果文化特性設定為 "en-US"，您會在輸出視窗中看到這個：

 `$100.00`

## <a name="see-also"></a>請參閱
 <xref:System.IFormattable.ToString%2A?displayProperty=fullName> <xref:System.Globalization.DateTimeFormatInfo>
 <xref:System.Globalization.NumberFormatInfo>
 <xref:System.Globalization.Calendar>
 <xref:System.Console.WriteLine%2A?displayProperty=fullName>
 <xref:System.String.Format%2A?displayProperty=fullName>
 [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)
