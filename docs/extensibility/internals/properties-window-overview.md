---
title: 屬性視窗概觀 |Microsoft Docs
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
ms.openlocfilehash: 05c772365c42037bfd97a2a31b80efc2f5f1a48b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347820"
---
# <a name="properties-window-overview"></a>屬性視窗概觀
**屬性** 視窗來顯示在 windows 中可用的兩個主要類型中選取的物件的屬性[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。 這兩種 windows 類型如下：

- 例如 方案總管、 類別檢視 和 物件瀏覽器工具視窗

- 包含這類編輯器和 forms 設計工具，以及 XML 編輯器、 HTML 編輯器的設計工具的文件視窗

## <a name="using-the-properties-window"></a>使用 [屬性] 視窗
 **屬性**視窗會顯示單一或多個選取的項目屬性。 如果選取多個項目，則會顯示所有選取的物件的所有屬性的交集。

 在表單設計視窗或 HTML 編輯器使用 COM + 中繼資料內所選物件的相關事件會顯示在**屬性**視窗。 例如，您可以在 [選取] 按鈕，並顯示其相關聯的事件，例如`OnClick`事件，可以連結到該按鈕。

 在顯示的事件**屬性**視窗主要用於搭配繫結至程式碼的物件。 如果您要編輯的檔案格式並沒有任何項目與程式碼，您不會有任何事件。 事件只會顯示在**屬性**之間執行的程式碼和特定事件，與特定物件相關聯的繫結時，視窗。 這個範例會在執行時啟動該物件的所選物件的程式碼。

 下表列出所使用的主要介面**屬性**視窗。

|介面名稱|描述|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|提供類別，以一份**屬性**視窗，並將每一個屬性對應至分類。|
|[IDispatch 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|公開物件的方法與屬性，以程式設計的工具以及其他支援自動化的應用程式。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|提供呼叫的省略符號 （...） 按鈕*建造商*，開啟強制回應對話方塊視窗物件本身所實作。 值，輕鬆地型別不是使用者在文字欄位中時，會使用它。 比方說，它可能會用來開啟色彩選擇器可讓您決定的 RGB 值。|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|提供用來更新中所顯示資訊的物件的存取權**屬性**視窗。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 是由 Vspackage 實作針對每個視窗，其中包含要顯示的相關屬性與可選取物件。|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|提供介面和結構的欄位類型的物件，例如方法的相關的資訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|可讓 Vspackage 接收通知的選取項目事件，並擷取目前的專案階層架構、 項目、 項目值和命令 UI 內容的相關資訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|提供的環境具有多個選取項目存取權。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|用來提供顯示在某些屬性上的名稱已當地語系化**屬性**視窗。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|通知目前的選取項目，項目值或命令 UI 內容的變更已註冊的 Vspackage。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|通知目前的選取範圍變更的環境，並提供新的選取項目與相關的階層] 和 [項目資訊的存取權。|

 如需詳細資訊`IDispatch`，請參閱 MSDN library。

## <a name="see-also"></a>另請參閱
- [擴充屬性](../../extensibility/internals/extending-properties.md)
- [屬性視窗中的欄位和介面](../../extensibility/internals/properties-window-fields-and-interfaces.md)