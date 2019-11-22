---
title: Visual Studio 2015 SDK 的新功能 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6735f929f52387f4cb40406d6918894e72bb40d3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299680"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Visual Studio&#39;2015 SDK 的新功能
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK 具有下列適用于 Visual Studio 2015、Visual Studio 2015 更新和 Visual Studio 2017 的全新和更新功能。

## <a name="visual-studio-2017"></a>Visual Studio 2017

從 Visual Studio 2017 開始，將不會再執行掃描自訂專案和專案範本。 相反地，延伸模組必須提供範本資訊清單檔，以描述這些範本的安裝位置。 您可以使用 Visual Studio 2017 來更新您的 VSIX 擴充功能。 如果您使用 MSI 部署擴充功能，您必須手動產生範本資訊清單檔。 如需詳細資訊，請參閱[升級自訂 Visual Studio 的專案與項目範本 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015)。 範本資訊清單架構記載于[Visual Studio 範本資訊清單架構參考](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference)中。

## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK Update 1
 Update 1 包含的工具可協助您的擴充功能適用于色彩主題和 Visual Studio 影像服務。

 這些主題位於[VSSDK 公用程式](../extensibility/internals/vssdk-utilities.md)區段底下：

- [色彩主題工具](../extensibility/internals/color-theming-tools.md)可協助您建立和編輯 Visual Studio 的自訂色彩。

- [映射服務工具](../extensibility/internals/image-service-tools.md)可讓您使用 Visual Studio 映射資訊清單檔案。

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>將 Visual Studio SDK 新增至 Visual Studio 的新方式
 從 Visual Studio 2015 開始，您不需要另外下載 Visual Studio SDK。 相反地，您可以將它安裝為正常安裝程式的一部分，也可以選擇稍後再安裝。 當您開啟或建立 VSIX 解決方案時，Visual Studio 將會要求您安裝 Visual Studio 擴充性工具。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="new-ways-of-creating-extensions"></a>建立擴充功能的新方式
 從 Visual Studio 2015 SDK 開始，視您使用的程式語言而定，您有不同的建立擴充功能選項。

### <a name="visual-c-and-visual-basic"></a>Visual C# 和 Visual Basic
 針對C#和 Visual Basic，有完整範圍的專案專案範本，可讓您建立 vspackage、功能表命令、工具視窗、編輯器分類器、編輯器裝飾和編輯器邊界延伸模組。 您可以將任何或全部新增至標準 VSIX 專案。 如需詳細資訊，請參閱：

- [建立具有功能表命令的擴充功能](../extensibility/creating-an-extension-with-a-menu-command.md)

- [使用工具視窗建立擴充功能](../extensibility/creating-an-extension-with-a-tool-window.md)

- [使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [使用 VSPackage 建立擴充功能](../extensibility/creating-an-extension-with-a-vspackage.md)

     VSPackage Wizard 不再于或 Visual Basic 中C#建立延伸模組。

### <a name="c"></a>C++
 針對C++，VSPackage Wizard 支援功能表命令、工具視窗和自訂編輯器。 在**Visual C++ /** 擴充性的 [**新增專案**] 對話方塊中尋找它。

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>VS SDK 透過 NuGet 參考元件
 若要增加擴充性專案的可攜性和共用，您可以使用 VS SDK 參考元件的 NuGet 版本。  這些適用于[VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility)所發佈的[nuget.org](https://www.nuget.org/) ，而且可以透過 [Visual Studio**參考/管理 nuget 封裝**] 對話方塊，輕鬆地新增至您的專案或方案。 您可以將個別參考加入至特定的擴充性元件，或使用 VS SDK[元封裝](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)一次加入所有 VS sdk 參考元件。 若要深入瞭解 NuGet，請參閱[Nuget 總覽](https://docs.microsoft.com/nuget/)和[使用對話方塊管理 nuget 套件](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio)。

 當您使用 VS SDK 參考元件的 NuGet 版本時，另一位使用者不需要安裝 VS SDK 即可開啟和建立您的專案。  NuGet 參考元件和 VS SDK build tools 會自動安裝在電腦上，以供該專案之用。

 VS SDK 專案範本會針對其參考和組建工具使用 NuGet，因此預設會取得 NuGet 的優點。

> [!NOTE]
> 您可以繼續使用 VS SDK 已安裝的參考元件與您的專案（位於 \<Visual Studio 安裝位置 > \ VSSDK\VisualStudioIntegration\Common\Assemblies），而現有的擴充性專案則不需要升級為使用 NuGet 套件。  [專案**參考]/[加入參考**] 對話方塊會繼續使用 VS SDK 已安裝的參考元件。
>
> 如果您想要修改現有的專案以使用 NuGet，請參閱[如何：將 Vspackage 遷移至 Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) ，其中包含將擴充性專案更新為 NuGet 套件的一節。

## <a name="light-bulbs"></a>Light 燈泡
 撰寫延伸模組程式碼最令人興奮的新方式之一，是由 Roslyn 專案所提供。 如需詳細資訊，請參閱[Roslyn](https://github.com/dotnet/Roslyn)。

 Light 燈泡是 VSSDK 隨附的一項新功能。 它們是用於 [Visual Studio 編輯器] 中的圖示，可展開以顯示一組程式碼重構動作，或針對內建程式碼分析器所識別的問題進行修正。 如需詳細資訊，請參閱[逐步解說：顯示燈泡建議](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)。

## <a name="updated-user-experience-guidelines"></a>更新的使用者經驗指導方針
 為 Visual Studio 設計新的延伸模組或功能？ 查看已更新和擴充的[Visual Studio 使用者經驗指導方針](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  您可以找到[色彩標記](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md)、[字型大小](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)、[對話版面配置規格](../extensibility/ux-guidelines/layout-for-visual-studio.md)，以及與 Visual Studio 緊密整合新 UI 所需的其他指引。
