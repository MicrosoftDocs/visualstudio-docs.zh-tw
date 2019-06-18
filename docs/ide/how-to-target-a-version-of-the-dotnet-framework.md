---
title: 以一個 .NET 版本為目標
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET [Visual Studio]
- .NET version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2c316610fc007e3e8642567c01a5172feb461bda
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747128"
---
# <a name="how-to-target-a-version-of-net"></a>作法：以 .NET 的一個版本為目標

本文描述如何在建立 .NET Framework 專案時以特定版本的 .NET framework 作為目標。 其也會描述如何變更現有 Visual Basic、C# 或 F# 專案中的目標版本。

> [!IMPORTANT]
> 如需如何變更 C++ 專案目標版本的資訊，請參閱[如何：修改目標 Framework 和平台工具組](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)。

## <a name="target-a-version-when-you-create-a-project"></a>在建立專案時設定目標版本

當您建立 .NET Framework 專案時，可用的 .NET Framework 版本會視已安裝的版本及所選的專案範本而定。

1. 在功能表列上，選擇 [檔案]   > [新增]   > [專案]  。

1. 針對您想要建立之專案類型選擇 .NET Framework 範本。

1. 從對話方塊底部的 [Framework]  下拉式清單中，選擇您想要作為專案目標的 .NET Framework 版本。

   架構清單只會顯示適用於您所選範本的版本。

   > [!NOTE]
   > 某些專案類型 (例如 .NET Core) 不會顯示 [Framework]  下拉式清單。

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 [新增專案] 對話方塊中的 [Framework] 下拉式清單](media/vside-newproject-framework.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![VS 2019 的 Framework 選取器](media/vs-2019/configure-new-project-framework.png)

   ::: moniker-end

1. 繼續[建立專案](create-new-project.md)。

## <a name="change-the-targeted-version"></a>變更目標版本

您可以遵循此程序來變更 Visual Basic、C# 或 F# 專案中的目標 .NET 版本。

1. 在方案總管  中開啟您所要變更專案的捷徑功能表，然後選擇 [屬性]  。

    ![Visual Studio [方案總管]、[屬性]](../ide/media/vs_slnexplorer_properties.png)

1. 在 [屬性]  視窗的左欄中，選擇 [應用程式]  索引標籤。

    ![Visual Studio 應用程式、[屬性]、[應用程式] 索引標籤](../ide/media/vs_slnexplorer_properties_applicationtab.png)

    > [!NOTE]
    > 在建立 UWP 應用程式之後，就無法變更 Windows 或 .NET 的目標版本。

1. 在 [目標 Framework]  清單中，選擇您要的版本。

1. 在出現的驗證對話方塊中，選擇 [是]  按鈕。

    專案將會卸載。 當您重新載入專案時，它會以您剛剛選擇的 .NET 版本為目標。

    > [!NOTE]
    > 如果您的程式碼包含與您目標版本不同的 .NET 版本參考，則在您編譯或執行程式碼時，可能會出現錯誤訊息。 若要解決這些錯誤，您必須修改參考。 請參閱[針對 .NET 目標錯誤進行疑難排解](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)。

## <a name="see-also"></a>另請參閱

- [Framework 目標概觀](../ide/visual-studio-multi-targeting-overview.md)
- [針對 .NET Framework 目標錯誤進行疑難排解](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [應用程式頁面、專案設計工具 (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [應用程式頁面、專案設計工具 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [如何：修改目標 Framework 和平台工具組 (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)