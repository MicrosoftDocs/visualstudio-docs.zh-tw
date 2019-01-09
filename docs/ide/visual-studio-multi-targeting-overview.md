---
title: 以 .NET Framework 為目標
ms.date: 02/06/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 763e02dbd491e132dc91ec7a79717fab1e645d86
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955197"
---
# <a name="visual-studio-multi-targeting-overview"></a>Visual Studio 多目標概觀

在 Visual Studio 中，您可以指定要讓專案使用的目標 .NET Framework 版本或設定檔。 如果應用程式會在另一部電腦上執行，則該應用程式的目標 Framework 版本必須與該電腦上安裝的 Framework 版本相容。

您也可以建立包含以不同 Framework 版本為目標之專案的方案。 Framework 目標有助於確保應用程式只使用指定的 Framework 版本中可供使用的功能。

> [!TIP]
> 您也可以針對不同平台的應用程式。 如需詳細資訊，請參閱[多目標](../msbuild/msbuild-multitargeting-overview.md)。

## <a name="framework-targeting-features"></a>Framework 目標功能

Framework 目標包括下列功能：

- 當您開啟以舊版 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 為目標的專案時，Visual Studio 會自動將專案升級，或保留其目標。

- 當您建立專案時，您可以指定要以哪一個版本的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 為目標。

- 您可以變更現有專案的目標 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本。

- 您可以在相同方案的數個不同專案中，以不同版本的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 為目標。

- 當您變更專案的目標 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本時，[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 會對參考和組態檔進行任何必要的變更。

當您使用以舊版 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 為目標的專案時，Visual Studio 會動態變更開發環境，例如：

- 它會篩選 [新增新項目] 對話方塊、[新增參考] 對話方塊，以及 [新增服務參考] 對話方塊中的項目，以省略目標版本中未提供的選項。

- 它會在有多個控制項可供使用時，篩選 [工具箱] 中的自訂控制項，以移除目標版本中未提供的控制項，只顯示最新版控制項。

- 它會篩選 **IntelliSense**，以省略目標版本中未提供的語言功能。

- 它會篩選 [屬性] 視窗中的屬性，以省略目標版本中未提供的屬性。

- 它會篩選功能表選項，以省略目標版本中未提供的選項。

- 對於組建，它會使用適用於目標版本的編譯器版本和編譯器選項。

> [!NOTE]
> Framework 目標不保證您的應用程式將會正確執行。 您必須測試應用程式，確定它能以目標版本執行。 您不能以早於 .NET Framework 2.0 版的 Framework 版本為目標。

## <a name="select-a-target-framework-version"></a>選取目標 Framework 版本

當您建立專案時，請在 [新增專案] 對話方塊中選取目標 .NET Framework 版本。 可用架構的清單包含適用於所選取範本類型的已安裝之架構版本。 對於不需要 .NET Framework 的範本類型 (如 .NET Core 範本)，系統會隱藏 [Framework] 下拉式清單。

![[新增專案] 對話方塊中的 [Framework] 下拉式清單](media/vside-newproject-framework.png)

在現有專案中，您可以在專案屬性對話方塊中變更目標 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本。 如需詳細資訊，請參閱[＜How to：以一個 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。

## <a name="resolve-system-and-user-assembly-references"></a>解析系統與使用者組件參考

若要設定目標 .NET Framework 版本，您必須先安裝適當的組件參考。 您可以在 [.NET 下載](https://www.microsoft.com/net/download/windows)頁面下載不同 .NET Framework 版本的開發人員套件。

[加入參考] 對話方塊會停用與目標 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本無關的系統組件，如此一來就不會不慎將系統組件新增至專案。 (系統組件是包含在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本中的 *.dll* 檔案)。無法解析屬於晚於目標版本之 Framework 版本的參考，也無法新增相依於這類參考的控制項。 如果您想要啟用這類參考，請將專案的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 目標重設為包含參考的目標。  如需詳細資訊，請參閱[＜How to：以一個 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。

如需組件參考的詳細資訊，請參閱[在設計階段時解析組件](../msbuild/resolving-assemblies-at-design-time.md)。

## <a name="enable-linq"></a>啟用 LINQ

當您以 .NET Framework 3.5 或更新版本為目標時，會自動新增 **System.Core** 的參考與 <xref:System.Linq> 的專案層級匯入 (僅限 Visual Basic)。 如果要使用 LINQ 功能，您必須同時開啟 `Option Infer` (僅限 Visual Basic)。 如果將目標變更為舊版 .NET Framework，就會自動移除參考和匯入。 如需詳細資訊，請參閱[使用 LINQ](/dotnet/csharp/tutorials/working-with-linq)。

## <a name="see-also"></a>另請參閱

- [多目標 (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [如何：修改目標 Framework 和平台工具組 (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)