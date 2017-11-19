---
title: "屬性會顯示方格 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35b36c357c9b98d81627eea0d511b0b4fd49f693
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="properties-display-grid"></a>屬性顯示格線
**屬性**視窗會顯示格線中的欄位。 左側資料行包含的屬性名稱。右邊的資料行包含的屬性值。  
  
## <a name="working-with-the-grid"></a>使用格線  
 兩個資料行清單會顯示可以在設計階段和其目前的設定變更的組態無關屬性。 請注意，可能不會顯示所有屬性。 屬性可以設為隱藏，比方說，藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A>方法。 尤其是要隱藏具有屬性的子屬性：  
  
1.  設定`pfDisplay`中的參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A>至`FALSE`。  
  
2.  設定`pfHide`中的參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A>至`TRUE`。  
  
 推播的資訊至**屬性**視窗中，IDE 使用<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>Vspackage 會呼叫每個視窗，其中包含可選取的物件與相關的屬性，以顯示在**屬性**視窗。 **方案總管 中**的實作<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>呼叫`GetProperty`使用<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>您取得的可瀏覽的物件階層架構中的專案階層架構中。  
  
 如果您的 VSPackage 不支援<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>，IDE 會嘗試使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>使用的值<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>階層項目或項目提供。  
  
 您不需要建立 VSPackage 的專案<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>因為 IDE 提供視窗封裝，實作該 (例如，**方案總管 中**) 建構<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>代替它。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>包含三個 IDE 所呼叫的方法：  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>包含要顯示在選取的物件數目**屬性**視窗。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>傳回`IDispatch`選取要顯示在物件**屬性**視窗。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>可讓任何傳回的物件<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>選取使用者。 這可讓 VSPackage 以視覺化方式更新選取項目顯示在 UI 中的使用者。  
  
 **屬性**視窗會擷取資訊從`IDispatch`來擷取所瀏覽屬性的物件。 屬性瀏覽器使用`IDispatch`它支援藉由查詢要求物件的哪些屬性`ITypeInfo`，這取自`IDispatch::GetTypeInfo`。 瀏覽器然後使用這些值來擴展**屬性**視窗，並變更方格中顯示個別屬性的值。 內容資訊是物件本身內維護。  
  
 因為傳回的物件支援`IDispatch`，呼叫端可以取得資訊，例如物件的名稱，藉由呼叫`IDispatch::Invoke`或`ITypeInfo::Invoke`與預先定義的分派識別項 (DISPID)，表示所需的資訊。 宣告的 Dispid 是負數，以確保它們與使用者定義的識別項不衝突。  
  
 **屬性**視窗會顯示不同類型的欄位，根據所選物件的特定屬性的屬性。 這些欄位包括編輯方塊、 下拉式清單和自訂編輯器對話方塊的連結。  
  
-   列舉的清單中包含的值藉由擷取<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>查詢以`IDispatch`。 從列舉清單取得的值可以變更屬性方格中，按兩下該欄位的名稱，或按一下值，然後從下拉式清單中選取新的值。 對於具有預先定義的列舉清單中的設定的屬性，按兩下 [屬性] 清單中的屬性名稱逐一循環顯示可用的選項。 預先定義的屬性，只有兩個選項，例如 true/false 與按兩下要切換這些選項的屬性名稱。  
  
-   如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A>是`false`，指出已變更值，值會以粗體文字顯示。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>用來判斷值是否可以重設為原始值。 因此，您可以變更回預設值上按一下滑鼠右鍵，然後選擇如果**重設**從顯示的功能表。 否則，您必須手動將值變更回預設值。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>也可讓您當地語系化和隱藏在設計階段期間所顯示的屬性名稱，但不會影響執行階段期間所顯示的屬性名稱。  
  
-   按一下省略符號 （...） 按鈕，就會顯示使用者可以從中選取 （例如色彩選擇器或字型 清單中） 的屬性值的清單。 <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>提供這些值。  
  
## <a name="see-also"></a>另請參閱  
 [擴充屬性](../../extensibility/internals/extending-properties.md)