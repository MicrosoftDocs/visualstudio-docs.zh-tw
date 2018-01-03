---
title: "MSBuild 多目標概觀 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
caps.latest.revision: "10"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0ca64f2a05e587fdaf3b7ee46e13abc49406cd65
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-multitargeting-overview"></a>MSBuild 多目標概觀
您可以使用 MSBuild，將應用程式編譯為在數個 .NET Framework 版本中的任一版上或數個系統平台中的任一個平台上執行。 例如，您可以將應用程式編譯為在 32 位元平台的 .NET Framework 2.0 上執行，也可以將同一個應用程式編譯為在 64 位元平台的 .NET Framework 4.5 上執行。  
  
> [!IMPORTANT]
>  除了名稱「多目標」之外，專案一次只能以一個架構和一個平台為目標。  
  
 這些是一部分的 MSBuild 目標功能︰  
  
-   您可以開發以較舊版 .NET Framework (例如 2.0、3.5 或 4 版) 為目標的應用程式。  
  
-   您可以將 .NET Framework 以外的架構作為目標，例如 Silverlight Framework。  
  
-   您可以將「Framework 設定檔」當做目標，這是預先定義的目標 Framework 子集。  
  
-   如果 .NET Framework 目前版本的 Service Pack 已發行，您可以將它當做目標。  
  
-   MSBuild 多目標可保證應用程式只使用目標 Framework 和平台中提供的功能。  
  
## <a name="target-framework-and-platform"></a>目標架構和平台  
 「目標架構」是建置專案以在其上執行的 .NET Framework 版本，而「目標平台」是建置專案以在其上執行的系統平台。  例如，您可能想要設定 .NET Framework 2.0 應用程式，在與 802x86 處理器系列 (x86) 相容的 32 位元平台上執行。 目標 Framework 和目標平台的組合稱為「目標內容」。 如需詳細資訊，請參閱[目標 Framework 和目標平台](../msbuild/msbuild-target-framework-and-target-platform.md)。  
  
## <a name="toolset-toolsversion"></a>Toolset (ToolsVersion)  
 工具組會將工具、工作以及用來建立應用程式的目標收集在一起。 工具組包括 csc.exe 和 vbc.exe 這類編譯器、一般 targets 檔案 (microsoft.common.targets) 和一般 tasks 檔案 (microsoft.common.tasks)。 4.5 工具組可以用來以 .NET Framework 版本 2.0、3.0、3.5、4 和 4.5 為目標。 不過，2.0 工具組只能用來以 .NET Framework 版本 2.0 為目標。 如需詳細資訊，請參閱 [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)。  
  
## <a name="reference-assemblies"></a>參考組件  
 工具組中所指定的參考組件可協助您設計和建置應用程式。 這些參考組件不僅會啟用特定目標組建，也會將 Visual Studio IDE 中的元件和功能限制為與目標相容的元件和功能。 如需詳細資訊，請參閱[在設計階段時解析組件](../msbuild/resolving-assemblies-at-design-time.md)。  
  
## <a name="configuring-targets-and-tasks"></a>設定目標和工作  
 您可以設定 MSBuild 目標和工作以跨處理序方式隨 MSBuild 一起執行，如此您就能以視為與目前執行之內容不同的內容作為目標。  例如，您可以在開發電腦以具有 .NET Framework 4.5 的 64 位元平台執行時，以 32 位元 .NET Framework 2.0 應用程式為目標。 如需詳細資訊，請參閱[設定目標和工作](../msbuild/configuring-targets-and-tasks.md)。  
  
## <a name="troubleshooting"></a>疑難排解  
 如果您嘗試參考不屬於目標內容的組件，則可能會發生錯誤。 如需這些錯誤和其處理方式的詳細資訊，請參閱[針對 .NET Framework 目標錯誤進行疑難排解](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)。