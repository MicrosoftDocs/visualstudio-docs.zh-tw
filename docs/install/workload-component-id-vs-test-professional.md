---
title: Visual Studio Test Professional 工作負載和元件識別碼
titleSuffix: ''
description: 使用 Visual Studio 工作負載和元件識別碼為通用測試人員提供整合式測試工具
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.date: 03/16/2020
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: 70c03438-8434-4921-ada0-c172519af431
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
open_to_public_contributors: false
ms.openlocfilehash: ee8d3d91f5079e23d5a0342c58b2db5a70e45f64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886466"
---
# <a name="visual-studio-test-professional-component-directory"></a>Visual Studio Test Professional 元件目錄

此頁面上的表格列出您可以用來透過命令列安裝 Visual Studio 的識別碼，或是您可以在 VSIX 資訊清單中指定為相依性的識別碼。 請注意，我們將會在發行 Visual Studio 更新時新增其他元件。

此外，也請注意此頁面的下列相關注意事項：

* 每個工作負載都有自己的小節 (後面接著工作負載識別碼)，以及一張工作負載可用元件的表格。
* 安裝工作負載時，預設會安裝「必要」元件。
* 如果您選擇，也可以安裝 **建議** 的和 **選用** 的元件。
* 我們還新增了一個章節，當中列出不屬於任何工作負載的額外元件。

當您在 VSIX 資訊清單中設定相依性時，必須僅指定「元件識別碼」。 請使用此頁面上的表格來決定我們的最基本元件相依性。 在某些情況下，這可能意謂著您僅指定一個來自工作負載的元件。 在其他情況下，則可能意謂著您指定來自單一工作負載的多個元件，或來自多個工作負載的多個元件。 如需詳細資訊，請參閱[如何︰將擴充性專案移轉至 Visual Studio 2017 (英文)](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) 頁面。

如需有關如何使用這些識別碼的詳細資訊，請參閱[使用命令列參數安裝 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) 頁面。 而如需其他產品的工作負載和元件識別碼清單，請參閱 [Visual Studio 2017 工作負載和元件識別碼 (英文)](workload-and-component-ids.md) 頁面。

## <a name="test-professional"></a>Test Professional

**識別碼：** Microsoft.VisualStudio.Workload.TestProfessional

**描述：** Test Professional 提供以通用測試人員作為目標的整合式測試工具，可協助他們在整個測試生命週期達成其測試需求。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.6.27406.0 | 必要
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager | 15.6.27406.0 | 必要

## <a name="unaffiliated-components"></a>非附屬元件

這些是未隨附於任何工作負載但可選取來作為個別元件的元件。

元件識別碼 | 名稱 | 版本
--- | --- | ---
n/a | n/a | n/a

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [Visual Studio 工作負載與元件識別碼](workload-and-component-ids.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數來安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [命令列參數範例](command-line-parameter-examples.md)
* [建立 Visual Studio 的離線安裝](create-an-offline-installation-of-visual-studio.md)
