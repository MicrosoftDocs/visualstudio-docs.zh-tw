---
title: 屬性視窗總覽 |Microsoft Docs
description: 瞭解在此總覽中，用來與 Visual Studio IDE 中的屬性視窗互動的介面。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a33d393cfd904bdae890f4ead9a4c25a6451460
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837290"
---
# <a name="properties-window-overview"></a>屬性視窗概觀
[ **屬性** ] 視窗是用來顯示在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式開發環境 (IDE) 所提供的兩個主要 windows 類型中所選取物件的屬性。 這兩種類型的 windows 為：

- 工具視窗，例如方案總管、類別檢視和物件瀏覽器

- 包含像是表單設計工具、XML 編輯器和 HTML 編輯器等編輯器和設計工具的檔視窗

## <a name="using-the-properties-window"></a>使用 [屬性] 視窗
 [ **屬性** ] 視窗會顯示單一或多個選取專案的屬性。 如果選取多個專案，則會顯示所有選定物件的所有屬性交集。

 在 [ **屬性** ] 視窗中，會顯示與表單設計視窗或 HTML 編輯器中使用 com + 中繼資料相關之選取物件的相關事件。 例如，您可以選取按鈕，並顯示其相關聯的事件，例如 `OnClick` 可連結至該按鈕的事件。

 顯示在 [ **屬性** ] 視窗中的事件主要是與系結至程式碼的物件搭配使用。 如果您編輯的檔案格式與程式碼沒有任何作用，就不會有任何事件。 當執行中的程式碼與特定物件相關聯的特定事件之間有系結時，事件才會顯示在 [ **屬性** ] 視窗中。 其中一個範例就是啟始物件時所執行之所選物件的程式碼後方。

 下表列出 [ **屬性** ] 視窗所使用的主要介面。

|介面名稱|描述|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|將類別清單提供給 [ **屬性** ] 視窗，並將每個屬性對應至類別目錄。|
|[IDispatch 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|將物件的方法和屬性公開給支援自動化的程式設計工具和其他應用程式。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|提供省略號 ( ... ) 稱為產生器的按鈕，可開啟由物件本身所 *執行的模式* 對話方塊視窗。 當使用者無法在文字欄位中輕鬆輸入值時使用。 例如，它可能用來開啟色彩選擇器，以決定您的 RGB 值。|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|提供物件的存取權，這些物件是用來更新 [ **屬性** ] 視窗中顯示的資訊。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 是由 Vspackage 針對每個視窗所執行，其中包含要顯示之相關屬性的可選取物件。|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|提供物件類型的相關資訊，例如介面的方法和結構的欄位。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|讓 Vspackage 接收選取事件的通知，以及取得目前專案階層、專案、專案值和命令 UI 內容的相關資訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|提供可存取多重選取專案的環境。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|用來在 [ **屬性** ] 視窗中顯示的某些屬性上提供當地語系化的名稱。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|通知已登錄 Vspackage 目前選取專案、元素值或命令 UI 內容的變更。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|通知環境目前選取範圍中的變更，並提供與新選項相關之階層和專案資訊的存取權。|

 如需有關的詳細資訊 `IDispatch` ，請參閱 MSDN library。

## <a name="see-also"></a>另請參閱
- [擴充屬性](../../extensibility/internals/extending-properties.md)
- [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md)
