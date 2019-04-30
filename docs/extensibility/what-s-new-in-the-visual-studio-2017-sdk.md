---
title: 什麼&#39;Visual Studio 2017 SDK 的新功能 |Microsoft Docs
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: caa7593c85351512e683f2cf93adeb3211e3e4d8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951186"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>什麼&#39;Visual Studio 2017 SDK 的新功能

Visual Studio SDK for Visual Studio 2017 具有下列全新和更新功能。

## <a name="vsix-v3-format"></a>VSIX v3 格式

若要支援新的輕量級安裝的 Visual Studio 2017，VSIX 擴充功能資訊清單格式已更新至版本 3 (VSIX v3)。

新的格式可支援：

* 明確宣告會偵測與 VSIXInstaller 安裝的必要條件。
* 在 延伸模組安裝 Ngen 組件。
* 安裝常用的擴充功能根目錄之外的資產。

若要深入了解這些變更，請參閱下列主題：

* [Visual Studio 2017 的擴充性的變更](breaking-changes-2017.md)
* [VSIX v3 中的 Ngen 支援](ngen-support.md)
* [安裝擴充功能資料夾以外之處](set-install-root.md)
* [Visual Studio 2017 擴充性的常見問題集](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>將擴充性專案移轉至 Visual Studio 2017

若要了解如何更新 Visual Studio 2017 的擴充性專案和其 VSIX 資訊清單，請參閱[How to:將擴充性專案移轉至 Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。

## <a name="custom-project-and-item-templates"></a>自訂專案與項目範本

啟動 Visual Studio 2017 中，自訂專案與項目範本的掃描將不會再執行。 相反地，延伸模組必須提供範本資訊清單檔案來描述這些範本的安裝位置。 您可以使用 Visual Studio 2017 更新您的 VSIX 擴充功能。 如果您部署使用 MSI 延伸模組，您必須以手動方式產生範本資訊清單檔。 如需詳細資訊，請參閱 < [Visual Studio 2017 的升級自訂專案與項目範本](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)。 範本資訊清單結構描述記載於[Visual Studio 範本資訊清單結構描述參考](../extensibility/visual-studio-template-manifest-schema-reference.md)。

## <a name="updated-extension-performance-guidelines"></a>更新延伸模組效能指導方針

新[How to:診斷延伸模組效能](how-to-diagnose-extension-performance.md)文章底下[管理 Vspackage](managing-vspackages.md)顯示如何偵測和分析在 Visual Studio 的延伸模組影響啟動和解決方案載入時間。
