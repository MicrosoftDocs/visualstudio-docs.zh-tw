---
title: "如何：指定應用程式圖示 (Visual Basic、C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 3309b02a50f3f14d166044c2d1cea35bdab3922f
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>如何：指定應用程式圖示 (Visual Basic、C#)

專案的 `Icon` 屬性指定已編譯的應用程式將會顯示在檔案總管和 Windows 工作列的圖示檔 (.ico)。

透過 [專案設計工具] 的 [應用程式] 窗格，即可存取 `Icon` 屬性；該屬性包含圖示清單，其中的圖示都已經用資源或內容檔案的形式新增至專案。

> [!NOTE]
> 設定應用程式的 Icon 屬性之後，您也可以設定應用程式中每個 [視窗] 或 [表單] 的 `Icon` 屬性。 如需 Windows Presentation Foundation (WPF) 獨立應用程式之視窗圖示的詳細資訊，請參閱 <xref:System.Windows.Window.Icon%2A> 屬性。

## <a name="to-specify-an-application-icon"></a>指定應用程式圖示

1. 在方案總管中，選擇專案節點 (而不是 [方案] 節點)。

1. 在功能表列上，依序選擇 [專案] > [屬性]。

1. 當 [專案設計工具] 出現時，請選擇 [應用程式] 索引標籤。

1. **(Visual Basic)**&mdash;在 [圖示] 清單中，選擇圖示檔 (.ico)。

    **C#**&mdash;選擇 [圖示] 清單附近的 [\<瀏覽...>] 按鈕，然後瀏覽至您想要之圖示檔的位置。

## <a name="see-also"></a>另請參閱

[專案設計工具、應用程式頁面 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)  
[專案設計工具，應用程式頁面 (C#)](../ide/reference/application-page-project-designer-csharp.md)
