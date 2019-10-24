---
title: 屬性視窗總覽 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61887844e06a88cab9eaa8ca8be7a89c124e2340
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725077"
---
# <a name="properties-window-overview"></a>屬性視窗概觀
[**屬性**] 視窗是用來顯示在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式開發環境（IDE）中可用的兩種主要 windows 類型中選取之物件的屬性。 這兩種 windows 類型為：

- 工具視窗，例如方案總管、類別檢視和物件瀏覽器

- 包含這類編輯器和設計工具的文件視窗，做為表單設計工具、XML 編輯器和 HTML 編輯器

## <a name="using-the-properties-window"></a>使用屬性視窗
 [**屬性**] 視窗會顯示單一或多個選取專案的屬性。 如果選取多個專案，則會顯示所有所選物件的所有屬性交集。

 [**屬性**] 視窗中會顯示與表單設計視窗內所選物件或使用 com + 中繼資料的 HTML 編輯器相關的事件。 例如，您可以選取一個按鈕，並顯示其相關聯的事件，例如可以連結到該按鈕的 `OnClick` 事件。

 [**屬性**] 視窗中顯示的事件主要是與系結至程式碼的物件搭配使用。 如果您要編輯的檔案格式與程式碼無關，就不會有任何事件。 只有在執行中的程式碼和與特定物件相關聯的特定事件之間有系結時，事件才會顯示在 [**屬性**] 視窗中。 其中一個範例是所選物件的程式碼後置，會在該物件啟動時執行。

 下表列出 [**屬性**] 視窗所使用的主要介面。

|介面名稱|描述|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|提供 [**屬性**] 視窗的分類清單，並將每個屬性對應至類別目錄。|
|[IDispatch 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|將物件的方法和屬性公開給支援自動化的程式設計工具和其他應用程式。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|提供稱為產生器的省略號（...）按鈕，可開啟物件*本身所實*作為的強制回應對話方塊視窗。 當使用者不容易在文字欄位中輸入值時使用。 例如，它可能會用來開啟色彩選擇器，以決定您的 RGB 值。|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|提供物件的存取權，用來更新 [**屬性**] 視窗中顯示的資訊。 Vspackage 會針對每個視窗（其中包含可選取要顯示的相關屬性），為其執行 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>。|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|提供物件類型的相關資訊，例如介面的方法和結構的欄位。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|可讓 Vspackage 接收選取事件的通知，以及取得目前專案階層、專案、元素值和命令 UI 內容的相關資訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|為環境提供多個選取範圍的存取權。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|用來在 [**屬性**] 視窗中顯示的某些屬性上提供當地語系化的名稱。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|通知已註冊 Vspackage 目前選取專案、元素值或命令 UI 內容的變更。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|通知環境目前選取範圍中的變更，並提供與新選取範圍相關之階層和專案資訊的存取權。|

 如需 `IDispatch` 的詳細資訊，請參閱 MSDN library。

## <a name="see-also"></a>請參閱
- [擴充屬性](../../extensibility/internals/extending-properties.md)
- [屬性視窗中的欄位和介面](../../extensibility/internals/properties-window-fields-and-interfaces.md)