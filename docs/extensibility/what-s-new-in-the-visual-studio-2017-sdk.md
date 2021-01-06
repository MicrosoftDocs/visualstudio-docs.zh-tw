---
title: '&apos;Visual Studio 2017 SDK 的新功能 |Microsoft Docs'
description: Visual Studio SDK 具有 Visual Studio 2017 的新功能和更新功能，包括更新的 VSIX 版本3格式。
ms.custom: SEO-VS-2020
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79e9df9a728ab9892694efa6489a8ea1fd675700
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877623"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Visual Studio 2017 SDK 的新功能&#39;

Visual Studio SDK 具有 Visual Studio 2017 的下列新功能和更新功能。

## <a name="vsix-v3-format"></a>VSIX v3 格式

為了支援 Visual Studio 2017 的新輕量安裝，VSIX 擴充功能資訊清單格式已更新為第3版 (VSIX v3) 。

新的格式支援：

* 明確宣告要由 VSIXInstaller 偵測並安裝的必要條件。
* 擴充功能安裝上的 Ngen 元件。
* 在一般的擴充功能根目錄之外安裝資產。

若要瞭解這些變更，請參閱下列主題：

* [Visual Studio 2017 的擴充性變更](breaking-changes-2017.md)
* [VSIX v3 中的 Ngen 支援](ngen-support.md)
* [在延伸模組資料夾之外進行安裝](set-install-root.md)
* [Visual Studio 2017 擴充性的常見問題](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>將擴充性專案遷移至 Visual Studio 2017

若要瞭解如何將您的擴充性專案及其 VSIX 資訊清單更新為 Visual Studio 2017，請參閱如何：將擴充性 [專案遷移至 Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。

## <a name="custom-project-and-item-templates"></a>自訂專案和專案範本

從 Visual Studio 2017 開始，將不會再執行自訂專案和專案範本的掃描。 相反地，此延伸模組必須提供描述這些範本之安裝位置的範本資訊清單檔。 您可以使用 Visual Studio 2017 來更新 VSIX 擴充功能。 如果您使用 MSI 部署擴充功能，您必須手動產生範本資訊清單檔案。 如需詳細資訊，請參閱 [升級 Visual Studio 2017 的自訂專案和專案範本](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)。 範本資訊清單架構記載于 [Visual Studio 範本資訊清單架構參考](../extensibility/visual-studio-template-manifest-schema-reference.md)中。

## <a name="updated-extension-performance-guidelines"></a>更新的延伸模組效能指導方針

有一項新的 how to：在 [[管理 vspackage](managing-vspackages.md) ] 底下[診斷延伸模組效能](how-to-diagnose-extension-performance.md)文章，以示範如何偵測和分析擴充功能對 Visual Studio 啟動和解決方案載入時間的影響。
