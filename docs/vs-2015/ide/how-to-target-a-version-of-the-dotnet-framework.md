---
title: 如何：以 .NET Framework 版本為目標 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 53
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7aae21e2c959939262b88db3b90367c4860d8a74
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670625"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>如何：以 .NET Framework 版本為目標
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本文件說明如何在建立專案時以某個 .NET Framework 版本為目標，以及如何變更現有 Visual Basic、Visual C# 或 Visual F# 專案的目標版本。

> [!IMPORTANT]
> 如需如何變更 C++ 專案之目標版本的詳細資訊，請參閱[如何：修改目標 Framework 和平台工具組](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)。

 **本主題內容**

- [在建立專案時設定目標版本](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)

- [變更目標版本](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)

## <a name="bkmk_new"></a> 在建立專案時設定目標版本
 當您建立專案時，做為目標的 .NET Framework 版本會決定您可以使用的範本。

> [!NOTE]
> 在 Visual Studio Express 版中，您必須先建立專案，才能變更目標，如本主題稍後的[變更目標版本](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)中所述。

#### <a name="to-target-a-version-when-you-create-a-project"></a>若要在建立專案時設定目標版本

1. 在功能表列上，選擇 [ **檔案**]、[ **新增**]、[ **專案**]。

2. 在 [新增專案] 對話方塊頂端的清單中，選擇要設定為專案目標的 .NET Framework 版本。

    > [!NOTE]
    > 通常，只有一個 .NET Framework 版本會與 Visual Studio 一起安裝。 如果您要以另一個版本為目標，則必須先確定該版本已安裝。 請參閱 [Visual Studio 多目標概觀](../ide/visual-studio-multi-targeting-overview.md)。

3. 在已安裝的範本清單中，選擇您要建立的專案類型，為專案命名，然後選擇 [確定] 按鈕。

     範本清單只會顯示您所選 .NET Framework 版本支援的那些專案。

## <a name="bkmk_existing"></a> 變更目標版本
 您可以遵循下列順序變更 Visual Basic、Visual C# 或 Visual F# 專案中的目標 .NET Framework 版本。

#### <a name="to-change-the-targeted-version"></a>若要變更目標版本

1. 在方案總管中開啟您所要變更專案的捷徑功能表，然後選擇 [屬性]。

     ![Visual Studio 方案總管屬性](../ide/media/vs-slnexplorer-properties.png "vs_slnExplorer_Properties")

    > [!IMPORTANT]
    > 如需如何變更 C++ 專案之目標版本的詳細資訊，請參閱[如何：修改目標 Framework 和平台工具組](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)。

2. 在 [屬性] 視窗的左欄中，選擇 **[應用程式]** 索引標籤。

     ![Visual Studio 應用程式屬性應用程式索引標籤](../ide/media/vs-slnexplorer-properties-applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")

    > [!NOTE]
    > 在建立 Windows 市集應用程式之後，就無法變更 Windows 或 .NET Framework 的目標版本。

3. 在 [目標 Framework] 清單中，選擇您要的版本。

4. 在出現的驗證對話方塊中，選擇 [是] 按鈕。

     專案將會卸載。 當您重新載入專案時，它會以您剛剛選擇的 .NET Framework 版本為目標。

    > [!NOTE]
    > 如果您的程式碼包含的 .NET Framework 版本參考與您的目標版本不同，則會在您編譯或執行程式碼時出現錯誤訊息。 若要解決這些錯誤，您必須修改參考。 請參閱[針對 .NET Framework 目標錯誤進行疑難排解](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)。

## <a name="see-also"></a>請參閱
 [Visual Studio 多目標總覽](../ide/visual-studio-multi-targeting-overview.md) [.NET Framework ASP.NET Web 專案的多重目標](https://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)[疑難排解 .NET Framework 目標錯誤](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)[應用程式頁面、專案設計工具（C#）](../ide/reference/application-page-project-designer-csharp.md) [應用程式頁面、專案設計工具（Visual Basic）](../ide/reference/application-page-project-designer-visual-basic.md)設定[專案](https://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)[如何：修改目標 Framework 和平臺工具](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)組
