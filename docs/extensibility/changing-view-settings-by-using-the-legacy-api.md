---
title: 使用舊版應用程式開發介面來變更檢視設定 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 18
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: dc68bf5f8a0e61b80200cd5454b78bcdda78cdfe
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>變更檢視設定，以使用舊版 API
設定核心編輯器功能，例如自動換行、 選取範圍邊界和虛擬空間，可以藉由使用者變更**選項** 對話方塊。 不過，您也可變更這些設定以程式設計的方式。  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>變更設定，以使用舊版 API  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>介面會公開一組文字編輯器屬性。 [文字] 檢視包含屬性 (GUID_EditPropCategory_View_MasterSettings) 的類別，表示文字檢視以程式設計方式變更設定的群組。 一旦已經以這種方式變更檢視設定，就無法變更在**選項**對話方塊，直到它們重設。  
  
 以下是一般的程序來變更檢視設定的核心編輯器執行個體。  
  
1.  呼叫`QueryInterface`上 (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) 的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>介面。  
  
2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>方法，並指定值的 GUID_EditPropCategory_View_MasterSettings`rguidCategory`參數。  
  
     執行此動作將指標傳回至<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>介面，其中包含檢視的強制屬性集。 永遠強制在這個群組中的任何設定。 如果設定不在此群組中，則它會遵循指定的選項**選項**對話方塊或使用者的命令。  
  
3.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>方法，並指定適當的設定值，在`idprop`參數。  
  
     例如，若要強制自動換行，呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>和指定的值為 VSEDITPROPID_ViewLangOpt_WordWrap，`vt`如`idprop`參數。 在這個呼叫，`vt`是變數類型為 VT_BOOL 和`vt.boolVal`為 VARIANT_TRUE。  
  
## <a name="resetting-changed-view-settings"></a>重設已變更之檢視設定  
 若要重設任何已變更之檢視的核心編輯器執行個體的設定，請呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A>方法並指定適當的設定值，在`idprop`參數。  
  
 例如，若要允許自動換行自由浮動，您會移除它屬性類別目錄藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A>和指定的值是針對 VSEDITPROPID_ViewLangOpt_WordWrap`idprop`參數。  
  
 若要一次移除核心編輯器的所有已變更的值，指定 VSEDITPROPID_ViewComposite_AllCodeWindowDefaults，如 vt 值`idprop`參數。 在這個呼叫，vt 是變數類型為 VT_BOOL，vt.boolVal 為 VARIANT_TRUE。  
  
## <a name="see-also"></a>另請參閱  
 [核心編輯器內](../extensibility/inside-the-core-editor.md)   
 [使用舊版 API 存取 theText 檢視](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [選項對話方塊](../ide/reference/options-dialog-box-visual-studio.md)