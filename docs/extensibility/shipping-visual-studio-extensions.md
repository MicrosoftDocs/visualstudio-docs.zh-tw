---
title: 運輸視覺工作室擴展 |微軟文件
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
ms.openlocfilehash: 767bb24bb5cb47f1af1452aa04ebdc91c778e284
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700116"
---
# <a name="shipping-visual-studio-extensions"></a>推出 Visual Studio 延伸模組
開發完擴展後,可以在其他計算機上安裝它,與朋友和同事共用它,或在可視化工作室應用商店上發佈。 在本節中,我們將解釋發佈和維護擴展程式所需的所有操作:使用 .vsix 檔、發佈、當地語系化和更新。

## <a name="working-with-vsix-extensions"></a>使用 VSIX 延伸
 您可以通過創建空白 VSIX 專案,然後向其中添加不同的專案範本來創建 VSIX 擴展。 有關詳細資訊,請參閱[VSIX 專案樣本](../extensibility/vsix-project-template.md)。

 您可以使用 VSIX 格式打包專案樣本、專案範本、VSPackage、託管擴展框架 (MEF) 元件、**工具箱**控制項、程式集和自訂類型(這包括 Visual Studio 2017 的自訂起始頁)。 VSIX 格式使用基於檔的部署。 有關 VSIX 套件的詳細資訊,請參閱[VSIX 套件的分析](../extensibility/anatomy-of-a-vsix-package.md)。

 VSIX 格式不支援代碼段的安裝。 它還不支援某些其他方案,如寫入全域程式集緩存 (GAC) 或系統註冊表。 如果需要在安裝中寫入 GAC 或註冊表,則必須使用 Windows 安裝程式。 有關詳細資訊,請參閱為[Windows 安裝程式部署準備延伸](../extensibility/preparing-extensions-for-windows-installer-deployment.md)。

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>將擴展發佈到可視化工作室市場
 只需將 .vsix 檔郵寄到其他人或放入伺服器,即可將擴展分發給其他人。 但是,讓你的代碼在很多人手中的最好方法是把它放到[視覺工作室市場](https://marketplace.visualstudio.com/vs)。 視覺工作室市場擴展可以通過**擴展和更新**提供給視覺工作室使用者。 如需詳細資訊，請參閱[尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)。

 有關演示如何將擴展上載到可視化工作室市場的完整示例,請參閱[演練:發佈可視化工作室擴展](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)。

## <a name="private-galleries"></a>Private Galleries
 在開發控制項、樣本和工具時,可以透過將它們發布到 Intranet 上的專用庫來與組織共享它們。 如需詳細資訊，請參閱 [Private Galleries](../extensibility/private-galleries.md)。

## <a name="localizing-your-extension"></a>本地化延伸
 如果您計劃在不同區域設置中發佈擴展,則應考慮本地化它。 有關相關內容的說明,請參閱[本地化 VSIX 套件](../extensibility/localizing-vsix-packages.md)。

## <a name="updating-and-versioning-your-extension"></a>更新並控制延伸
 發佈擴展后,總有一段時間需要更新它。 要瞭解如何更新已在可視化工作室應用商店上發佈的擴展,請參閱[如何:更新擴展](../extensibility/how-to-update-a-visual-studio-extension.md)。

 您可以將擴展設定為支援多個版本的 Visual Studio。 有關詳細資訊,請參閱[支援可視化工作室的多個版本](../extensibility/supporting-multiple-versions-of-visual-studio.md)。

## <a name="related-topics"></a>相關主題

|Title|描述|
|-----------|-----------------|
|[開始使用 VSIX 專案範本](../extensibility/getting-started-with-the-vsix-project-template.md)|說明如何使用 VSIX 專案範本安裝自定義專案範本。|
|[VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)|描述 VSIX 套件的元件。|
|[VSIX 專案範本](../extensibility/vsix-project-template.md)|提供有關如何打包和發佈擴展的分步說明。|
|[將 VSIX 封裝當地語系化](../extensibility/localizing-vsix-packages.md)|說明如何使用擴展.vsixlangpack 檔案為安裝過程提供本地化文本。|
|[如何：更新延伸模組](../extensibility/how-to-update-a-visual-studio-extension.md)|介紹如何更新系統上的擴展以及如何將更新部署到現有的 Visual Studio 擴展。|
|[如何︰將相依性加入至 VSIX 封裝](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|描述如何添加對 VSIX 部署套件的引用。|
|[準備適用於 Windows Installer 部署的延伸模組](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|說明如何使用 Windows 安裝程式部署擴展。|
|[簽署 VSIX 封裝](../extensibility/signing-vsix-packages.md)|說明如何對 VSIX 包進行簽名。|
|[私用組件庫](../extensibility/private-galleries.md)|說明如何為擴展創建專用庫。|
|[支援多個 Visual Studio 版本](../extensibility/supporting-multiple-versions-of-visual-studio.md)|演示如何讓擴展支援多個版本的 Visual Studio。|
|[尋找 Visual Studio](locating-visual-studio.md)|介紹如何查找用於自定義擴展部署的可視化工作室實例。|
