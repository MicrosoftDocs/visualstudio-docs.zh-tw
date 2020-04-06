---
title: 視覺工作室 2017 SDK 中的&#39;新增功能 |微軟文件
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88330aa68f2a3752431fd2fbe6c5c1c649acbb8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697201"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>視覺工作室 2017 SDK 中的&#39;新增功能

Visual Studio SDK 具有以下 Visual Studio 2017 的新功能和更新功能。

## <a name="vsix-v3-format"></a>VSIX v3 格式

為了支援 Visual Studio 2017 的新輕型安裝,VSIX 擴展清單格式已更新為版本 3 (VSIX v3)。

新格式支援:

* 顯式聲明由 VSIX 安裝程式檢測到和安裝的先決條件。
* 擴展安裝上的 Ngen 程式集。
* 在通常的擴展根目錄之外安裝資源。

要瞭解這些更改,請參閱以下主題:

* [2017 年可視化工作室擴充性的更改](breaking-changes-2017.md)
* [VSIX v3 中的 Ngen 支援](ngen-support.md)
* [在延伸模組資料夾之外進行安裝](set-install-root.md)
* [Visual Studio 2017 擴充性常見問題](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>將擴充性項目移到 Visual Studio 2017

要瞭解如何將擴充性專案及其 VSIX 清單更新到 Visual Studio 2017,請參閱[如何:將擴充性專案遷移到 Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。

## <a name="custom-project-and-item-templates"></a>自訂項目與專案樣本

從 Visual Studio 2017 開始,將不再執行自定義專案和專案範本的掃描。 相反,擴展必須提供描述這些範本的安裝位置的範本清單檔。 您可以使用 Visual Studio 2017 更新 VSIX 擴展。 如果使用 MSI 部署副檔名,則必須手動生成範本清單檔。 有關詳細資訊,請參閱為[Visual Studio 2017 升級自訂項目和專案範本](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)。 範本清單架構記錄在[可視化工作室範本清單架構引用](../extensibility/visual-studio-template-manifest-schema-reference.md)中。

## <a name="updated-extension-performance-guidelines"></a>更新延伸效能指南

在[「管理 VSPackages」](managing-vspackages.md)下,有一個新的[「如何:診斷擴展性能](how-to-diagnose-extension-performance.md)文章」,以示範如何檢測和分析擴展對 Visual Studio 啟動和解決方案載入時間的影響。
