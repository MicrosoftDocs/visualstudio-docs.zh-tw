---
title: 項目類型 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, adding
- projects [Visual Studio SDK], adding new types
ms.assetid: 263a084f-f97a-4e09-add7-f0e8a6a27daf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b343eeeee0912a6e9cad57ca6d35c33845e4dd4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706269"
---
# <a name="project-types"></a>專案類型
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]包括語言(如和[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)][!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]) 的多個項目類型。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]還允許您創建自己的項目類型。

## <a name="in-this-section"></a>本節內容
- [基本功能](../../extensibility/internals/project-type-essentials.md)

 顯示必須開始處理項目類型的重要資訊。

- [建立專案類型](../../extensibility/internals/creating-project-types.md)

 討論項目類型的設計。

- [將命令加入至方案總管工具列](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)

 詳細說明向[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**解決方案資源管理員**工具列添加按鈕必須遵循的步驟。

- [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)

 討論如何向項目類型添加範本,以便用戶可以根據模式創建新專案和專案項。

- [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)

 提供有關如何管理項目類型支援的項的資訊。

- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)

 討論項目類型如何支援配置選項,如調試和發佈,這些選項控制專案的生成、調試方式等。

- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)

 提供有關如何向項目類型添加對原始程式碼管理系統的支援的資訊。

- [巢狀專案](../../extensibility/internals/nesting-projects.md)

 說明項目類型如何支援*嵌套*,以便可以在**解決方案資源管理器**中將專案分組在一起。

- [升級專案](../../extensibility/internals/upgrading-projects.md)

 描述項目類型如何參與升級嚮導,以從[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的早期版本升級專案檔。

- [架構](../../extensibility/internals/project-types-architecture.md)

 提供有關項目類型的詳細技術資訊。

## <a name="related-sections"></a>相關章節
- [階層和選取範圍](../../extensibility/internals/hierarchies-and-selection.md)

 概述了[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成開發環境 (IDE) 如何將項目顯示為層次結構。

- [專案子類型](../../extensibility/internals/project-subtypes.md)

 提供指向專案子類型主題的連結。 專案子類型支援大多數項目類型的擴展,包括您自己的項目類型。

- [專案](../../extensibility/internals/projects.md)

 描述如何擴展[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案系統。
