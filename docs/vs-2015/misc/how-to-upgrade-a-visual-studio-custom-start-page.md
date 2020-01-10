---
title: 如何：升級自訂起始頁 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 78342ce6-36c8-485b-a5f6-760e7a420a26
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: a7854de705a961463b1e8435e7340548cfc23bf3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293379"
---
# <a name="how-to-upgrade-a-visual-studio-custom-start-page"></a>如何：升級 Visual Studio 自訂起始頁
依照下列步驟，即可將 Visual Studio 2010 或 Visual Studio 2012 自訂起始頁升級成 Visual Studio 2015。

> [!WARNING]
> 在這個程序中升級的自訂起始頁是使用 Visual Studio 組件庫中的 [自訂起始頁](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.CustomStartPageProjectTemplate) 樣板所建立的自訂起始頁。 您的起始頁可能有需要升級的其他功能。

### <a name="to-upgrade-a-custom-start-page-to-visual-studio-2015"></a>將自訂起始頁升級至 Visual Studio 2015

1. 請確定已安裝 Visual Studio 2015 和 Visual Studio 2015 SDK。 您可以從 [Microsoft Visual Studio 2013 SDK](https://my.visualstudio.com/Downloads?pid=1436)下載 VSSDK。

2. 開啟您的自訂樣板專案。 您會看到訊息，通知您要升級專案。 按一下 [確定] ，並等候升級完成。

3. 在起始頁專案和控制項專案的專案屬性中，確定 [目標架構] 至少為 .NET Framework 4.5。

4. 在起始頁專案之專案屬性的 [偵錯] 分類中，設定 devenv.exe 之 Visual Studio 2015 版本的路徑。

5. 在這兩個專案的專案參考中，移除 Microsoft.VisualStudio.Shell.11.0 的參考，並將參考加入 Microsoft.VisualStudio.Shell.14.0。

6. 使用 XML 編輯器開啟 StartPage.xaml，然後進行下列變更：

    1. 更新命名空間。 變更下列各行：

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"
        ```

         為下列內容：

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.142.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.14.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        ```

7. 開啟 MyControl.xaml，並將命名空間參考 `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"` 變更為 `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"` 。