---
title: 推出 Visual Studio 擴充功能 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ea2217614ed27a98281cce7a3d34b72f74ae803
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433015"
---
# <a name="shipping-visual-studio-extensions"></a>推出 Visual Studio 延伸模組
您完成開發您的擴充功能之後，您可以將它安裝在其他電腦上、 與朋友和同事，共用或 Visual Studio Marketplace 上發行它。 在本節中，我們說明您需要執行以發佈及維護您的延伸模組的所有項目： 使用.vsix 檔案、 發佈、 當地語系化，及更新。

## <a name="working-with-vsix-extensions"></a>使用 VSIX 擴充功能
 您可以藉由建立空白的 VSIX 專案，並再新增另一個項目範本來建立 VSIX 擴充功能。 如需詳細資訊，請參閱 < [VSIX 專案範本](../extensibility/vsix-project-template.md)。

 您可以使用 VSIX 格式封裝專案範本、 項目範本，Vspackage，Managed Extensibility Framework (MEF) 元件，來**工具箱**控制項、 組件和自訂類型 （這包括自訂起始頁視覺效果Studio 2017)。 VSIX 格式使用檔案為基礎的部署。 如需 VSIX 封裝的詳細資訊，請參閱[VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)。

 VSIX 格式不支援安裝的程式碼片段。 它也不支援某些其他案例，例如寫入至全域組件快取 (GAC) 中，或系統登錄。 如果您需要寫入至 GAC 中，或是在安裝中的登錄，您必須使用 Windows 安裝程式。 如需詳細資訊，請參閱 <<c0> [ 準備擴充功能的 Windows Installer 部署](../extensibility/preparing-extensions-for-windows-installer-deployment.md)。

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Visual Studio Marketplace 中發佈您的延伸模組
 您可以將擴充散佈給其他人只要郵寄.vsix 檔案，或將放在伺服器上。 但很多人的手中取得您的程式碼的最佳方式是將它放在[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。 Visual Studio Marketplace 擴充功能可用於 Visual Studio 使用者透過**擴充功能和更新**。 如需詳細資訊，請參閱[尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)。

 如需示範如何上傳至 Visual Studio Marketplace 的延伸模組的完整範例，請參閱[逐步解說：發行 Visual Studio 擴充功能](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)。

## <a name="private-galleries"></a>Private Galleries
 當您開發控制項、 範本和工具，則您可以張貼到您內部網路上的私用組件庫與您的組織共用它們。 如需詳細資訊，請參閱[私用組件庫](../extensibility/private-galleries.md)。

## <a name="localizing-your-extension"></a>當地語系化您的延伸模組
 如果您計劃發行您的延伸模組，在不同的地區設定中，您應該考慮將它當地語系化。 如需相關資訊的說明，請參閱 <<c0> [ 當地語系化 VSIX 封裝](../extensibility/localizing-vsix-packages.md)。

## <a name="updating-and-versioning-your-extension"></a>更新與版本控制您的延伸模組
 發佈您的擴充功能之後，會出現一次當您需要更新它。 若要了解如何更新 Visual Studio Marketplace 發佈的延伸模組，請參閱[How to:更新擴充功能](../extensibility/how-to-update-a-visual-studio-extension.md)。

 您可以設定您的延伸模組，以支援多個版本的 Visual Studio。 如需詳細資訊，請參閱 <<c0> [ 支援多個版本的 Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[開始使用 VSIX 專案範本](../extensibility/getting-started-with-the-vsix-project-template.md)|說明如何使用 VSIX 專案範本，若要安裝自訂專案範本。|
|[VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)|描述 VSIX 套件的元件。|
|[VSIX 專案範本](../extensibility/vsix-project-template.md)|提供有關如何封裝和發行延伸模組的逐步指示。|
|[將 VSIX 封裝當地語系化](../extensibility/localizing-vsix-packages.md)|說明如何藉由使用 extension.vsixlangpack 檔案安裝程序提供當地語系化的文字。|
|[如何：更新延伸模組](../extensibility/how-to-update-a-visual-studio-extension.md)|描述如何更新您的系統上的擴充功能，以及如何將更新部署至現有的 Visual Studio 擴充功能。|
|[如何：將相依性新增至 VSIX 套件](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|描述如何將參考加入至 VSIX 部署封裝。|
|[準備適用於 Windows Installer 部署的擴充功能](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|說明如何使用 Windows 安裝程式將延伸模組部署。|
|[簽署 VSIX 封裝](../extensibility/signing-vsix-packages.md)|說明如何簽署 VSIX 封裝。|
|[私用組件庫](../extensibility/private-galleries.md)|說明如何建立擴充功能私用組件庫。|
|[支援多個 Visual Studio 版本](../extensibility/supporting-multiple-versions-of-visual-studio.md)|示範如何延伸模組支援多個版本的 Visual Studio。|
|[尋找 Visual Studio](locating-visual-studio.md)|描述如何尋找自訂延伸模組部署的 Visual Studio 執行個體。|
