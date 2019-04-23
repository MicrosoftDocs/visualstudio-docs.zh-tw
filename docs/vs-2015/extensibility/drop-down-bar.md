---
title: 下拉式清單列 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4296a8fa4146a52d167bce3d8b051aa3ca073
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60055973"
---
# <a name="drop-down-bar"></a>下拉式清單列
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在下拉式清單列提供程式碼視窗頂端，並包含兩個下拉式清單。  
  
## <a name="drop-down-bar-interfaces"></a>下拉式清單列介面  
 在  [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]，比方說，在下拉式清單列包含清單[!INCLUDE[vcprvc](../includes/vcprvc-md.md)]項目和[!INCLUDE[vcprvc](../includes/vcprvc-md.md)]項目成員函式，如下圖所示。  
  
 ![卸除&#45;向下橫條](../extensibility/media/vsdropdown-bar.gif "vsDropdown_bar")  
下拉式清單列  
  
 當實作的下拉式清單列時，有四個介面，最重要的一點：  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     實作這個介面來插入下拉式清單列的內容。 每個下拉式清單的組合可以包含純文字或花俏的文字 (粗體、 底線、 或斜體)，能視窗文字的字型色彩標示、 灰色的字型，而且可以選擇性地提供下拉式清單項目旁邊的小型點陣圖。 類似於<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>介面，映像清單中，會提供點陣圖影像。 每個下拉式清單組合都可以有不同的映像清單;不過，每個映像清單必須包含相同的高度的映像。 此外，使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A>方法中，您可以為每個組合提供工具提示。  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     呼叫這個介面來建立或終結程式碼視窗的下拉式清單列。 此介面也可用來判斷是否下拉式清單列已附加至程式碼視窗呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A>方法。 呼叫<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>for<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>從<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>。  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     呼叫此介面，以便直接與下拉式清單列通訊。 您可以使用此介面，以強制重新整理的下拉式清單列內容，或變更其中一個清單方塊中的選取項目。  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     如果您已經註冊`ShowDropdownBarOption`在您的語言服務登錄機碼中，然後您的程式碼視窗管理員必須監視同步處理是否應該顯示在下拉式清單列相關的使用者喜好設定與此事件。 如果您沒有註冊的語言服務金鑰，此選項，則上已停用的選項，即可顯示或隱藏下拉式清單列**選項**功能表。  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>附加至程式碼視窗的下拉式清單列  
 若要建立時，請將下拉式清單列附加至程式碼視窗中，語言服務應該附加至下拉式清單列時<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>呼叫方法。 如果呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A>方法會指示下拉式清單列不尚未存在，則呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>。 若要存取<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>介面，請呼叫<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>從<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>指標傳回給您時您<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>實作已附加。  
  
## <a name="see-also"></a>另請參閱  
 [使用舊版 API 的自訂程式碼 Windows](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [舊版語言服務中對巡覽列的支援](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)
