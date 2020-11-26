---
title: 撰寫 Windows Installer 套件 |Microsoft Docs
description: 瞭解如何撰寫包含檔案與登錄資料的資料庫資料表之 Visual Studio 的 Windows Installer 套件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 82c96bdf8e73f7d40b41220524edef022c216f1b
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190118"
---
# <a name="author-a-windows-installer-package"></a>撰寫 Windows Installer 套件
資料會驅動 Windows Installer 模型。 例如，您不需要撰寫程式腳本來複製檔案和寫入登錄專案，而是撰寫包含檔案和登錄資料的資料庫資料表中的資料列和資料行。

## <a name="database-entries"></a>資料庫專案
若要安裝 VSPackage，Windows Installer 套件必須包含資料庫專案，才能執行下列工作：

- 搜尋系統，以 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用包含 AppSearch、CompLocator、RegLocator、DrLocator 和 Signature) 的 Windows Installer 資料表，找出您的 VSPackage 版本支援 (。

- 如果未安裝支援的版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，或者不符合 VSPackage 的另一個系統需求 (使用 LaunchCondition 資料表) ，請取消安裝。

- 使用目錄、元件和檔案資料表) 安裝 VSPackage 和相依檔案 (。

- 將 VSPackage 的適當資訊新增至登錄 (使用登錄資料表) 。

- 藉 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 由使用 CustomAction 資料表) 呼叫 **devenv.exe/setup** (，來整合 VSPackage。

如需詳細資訊，請參閱 [Windows Installer](/windows/desktop/Msi/windows-installer-portal)。

## <a name="setup-tools"></a>設定工具
各種協力廠商安裝工具提供 Windows Installer 套件的開發環境。 以下是可用的免費工具：

- InstallShield 限量版

   您可以透過 Visual Studio 的 [ **新增專案** ] 對話方塊取得受限版本的 InstallShield。 展開 [ **其他專案類型** ]，然後選取 [ **安裝和部署**]。 選取 [InstallShield] 範本。

- Windows Installer XML 工具組

   Windows Installer XML (WiX) 工具組會建立 XML 來源檔案的 Windows Installer 套件。 WiX 工具組是 Microsoft 開放原始碼專案。 您可以從 [Wix 工具](https://sourceforge.net/projects/wix/)組下載原始程式碼和可執行檔。

   若為使用整合至的商業產品 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ，請參閱 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)。

## <a name="see-also"></a>另請參閱
- [使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
