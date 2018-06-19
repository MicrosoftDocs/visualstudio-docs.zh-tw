---
title: 開啟動態工具視窗 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdd3a4a8d85ed7d0f5884e7f11b8778eb3b420a2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138284"
---
# <a name="opening-a-dynamic-tool-window"></a>開啟動態工具視窗
從上一個功能表或對等的鍵盤快速鍵的命令通常開啟的工具視窗。 有時候，不過，您可能需要開啟特定 UI 內容會套用，且當 UI 內容不再適用時，關閉時的工具視窗。 工具視窗的這些型別稱為*動態*或*自動可見*。  
  
> [!NOTE]
>  如需預先定義的 UI 內容，請參閱<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>。 針對  
  
 如果您想要開啟 啟動時，動態工具視窗，而且有可能建立失敗，您必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx>介面，並測試中的失敗狀況<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A>方法。 為了讓 shell 知道您擁有動態工具視窗應該開啟，在啟動時，您必須加入`SupportsDynamicToolOwner`套件登錄值 （設定為 1）。 此值不是標準的一部分<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>，因此您必須建立自訂屬性，將它加入。 如需自訂屬性的詳細資訊，請參閱[使用自訂註冊屬性來登錄延伸模組](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension)。  
  
 使用<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>開啟工具視窗。 視需要建立工具視窗。  
  
> [!NOTE]
>  使用者可以關閉動態工具視窗。 如果您想要建立功能表命令，讓使用者可以重新開啟工具視窗時，應該開啟工具視窗，並已停用其他方式的同一 UI 內容中啟用功能表命令。  
  
### <a name="to-open-a-dynamic-tool-window"></a>若要開啟動態工具視窗  
  
1.  建立 VSIX 專案，名為**DynamicToolWindow**並新增名為的工具視窗項目範本**DynamicWindowPane.cs**。 如需詳細資訊，請參閱[建立工具視窗擴充](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
2.  在 DynamicWindowPanePackage.cs 檔案中，尋找 DynamicWindowPanePackage 宣告。 新增<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>和<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>註冊工具視窗的屬性。  
  
    ```vb  
    [ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackage.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     上面的屬性註冊為暫時性的視窗關閉後重新開啟 Visual Studio 時，不會保存，名為 DynamicWindowPane 工具視窗。 開啟 DynamicWindowPane 每當<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string>套用，且否則關閉。  
  
3.  建置此專案並開始偵錯。 實驗執行個體應該會出現。 您不應該看到工具視窗。  
  
4.  實驗執行個體中開啟專案。 工具視窗應該會出現。