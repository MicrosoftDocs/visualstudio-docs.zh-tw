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
ms.openlocfilehash: d47e40a5c38eeb7898aa179282fa55bbe17ef1d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917336"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Visual Studio 2015 SDK 的新功能&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK 有下列適用于 Visual Studio 2015、Visual Studio 2015 更新和 Visual Studio 2017 的新功能和更新功能。

## <a name="visual-studio-2017"></a>Visual Studio 2017

從 Visual Studio 2017 開始，將不會再執行自訂專案和專案範本的掃描。 相反地，此延伸模組必須提供描述這些範本之安裝位置的範本資訊清單檔。 您可以使用 Visual Studio 2017 來更新 VSIX 擴充功能。 如果您使用 MSI 部署擴充功能，您必須手動產生範本資訊清單檔案。 如需詳細資訊，請參閱 [升級自訂 Visual Studio 的專案與項目範本 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015)。 範本資訊清單架構記載于 [Visual Studio 範本資訊清單架構參考](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference)中。

## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK Update 1
 Update 1 包含一些工具，可協助您的擴充功能搭配色彩主題和 Visual Studio 影像服務運作。

 這些主題位於 [VSSDK 公用程式](../extensibility/internals/vssdk-utilities.md) 區段底下：

- [色彩主題工具](../extensibility/internals/color-theming-tools.md)可協助您建立和編輯 Visual Studio 的自訂色彩。

- [映射服務工具](../extensibility/internals/image-service-tools.md)可讓您使用 Visual Studio 映射資訊清單檔案。

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>將 Visual Studio SDK 新增至 Visual Studio 的新方法
 從 Visual Studio 2015 開始，您不需要另外下載 Visual Studio SDK。 相反地，您可以將它安裝為一般安裝程式的一部分，也可以選擇稍後再進行安裝。 當您開啟或建立 VSIX 方案時，Visual Studio 會要求您安裝 Visual Studio 擴充性工具。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="new-ways-of-creating-extensions"></a>建立延伸模組的新方式
 從 Visual Studio 2015 SDK 開始，視您使用的程式設計語言而定，有不同的選項可用來建立擴充功能。

### <a name="visual-c-and-visual-basic"></a>Visual C# 和 Visual Basic
 針對 c # 和 Visual Basic，有一個完整範圍的專案專案範本，可讓您建立 Vspackage、功能表命令、工具視窗、編輯器分類器、編輯器裝飾和編輯器邊界延伸。 您可以將任何或所有這些專案新增至標準 VSIX 專案。 如需詳細資訊，請參閱：

- [建立具有功能表命令的擴充功能](../extensibility/creating-an-extension-with-a-menu-command.md)

- [使用工具視窗建立擴充功能](../extensibility/creating-an-extension-with-a-tool-window.md)

- [使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [使用 VSPackage 建立擴充功能](../extensibility/creating-an-extension-with-a-vspackage.md)

     VSPackage Wizard 不再以 c # 或 Visual Basic 建立延伸模組。

### <a name="c"></a>C++
 針對 c + +，VSPackage Wizard 支援功能表命令、工具視窗和自訂編輯器。 在**Visual C++/** 擴充性的 [**新增專案**] 對話方塊中尋找它。

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>透過 NuGet 的 VS SDK 參考元件
 若要提升擴充性專案的可攜性和共用，您可以使用 VS SDK 參考元件的 NuGet 版本。  這些都可在[VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility)發佈的[nuget.org](https://www.nuget.org/)上使用，並可透過 Visual Studio**參考/管理 nuget 封裝**] 對話方塊輕鬆地新增至您的專案或方案。 您可以將個別參考新增至特定的擴充性元件，或使用 VS SDK [中繼封裝](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)一次加入所有 VS sdk 參考元件。 若要深入瞭解 NuGet，請參閱 [Nuget 總覽](/nuget/) 和 [使用對話方塊管理 nuget 套件](/nuget/consume-packages/install-use-packages-visual-studio)。

 當您使用 NuGet 版本的 VS SDK 參考元件時，其他使用者不需要安裝 VS SDK 來開啟和建立您的專案。  NuGet 參考元件和 VS SDK build tools 會自動安裝在其電腦上的該專案。

 VS SDK 專案範本會使用 NuGet 作為參考和組建工具，因此您預設會獲得 NuGet 的優點。

> [!NOTE]
> 您可以繼續使用 VS SDK 安裝的參考元件與專案 (位於 \<Visual Studio Install Location> \ VSSDK\VisualStudioIntegration\Common\Assemblies) ，而且現有的擴充專案不需要升級為使用 NuGet 套件。  [專案 **參考]/[加入參考** ] 對話方塊會繼續使用 VS SDK 已安裝的參考元件。
>
> 如果您想要修改現有的專案以使用 NuGet，請參閱 [如何：將 Vspackage 遷移至 Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) ，其中有一節說明如何將擴充性專案更新為 nuget 套件。

## <a name="light-bulbs"></a>燈泡
 Roslyn 專案提供撰寫擴充程式碼最令人興奮的新方法之一。 如需詳細資訊，請參閱 [Roslyn](https://github.com/dotnet/Roslyn)。

 Light 燈泡是 VSSDK 隨附的新功能。 它們是 Visual Studio 編輯器中使用的圖示，這些圖示會展開以顯示一組程式碼重構動作，或針對內建程式碼分析器所識別的問題進行修正。 如需詳細資訊，請參閱 [逐步解說：顯示燈泡建議](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)。

## <a name="updated-user-experience-guidelines"></a>更新的使用者經驗指導方針
 設計 Visual Studio 的新擴充功能或功能？ 查看已更新和擴充的 [Visual Studio 使用者經驗指導方針](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  您將會發現您需要的 [色彩標記](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md)、 [字型大小](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)、 [對話方塊配置規格](../extensibility/ux-guidelines/layout-for-visual-studio.md)，以及您需要的其他指導方針，以將新的 UI 與 Visual Studio 緊密整合。
