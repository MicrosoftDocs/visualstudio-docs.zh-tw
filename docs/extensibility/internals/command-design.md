---
title: 命令設計 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 43b83e5a02fb84ad09531f87b3120168bad0b2e0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="command-design"></a>命令的設計
當您將命令加入 VSPackage 時，您必須指定所在出現、 時，以及它的方式處理。  
  
## <a name="defining-commands"></a>定義命令  
 若要定義新的命令，包括 VSPackage 專案中的 Visual Studio 命令表 (.vsct) 檔案。 如果您使用 Visual Studio Package 範本建立 VSPackage，專案會包含這些檔案。 如需詳細資訊，請參閱[Visual Studio 命令表 (。Vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
 Visual Studio 會合併，讓它可以顯示命令找到的所有.vsct 檔案。 因為這些檔案是不同的二進位 VSPackage，Visual Studio 並沒有載入要尋找命令的封裝。 如需詳細資訊，請參閱[如何 Vspackage 加入使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
 Visual Studio 會使用<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>註冊屬性來定義功能表資源和命令。 如需詳細資訊，請參閱[實作](../../extensibility/internals/command-implementation.md)。  
  
 命令可以在執行階段變更許多不同的方法。 它們可以顯示或隱藏、 啟用或停用。 它們可以顯示不同的文字或圖示，或包含不同的值。 Visual Studio 載入 VSPackage 之前，可能會執行更多的自訂。 如需詳細資訊，請參閱[如何 Vspackage 加入使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
## <a name="command-handlers"></a>命令處理常式  
 當您建立的命令時，您必須提供事件處理常式來執行命令。 如果使用者選取命令，則必須適當地路由傳送。 路由的命令時，表示傳送至正確的 VSPackage，以啟用或停用、 隱藏或顯示，並執行它，如果使用者選擇要執行這項操作。 如需詳細資訊，請參閱[路由演算法](../../extensibility/internals/command-routing-algorithm.md)。  
  
## <a name="the-visual-studio-command-environment"></a>Visual Studio 命令環境  
 Visual Studio 可以裝載任何數目的 Vspackage，以及每個都可以構成其本身的命令集。 環境會顯示適用於目前工作的命令。 如需詳細資訊，請參閱[可用性](../../extensibility/internals/command-availability.md)和[選擇內容物件](../../extensibility/internals/selection-context-objects.md)。  
  
 定義新的命令、 功能表、 工具列或快顯功能表的 VSPackage 的命令資訊提供給 Visual Studio 在安裝期間，透過參考原生或 managed 組件中的資源的登錄項目。 每項資源，然後參考二進位資料 (.cto) 資源檔，當您編譯的 Visual Studio 命令表 (.vsct) 檔案產生。 這可讓 Visual Studio 提供合併的命令集、 功能表和工具列，而不必載入每個已安裝的 VSPackage。  
  
### <a name="command-organization"></a>命令的組織  
 將環境置於依照群組、 優先權和功能表命令。  
  
-   群組是邏輯集合的相關命令，例如，**剪下**，**複製**，和**貼上**命令群組。 群組是出現在功能表的命令。  
  
-   優先順序會決定在群組中的個別命令功能表出現的順序。  
  
-   功能表做為容器的群組。  
  
 某些命令、 群組和功能表會預先定義的環境。 如需詳細資訊，請參閱[預設命令、 群組及工具列位置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)。  
  
 命令可以指派給主要群組。 主要群組控制在主功能表結構和命令的位置**自訂** 對話方塊。 命令可以出現在多個群組。例如，命令可以是主功能表上、 快顯功能表和工具列。 如需詳細資訊，請參閱[如何 Vspackage 加入使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。  
  
### <a name="command-routing"></a>命令傳送  
 叫用和路由傳送命令適用於 Vspackage 的程序不同的物件執行個體上呼叫方法的程序。  
  
 環境將命令路由 (local) 的最內層命令內容，此作業取決於目前的選取範圍，起始到最外層 （全域） 內容。 無法執行命令的第一個內容是處理它。 如需詳細資訊，請參閱[路由演算法](../../extensibility/internals/command-routing-algorithm.md)。  
  
 在大部分情況下，環境會處理命令使用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。 命令路由配置可讓許多不同的物件來處理命令，因為<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>可以實作任意數目的物件; 這些包括 Microsoft ActiveX 控制項、 視窗檢視實作、 文件物件、 專案階層並 （適用於全域的命令） VSPackage 物件本身。 在某些特殊情況下，例如，路由傳送命令在階層中，<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>必須實作介面。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[實作](../../extensibility/internals/command-implementation.md)|描述如何在 VSPackage 中實作命令。|  
|[可用性](../../extensibility/internals/command-availability.md)|描述 Visual Studio 內容如何決定可用的命令。|  
|[路由的演算法](../../extensibility/internals/command-routing-algorithm.md)|描述 Visual Studio 命令路由架構如何讓由不同的 Vspackage 的命令。|  
|[放置指導方針](../../extensibility/internals/command-placement-guidelines.md)|建議如何將命令放在 Visual Studio 環境。|  
|[VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|描述如何 Vspackage 可以充分利用 Visual Studio 命令架構。|  
|[預設的命令、群組及工具列位置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|描述 Vspackage 如何最適合使用隨附在 Visual Studio 中的命令。|  
|[管理 VSPackage](../../extensibility/managing-vspackages.md)|描述 Visual Studio 如何載入 Vspackage。|  
|[Visual Studio 命令表檔案 (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|提供 XML.vsct 檔案，可用來描述的配置和外觀的 Vspackage 中命令的相關資訊。|