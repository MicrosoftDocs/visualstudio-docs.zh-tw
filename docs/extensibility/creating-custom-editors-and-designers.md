---
title: 建立自訂編輯器和設計師 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9f56b82225e1e40782b6753bea03d3c1780f596
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739482"
---
# <a name="create-custom-editors-and-designers"></a>建立自訂編輯器和設計器

Visual Studio 整合式開發環境 (IDE) 可以承載不同類型的編輯器:

- 視覺工作室核心編輯器

- 自訂編輯器

- 外部編輯器

- 設計工具

以下資訊可説明您選擇所需的編輯器類型。

## <a name="types-of-editor"></a>編輯器型別

有關 Visual Studio 核心編輯器的資訊,請參閱[延伸編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)。

### <a name="custom-editors"></a>自訂編輯器
 自定義編輯器是專為在特殊情況下工作而設計的編輯器。 例如,您可以創建一個編輯器,其功能是將數據讀取和寫入特定存儲庫(如 Microsoft Exchange 伺服器)。 如果希望編輯器僅與項目類型配合使用,或者希望編輯器僅具有幾個特定命令,請選擇自定義編輯器。 但是請注意,使用者將無法使用自定義編輯器編輯標準[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案。

 自定義編輯器可以使用編輯器工廠,並將有關編輯器的資訊添加到註冊表中。 但是,與自定義編輯器關聯的項目類型可以以其他方式實例化自定義編輯器。

 自定義編輯器可以使用就地啟動或簡化嵌入來實現檢視。

### <a name="external-editors"></a>外部編輯器
 外部編輯器是未整合到可視化工作室的編輯,例如Microsoft Word、記事本或Microsoft FrontPage。 例如,如果您從 VSPackage 向該編輯器傳遞文本,則可以調用此類編輯器。 外部編輯器自行註冊,可在可視化工作室外使用。 當您調用外部編輯器時,它可以嵌入到主機視窗中,然後它將顯示在 IDE 視窗中。 如果沒有,則 IDE 會為其創建單獨的視窗。

 該方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A><xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>使用 枚舉設置文檔優先順序。 如果指定`DP_External`了該值,則外部編輯器可以打開該檔。

## <a name="editor-design-decisions"></a>編輯器設計決策
 以下設計問題將協助您選擇最適合您的應用程式的編輯器類型:

- 您的應用程式是否會將其數據保存在檔中? 如果它將資料儲存在檔案中,它們是否採用自訂格式或標準格式?

   如果使用標準檔案格式,除了專案之外的其他項目類型將能夠打開和讀取/寫入數據。 但是,如果您使用自訂檔案格式,則只有項目類型才能打開和讀取/寫入數據。

   如果專案使用檔,則應自定義標準編輯器。 如果專案不使用檔,而是使用資料庫或其他儲存庫中的專案,則應創建自定義編輯器。

- 編輯器是否需要託管 ActiveX 控制項?

   如果編輯器承載 ActiveX 控制件,則實現就地啟動編輯器,如[就地啟動](/visualstudio/misc/in-place-activation?view=vs-2015)中所述。 如果它不承載 ActiveX 控制項,則使用簡化的嵌入編輯器或[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]自訂 預設編輯器。

- 您的編輯會支援多個檢視嗎? 如果希望編輯器的檢視與預設編輯器同時可見,則必須支援多個檢視。

   如果編輯器需要支援多個檢視,則編輯器的文檔數據和文檔檢視對象必須是單獨的物件。 有關詳細資訊,請參閱[支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)。

   如果編輯器支援多個檢視,您是否計劃對文件資料物件使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器的文字緩衝區實現(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件)? 也就是說,是否要支援編輯器與[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器並排查看? 執行此操作的能力是表單設計器的基礎。

- 如果需要託管外部編輯器,編輯器是否可以嵌入到內部[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?

   如果可以嵌入它,則應為外部編輯器建立主機視窗,<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>然後呼叫方法並將 entle 設定<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>`DP_External`為 。 如果無法嵌入編輯器,IDE 將自動為其創建單獨的視窗。

## <a name="in-this-section"></a>本節內容

[演練:建立自訂編輯器](../extensibility/walkthrough-creating-a-custom-editor.md)\
說明如何創建自定義編輯器。

[演練:向自訂編輯器新增功能](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
說明如何向自定義編輯器添加功能。

[設計器初始化與中繼資料設定](../extensibility/designer-initialization-and-metadata-configuration.md)\
說明如何初始化設計器。

[提供設計人員提供復原支援](../extensibility/supplying-undo-support-to-designers.md)\
說明如何為設計人員提供撤銷支援。

[自訂編輯器中的語法著色](../extensibility/syntax-coloring-in-custom-editors.md)\
解釋核心編輯器和自定義編輯器中的語法著色之間的區別。

[自訂編輯器中的文件資料與文件檢視](../extensibility/document-data-and-document-view-in-custom-editors.md)\
說明如何在自定義編輯器中實現文檔數據和文檔檢視。

## <a name="related-sections"></a>相關章節

[編輯器中的舊介面](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)\
說明如何通過舊 API 訪問核心編輯器。

[開發傳統語言服務](../extensibility/internals/developing-a-legacy-language-service.md)\
說明如何實現語言服務。

[擴展視覺工作室的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)\
說明如何創建與的其餘部分匹配的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]UI 元素。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
