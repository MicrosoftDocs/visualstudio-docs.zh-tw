---
title: 屬性顯示格線 |Microsoft Docs
description: 瞭解在屬性視窗的方格中找到屬性名稱和屬性值欄位的位置，以及如何在擴充屬性中使用方格。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0dd336701fc25497fdecba8b5b9860a02447558d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970045"
---
# <a name="properties-display-grid"></a>屬性顯示格線

[ **屬性** ] 視窗會在方格中顯示欄位。 左邊的資料行包含屬性名稱;右邊的資料行包含屬性值。

## <a name="work-with-the-grid"></a>使用格線

這兩個數據行的清單會顯示與設定無關的屬性，這些屬性可以在設計階段變更，也可以變更其目前的設定。 請注意，可能不會顯示所有屬性。 您可以將屬性設定為隱藏，例如，藉由執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> 方法。 明確地說，若要隱藏具有子屬性的屬性：

1. 將 `pfDisplay` 參數設定 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> 為 `FALSE` 。

2. 將 `pfHide` 參數設定 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> 為 `TRUE` 。

為了將資訊推送至 [ **屬性** ] 視窗，IDE 會使用 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 針對每個包含可選取物件的視窗，以及要在 [ **屬性** ] 視窗中顯示相關屬性的視窗，會呼叫 vspackage。 **方案總管** <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 使用 __VSHPROPID 來執行 `GetProperty` 呼叫 [。](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) 在您的專案階層中 VSHPROPID_BrowseObject，以取得階層中可流覽的物件。

如果您的 VSPackage 不支援 [__VSHPROPID。VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)，IDE 會嘗試使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> __VSHPROPID 的值 [。](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) 階層專案或專案所提供的 VSHPROPID_SelContainer。

您的專案 VSPackage 不需要建立， <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 因為 IDE 提供的視窗封裝會 (，例如， **方案總管**) 代窗結構 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 。

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 由 IDE 呼叫的三個方法所組成：

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> 包含選取要在 [ **屬性** ] 視窗中顯示的物件數目。

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> 傳回 `IDispatch` 已選取要在 [ **屬性** ] 視窗中顯示的物件。

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> 讓使用者可以選取所傳回的任何物件 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> 。 這可讓 VSPackage 以視覺方式更新 UI 中顯示給使用者的選取專案。

[ **屬性** ] 視窗會從 `IDispatch` 物件中取出資訊，以抓取所流覽的屬性。 屬性瀏覽器 `IDispatch` 會使用來向物件要求查詢所支援的屬性 `ITypeInfo` ，它是從取得的 `IDispatch::GetTypeInfo` 。 瀏覽器接著會使用這些值來填入 [ **屬性** ] 視窗，並變更方格中顯示之個別屬性的值。 屬性資訊會在物件本身內進行維護。

由於傳回的物件支援 `IDispatch` ，呼叫者可以透過呼叫 `IDispatch::Invoke` 或搭配 `ITypeInfo::Invoke` 預先定義的分派識別碼 (DISPID) 來取得資訊（例如物件的名稱），以代表所需的資訊。 宣告的 Dispid 是負的，以確保它們不會與使用者定義的識別碼衝突。

[ **屬性** ] 視窗會根據所選物件的特定屬性屬性，顯示不同類型的欄位。 這些欄位包含編輯方塊、下拉式清單和自訂編輯器對話方塊的連結。

- 查詢會將列舉清單中包含的值取出 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> `IDispatch` 。 您可以在 [屬性] 方格中，按兩下功能變數名稱，或按一下值，然後從下拉式清單中選取新值，藉以變更從列舉清單取得的值。 針對已從列舉清單中預先定義之設定的屬性，按兩下 [屬性] 清單中的屬性名稱，即可迴圈查看可用的選項。 針對只有兩個選項（例如 true/false）的預先定義屬性，按兩下屬性名稱以在選擇之間切換。

- 如果 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> 為 `false` ，表示值已變更，則會以粗體文字顯示值。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> 用來判斷值是否可以重設為原始值。 若是如此，您可以在值上按一下滑鼠右鍵，然後從顯示的功能表中選擇 [ **重設** ]，以變更回預設值。 否則，您必須手動將值變更回預設值。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 也可讓您當地語系化和隱藏設計階段所顯示的屬性名稱，但不會影響執行時間所顯示的屬性名稱。

- 按一下省略號 ( ... ) 按鈕會顯示內容值的清單，使用者可以從中選取 (例如色彩選擇器或字型清單) 。 <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> 提供這些值。

## <a name="see-also"></a>另請參閱

- [擴充屬性](../../extensibility/internals/extending-properties.md)
