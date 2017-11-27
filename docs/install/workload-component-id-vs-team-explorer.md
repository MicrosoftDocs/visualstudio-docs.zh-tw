---
title: "Visual Studio Team Explorer 2017 工作負載和元件識別碼 | Microsoft Docs"
description: "使用 Visual Studio 工作負載和元件識別碼為通用測試人員提供整合式測試工具"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 10/09/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology: vs-ide-install
ms.assetid: c6ef9a3b-d13d-49b4-9faa-51fa06b21e1f
ms.openlocfilehash: d4590db9e33d955f7e0c1b77845cf3819bc0d68e
ms.sourcegitcommit: 2c7f48ad6073a81fa927568793633f26cc1f0b15
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="visual-studio-team-explorer-2017-component-directory"></a>Visual Studio Team Explorer 2017 元件目錄

此頁面上的表格列出您可以用來透過命令列安裝 Visual Studio 的識別碼。 請注意，我們將會在發行 Visual Studio 更新時新增其他元件。

此外，也請注意此頁面的下列相關注意事項：

* 每個工作負載都有自己的小節 (後面接著工作負載識別碼)，以及一張工作負載可用元件的表格。
* 安裝工作負載時，預設會安裝「必要」元件。 您也可以選擇安裝「建議」元件和「選擇性」元件。
* 我們還新增了一個章節，當中列出不屬於任何工作負載的額外元件。

如需有關如何使用這些識別碼的詳細資訊，請參閱[使用命令列參數安裝 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) 頁面。 而如需其他產品的工作負載和元件識別碼清單，請參閱 [Visual Studio 2017 工作負載和元件識別碼 (英文)](workload-and-component-ids.md) 頁面。

## <a name="visual-studio-core-editor-included-with-visual-studio-team-explorer-2017"></a>Visual Studio 核心編輯器 (隨附於 Visual Studio Team Explorer 2017)

**識別碼：**Microsoft.VisualStudio.Workload.CoreEditor

**描述：**Visual Studio 核心殼層體驗，包括語法感知程式碼編輯、原始程式碼控制及工作項目管理。

### <a name="components-included-by-this-workload"></a>此工作負載所包含的元件

元件識別碼 | 名稱 | 版本 | 相依性類型
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio 核心編輯器 | 15.0.26606.0 | 必要

## <a name="unaffiliated-components"></a>非附屬元件

這些是未隨附於任何工作負載但可選取來作為個別元件的元件。

元件識別碼 | 名稱 | 版本
--- | --- | ---
N/A | N/A | N/A

## <a name="get-support"></a>取得支援
有時可能會發生一些問題。 如果您的 Visual Studio 安裝失敗，請參閱[針對 Visual Studio 2017 安裝和升級問題進行疑難排解](troubleshooting-installation-issues.md)頁面，以取得疑難排解祕訣。 同樣地，您可以透過 Visual Studio IDE 中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具向我們報告產品問題，或者在 [UserVoice](https://visualstudio.uservoice.com/forums/121579) 上與我們分享建議。 您可以在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/) \(英文\) 追蹤產品問題，也可以在那裡詢問問題和尋找解答。 您也可以透過我們在 [Gitter 社群中的 Visual Studio 交談](https://gitter.im/Microsoft/VisualStudio) \(英文\)，與我們以及其他 Visual Studio 開發人員進行互動 (需要 [GitHub](https://github.com/) 帳戶)。

## <a name="see-also"></a>請參閱

* [Visual Studio 工作負載與元件識別碼](workload-and-component-ids.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [命令列參數範例](command-line-parameter-examples.md)
* [建立 Visual Studio 的離線安裝](create-an-offline-installation-of-visual-studio.md)
