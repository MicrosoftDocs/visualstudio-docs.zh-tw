---
title: 運送 Visual Studio 延伸模組 |Microsoft Docs
description: 瞭解如何發佈和維護您的 Visual Studio SDK 擴充功能，包括使用 .vsix 檔案、發行、當地語系化和更新。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 812fc4f4e2f8dcf54876e2764f0c091f16348496
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715999"
---
# <a name="shipping-visual-studio-extensions"></a>推出 Visual Studio 延伸模組
在您完成擴充功能的開發之後，您可以將它安裝在其他電腦上、與您的朋友和同事共用，或將它發佈到 Visual Studio Marketplace 上。 在本節中，我們將說明發行和維護您的延伸模組所需執行的所有作業：使用 .vsix 檔案、發行、當地語系化和更新。

## <a name="working-with-vsix-extensions"></a>使用 VSIX 擴充功能
 您可以建立一個空白的 VSIX 專案，然後在其中加入不同的專案範本，藉以建立 VSIX 擴充功能。 如需詳細資訊，請參閱 [VSIX 專案範本](../extensibility/vsix-project-template.md)。

 您可以使用 VSIX 格式來封裝專案範本、專案範本、Vspackage、Managed Extensibility Framework (MEF) 元件、 **工具箱** 控制項、元件和自訂類型 (這包括 Visual Studio 2017) 的自訂起始頁。 VSIX 格式使用以檔案為基礎的部署。 如需 VSIX 封裝的詳細資訊，請參閱 [Vsix 封裝的剖析](../extensibility/anatomy-of-a-vsix-package.md)。

 VSIX 格式不支援安裝程式碼片段。 它也不支援某些其他案例，例如寫入全域組件快取 (GAC) 或系統登錄。 如果您需要在安裝中寫入 GAC 或登錄，則必須使用 Windows Installer。 如需詳細資訊，請參閱 [準備 Windows Installer 部署的擴充](../extensibility/preparing-extensions-for-windows-installer-deployment.md)功能。

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>將您的延伸模組發佈至 Visual Studio Marketplace
 您可以將延伸模組散發給其他人，只要將 .vsix 檔案郵寄或放在伺服器上即可。 但是讓您的程式碼在許多人手上的最佳方式，就是把它放在 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。 Visual Studio Marketplace 擴充功能可透過 **擴充功能和更新** Visual Studio 使用者使用。 如需詳細資訊，請參閱[尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)。

 如需示範如何將延伸模組上傳至 Visual Studio Marketplace 的完整範例，請參閱 [逐步解說：發行 Visual Studio 擴充](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)功能。

## <a name="private-galleries"></a>Private Galleries
 當您開發控制項、範本和工具時，可以將它們張貼至內部網路上的私人資源庫，以與組織共用。 如需詳細資訊，請參閱 [Private Galleries](../extensibility/private-galleries.md)。

## <a name="localizing-your-extension"></a>當地語系化您的延伸模組
 如果您打算在不同的地區設定中發行您的延伸模組，您應該考慮將它當地語系化。 如需相關事項的說明，請參閱 [當地語系化 VSIX 套件](../extensibility/localizing-vsix-packages.md)。

## <a name="updating-and-versioning-your-extension"></a>更新您的延伸模組並進行版本控制
 發佈您的延伸模組之後，您將會有一段時間需要更新。 若要瞭解如何更新已在 Visual Studio Marketplace 上發行的延伸模組，請參閱 [如何：更新擴充](../extensibility/how-to-update-a-visual-studio-extension.md)功能。

 您可以設定您的延伸模組，以支援多個版本的 Visual Studio。 如需詳細資訊，請參閱 [支援 Visual Studio 的多個版本](../extensibility/supporting-multiple-versions-of-visual-studio.md)。

## <a name="related-topics"></a>[相關主題]

|標題|描述|
|-----------|-----------------|
|[開始使用 VSIX 專案範本](../extensibility/getting-started-with-the-vsix-project-template.md)|說明如何使用 VSIX 專案範本來安裝自訂專案範本。|
|[VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)|描述 VSIX 封裝的元件。|
|[VSIX 專案範本](../extensibility/vsix-project-template.md)|提供有關如何封裝和發佈延伸模組的逐步指示。|
|[將 VSIX 封裝當地語系化](../extensibility/localizing-vsix-packages.md)|說明如何使用 vsixlangpack 檔案，提供安裝程式的當地語系化文字。|
|[如何：更新延伸模組](../extensibility/how-to-update-a-visual-studio-extension.md)|說明如何更新系統上的延伸模組，以及如何將更新部署至現有的 Visual Studio 延伸模組。|
|[如何︰將相依性加入至 VSIX 封裝](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|說明如何加入 VSIX 部署封裝的參考。|
|[準備適用於 Windows Installer 部署的延伸模組](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|說明如何使用 Windows Installer 部署擴充功能。|
|[簽署 VSIX 封裝](../extensibility/signing-vsix-packages.md)|說明如何簽署 VSIX 套件。|
|[私用資源庫](../extensibility/private-galleries.md)|說明如何建立擴充功能的私用資源庫。|
|[支援多個 Visual Studio 版本](../extensibility/supporting-multiple-versions-of-visual-studio.md)|說明如何讓您的延伸模組支援多個版本的 Visual Studio。|
|[尋找 Visual Studio](locating-visual-studio.md)|說明如何尋找自訂延伸模組部署的 Visual Studio 實例。|
