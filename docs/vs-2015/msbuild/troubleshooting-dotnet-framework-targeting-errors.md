---
title: 針對 .NET Framework 目標錯誤進行疑難排解 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7795a5577a385542828a3d7c14670696f630544d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430443"
---
# <a name="troubleshooting-net-framework-targeting-errors"></a>疑難排解 .NET Framework 目標錯誤
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題說明可能因參考問題造成的 MSBuild 錯誤，以及如何解決這些錯誤。  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>您參考了以不同 .NET Framework 版本為目標的專案或組件  
 您可以建立以不同版本 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 為目標的專案或組件為參考的應用程式。 例如，您可以建立目標為 [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 用戶端設定檔的應用程式，但參考目標為 .NET Framework 2.0 的組件。 不過，如果您建立的專案是是以舊版的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 為目標，就無法將該專案中的參考設定為以 [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 用戶端設定檔或 [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 本身為目標的專案或組件。 若要解決這個錯誤，請確定您應用程式的目標設定檔，與應用程式所參考之專案或組件的目標設定檔相容。  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>您將專案的目標重定為不同版本的 .NET Framework  
 如果您變更應用程式的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 目標版本，Visual Studio 會變更一些參考，但您可能要手動更新某些參考。 例如，如果您變更應用程式將目標設定為 [!INCLUDE[net_v35SP1_long](../includes/net-v35sp1-long-md.md)]，且該應用程式有依賴 [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 用戶端設定檔的資源或設定，就可能發生其中一個前述的錯誤。  
  
 若要解決應用程式設定，請開啟 [方案總管]，選擇 [顯示所有檔案]，然後在 Visual Studio 的 XML 編輯器中編輯 app.config 檔案。 將設定中的版本變更為符合 .NET Framework 的適當版本。 例如，您可以將版本設定從 4.0.0.0 變更為 2.0.0.0。 同樣地，針對加入資源的應用程式，請開啟 [方案總管]，選擇 [顯示所有檔案] 按鈕，展開 [我的專案]\(Visual Basic) 或 [屬性]\ (C#)，然後在 Visual Studio 的 XML 編輯器中編輯 Resources.resx 檔案。 將版本設定從 4.0.0.0 變更為 2.0.0.0。  
  
 如果您的應用程式具有資源 (例如圖示或點陣圖) 或設定 (例如資料連接字串)，您也可以透過在 [專案設計工具] 的 [設定] 頁面上移除所有的項目，然後重新加入必要的設定來解決錯誤。  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>您將專案的目標重定為不同版本的 .NET Framework 後無法解析參考  
 如果您將專案的目標重定為不同版本的 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]，在某些情況下可能會無法正確解析您的參考。 對組件進行明確的完整參考通常會造成這個問題，但您可以將無法解析的參考移除，然後將它們重新加回專案來解決這個問題。 或者，您可以編輯專案檔來取代參考。 首先，您要移除下列形式的參考：  
  
```  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 然後以簡單的形式取代它們：  
  
```  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
> 在關閉並重新開啟專案後，您也應該重建它，以確保能夠正確解析所有參考。  
  
## <a name="see-also"></a>另請參閱  
 [如何：.NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [.NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)   
 [以特定的 .NET Framework 版本為目標](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [多目標](../msbuild/msbuild-multitargeting-overview.md)
