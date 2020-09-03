---
title: 使用舊版 API 變更視圖設定 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7d58d1477b9d7f58242f8cb4db7c3c360c248b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184470"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>使用舊版 API 變更檢視設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用者可以透過 [ **選項** ] 對話方塊來變更核心編輯器功能的設定，例如自動換行、選取邊界和虛擬空間。 不過，您也可以透過程式設計方式變更這些設定。  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>使用舊版 API 變更設定  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>介面會公開一組文字編輯器屬性。 文字視圖包含屬性的類別 (GUID_EditPropCategory_View_MasterSettings) ，代表文字視圖的程式設計變更設定群組。 當您以這種方式變更視圖設定之後，就無法在 [ **選項** ] 對話方塊中變更它們，直到重設為止。  
  
 以下是變更核心編輯器實例之視圖設定的一般程式。  
  
1. `QueryInterface`在介面 () 上呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> 。  
  
2. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> 方法，並為參數指定 GUID_EditPropCategory_View_MasterSettings 的值 `rguidCategory` 。  
  
     這麼做會傳回介面的指標 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> ，其中包含一組適用于視圖的強制屬性。 此群組中的任何設定都會永久強制執行。 如果設定不在此群組中，則會遵循 [ **選項** ] 對話方塊或使用者命令中指定的選項。  
  
3. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> 方法，在參數中指定適當的設定值 `idprop` 。  
  
     例如，若要強制自動換行，請 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> 針對參數呼叫並指定 VSEDITPROPID_ViewLangOpt_WordWrap 的值 `vt` `idprop` 。 在此呼叫中， `vt` 是類型 VT_BOOL 的變數，而且 `vt.boolVal` 是 VARIANT_TRUE。  
  
## <a name="resetting-changed-view-settings"></a>重設變更的視圖設定  
 若要重設核心編輯器實例的任何已變更視圖設定，請呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> 方法，並在參數中指定適當的設定值 `idprop` 。  
  
 例如，若要允許自動換行至浮點數，您可以呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> 並指定參數的 VSEDITPROPID_ViewLangOpt_WordWrap 值，從屬性類別中移除它 `idprop` 。  
  
 若要一次移除核心編輯器的所有變更設定，請為參數指定 VSEDITPROPID_ViewComposite_AllCodeWindowDefaults、vt 的值 `idprop` 。 在此呼叫中，vt 是 VT_BOOL 類型的變數，而 boolVal 是 VARIANT_TRUE。  
  
## <a name="see-also"></a>另請參閱  
 [在核心編輯器中](../extensibility/inside-the-core-editor.md)   
 [使用舊版 API 存取文字 View](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [選項對話方塊](../ide/reference/options-dialog-box-visual-studio.md)
