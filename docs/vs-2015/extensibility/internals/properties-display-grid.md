---
title: 屬性會顯示格線 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5fd5e17d764336cda450c726023b209f89f194a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180388"
---
# <a name="properties-display-grid"></a>屬性顯示格線
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**屬性**視窗會顯示在方格內的欄位。 左側的資料行包含的屬性名稱;右邊的資料行包含的屬性值。  
  
## <a name="working-with-the-grid"></a>使用格線  
 兩個資料行清單會顯示您可以在設計階段，以及其目前的設定變更的組態無關屬性。 請注意，可能不會顯示所有屬性。 屬性可以設為隱藏，比方說，是藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A>方法。 具體來說，要隱藏具有屬性的子屬性，請[隱藏屬性，有子屬性](../../misc/hiding-properties-that-have-child-properties.md)。  
  
 推播的資訊**屬性** 視窗中，IDE 會使用<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 會呼叫每個視窗，其中包含可選取的物件與相關的屬性，以顯示在 Vspackage**屬性**視窗。 **方案總管**的實作<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>呼叫`GetProperty`使用<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>您的專案階層架構，來取得階層中的可瀏覽物件中。  
  
 如果 VSPackage nepodporuje <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>，IDE 會嘗試使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>使用的值<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>的階層項目或項目提供。  
  
 您不需要建立 VSPackage 的專案<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>因為 IDE 提供視窗封裝實作它 (例如**方案總管 中**) 建構<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>代替它。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 包含 IDE 所呼叫的三種方法：  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> 包含要顯示在選取的物件數目**屬性**視窗。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> 會傳回`IDispatch`選取要顯示在物件**屬性**視窗。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> 可讓任何所傳回的物件<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>選取使用者。 這可讓 VSPackage 以視覺化方式更新選取項目顯示在 UI 中的使用者。  
  
  **屬性** 視窗中擷取資訊從`IDispatch`以擷取瀏覽屬性的物件。 使用屬性瀏覽器`IDispatch`它支援藉由查詢要求之物件的哪些屬性`ITypeInfo`，這取自`IDispatch::GetTypeInfo`。 瀏覽器然後使用這些值來擴展**屬性**視窗並變更方格中顯示個別屬性的值。 屬性資訊會維護物件本身內。  
  
  因為傳回的物件支援`IDispatch`，呼叫者可以取得資訊，例如物件的名稱，藉由呼叫`IDispatch::Invoke`或`ITypeInfo::Invoke`使用預先定義的分派識別項 (DISPID)，表示所要的資訊。 宣告的 Dispid 是負數，以確保它們不會與使用者定義的識別項衝突。  
  
  **屬性**視窗會顯示不同類型的欄位，根據所選物件的特定屬性的屬性。 這些欄位包含編輯方塊、 下拉式清單和自訂編輯器對話方塊的連結。  
  
- 列舉的清單中包含的值藉由擷取<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>查詢`IDispatch`。 從列舉清單取得的值可以變更屬性方格中，按兩下欄位名稱，或按一下值，然後從下拉式清單中選取新的值。 有預先定義的列舉清單中的設定的屬性，按兩下 [屬性] 清單中的屬性名稱逐一循環顯示可用的選項。 預先定義的屬性，只有兩個選擇，例如 true/false 時，請按兩下要切換這些選項的屬性名稱。  
  
- 如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A>是`false`，表示值已變更，以粗體文字顯示值。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> 用來判斷值，是否可以重設為原始值。 如果因此，您可以變更回預設值上按一下滑鼠右鍵，然後選擇**重設**從顯示的功能表。 否則，您必須手動變更此值設回預設值。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 也可讓您當地語系化和隱藏在設計階段期間所顯示的屬性名稱，但不會影響執行階段期間所顯示的屬性名稱。  
  
- 按一下省略符號 （...） 按鈕，就會顯示使用者可以從中選取 （例如，色彩選擇器或 [字型] 清單中） 的屬性值的清單。 <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> 提供這些值。  
  
## <a name="see-also"></a>另請參閱  
 [擴充屬性](../../extensibility/internals/extending-properties.md)
