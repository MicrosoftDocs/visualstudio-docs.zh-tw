---
title: "在 Visual Studio 中以 .NET Framework 為目標 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: c3d388238b443fcb717502a893a674f99a315f38
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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

- 它會篩選 [新增專案] 對話方塊、[加入新項目] 對話方塊、[加入新參考] 對話方塊和 [加入服務參考] 對話方塊中的項目，以省略目標版本中未提供的選項。

- 它會在有多個控制項可供使用時，篩選 [工具箱] 中的自訂控制項，以移除目標版本中未提供的控制項，只顯示最新版控制項。

- 它會篩選 IntelliSense，以省略目標版本中未提供的語言功能。

- 它會篩選 [屬性] 視窗中的屬性，以省略目標版本中未提供的屬性。

- 它會篩選功能表選項，以省略目標版本中未提供的選項。

- 對於組建，它會使用適用於目標版本的編譯器版本和編譯器選項。

> [!NOTE]
> Framework 目標不保證您的應用程式將會正確執行。 您必須測試應用程式，確定它能以目標版本執行。 您不能以早於 .NET Framework 2.0 版的 Framework 版本為目標。

## <a name="selecting-a-target-framework-version"></a>選取目標 Framework 版本

當您建立專案時，請在 [新增專案] 對話方塊中選取目標 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本。 可用的專案範本清單會根據選取項目進行篩選。 在現有專案中，您可以在專案屬性對話方塊中變更目標 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本。 如需詳細資訊，請參閱[如何：以 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。

## <a name="resolving-system-and-user-assembly-references"></a>解析系統與使用者組件參考

若要設定目標 .NET Framework 版本，您必須先安裝適當的組件參考。 您可以在 [.NET 下載](https://www.microsoft.com/net/download/windows)頁面下載不同 .NET Framework 版本的開發人員套件。

> [!NOTE]
> 如果您是以 .NET Framework 4 或 3.5 為目標，而且想要深入了解 Client Profile 和其使用時機，請參閱 .NET Framework 4 文件中的 [.NET Framework Client Profile](http://msdn.microsoft.com/library/cc656912\(v=vs.100\).aspx)。

[加入參考] 對話方塊會停用與目標 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本無關的系統組件，如此一來就不會不慎將系統組件新增至專案。 (系統組件是包含在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本中的 .dll 檔案)。無法解析屬於晚於目標版本之 Framework 版本的參考，也無法新增相依於這類參考的控制項。 如果您想要啟用這類參考，請將專案的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 目標重設為包含參考的目標。  如需詳細資訊，請參閱[如何：以 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。

如需組件參考的詳細資訊，請參閱[在設計階段時解析組件](../msbuild/resolving-assemblies-at-design-time.md)。

## <a name="enabling-linq"></a>啟用 LINQ

當您以 .NET Framework 3.5 或更新版本為目標時，會自動新增 System.Core 的參考與 System.Linq 的專案層級匯入 (僅限 Visual Basic)。 如果要使用 LINQ 功能，您必須同時開啟 [推斷選項] (僅限 Visual Basic)。 如果將目標變更為舊版 .NET Framework，就會自動移除參考和匯入。 如需詳細資訊，請參閱[使用 LINQ](/dotnet/csharp/tutorials/working-with-linq)。

## <a name="see-also"></a>另請參閱

[多目標 (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)  
[如何：修改目標 Framework 和平台工具組 (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)  
[平台相容性與系統需求](http://www.microsoft.com/visualstudio/eng/products/compatibility)