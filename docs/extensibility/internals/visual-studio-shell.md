---
title: 視覺工作室外殼 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb89fc3b82dc7f142714608d8a669e368216c729
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704007"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
shell[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合的主要代理。 shell 提供必要的功能,使 VSPackages 能夠共用公共服務。 由於體系結構目標是[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在 VSPackages 中賦予主要功能,因此 shell 是一個框架,用於提供基本功能並支援其元件 VSPackages 之間的交叉通訊。

## <a name="shell-responsibilities"></a>殼牌職責
 shell 具有以下關鍵職責:

- 支援(透過 COM 介面)使用者介面 (UI) 的基本元素。 其中包括預設選單和工具列、文檔視窗框架或多文檔介面 (MDI) 子視窗,以及工具視窗框架和停靠支援。

- 在正在執行的文件表 (RDT) 中維護所有當前打開的文件的運行清單,以便協調文檔的持久性,並保證不能以多種方式或不相容的方式打開一個文件。

- 支援命令路由和命令處理介面。 `IOleCommandTarget`

- 在適當時間載入 VS 包。 為了改進外殼的性能,必須延遲載入 VSPackage。

- 管理某些共用服務,如<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>提供基本 shell 功能<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>,以及 提供基本視窗功能。

- 管理解決方案 (.sln) 檔案。 解決方案包含相關項目組,類似於 Visual C++ 6.0 中的工作區 (.dsw) 檔。

- 跟蹤殼範圍的選擇、上下文和貨幣。 shell 追蹤以下型態的項目:

  - 目前項目

  - 目前項目項目或目前的項目 ID<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - **屬性**視窗或`SelectionContainer`

  - 控制命令、選單和工具列可見性 UI 內容的 ID 與 CmdUIGuids

  - 目前活動元素,如作用視窗、文件與復原管理員

  - 驅動動態說明的使用者內容內容

  外殼還調解已安裝的 VS 包和當前服務之間的通信。 它支援 shell 的核心功能,並使它們可用於 整合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在中的所有 VSPackages。 這些核心功能包括以下專案:

- **關於**對話框與初始螢幕

- **新增與新增現有項目**對話框

- **類別檢視**視窗與**物件瀏覽器**

- **參考**對話框

- **文件大綱**視窗

- **動態說明**視窗

- **尋找**與**取代**

- **在「新增****」選單上開啟項目與****開啟檔案**對話框

- **「工具」** 選單上**的選項**對話框

- **屬性**視窗

- **方案總管**

- **工作清單**視窗

- **工具箱**

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackage](../../extensibility/internals/vspackages.md)
