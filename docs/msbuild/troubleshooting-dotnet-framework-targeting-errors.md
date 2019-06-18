---
title: 針對 .NET Framework 目標錯誤進行疑難排解 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 465952fa41eab7d112ca839be2940cded3d69b33
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744618"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>針對 .NET Framework 目標錯誤進行疑難排解
本主題說明可能因參考問題造成的 MSBuild 錯誤，以及如何解決這些錯誤。

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>您參考了以不同 .NET Framework 版本為目標的專案或組件
 您可以建立會參考以不同 .NET Framework 版本為目標之專案或組件的應用程式。 例如，您可以建立以適用於 .NET Framework 4 的用戶端設定檔為目標的應用程式，但讓該應用程式參考以 .NET Framework 2.0 為目標的組件。 不過，如果您建立的專案是以舊版 .NET Framework 為目標，就無法將該專案中的參考設定至以適用於 .NET Framework 4 的用戶端設定檔或 .NET Framework 4 本身為目標的專案或組件。 若要解決這個錯誤，請確定您應用程式的目標設定檔，與應用程式所參考之專案或組件的目標設定檔相容。

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>您將專案的目標重定為不同版本的 .NET Framework
 如果您變更您應用程式的 .NET Framework 目標版本，Visual Studio 會自動變更一些參考，但您可能需要手動更新其他參考。 例如，如果您將應用程式變更為以 [!INCLUDE[net_v35SP1_long](../msbuild/includes/net_v35sp1_long_md.md)] 為目標，且該應用程式具有依賴適用於 .NET Framework 4 之用戶端設定檔的資源或設定，就可能發生上述的其中一個錯誤。

 若要解決應用程式設定，請開啟 [方案總管]  ，選擇 [顯示所有檔案]  ，然後在 Visual Studio 的 XML 編輯器中編輯 *app.config* 檔案。 將設定中的版本變更為符合 .NET Framework 的適當版本。 例如，您可以將版本設定從 4.0.0.0 變更為 2.0.0.0。 同樣地，針對加入資源的應用程式，請開啟 [方案總管]  ，選擇 [顯示所有檔案]  按鈕，展開 [我的專案]  (Visual Basic) 或 [屬性]  (C#)，然後在 Visual Studio 的 XML 編輯器中編輯 *Resources.resx* 檔案。 將版本設定從 4.0.0.0 變更為 2.0.0.0。

 如果您的應用程式具有資源 (例如圖示或點陣圖) 或設定 (例如資料連接字串)，您也可以透過在 [專案設計工具]  的 [設定]  頁面上移除所有的項目，然後重新加入必要的設定來解決錯誤。

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>您將專案的目標重定為不同版本的 .NET Framework 後無法解析參考
 如果您將專案的目標重新設定為不同版本的 .NET Framework，系統在某些情況下可能會無法正確解析您的參考。 對組件進行明確的完整參考通常會造成這個問題，但您可以將無法解析的參考移除，然後將它們重新加回專案來解決這個問題。 或者，您可以編輯專案檔來取代參考。 首先，您要移除下列形式的參考：

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 然後以簡單的形式取代它們：

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
> 在關閉並重新開啟專案後，您也應該重建它，以確保能夠正確解析所有參考。

## <a name="see-also"></a>另請參閱

- [如何：以一個 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)
- [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile)
- [Framework 目標概觀](../ide/visual-studio-multi-targeting-overview.md)
- [多目標](../msbuild/msbuild-multitargeting-overview.md)