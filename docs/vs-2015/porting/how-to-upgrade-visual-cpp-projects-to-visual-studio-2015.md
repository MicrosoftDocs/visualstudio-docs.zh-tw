---
title: 如何：將 Visual C++ 專案升級為 Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- projects [C++], upgrading
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 198a848f953881af5a7ac4b042c74b368d202d06
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425893"
---
# <a name="how-to-upgrade-visual-c-projects-to-visual-studio-2015"></a>如何：將 Visual C++ 專案升級為 Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 2017 的最新文件，請參閱 [VisualC++ 移植和升級指南](https://docs.microsoft.com/cpp/porting/visual-cpp-porting-and-upgrading-guide)。

第一次開啟使用舊版 Visual Studio 建立的 Visual C++ 專案時，系統可能會提示您更新專案。 訊息詢問您是否要升級到 Visual C++ 編譯器和程式庫的最新版本。 升級選項取決於用於建立專案的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 版本。

 您可以使用 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 開啟、編輯和建置在 [!INCLUDE[win8](../includes/win8-md.md)] 中建立的 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]專案，但若要建立新的 [!INCLUDE[win8](../includes/win8-md.md)] 專案，您必須使用 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]  (若要建立 [!INCLUDE[win81](../includes/win81-md.md)] 專案，您必須使用 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)])。

 若要建立 Windows 10 專案，您必須使用 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]。

 如果沒有提示您更新專案，您可能不需要執行任何動作來升級專案。

- 如果專案 (.vcproj) 是在比 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 還要舊的 [!INCLUDE[vs2010](../includes/vs2010-md.md)]版本中建立的，您必須更新專案。

- 如果專案 (.vcxproj) 是在 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]、  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]或 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中建立的，您有兩個選擇：

    - 您可以略過更新。 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] 會載入專案而不進行任何變更 (如果可以在含 SP1 的 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]、[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 或 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 中存取 Visual C++ 工具)。 您可以在具有 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]的相同電腦上安裝建立專案所使用的 Visual Studio 版本，以提供這項存取權。 如需詳細資訊，請參閱 [Installing Visual Studio Versions Side-by-Side](../install/install-visual-studio-versions-side-by-side.md)。

    - 若要更新專案，您可允許 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 進行本主題稍後說明的變更。 如果您的方案有一個以上的 Visual C++ 專案，則必須全部更新。

        > [!NOTE]
        > 如果您在第一次提示時拒絕更新，稍後可以選取 [專案]  功能表上的 [更新 VC++ 專案]  更新專案。 如果命令未出現，則不需要更新。

## <a name="upgrading-a-visual-c-project"></a>升級 Visual C++ 專案
 如果您允許 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] 自動更新專案，則會進行下列變更：

- 變更專案，讓它使用 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] 編譯器和程式庫 (PlatformToolset = VisualStudio v140)。

- 若是 [!INCLUDE[cppcli](../includes/cppcli-md.md)] 專案，則會將 TargetFrameworkVersion 變更為 .NET Framework 4.5.2。

## <a name="continuing-to-work-with-a-custom-platformtoolset"></a>繼續使用自訂 PlatformToolset
 如果您想要繼續使用 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]中的自訂 PlatformToolset，此工具組必須位於 x86 電腦的 %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ 底下，或者位於 x64 電腦的 %ProgramFiles (x86)%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ 底下。 如需如何建立自訂 PlatformToolset 的詳細資訊，請參閱 Visual C++ 團隊部落格中的 [C++ 原生多目標](http://go.microsoft.com/fwlink/?LinkId=248587) 。

## <a name="see-also"></a>請參閱
 [Visual C++ 移植和升級指南](http://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb) [移植、移轉和升級 Visual Studio 專案](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
