---
title: 擴充和自訂工具 Windows |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90ba7833a48647043fcb9b6d8ca9095be7cabef0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486329"
---
# <a name="extending-and-customizing-tool-windows"></a>延伸和自訂工具視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[延伸和自訂工具 Windows](https://docs.microsoft.com/visualstudio/extensibility/extending-and-customizing-tool-windows)。  
  
Visual Studio 提供許多不同類型的 windows，例如工具視窗、 文件視窗和對話方塊視窗。 屬性 視窗、 輸出 視窗中，等工作清單 視窗中，其他視窗是工具視窗的類型。  
  
## <a name="tool-windows"></a>工具視窗  
 Visual Studio 工具視窗是不是以檔案為基礎的通常是唯讀視窗。 在這種情況下，它們與文件視窗不同，而文件視窗會以讀寫模式顯示檔案。 [工具箱] 、 **方案總管**、[屬性]  視窗和 [網頁瀏覽器]  是工具視窗範例。  
  
 若要了解如何建立簡單的工具視窗，請參閱[加入工具視窗](../extensibility/adding-a-tool-window.md)。  
  
 若要向 Visual Studio 中的工具視窗，請參閱[註冊的工具視窗](../extensibility/registering-a-tool-window.md)。  
  
 工具視窗預設是單一執行個體，這表示一次只能開啟工具視窗的一個執行個體。 單一執行個體工具視窗在開啟之後，除非關閉 IDE，否則仍然會持續開啟。 當您關閉單一執行個體工具視窗時，就會變更其可見性。 您也可以建立多執行個體工具視窗，這樣即可同時開啟視窗的多個執行個體。 請參閱[建立多個執行個體工具視窗](../extensibility/creating-a-multi-instance-tool-window.md)如需詳細資訊。  
  
 工具視窗可以是*動態*，這表示會顯示時的相關的 UI 內容會套用。 使用自動顯示可以減少 IDE 中視窗的雜亂。 如需詳細資訊，請參閱 <<c0> [ 開啟動態工具視窗](../extensibility/opening-a-dynamic-tool-window.md)。  
  
 在文件框架中，可以停駐、浮動或標籤工具視窗。 工具視窗框架是由 IDE 所提供，並可用來控制大小、位置、停駐狀態和其他持續性屬性。 工具視窗窗格會顯示內容。 只有在第一次開啟工具視窗時，才會套用預設大小和位置；之後，就會持續保存工具視窗狀態。  
  
 工具視窗窗格可以裝載 WPF 使用者控制項，並支援工具列。 您可以覆寫<xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A>屬性來傳回裝載之控制項的控制代碼。  
  
 您可以將許多不同的功能加入工具視窗。 例如，您可以在其中加入工具列：[新增至工具視窗的工具列](../extensibility/adding-a-toolbar-to-a-tool-window.md)或快顯功能表：[加入工具視窗中的捷徑功能表](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)。 您可以將搜尋控制項，可讓您搜尋工具視窗內的項目：[加入至工具視窗的搜尋](../extensibility/adding-search-to-a-tool-window.md)。  
  
 您可以訂閱工具視窗事件：[訂閱事件](../extensibility/subscribing-to-an-event.md)。  
  
## <a name="extending-existing-tool-windows"></a>擴充現有工具 Windows  
 關於您的工具視窗將資訊新增至新**選項**頁面和新的設定上**屬性**頁面上，寫入**工作清單**並**輸出** windows。 如需詳細資訊，請參閱 <<c0> [ 擴充屬性、 工作清單、 輸出和選項的 Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)並[擴充屬性、 工作清單、 輸出和選項 Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)。  
  
## <a name="modal-dialog-boxes"></a>強制回應對話方塊  
 在 Visual Studio 擴充功能中您應該建立強制回應對話方塊，藉由從它們衍生<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>，可讓您控制它們和其餘的 UI。 如需詳細資訊，請參閱 。 [建立和管理強制回應對話方塊](../extensibility/creating-and-managing-modal-dialog-boxes.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用工具視窗建立擴充功能](../extensibility/creating-an-extension-with-a-tool-window.md)

