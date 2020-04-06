---
title: 屬性顯示格線 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d094c32ba8a64fc636f3fb6dfb2944dc3955628a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706180"
---
# <a name="properties-display-grid"></a>屬性顯示格線

**屬性「** 視窗顯示格格中的欄位」。 左列包含屬性名稱;第二列包含屬性名稱。右列包含屬性值。

## <a name="work-with-the-grid"></a>使用格線

兩列清單顯示可在設計時間更改的與配置無關的屬性及其當前設置。 請注意,可能無法顯示所有屬性。 屬性可以設定為隱藏,例如,透過實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A>方法 。 具體而言,要隱藏具有子屬性的屬性:

1. 將`pfDisplay`<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A>參數`FALSE`設定為 。

2. 將`pfHide`<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A>參數`TRUE`設定為 。

要將資訊推送到 **「屬性」** 視窗,IDE<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>會使用 。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>VSPackages 為包含要在 **「屬性」** 視窗中顯示的相關屬性的可選物件的每個視窗呼叫 VSPackages。 **解決方案資源管理員**使用__VSHPROPID<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>實用`GetProperty`呼叫[。VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)專案層次結構中獲取層次結構中的可瀏覽物件。

如果您的 VS 套件不支援[__VSHPROPID。VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>),IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>嘗試使用[值__VSHPROPID。VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>)層次結構項或項供應。

專案 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>不需要建立 ,因為實現它的 IDE 提供的視窗套件(例如,<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>**解決方案資源管理員**) 代表它建構。

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>由 IDE 呼叫的三種方法組成:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>包含選擇要在 **「屬性」** 視窗中顯示的物件數。

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>返回選擇要`IDispatch`在 **「屬性」** 視窗中顯示的物件。

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>使返回的任何物件<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>都成為可能,由用戶選擇。 這允許 VSPackage 直覺地更新在 UI 中顯示的選擇。

屬性**Properties**視窗`IDispatch`從 物件中提取資訊以檢索正在瀏覽的屬性。 屬性瀏覽器用於`IDispatch`透過查詢`ITypeInfo`(從`IDispatch::GetTypeInfo`中獲取)詢問物件支援的屬性。 然後,瀏覽器使用這些值填充 **「屬性」** 視窗並更改格格中顯示的單個屬性的值。 屬性資訊在物件本身中維護。

由於返回的物件支援`IDispatch`,因此調用方可以通過調`IDispatch::Invoke``ITypeInfo::Invoke`用或 使用表示所需資訊的預定義調度識別碼 (DISPID) 來獲取物件名稱等資訊。 聲明的 DISPID 為負值,以確保它們不與使用者定義的標識符衝突。

屬性**視窗**顯示不同類型的欄位,具體取決於選取物件的特定屬性的屬性。 這些欄位包括編輯框、下拉清單和指向自訂編輯器對話方塊的連結。

- 列舉清單中包含的值由<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>`IDispatch`查詢 取出 。 通過按兩下欄位名稱,或者按一下該值並從下拉清單中選擇新值,可以在屬性網格中更改從枚舉清單中獲取的值。 對於具有枚舉清單中預定義設置的屬性,按兩下「屬性」清單中的屬性名稱會迴圈流覽可用選項。 對於只有兩個選項的預定義屬性(如真/假),按兩下屬性名稱在選項之間切換。

- 如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A>`false`為 ,指示該值已更改,則該值以粗體文本顯示。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>用於確定該值是否可以重置為原始值。 如果是這樣,您可以通過右鍵單擊值並從顯示的菜單中選擇 **「重置」** 來更改回預設值。 否則,您必須手動將值更改回預設值。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>還允許您本地化和隱藏設計期間顯示的屬性的名稱,但不會影響運行時顯示的屬性名稱。

- 按一下省略號 (...) 按鈕將顯示使用者可以從中選擇的屬性值清單(如顏色選取器或字型清單)。 <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>提供這些值。

## <a name="see-also"></a>另請參閱

- [延伸屬性](../../extensibility/internals/extending-properties.md)
