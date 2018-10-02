---
title: MSBuild 目標 Framework 和目標平台 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e699096af425897e3bd3c724b483cc3fea2ffb29
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500032"
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild 目標 Framework 和目標平台
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[MSBuild 目標 Framework 和目標平台](https://docs.microsoft.com/visualstudio/msbuild/msbuild-target-framework-and-target-platform)。  
  
  
您可以建置專案，以在特定 .NET Framework 版本的「目標 Framework」，以及特定軟體架構的「目標平台」上執行。  例如，您可以在目標為 .NET Framework 2.0 以及與 802x86 處理器系列 (“x86”) 相容的 32 位元平台上，執行應用程式。 目標 Framework 和目標平台的組合稱為「目標內容」。  
  
## <a name="target-framework-and-profile"></a>目標 Framework 和設定檔  
 目標 Framework 是建置的專案執行所在的特定 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 版本。 由於目標 Framework 啟用由該版 Framework 獨佔的編譯器功能和組件參考，因此需要目標 Framework 的規格。  
  
 以下是目前可供使用的 .NET Framework 版本：  
  
-   [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 (隨附於 Visual Studio 2005)  
  
-   [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.0 (隨附於 [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)])  
  
-   [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.5 (隨附於 [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)])  
  
-   [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4 (隨附於 Visual Studio 2010)  
  
-   [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5 (隨附於 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)])  
  
-   [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5.1 (隨附於 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)])  
  
-   [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5.2  
  
-   [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.6 (隨附於 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)])  
  
 組件清單中每一個組件所參考的 .NET Framework 版本各自不同。 例如，除非您專案是以 .NET Framework 3.0 (含) 以上版本為目標，否則您無法建置 Windows Presentation Foundation (WPF) 應用程式。  
  
 目標 Framework 是在專案檔的 `TargetFrameworkVersion` 屬性中指定。 您可以在 Visual Studio 整合式開發環境 (IDE) 中，使用專案屬性頁來變更專案的目標 Framework。 如需詳細資訊，請參閱[如何：以 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。 `TargetFrameworkVersion` 的可用值包括 `v2.0`、`v3.0`、`v3.5`、`v4.0`、`v4.5`、`v4.5.1`、`v4.5.2` 和 `v4.6`。  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 「目標設定檔」是目標 Framework 的子集。 例如，.NET Framework 4 用戶端設定檔不包含 MSBuild 組件的參考。  
  
 目標設定檔是在專案檔的 `TargetFrameworkProfile` 屬性中指定。 您可以在 IDE 中，使用專案屬性頁中的目標 Framework 控制項來變更目標設定檔。 如需詳細資訊，請參閱[如何：以 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>目標平台  
 「平台」是定義特定執行階段環境的軟硬體組合。 例如，套用至物件的  
  
-   `x86` 指定在 Intel 80x86 處理器或其對等項目上執行的 32 位元 Windows 作業系統。  
  
-   `Xbox` 指定 Microsoft Xbox 360 平台。  
  
 「目標平台」是建置專案以在其上方執行的目標特定平台。 目標平台是在專案檔的 `Platform` 建置屬性中指定。 您可以在 IDE 中，使用專案屬性頁或 [組態管理員] 來變更目標平台。  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
</PropertyGroup>  
  
```  
  
 「目標組態」是目標平台的子集。 例如，`x86``Debug` 組態不包含大部分的程式碼最佳化。 目標組態是在專案檔的 `Configuration` 建置屬性中指定。 您可以使用專案屬性頁或 [組態管理員] 來變更目標組態。  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [多目標](../msbuild/msbuild-multitargeting-overview.md)



