---
title: 目標 .NET Framework
description: 瞭解如何指定您要作為專案目標的 .NET Framework 版本，讓應用程式只能使用指定版本中可用的功能。
ms.date: 03/31/2020
ms.topic: overview
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9bc20c2ee08a2b838e0fd1ab14ee9a8388912542
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479728"
---
# <a name="framework-targeting-overview"></a>Framework 目標概觀

在 Visual Studio 中，您可以指定要讓專案設為目標的 .NET 版本。 Framework 目標有助於確保應用程式只使用指定 Framework 版本中可供使用的功能。 若要讓 .NET Framework 應用程式在另一部電腦上執行，該應用程式的目標 Framework 版本必須與該電腦上所安裝的 Framework 版本相容。

Visual Studio 解決方案可以包含以不同 .NET 版本為目標的專案。  不過，請注意，您只能使用單一組建的參考條件，或針對每個版本以遞迴方式建立不同的二進位檔，以建立單一版本的 .NET。  如需目標 Framework 的詳細資訊，請參閱[目標 Framework](/dotnet/standard/frameworks)。

> [!TIP]
> 您也可以針對不同平台的應用程式。 如需詳細資訊，請參閱[多目標](../msbuild/msbuild-multitargeting-overview.md)。

## <a name="framework-targeting-features"></a>Framework 目標功能

Framework 目標包括下列功能：

- 當您開啟以舊版 Framework 為目標的專案時，Visual Studio 可以自動將該專案升級，或是保留其目標。

- 當您建立 .NET Framework 專案時，您可以指定想要作為目標的 .NET Framework 版本。

- 您可以在單一專案中[以多個 Framework 為目標](/dotnet/standard/frameworks#how-to-specify-target-frameworks)。

- 在相同方案中，您可以讓數個不同的專案個別以不同版本的 .NET 為目標。

- 您可以變更現有專案的目標 .NET 版本。

   當您變更專案的目標 .NET 版本時，Visual Studio 會對參考和設定檔進行必要的變更。

當您使用以舊版 Framework 為目標的專案時，Visual Studio 會動態地變更開發環境，如下所示：

- 它會篩選 [新增新項目] 對話方塊、[新增參考] 對話方塊，以及 [新增服務參考] 對話方塊中的項目，以省略目標版本中未提供的選項。

- 它會在有多個控制項可供使用時，篩選 [工具箱] 中的自訂控制項，以移除目標版本中未提供的控制項，只顯示最新版控制項。

- 它會篩選 **IntelliSense** 以省略目標版本中未提供的語言功能。

- 它會篩選 [屬性] 視窗中的屬性，以省略目標版本中未提供的屬性。

- 它會篩選功能表選項，以省略目標版本中未提供的選項。

- 對於組建，它會使用適用於目標版本的編譯器版本和編譯器選項。

> [!NOTE]
> - Framework 目標不保證您的應用程式將會正確執行。 您必須測試應用程式，確定它能以目標版本執行。
> - 您不能以低於 .NET Framework 2.0 的 Framework 版本為目標。

## <a name="select-a-target-framework-version"></a>選取目標 Framework 版本

當您建立 .NET Framework 專案時，您可以在選取專案範本後選取目標 .NET Framework 版本。 可用架構的清單包含適用於所選取範本類型的已安裝之架構版本。 針對非 .NET Framework 的專案範本 (例如 .NET Core 範本)，系統會隱藏 [Framework] 下拉式清單。

::: moniker range="vs-2017"

![VS 2017 的 Framework 下拉式清單](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![VS 2019 的 Framework 下拉式清單](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="change-the-target-framework"></a>變更目標 Framework

在現有 Visual Basic、C# 或 F# 專案中，您可以在 [專案屬性] 對話方塊中變更目標 .NET 版本。 如需如何變更 C++ 專案之目標版本的資訊，請改為參閱[如何修改目標 Framework 和平台工具組](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)。

1. 在 [方案總管] 中，開啟您所要變更專案的右鍵功能表，然後選擇 [屬性]。

1. 在 [ **屬性** ] 視窗的左欄中，選擇 [ **應用程式** ] 索引標籤。

   ![[專案屬性應用程式] 索引標籤](../ide/media/vs_slnexplorer_properties_applicationtab.png)

   > [!NOTE]
   > 在建立 UWP 應用程式之後，就無法變更 Windows 或 .NET 的目標版本。

1. 在 [目標 Framework] 清單中，選擇您要的版本。

1. 在出現的驗證對話方塊中，選擇 [是] 按鈕。

   專案將會卸載。 當您重新載入專案時，它會以您剛剛選擇的 .NET 版本為目標。

> [!NOTE]
> 如果您的程式碼包含與您目標版本不同的 .NET 版本參考，則在您編譯或執行程式碼時，可能會出現錯誤訊息。 若要解決這些錯誤，請修改參考。 請參閱[針對 .NET 目標錯誤進行疑難排解](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)。

> [!TIP]
> 視目標 Framework 而定，它可以在專案檔中以下列方式呈現：
>
> - 針對 .NET Core 應用程式：`<TargetFramework>netcoreapp2.1</TargetFramework>`
> - 針對 .NET Standard 應用程式：`<TargetFramework>netstandard2.0</TargetFramework>`
> - 針對 .NET Framework 應用程式：`<TargetFrameworkVersion>v4.7.2</TargetFrameworkVersion>`

## <a name="resolve-system-and-user-assembly-references"></a>解析系統與使用者組件參考

若要設定目標 .NET 版本，您必須先安裝適當的組件參考。 您可以在 [.NET 下載](https://www.microsoft.com/net/download/windows) \(英文\) 頁面上下載不同 .NET 版本的開發人員套件。

針對 .NET Framework 專案，[新增參考] 對話方塊會停用與目標 .NET Framework 版本無關的系統組件，如此一來就不會不慎將那些系統組件新增至專案。  (系統元件是包含在 .NET Framework 版本中的 *.dll* 檔。不會解析屬於高於目標版本之 Framework 版本的 ) 參考，也無法新增相依于這類參考的控制項。 如果您想要啟用這類參考，請將專案的 .NET Framework 目標重設為包含參考的目標。

如需組件參考的詳細資訊，請參閱[在設計階段時解析組件](../msbuild/resolving-assemblies-at-design-time.md)。

## <a name="enable-linq"></a>啟用 LINQ

當您以 .NET Framework 3.5 或更新版本為目標時，會自動新增 **System.Core** 的參考與 <xref:System.Linq> 的專案層級匯入 (僅限 Visual Basic)。 如果要使用 LINQ 功能，您必須同時開啟 `Option Infer` (僅限 Visual Basic)。 如果將目標變更為舊版 .NET Framework，就會自動移除參考和匯入。 如需詳細資訊，請參閱[使用 LINQ](/dotnet/csharp/tutorials/working-with-linq)。

## <a name="see-also"></a>另請參閱

- [目標架構](/dotnet/standard/frameworks)
- [多目標 (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [如何：修改目標 framework 和平臺工具組 (c + +) ](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
