---
title: 什麼&#39;Visual Studio 2017 SDK 中的新 s |Microsoft 文件
ms.custom: ''
ms.date: 10/31/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: abc1f12a5a6c7368bc47e8f4e924d109dcf87f57
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>什麼&#39;s Visual Studio 2017 SDK 的新功能

Visual Studio SDK 的 Visual Studio 2017 具有下列全新和更新功能。

## <a name="vsix-v3-format"></a>VSIX v3 格式

若要支援新的輕量級安裝的 Visual Studio 2017，VSIX 擴充功能資訊清單格式已更新為版本 3 (VSIX v3)。

新的格式可支援：

* 明確宣告偵測到並 VSIXInstaller 所安裝的必要條件。
* 在 擴充功能安裝 Ngen'ing 組件。
* 安裝資產一般副檔名根目錄以外的位置。

若要深入了解這些變更，請參閱下列主題：

* [擴充性 2017年的變更](breaking-changes-2017.md)
* [VSIX v3 中的 Ngen 支援](ngen-support.md)
* [在擴充功能資料夾之外進行安裝](set-install-root.md)
* [Asked Questions for Visual Studio 2017 擴充性](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>移轉至 Visual Studio 2017 的擴充性專案

若要深入了解如何更新 Visual Studio 2017 擴充性專案和其 VSIX 資訊清單，請參閱[How to： 將擴充性專案移轉至 Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。

## <a name="custom-project-and-item-templates"></a>自訂專案與項目範本

從 Visual Studio 2017，掃描自訂專案與項目範本將不會再執行。 相反地，延伸模組必須提供範本資訊清單檔案來描述這些範本的安裝位置。 您可以使用 Visual Studio 2017 更新您的 VSIX 擴充功能。 如果您部署使用 MSI 延伸模組，您必須手動產生範本資訊清單檔案。 如需詳細資訊，請參閱[升級自訂專案與 Visual Studio 2017 的項目範本](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)。 範本資訊清單結構描述會記載在[Visual Studio 範本資訊清單結構描述參考](../extensibility/visual-studio-template-manifest-schema-reference.md)。

## <a name="updated-extension-performance-guidelines"></a>更新擴充功能效能指導方針

新[如何： 診斷延伸模組效能](how-to-diagnose-extension-performance.md)下的主題[管理 Vspackage](managing-vspackages.md)顯示如何偵測及分析在 Visual Studio 擴充功能影響啟動及方案載入速度。
