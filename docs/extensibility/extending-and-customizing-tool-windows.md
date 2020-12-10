---
title: 擴充和自訂工具視窗 |Microsoft Docs
description: 瞭解如何擴充和自訂 Visual Studio 提供的工具視窗，包括屬性視窗、[輸出] 視窗和 [工作清單] 視窗。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ca7f6aa0c029cd3d85ba569aa93d6ae2087afd52
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995859"
---
# <a name="extend-and-customize-tool-windows"></a>擴充和自訂工具視窗
Visual Studio 提供數種不同類型的 windows，例如工具視窗、文件視窗和對話方塊視窗。 其他視窗（例如 [ **屬性** ] 視窗、[ **輸出** ] 視窗和 [ **工作清單** ] 視窗）都是工具視窗的類型。

## <a name="tool-windows"></a>工具視窗
 Visual Studio 工具視窗通常是唯讀的視窗，不是以檔案為基礎。 在這種情況下，它們與文件視窗不同，而文件視窗會以讀寫模式顯示檔案。 [工具箱] 、 **方案總管**、[屬性]  視窗和 [網頁瀏覽器]  是工具視窗範例。

 若要瞭解如何建立簡單的工具視窗，請參閱 [加入工具視窗](../extensibility/adding-a-tool-window.md)。

 若要向 Visual Studio 註冊工具視窗，請參閱 [註冊工具視窗](../extensibility/registering-a-tool-window.md)。

 工具視窗預設是單一執行個體，這表示一次只能開啟工具視窗的一個執行個體。 單一執行個體工具視窗在開啟之後，除非關閉 IDE，否則仍然會持續開啟。 當您關閉單一實例工具視窗時，只會變更其可見度。 您也可以建立多執行個體工具視窗，這樣即可同時開啟視窗的多個執行個體。 如需詳細資訊，請參閱 [建立多實例工具視窗](../extensibility/creating-a-multi-instance-tool-window.md) 。

 工具視窗可以是 *動態* 的，也就是說，只要套用其相關的 UI 內容，就會顯示這些視窗。 使用自動顯示可以減少 IDE 中視窗的雜亂。 如需詳細資訊，請參閱 [開啟動態工具視窗](../extensibility/opening-a-dynamic-tool-window.md)。

 在文件框架中，可以停駐、浮動或標籤工具視窗。 工具視窗框架是由 IDE 所提供，並可用來控制大小、位置、停駐狀態和其他持續性屬性。 工具視窗窗格會顯示內容。 只有在第一次開啟工具視窗時，才會套用預設大小和位置；之後，就會持續保存工具視窗狀態。

 工具視窗窗格可以裝載 WPF 使用者控制項，並支援工具列。 您可以覆寫 <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> 屬性來傳回所裝載控制項的控制代碼。

 您可以將許多不同的功能新增至工具視窗。 例如，您可以加入工具列： [將工具列加入至工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md) 或快捷方式功能表： [在工具視窗中加入快捷方式功能表](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)。 您可以新增搜尋控制項，讓您在工具視窗內搜尋專案： [將搜尋新增至工具視窗](../extensibility/adding-search-to-a-tool-window.md)。

 您可以訂閱工具視窗事件： [訂閱事件](../extensibility/subscribing-to-an-event.md)。

## <a name="extend-existing-tool-windows"></a>擴充現有的工具視窗
 您可以將工具視窗的相關資訊新增至新的 [ **選項** ] 頁面，並將 [ **屬性** ] 頁面上的新設定寫入至 [ **工作清單** ] 和 [ **輸出** ] 視窗。 如需詳細資訊，請參閱 [擴充屬性、工作清單、輸出和選項視窗](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)。

## <a name="modal-dialog-boxes"></a>強制回應對話方塊
 在 Visual Studio 擴充功能中，您應該建立強制回應對話方塊，方法是從衍生它們 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> ，讓您控制這些對話方塊和 UI 的其餘部分。 如需詳細資訊，請參閱 [建立和管理模式對話方塊](../extensibility/creating-and-managing-modal-dialog-boxes.md)。

## <a name="see-also"></a>另請參閱
- [使用工具視窗建立擴充功能](../extensibility/creating-an-extension-with-a-tool-window.md)
- [擴充專案](../extensibility/extending-projects.md)
- [擴充解決方案](../extensibility/extending-solutions.md)
