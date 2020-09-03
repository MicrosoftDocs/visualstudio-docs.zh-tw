---
title: 多目標概觀 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9e8b53c5bd4d6045d7582c24be865ae216f1114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851093"
---
# <a name="visual-studio-multi-targeting-overview"></a>Visual Studio 多目標概觀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在這個版本的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中，您可以指定應用程式所需的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本。 因此，如果您要使用這個版本的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 繼續開發您在舊版中開始的專案，您不必變更 Framework 目標。 您也可以建立包含以不同 Framework 版本為目標之專案的方案。 Framework 目標也有助於確保應用程式只使用指定的 Framework 版本中可供使用的功能。

> [!TIP]
> 您也可以針對不同平台的應用程式。 如需詳細資訊，請參閱 [多目標](../msbuild/msbuild-multitargeting-overview.md)

## <a name="framework-targeting-features"></a>Framework 目標功能
 Framework 目標包括下列功能：

- 當您開啟以舊版 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 為目標的專案時，[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 會自動將專案升級，或保留其目標。

- 當您建立專案時，您可以指定要以哪一個版本的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 為目標。

- 您可以變更現有專案的目標 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本。

- 您可以在相同方案的數個不同專案中，以不同版本的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 為目標。

- 當您變更專案的目標 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本時，[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 會對參考和組態檔進行任何必要的變更。

  當您使用以舊版 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 為目標的專案時，Visual Studio 會動態變更開發環境，例如：

- 它會篩選 [新增專案]**** 對話方塊、[加入新項目]**** 對話方塊、[加入新參考]**** 對話方塊和 [加入服務參考]**** 對話方塊中的項目，以省略目標版本中未提供的選項。

- 它會在有多個控制項可供使用時，篩選 [工具箱]**** 中的自訂控制項，以移除目標版本中未提供的控制項，只顯示最新版控制項。

- 它會篩選 IntelliSense，以省略目標版本中未提供的語言功能。

- 它會篩選 [屬性]**** 視窗中的屬性，以省略目標版本中未提供的屬性。

- 它會篩選功能表選項，以省略目標版本中未提供的選項。

- 對於組建，它會使用適用於目標版本的編譯器版本和編譯器選項。

> [!NOTE]
> Framework 目標不保證您的應用程式將會正確執行。 您必須測試應用程式，確定它能以目標版本執行。 您不能以早於 .NET Framework 2.0 版的 Framework 版本為目標。

## <a name="selecting-a-target-framework-version"></a>選取目標 Framework 版本
 當您建立專案時，請在 [新增專案]**** 對話方塊中選取目標 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本。 可用的專案範本清單會根據選取項目進行篩選。 在現有專案中，您可以在專案屬性對話方塊中變更目標 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本。 如需詳細資訊，請參閱 [如何：以 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。

> [!NOTE]
> 在 Visual Studio Express 版中，您無法在 [新增專案]**** 對話方塊中設定目標 Framework。

## <a name="resolving-system-and-user-assembly-references"></a>解析系統與使用者組件參考
 若要設定目標 .NET Framework 版本，您必須先安裝適當的組件參考。 .NET Framework 2.0、3.0 和 3.5 版的組件參考隨附在 .NET Framework 3.5 SP1 中，可從 [Microsoft Download Center, Microsoft Visual Studio](https://www.microsoft.com/download/details.aspx?id=25150) (Microsoft 下載中心的 Microsoft Visual Studio) 網站進行下載。 您也可以從 [Visual Studio 下載](https://msdn.microsoft.com/vstudio/bb984878.aspx)網站取得 .NET Framework 3.5 Client Profile、.NET Framework 4、.NET Framework 4 Client Profile 和 Silverlight 的組件參考。

> [!NOTE]
> .NET Framework Client Profile 是 .NET Framework 的子集，提供一組有限的程式庫和功能。 如需 Client Profile 的詳細資訊，請參閱 [.NET Framework Client Profile](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)。

 [加入參考]**** 對話方塊會停用與目標 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本無關的系統組件，如此一來就不會不慎將系統組件新增至專案。  (系統元件是包含在版本中的 .dll 檔案。 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 屬於目標版本之 framework 版本的 ) 參考將無法解析，且相依于這類參考的控制項無法加入。 如果您想要啟用這類參考，請將專案的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 目標重設為包含參考的目標。  如需詳細資訊，請參閱[專案設計工具簡介](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7)。

 如需組件參考的詳細資訊，請參閱[在設計階段時解析組件](../msbuild/resolving-assemblies-at-design-time.md)。

## <a name="enabling-linq"></a>啟用 LINQ
 當您以 .NET Framework 3.5 或更新版本為目標時，會自動新增 System.Core 的參考與 System.Linq 的專案層級匯入 (僅限 Visual Basic)。 如果要使用 LINQ 功能，您必須同時開啟 [推斷選項]\ (僅限 Visual Basic)。 如果將目標變更為舊版 .NET Framework，就會自動移除參考和匯入。 如需詳細資訊，請參閱[如何：建立 LINQ 專案](https://msdn.microsoft.com/library/a929e653-09a3-44be-881f-68ca33f192b2)。

## <a name="see-also"></a>另請參閱
[多目標](../msbuild/msbuild-multitargeting-overview.md) 
[.NET Framework ASP.NET Web 專案](https://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76) 
 的多目標[平臺相容性和系統需求](/visualstudio/productinfo/vs2015-compatibility-vs)
