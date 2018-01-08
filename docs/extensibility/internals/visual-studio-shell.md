---
title: "Visual Studio Shell |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9240df0a4f551ab4fa47fc2ceacaf0654dc562e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]殼層是在整合的主要代理程式[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 此命令介面提供必要的功能，讓 VSPackages 共用通用的服務。 因為架構的目標[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]背心 Vspackage 中的主要功能是殼層是一種架構來提供基本功能，並支援 Vspackage 及其元件之間的互通。  
  
## <a name="shell-responsibilities"></a>殼層責任  
 在 shell 具有下列索引鍵的責任：  
  
-   （透過 COM 介面） 支援使用者介面 (UI) 的基本項目。 這些包括預設功能表和工具列、 文件視窗框架或多重文件介面 (MDI) 子視窗和工具視窗框架和停駐支援。  
  
-   維護執行的所有目前開啟的文件中執行的文件資料表 (RDT) 清單，以便協調的文件的持續性，並保證在一個以上的方法，或不相容的方式，就無法開啟該文件。  
  
-   支援的命令路由和命令處理介面， `IOleCommandTarget`。  
  
-   在適當的時間載入 Vspackage。 延遲載入 VSPackage 是為了改善效能的殼層。  
  
-   管理特定的共用服務，例如<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>，這樣會提供基本的殼層功能和<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>，提供基本視窗化功能。  
  
-   管理方案 (.sln) 檔案。 方案包含相關的專案，類似於 Visual c + + 6.0 中的工作區 (.dsw) 檔案群組。  
  
-   追蹤整個殼層的選取項目、 內容和貨幣。 殼層會追蹤下列項目類型：  
  
    -   目前的專案  
  
    -   目前的專案項目或項目目前的識別碼。<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   目前的選取範圍**屬性**視窗或`SelectionContainer`  
  
    -   UI 內容識別碼或 CmdUIGuids 控制命令、 功能表和工具列的可見性  
  
    -   目前作用中的項目，例如使用中視窗、 文件，並復原管理員  
  
    -   使用者內容屬性動態說明該磁碟機  
  
 殼層也會調解安裝的 Vspackage 和目前的服務之間的通訊。 它支援的殼層的核心功能，使其可整合至所有 vspackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 這些核心功能包括下列項目：  
  
-   **關於**對話方塊方塊與啟動顯示畫面  
  
-   **加入新功能和加入現有項目**對話方塊  
  
-   **類別檢視**視窗和**物件瀏覽器**  
  
-   **參考**對話方塊  
  
-   **文件大綱**視窗  
  
-   **動態說明**視窗  
  
-   **尋找**和**取代**  
  
-   **開啟專案**和**開啟檔案**對話方塊上**新增**功能表  
  
-   **選項** 對話方塊上的**工具**功能表  
  
-   **屬性**視窗  
  
-   **方案總管**  
  
-   **工作清單**視窗  
  
-   **工具箱**  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [VSPackage](../../extensibility/internals/vspackages.md)