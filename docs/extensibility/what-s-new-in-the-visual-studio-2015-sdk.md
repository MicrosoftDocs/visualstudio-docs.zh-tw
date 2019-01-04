---
title: 什麼&#39;Visual Studio 2015 SDK 的新功能 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4c5a84da9fef0bee2a4701337ea62864f5fd34b3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952838"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>什麼&#39;的新功能 Visual Studio 2015 SDK
Visual Studio SDK for Visual Studio 2015 中，更新，Visual Studio 2015 和 Visual Studio 2017 具有下列全新和更新功能。  
  
## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK Update 1  
 Update 1 包含工具，可協助您順利使用的色彩佈景主題和 Visual Studio 映像服務的延伸模組。  
  
 這些主題正在[VSSDK 公用程式](../extensibility/internals/vssdk-utilities.md)區段：  
  
-   [色彩佈景主題工具](../extensibility/internals/color-theming-tools.md)幫助您建立和編輯 Visual Studio 自訂色彩。  
  
-   [影像服務工具](../extensibility/internals/image-service-tools.md)可讓您使用 Visual Studio 映像資訊清單檔案。  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>將 Visual Studio SDK 新增至 Visual Studio 的新方式  
 從 Visual Studio 2015 中，您不需要個別下載 Visual Studio SDK。 相反地，您可以將它安裝為標準安裝程序的一部分，或更新版本上安裝時，您可以選擇。 當您開啟或建立 VSIX 方案時，Visual Studio 會要求您安裝 Visual Studio 擴充性工具。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="new-ways-of-creating-extensions"></a>建立擴充功能的新方法  
 您從 Visual Studio 2015 SDK，有不同的選項，可建立擴充功能，您使用的程式設計語言而定。  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# 和 Visual Basic  
 對於 C# 和 Visual Basic 中，沒有完整的專案項目範本可讓您建立 Vspackage，功能表命令、 工具視窗、 編輯器分類器、 編輯器裝飾和編輯器邊界延伸模組。 您可以將任何或所有這些範本新增至標準的 VSIX 專案。 如需詳細資訊，請參閱:  
  
-   [建立具有功能表命令的擴充功能](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [建立工具視窗的延伸模組](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [使用 VSPackage 建立擴充功能](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     VSPackage 精靈不會再建立 C# 或 Visual Basic 中的延伸模組。  
  
### <a name="c"></a>C++  
 C + +，VSPackage 精靈支援功能表命令、 工具視窗和自訂編輯器。 在尋求**新的專案** 對話方塊中的**Visual c + + / 擴充性**。  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>透過 NuGet VS SDK 參考組件  
 如需提升可攜性和擴充性專案的共用，您可以使用 VS SDK 參考組件的 NuGet 版本。 這些組件位於[nuget.org](http://www.nuget.org)發佈[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)可以輕鬆地新增至您的專案或解決方案，透過 Visual Studio 和**參考 / 管理NuGet 套件**對話方塊。 您可以個別將參考加入至特定的擴充性的組件，或新增所有 VS SDK 都參考組件，使用 VS SDK 一次[中繼套件](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)。 若要深入了解 NuGet，請參閱[NuGet 文件](/NuGet)並[套件管理員 UI](/NuGet/Tools/Package-Manager-UI)主題。  
  
 當您使用 VS SDK 參考組件的 NuGet 版本時，另一位使用者不需要安裝 VS SDK 來開啟並建置您的專案。  NuGet 參考組件和 VS SDK 建置工具會自動將該專案在電腦上安裝。  
  
 VS SDK 項目範本用於其參考的 NuGet，及建置工具，因此您會取得預設 NuGet 的優點。  
  
> [!NOTE]
>  您可以繼續使用您的專案中安裝 VS SDK 參考組件 (位於\<Visual Studio 安裝位置 > \ VSSDK\VisualStudioIntegration\Common\Assemblies)，不是需要現有的擴充性專案若要使用 NuGet 套件升級。  專案**參考] / [加入參考**對話方塊會繼續使用已安裝的 VS SDK 參考組件。  
>   
>  如果您想要修改您現有的專案，以使用 NuGet，請參閱[How to:將 VSPackages 移轉至 Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)具有擴充性專案更新至 NuGet 套件的區段。  
  
## <a name="light-bulbs"></a>燈泡  
 其中一種最令人興奮的新方式撰寫延伸模組程式碼是由 Roslyn 專案中提供。 如需詳細資訊，請參閱 < [Roslyn](https://github.com/dotnet/Roslyn)。  
  
 燈泡是隨附於 VSSDK 的新功能。 也就是使用 Visual Studio 編輯器中的圖示展開以顯示一組程式碼重構動作或修正的內建的程式碼分析器所識別的問題。 如需詳細資訊，請參閱[逐步解說：Displaying Light Bulb Suggestions](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)。  
  
## <a name="updated-user-experience-guidelines"></a>更新的使用者經驗指導方針  
 適用於 Visual Studio 中設計新的擴充功能？ 查看已更新及擴充[Visual Studio 使用者經驗指導方針](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  您會發現[色彩語彙基元](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md)，[字型大小](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)，[對話方塊版面配置規格](../extensibility/ux-guidelines/layout-for-visual-studio.md)，和其他指南，您需要與 Visual Studio 完美整合，您的新 UI。