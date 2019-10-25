---
title: Visual Studio Shell |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60aa48da701857508f9b6fd7fc3d9d0c0603046e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722047"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell 是 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中整合的主要代理程式。 Shell 提供了必要的功能，可讓 Vspackage 共用通用的服務。 因為 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的架構目標是要在 Vspackage 中背心主要功能，所以 shell 是提供基本功能並支援其元件 Vspackage 間交互通訊的架構。

## <a name="shell-responsibilities"></a>Shell 責任
 Shell 具有下列重要責任：

- 支援（透過 COM 介面）使用者介面（UI）的基本元素。 這些包括預設的功能表和工具列、文件視窗框架或多重文件介面（MDI）子視窗，以及工具視窗框架，以及銜接支援。

- 維護執行中檔資料表（RDT）中所有目前開啟之檔的執行中清單，以協調檔的持續性，並確保一份檔無法以一種以上的方式開啟，或以不相容的方式開啟。

- 支援命令路由和命令處理介面，`IOleCommandTarget`。

- 在適當時間載入 Vspackage。 延遲載入 VSPackage 是改善 shell 效能的必要項。

- 管理特定的共用服務，例如提供基本 shell 功能的 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>，以及 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>，提供基本的視窗化功能。

- 管理解決方案（.sln）檔案。 解決方案包含相關專案的群組，類似于 Visual C++ 6.0 中的工作區（. dsw）檔案。

- 追蹤 shell 範圍的選取專案、內容和貨幣。 Shell 會追蹤下列類型的專案：

  - 目前的專案

  - 目前的專案專案或 ItemID 目前的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - [**屬性**] 視窗或 `SelectionContainer` 的目前選取範圍

  - 控制命令、功能表和工具列之可見度的 UI 內容識別碼或 CmdUIGuids

  - 目前作用中的元素，例如使用中視窗、檔和復原管理員

  - 驅動動態說明的使用者內容屬性

  Shell 也會調節已安裝 Vspackage 和目前服務之間的通訊。 它支援 shell 的核心功能，並可供 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中整合的所有 Vspackage 使用。 這些核心功能包括下列專案：

- **關於**對話方塊和啟動顯示畫面

- [**加入新的] 和 [新增現有專案**] 對話方塊

- **類別檢視**視窗和**物件瀏覽器**

- **參考**對話方塊

- **檔大綱**視窗

- **動態**說明視窗

- **尋找**和**取代**

- **開啟 [專案**]，然後在 [**新增**] 功能表上**開啟**[檔案] 對話方塊

- [**工具**] 功能表上的 [**選項**] 對話方塊

- **屬性**視窗

- **方案總管**

- **工作清單**視窗

- **工具箱**

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackage](../../extensibility/internals/vspackages.md)