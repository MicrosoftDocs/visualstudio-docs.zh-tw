---
title: Visual Studio Shell |Microsoft Docs
description: Visual Studio shell 是 Visual Studio 中整合的主要代理程式，並提供基本功能，並支援 Vspackage 之間的交叉通訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5dafd90294fd0968c78846d4162c1ff02c584f3f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074336"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Shell 是中整合的主要代理程式 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 Shell 提供必要的功能，讓 Vspackage 共用一般服務。 由於的架構目標 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 是要在 vspackage 中背心主要功能，因此 shell 是一個架構，可提供基本功能，並支援其元件 vspackage 之間的交叉通訊。

## <a name="shell-responsibilities"></a>Shell 責任
 Shell 具有下列主要責任：

- 透過 COM 介面支援 () 使用者介面 (UI) 的基本元素。 這些包括預設功能表和工具列、文件視窗框架或多重文件介面 (MDI) 子視窗和工具視窗框架，以及銜接支援。

- 在執行中的檔資料表中維護目前開啟之所有檔的執行清單 (RDT) ，以協調檔的持續性，並確保一份檔無法以多種方式開啟，或以不相容的方式開啟。

- 支援命令路由和命令處理介面 `IOleCommandTarget` 。

- 在適當的時間載入 Vspackage。 需要延遲載入 VSPackage，才能改善 shell 的效能。

- 管理某些共用服務，例如 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> 提供基本的 shell 功能，以及提供 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 基本的視窗功能。

- 管理 ( .sln) 檔案的方案。 解決方案包含相關專案的群組，類似于 Visual C++ 6.0 中的工作區 ( dsw) 檔案。

- 追蹤整個 shell 的選取範圍、內容和貨幣。 Shell 會追蹤下列專案類型：

  - 目前的專案

  - 目前的專案專案，或 ItemID 目前的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - [ **屬性** ] 視窗的目前選取範圍或 `SelectionContainer`

  - 控制命令、功能表和工具列之可見度的 UI 內容識別碼或 CmdUIGuids

  - 目前作用中的元素，例如使用中視窗、檔和復原管理員

  - 驅動動態說明的使用者內容屬性

  Shell 也會協調已安裝 Vspackage 與目前服務之間的通訊。 它支援 shell 的核心功能，並使其可供在中整合的所有 Vspackage 使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 這些核心功能包括下列專案：

- **關於** 對話方塊和啟動顯示畫面

- [**加入新專案] 和 [加入現有專案**] 對話方塊

- **類別檢視** 視窗和 **物件瀏覽器**

- **參考** 對話方塊

- [**檔大綱**] 視窗

- **動態** 說明視窗

- **尋找** 和 **取代**

- **開啟 [專案**]，然後在 [**新增**] 功能表上 **開啟**[檔案] 對話方塊

- [**工具**] 功能表上的 [**選項**] 對話方塊

- **屬性** 視窗

- **方案總管**

- **工作清單** 視窗

- **工具箱**

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackages](../../extensibility/internals/vspackages.md)
