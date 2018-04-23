---
title: 擴充及自訂工具視窗 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ef4f656ed7b7ab7facbcfb470fca98327276cce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="extending-and-customizing-tool-windows"></a>擴充及自訂工具視窗
Visual Studio 提供許多不同類型的視窗，例如工具視窗、 文件視窗和對話方塊視窗。 [屬性] 視窗、 [輸出] 視窗和 [工作清單] 視窗中，例如其他視窗是工具視窗的類型。  
  
## <a name="tool-windows"></a>工具視窗  
 Visual Studio 工具視窗是不是以檔案為基礎的通常是唯讀視窗。 在這種情況下，它們與文件視窗不同，而文件視窗會以讀寫模式顯示檔案。 [工具箱] 、 **方案總管**、[屬性]  視窗和 [網頁瀏覽器]  是工具視窗範例。  
  
 若要了解如何建立簡單的工具視窗，請參閱[加入工具視窗](../extensibility/adding-a-tool-window.md)。  
  
 若要向 Visual Studio 工具視窗，請參閱[註冊工具視窗](../extensibility/registering-a-tool-window.md)。  
  
 工具視窗預設是單一執行個體，這表示一次只能開啟工具視窗的一個執行個體。 單一執行個體工具視窗在開啟之後，除非關閉 IDE，否則仍然會持續開啟。 當您關閉單一執行個體工具視窗時，變更其可見性。 您也可以建立多執行個體工具視窗，這樣即可同時開啟視窗的多個執行個體。 請參閱[建立多個執行個體工具視窗](../extensibility/creating-a-multi-instance-tool-window.md)如需詳細資訊。  
  
 工具視窗可以是*動態*，這表示，才看得見每當相關的 UI 內容會套用。 使用自動顯示可以減少 IDE 中視窗的雜亂。 如需詳細資訊，請參閱[開啟動態工具視窗](../extensibility/opening-a-dynamic-tool-window.md)。  
  
 在文件框架中，可以停駐、浮動或標籤工具視窗。 工具視窗框架是由 IDE 所提供，並可用來控制大小、位置、停駐狀態和其他持續性屬性。 工具視窗窗格會顯示內容。 只有在第一次開啟工具視窗時，才會套用預設大小和位置；之後，就會持續保存工具視窗狀態。  
  
 工具視窗窗格可以裝載 WPF 使用者控制項，並支援工具列。 您可以覆寫<xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A>屬性，以傳回裝載控制項的控制代碼。  
  
 您可以將許多不同的功能加入工具視窗。 例如，您可以在其中加入工具列：[工具列加入工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md)或快顯功能表：[快顯功能表加入工具視窗中](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)。 您可以將搜尋控制項，可讓您搜尋工具視窗內的項目：[加入搜尋工具視窗](../extensibility/adding-search-to-a-tool-window.md)。  
  
 您可以訂閱工具視窗事件：[訂閱事件](../extensibility/subscribing-to-an-event.md)。  
  
## <a name="extending-existing-tool-windows"></a>擴充現有的工具視窗  
 您可以將資料加入工具視窗的相關新**選項**頁面和新的設定上**屬性**頁面上，寫入**工作清單**和**輸出** windows。 如需詳細資訊，請參閱[擴充屬性、 工作清單、 輸出和選項 Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)和[擴充屬性、 工作清單、 輸出和選項 Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)。  
  
## <a name="modal-dialog-boxes"></a>強制回應對話方塊  
 您應該在 Visual Studio 擴充功能中建立強制回應對話方塊藉由從它們衍生<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>，可讓您控制它們和其餘的 UI。 如需詳細資訊，請參閱 。 [建立和管理的強制回應對話方塊](../extensibility/creating-and-managing-modal-dialog-boxes.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用工具視窗建立擴充功能](../extensibility/creating-an-extension-with-a-tool-window.md)