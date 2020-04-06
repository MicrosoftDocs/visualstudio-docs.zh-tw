---
title: 視覺工作室 2015 SDK 中的原始程式碼控制新增功能 |微軟文件
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f90ae3e1d327b10e99713ad28aa2d5a06c0be34b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703402"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>視覺化工作室 2015 SDK 的原始碼管理新增功能

在[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]中,可以通過實現原始程式碼管理 VSPackage 提供深度整合的原始程式碼管理解決方案。 本節介紹原始程式碼管理 VS包的功能,並提供實現步驟的概述。

## <a name="the-source-control-vspackage"></a>原始碼管理 VS 套件

Visual Studio 支援兩種類型的原始程式碼管理解決方案。 在所有版本的 Visual Studio 中,您仍然可以整合式基於原始碼管理外掛程式 API 的外掛程式。 您還可以為原始程式碼管理建立 VSPackage,該路徑提供深度整合[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]路徑, 適用於需要高度複雜和自主的原始程式碼管理解決方案。

VSPackage 幾乎可以向 Visual Studio 添加任何類型的功能。 原始碼管理 VSPackage 為 Visual Studio 提供了完整的原始碼管理功能,從向使用者呈現的 UI 到與原始碼管理系統的後端通訊。

實現原始碼管理 VSPackage 需要"全無"策略。 原始碼管理 VSPackage 的建立者必須投入大量精力來實現許多原始碼管理介面和新的 UI 元素(對話框、功能表和工具列),以涵蓋整個原始碼管理功能,以及任何包成功與 Visual Studio 整合所需的介面。

以下步驟概述了實現原始程式碼管理包所需的內容。 關於詳細資訊,請參考[原始碼管理 VS 套件](../../extensibility/internals/creating-a-source-control-vspackage.md)。

1. 創建提供專用原始程式碼管理服務的 VSPackage。

2. 在 Visual Studio 提供的原始程式碼管理<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2><xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>相關服務中實現介面(例如,和介面)。

3. 註冊原始碼管理 VSPackage。

4. 實現所有原始碼管理 UI,包括選單項、對話框、工具列和上下文選單。

5. 所有與原始程式碼管理相關的事件在啟動時都會傳遞到原始程式碼管理 VSackage,並且必須由您的 VSPackage 處理。

6. 原始碼管理 VSPackage 必須偵聽事件,<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>例如實現介面的事件以及追蹤專案文檔 (TPD) 事件(由<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>介面實現),並採取必要的操作。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [概觀](../../extensibility/internals/source-control-integration-overview.md)
- [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)
