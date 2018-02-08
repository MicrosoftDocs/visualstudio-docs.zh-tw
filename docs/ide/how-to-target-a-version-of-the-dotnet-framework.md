---
title: "如何：以 .NET Framework 版本為目標 | Microsoft Docs"
ms.custom: 
ms.date: 12/08/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: da2e236c39cce72670a47212aedabb87afa4d217
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>如何：以 .NET Framework 版本為目標

本文件描述如何在建立專案時以某個 .NET Framework 版本為目標，以及如何變更現有 Visual Basic、Visual C# 或 Visual F# 專案的目標版本。

> [!IMPORTANT]
> 如需如何變更 C++ 專案之目標版本的詳細資訊，請參閱[如何：修改目標 Framework 和平台工具組](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)。

## <a name="targeting-a-version-when-you-create-a-project"></a>在建立專案時設定目標版本

當您建立專案時，做為目標的 .NET Framework 版本會決定您可以使用的範本。

### <a name="to-target-a-version-when-you-create-a-project"></a>若要在建立專案時設定目標版本

1.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。

2.  在 [新增專案] 對話方塊頂端的清單中，選擇要設定為專案目標的 .NET Framework 版本。

3.  在已安裝的範本清單中，選擇您要建立的專案類型，為專案命名，然後選擇 [確定] 按鈕。

    範本清單只會顯示您所選 .NET Framework 版本支援的那些專案。

## <a name="changing-the-target-version"></a>變更目標版本

您可以遵循下列順序變更 Visual Basic、C# 或 Visual F# 專案中的目標 .NET Framework 版本。

如需如何變更 C++ 專案之目標版本的詳細資訊，請參閱[如何：修改目標 Framework 和平台工具組](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)。

### <a name="to-change-the-targeted-version"></a>若要變更目標版本

1.  在方案總管中開啟您所要變更專案的捷徑功能表，然後選擇 [屬性]。

    ![Visual Studio 方案總管的 [屬性]](../ide/media/vs_slnexplorer_properties.png "vs_slnExplorer_Properties")

2. 在 [屬性] 視窗的左欄中，選擇 **[應用程式]** 索引標籤。

    ![Visual Studio 應用程式、[屬性]、[應用程式] 索引標籤](../ide/media/vs_slnexplorer_properties_applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")

    > [!NOTE]
    > 在建立 UWP 應用程式之後，就無法變更 Windows 或 .NET Framework 的目標版本。

3.  在 [目標 Framework] 清單中，選擇您要的版本。

4.  在出現的驗證對話方塊中，選擇 [是] 按鈕。

    專案將會卸載。 當您重新載入專案時，它會以您剛剛選擇的 .NET Framework 版本為目標。

    > [!NOTE]
    > 如果您的程式碼包含的 .NET Framework 版本參考與您的目標版本不同，則會在您編譯或執行程式碼時出現錯誤訊息。 若要解決這些錯誤，您必須修改參考。 請參閱[針對 .NET Framework 目標錯誤進行疑難排解](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)。

## <a name="see-also"></a>另請參閱

[Visual Studio 多目標概觀](../ide/visual-studio-multi-targeting-overview.md)  
[進行 .NET Framework 目標錯誤的疑難排解](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)  
[專案設計工具，應用程式頁面 (C#)](../ide/reference/application-page-project-designer-csharp.md)  
[專案設計工具、應用程式頁面 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)  
[如何：修改目標 Framework 和平台工具組 (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)