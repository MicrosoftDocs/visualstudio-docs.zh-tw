---
title: 屬性視窗概述 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 445a43cec976f363873c89dfe9b8e05429aebaf2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706036"
---
# <a name="properties-window-overview"></a>屬性視窗概觀
屬性**視窗**[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]用於顯示 在整合式開發環境 (IDE) 中可用的兩種主要視窗類型中選擇的物件的屬性。 這兩種類型的視窗是:

- 工具視窗,如解決方案資源管理員、類檢視和物件瀏覽器

- 包含表單設計師、XML 編輯器及 HTML 編輯器及編輯器和設計器的文件視窗

## <a name="using-the-properties-window"></a>使用屬性視窗
 屬性 **「視窗**顯示單個或多個選定項目的屬性。 如果選擇了多個項,將顯示所有選定物件的所有屬性的交集。

 與表單表型設計視窗中的選擇的物件相關的事件或使用 COM+ 中繼資料的 HTML 編輯器將顯示在 **「屬性」** 視窗中。 例如,您可以選擇一個按鈕並顯示其關聯的事件,如事件`OnClick`,該事件可以連結到該按鈕。

 **屬性**視窗中顯示的事件主要與綁定到代碼的物件一起使用。 如果要編輯與代碼無關的檔案格式,則不會有任何事件。 僅當正在運行的代碼與與特定物件關聯的某些事件之間存在綁定時,事件才會顯示在 **「屬性」** 視窗中。 例如,在啟動該物件時執行的選定物件後面的代碼。

 下表列出了**屬性**視窗使用的主要介面。

|介面名稱|描述|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|向 **「屬性」** 視窗提供類別清單,並將每個屬性映射到類別。|
|[I調度介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|向支援自動化的程式設計工具和其他應用程式公開物件的方法和屬性。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|提供稱為生成器的橢圓 (...) 按鈕,這些*生成器*打開由物件本身實現的模式對話框視窗。 當使用者不容易在文本欄位中鍵入值時使用。 例如,它可用於打開一個顏色選取器,確定RGB值。|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|提供對用於更新 **「屬性」** 視窗中顯示的資訊的物件的訪問。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>由 VSPackages 為每個包含要顯示相關屬性的可選物件的窗口實現。|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|提供有關物件類型的資訊,例如介面的方法和結構的欄位。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|使 VSPackages 能夠接收選擇事件的通知,並檢索有關當前專案層次結構、項、元素值和命令 UI 上下文的資訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|為環境提供對多個選擇的訪問。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|用於在 **「屬性」** 視窗中顯示的某些屬性上提供當地語系化名稱。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|通知已註冊的 VS 包對當前選擇、元素值或命令 UI 上下文的更改。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|通知環境當前所選內容的變化,並提供對與新選擇相關的層次結構和專案資訊的訪問。|

 有關的詳細資訊`IDispatch`,請參閱 MSDN 庫。

## <a name="see-also"></a>另請參閱
- [擴充屬性](../../extensibility/internals/extending-properties.md)
- [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md)
