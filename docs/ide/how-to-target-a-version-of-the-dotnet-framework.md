---
title: 在 Visual Studio 中將某個 .NET Framework 版本設定為目標
ms.date: 02/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- .NET Framework version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 36599475e743259d8cf09d24172a633b54b09693
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752303"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>如何：將 .NET Framework 的某個版本設定為目標

本文件描述如何在建立專案時以某個 .NET Framework 版本為目標，以及如何變更現有 Visual Basic、Visual C# 或 Visual F# 專案的目標版本。

> [!IMPORTANT]
> 如需如何變更 C++ 專案之目標版本的資訊，請參閱[如何：修改目標 Framework 和平台工具組](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)。

## <a name="to-target-a-version-when-you-create-a-project"></a>若要在建立專案時設定目標版本

當您建立專案時，可用的 .NET Framework 版本視已安裝的版本，以及在 [新增專案] 對話方塊中選取的範本而定。

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]。

1. 在已安裝範本的清單中，選擇您要建立之專案的類型，然後輸入專案名稱。

1. 從 [新增專案] 對話方塊方塊底部的 [Framework] 下拉式清單中，選擇您想要作為專案目標的 .NET Framework 版本。

    架構清單只會顯示適用於您所選範本的版本。 某些專案類型 (如 .NET Core) 不需要.NET Framework。 在此情況下，系統會隱藏 [Framework] 下拉式清單。

    ![[新增專案] 對話方塊中的 [Framework] 下拉式清單](media/vside-newproject-framework.png)

1. 選擇 [確定]  按鈕。

## <a name="to-change-the-targeted-version"></a>若要變更目標版本

您可以遵循下列順序變更 Visual Basic、C# 或 Visual F# 專案中的目標 .NET Framework 版本。

如需如何變更 C++ 專案之目標版本的資訊，請參閱[如何：修改目標 Framework 和平台工具組](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)。

1. 在方案總管中開啟您所要變更專案的捷徑功能表，然後選擇 [屬性]。

    ![Visual Studio [方案總管]、[屬性]](../ide/media/vs_slnexplorer_properties.png)

1. 在 [屬性] 視窗的左欄中，選擇 [應用程式] 索引標籤。

    ![Visual Studio 應用程式、[屬性]、[應用程式] 索引標籤](../ide/media/vs_slnexplorer_properties_applicationtab.png)

    > [!NOTE]
    > 在建立 UWP 應用程式之後，就無法變更 Windows 或 .NET Framework 的目標版本。

1. 在 [目標 Framework] 清單中，選擇您要的版本。

1. 在出現的驗證對話方塊中，選擇 [是] 按鈕。

    專案將會卸載。 當您重新載入專案時，它會以您剛剛選擇的 .NET Framework 版本為目標。

    > [!NOTE]
    > 如果您的程式碼包含的 .NET Framework 版本參考與您的目標版本不同，則會在您編譯或執行程式碼時出現錯誤訊息。 若要解決這些錯誤，您必須修改參考。 請參閱[針對 .NET Framework 目標錯誤進行疑難排解](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 多目標概觀](../ide/visual-studio-multi-targeting-overview.md)
- [針對 .NET Framework 目標錯誤進行疑難排解](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [應用程式頁面、專案設計工具 (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [應用程式頁面、專案設計工具 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [如何：修改目標 Framework 和平台工具組 (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)