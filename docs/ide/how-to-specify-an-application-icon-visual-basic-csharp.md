---
title: 如何：指定應用程式圖示 (Visual Basic、C#)
description: 瞭解如何使用 Icon 屬性來指定檔案總管的圖示，以及針對已編譯的應用程式顯示的 Windows 工作列。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 34405fd52b49e89c2fa0fc95ec1268448bad3061
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596907"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>如何：指定應用程式圖示 (Visual Basic、C#)

專案的 `Icon` 屬性指定已編譯的應用程式將會顯示在 **檔案總管** 和 Windows 工作列的圖示檔 (*.ico*)。

透過 [專案設計工具] 的 [應用程式] 窗格，即可存取 `Icon` 屬性；該屬性包含圖示清單，其中的圖示都已經用資源或內容檔案的形式新增至專案。

> [!NOTE]
> 設定應用程式的 Icon 屬性之後，您也可以設定應用程式中每個 [視窗] 或 [表單] 的 `Icon` 屬性。 如需 Windows Presentation Foundation (WPF) 獨立應用程式之視窗圖示的詳細資訊，請參閱 <xref:System.Windows.Window.Icon%2A> 屬性。

## <a name="to-specify-an-application-icon"></a>指定應用程式圖示

1. 在方案總管中，選擇專案節點 (而不是 [方案] 節點)。

1. 在功能表列上，選擇 [**專案**  >  **屬性**]。

1. 當 [專案設計工具] 出現時，請選擇 [應用程式] 索引標籤。

1. **(Visual Basic)** &mdash;在 [**圖示**] 清單中，選擇 (*.ico*) 檔案的圖示。

    **C #** &mdash;在 **圖示** 清單附近，選擇該 **\<Browse...>** 按鈕，然後流覽至您想要的圖示檔位置。

## <a name="see-also"></a>另請參閱

- [[專案設計工具]、[應用程式] 頁面 (Visual Basic) ](../ide/reference/application-page-project-designer-visual-basic.md)
- [應用程式頁面、專案設計工具 (c # ) ](../ide/reference/application-page-project-designer-csharp.md)
