---
title: 什麼&#39;Visual Studio 2015 SDK 中的新 s |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6488f28f2963e17c716c2e9d395ddf77f270e7b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>什麼&#39;s Visual Studio 2015 SDK 的新功能
Visual Studio SDK 的 Visual Studio 2015、 Visual Studio 2015 更新和 Visual Studio 2017 具有下列新增和更新功能。  
  
## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK Update 1  
 Update 1 包含可協助您搭配色彩佈景主題和 Visual Studio 映像服務的擴充功能工具。  
  
 這些主題受到[VSSDK 公用程式](../extensibility/internals/vssdk-utilities.md)> 一節：  
  
-   [色彩佈景主題工具](../extensibility/internals/color-theming-tools.md)協助您建立和編輯 Visual Studio 自訂色彩。  
  
-   [映像服務工具](../extensibility/internals/image-service-tools.md)可讓您使用 Visual Studio 映像資訊清單檔案。  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>若要加入至 Visual Studio 的 Visual Studio SDK 的新方式  
 從 Visual Studio 2015 開始，您不需要個別下載 Visual Studio SDK。 相反地，您可以將它安裝為標準安裝程序的一部分，或您可以選擇稍後安裝它。 當您開啟或建立 VSIX 方案時，Visual Studio 會要求您安裝 Visual Studio 擴充性工具。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="new-ways-of-creating-extensions"></a>建立擴充功能的新方式  
 您從 Visual Studio 2015 SDK 開始，有不同的選項，可建立擴充功能，您使用的程式設計語言而定。  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# 和 Visual Basic  
 對於 C# 和 Visual Basic 中，沒有完整的專案項目範本可讓您建立 Vspackage，功能表命令、 工具視窗、 編輯器分類器、 編輯器裝飾和編輯器邊界延伸模組。 您可以新增任何或所有的這些標準的 VSIX 專案。 如需詳細資訊，請參閱:  
  
-   [建立具有功能表命令的擴充功能](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [使用工具視窗建立擴充功能](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [使用 VSPackage 建立擴充功能](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     VSPackage 精靈不會再建立擴充功能，以 C# 或 Visual Basic。  
  
### <a name="c"></a>C++  
 C + +，VSPackage 精靈支援功能表命令、 工具視窗和自訂編輯器。 尋找在**新專案**對話方塊**Visual c + + / 擴充性**。  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>透過 NuGet VS SDK 的參考組件  
 增加的可攜性和擴充性專案的共用，您可以使用 VS SDK 的參考組件的 NuGet 版本。  這些是用於[nuget.org](http://www.nuget.org)所發行[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)並可輕鬆地加入至專案或透過 Visual Studio 方案**參考 / 管理 NuGet封裝**對話方塊。 您可以個別將參考加入至特定的擴充性的組件，或新增所有 VS SDK 都參考一次使用 VS SDK 的組件[中繼封裝](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)。 若要深入了解 NuGet，請參閱[NuGet 文件](/NuGet)和[封裝管理員 UI](/NuGet/Tools/Package-Manager-UI)主題。  
  
 當您使用 VS SDK 的參考組件的 NuGet 版本時，另一位使用者不需要安裝 VS SDK，以開啟和建置您的專案。  NuGet 參考組件和 VS SDK 建置工具會自動安裝該專案的電腦上。  
  
 VS SDK 項目範本供參考使用 NuGet 和建置工具，因此您會取得預設 NuGet 的優點。  
  
> [!NOTE]
>  您可以繼續使用安裝 VS SDK 的參考組件，以您的專案 (位於  \<Visual Studio 安裝位置 > \ VSSDK\VisualStudioIntegration\Common\Assemblies)，不需要是現有的擴充性專案升級為使用 NuGet 封裝。  專案**參考 / 加入參考**對話方塊會繼續使用安裝 VS SDK 的參考組件。  
>   
>  如果您想要修改現有的專案使用 NuGet，請參閱[How to： 將 VSPackages 移轉至 Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)具有擴充性專案更新至 NuGet 封裝 > 一節。  
  
## <a name="light-bulbs"></a>燈泡  
 其中一種最令人興奮的新方式撰寫延伸模組程式碼係由 Roslyn 專案。 如需詳細資訊，請參閱[Roslyn](https://github.com/dotnet/Roslyn)。  
  
 燈泡是隨附於 VSSDK 的新功能。 它們是在 Visual Studio 編輯器中使用的圖示展開以顯示一組程式碼重構動作或修正的內建的程式碼分析器所識別的問題。 如需詳細資訊，請參閱[逐步解說： 顯示燈泡建議](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)。  
  
## <a name="updated-user-experience-guidelines"></a>更新的使用者經驗指導方針  
 適用於 Visual Studio 中設計新的擴充功能？ 簽出已更新及擴充[Visual Studio 使用者經驗指導方針](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  您可以找到[色彩語彙基元](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md)，[字型大小](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)，[對話方塊版面配置規格](../extensibility/ux-guidelines/layout-for-visual-studio.md)，和其他您需要順暢地整合新的 UI 與 Visual Studio 的指引。