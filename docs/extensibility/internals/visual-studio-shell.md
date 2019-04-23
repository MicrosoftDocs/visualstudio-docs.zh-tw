---
title: Visual Studio Shell | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65f3090c6b96290527d2508ba47c899c81d6e6dd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067075"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell 是主要的代理程式中整合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 此命令介面提供必要的功能，可讓 Vspackage 共用通用的服務。 因為架構的目標[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是背心主要功能，在 Vspackage 中，命令介面是一個架構，可提供基本功能，並且支援 Vspackage 及其元件之間的跨通訊。

## <a name="shell-responsibilities"></a>Shell 責任
 在 shell 具有下列重要的責任：

- 支援 （透過 COM 介面） 的使用者介面 (UI) 的基本項目。 這些包括預設功能表和工具列、 文件視窗框架或多重文件介面 (MDI) 子視窗和工具視窗框架和停駐支援。

- 維護執行中執行的文件資料表 (RDT) 所有目前開啟的文件的清單，以協調的持續性文件，並保證在多個方法，或不相容的方式，就無法開啟該文件。

- 支援的命令路由和命令處理介面， `IOleCommandTarget`。

- 在適當的時間載入 Vspackage。 延遲載入 VSPackage 是為了改善效能的殼層。

- 管理特定的共用服務，例如<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>，它提供了基本的殼層功能和<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>，提供基本視窗化功能。

- 管理方案 (.sln) 檔案。 解決方案包含相關的專案，類似於 視覺效果中的工作區 (.dsw) 檔案群組C++6.0。

- 追蹤整個殼層的選取項目、 內容和貨幣。 殼層會追蹤下列項目類型：

  - 目前的專案

  - 目前的專案項目或項目目前的識別碼。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - 目前的選取範圍，如**屬性**視窗或 `SelectionContainer`

  - Id 或控制的可見性命令、 功能表和工具列的 CmdUIGuids UI 內容

  - 目前使用中的項目，例如使用中視窗、 文件，並復原管理員

  - 使用者內容屬性動態說明該磁碟機

  殼層也會調解在已安裝的 Vspackage 和目前的服務間的通訊。 它支援的殼層的核心功能，並使其可供所有的 vspackage 中整合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 這些核心功能包括下列項目：

- **關於**對話方塊和開頭顯示畫面

- **加入 新增 和 加入現有項目**對話方塊

- **類別檢視** 視窗和**物件瀏覽器**

- **參考**對話方塊

- **文件大綱**視窗

- **動態說明**視窗

- **尋找**和**取代**

- **開啟專案**並**開啟的檔案**上的對話方塊**新增**功能表

- **選項**對話方塊上的**工具**功能表

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