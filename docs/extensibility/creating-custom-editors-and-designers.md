---
title: 建立自訂編輯器和設計工具 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0ddfe2b61c8ef08d77fbb7c841b3bb69c167af2f
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903733"
---
# <a name="create-custom-editors-and-designers"></a>建立自訂編輯器和設計工具

Visual Studio 整合式開發環境（IDE）可以裝載不同類型的編輯器：

- Visual Studio 核心編輯器

- 自訂編輯器

- 外部編輯器

- 設計工具

下列資訊可協助您選擇所需的編輯器類型。

## <a name="types-of-editor"></a>編輯器的類型

如需 Visual Studio 核心編輯器的相關資訊，請參閱[擴充編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)。

### <a name="custom-editors"></a>自訂編輯器
 自訂編輯器是專為在特殊情況下工作而設計的。 例如，您可以建立一個編輯器，其功能是用來讀取和寫入資料至特定儲存機制，例如 Microsoft Exchange server。 如果您想要只搭配專案類型使用的編輯器，或如果您想要只有幾個特定命令的編輯器，請選擇自訂編輯器。 不過，請注意，使用者將無法使用自訂編輯器來編輯標準 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案。

 自訂編輯器可以使用編輯器 factory，並將編輯器的相關資訊新增至登錄。 不過，與自訂編輯器相關聯的專案類型可以透過其他方式具現化自訂編輯器。

 自訂編輯器可以使用就地啟用或簡化內嵌來執行視圖。

### <a name="external-editors"></a>外部編輯器
 外部編輯器是未整合到 Visual Studio 的編輯器，例如 Microsoft Word、記事本或 Microsoft FrontPage。 例如，如果您要從 VSPackage 傳遞文字給它，您可能會呼叫這類編輯器。 外部編輯器會自行註冊，並可在 Visual Studio 外部使用。 當您呼叫外部編輯器，而且它可以內嵌在主視窗中時，它會出現在 IDE 的視窗中。 如果沒有，則 IDE 會為它建立另一個視窗。

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>方法會使用列舉來設定檔優先權 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 。 如果 `DP_External` 指定了值，就可以由外部編輯器開啟檔案。

## <a name="editor-design-decisions"></a>編輯器設計決策
 下列設計問題可協助您選擇最適合您應用程式的編輯器類型：

- 您的應用程式是否會將其資料儲存在檔案中？ 如果它會將資料儲存在檔案中，它們會採用自訂或標準格式嗎？

   如果您使用標準檔案格式，除了專案之外，其他專案類型也可以開啟和讀取/寫入資料。 不過，如果您使用自訂檔案格式，只有您的專案類型才能夠開啟和讀取/寫入資料。

   如果您的專案使用檔案，則您應該自訂標準編輯器。 如果您的專案不使用檔案，而是使用資料庫或其他存放庫中的專案，則您應該建立自訂編輯器。

- 您的編輯器是否需要裝載 ActiveX 控制項？

   如果您的編輯器裝載 ActiveX 控制項，則會如就地[啟用](/visualstudio/misc/in-place-activation?view=vs-2015)中所述，執行就地啟用編輯器。 如果未裝載 ActiveX 控制項，則請使用簡化的內嵌編輯器，或自訂 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 預設編輯器。

- 您的編輯器是否支援多個視圖？ 如果您想要讓編輯器的視圖與預設編輯器同時可見，您必須支援多個視圖。

   如果您的編輯器需要支援多個視圖，則編輯器的檔資料和檔視圖物件必須是個別的物件。 如需詳細資訊，請參閱[支援多個檔視圖](../extensibility/supporting-multiple-document-views.md)。

   如果您的編輯器支援多個視圖，您是否計畫將 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 核心編輯器的文字緩衝區實（ <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 物件）用於檔資料物件？ 也就是，您是否想要同時支援您的編輯器視圖與 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 核心編輯器？ 執行這項操作的能力是表單設計工具的基礎。

- 如果您需要裝載外部編輯器，編輯器是否可以內嵌在內 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ？

   如果可以內嵌，您應該為外部編輯器建立主視窗，然後呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 方法，並將 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 列舉值設定為 `DP_External` 。 如果編輯器無法內嵌，IDE 會自動為其建立個別的視窗。

## <a name="in-this-section"></a>本節內容

[逐步解說：建立自訂編輯器](../extensibility/walkthrough-creating-a-custom-editor.md)\
說明如何建立自訂編輯器。

[逐步解說：將功能加入至自訂編輯器](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
說明如何將功能加入至自訂編輯器。

[設計工具初始化和中繼資料設定](../extensibility/designer-initialization-and-metadata-configuration.md)\
說明如何初始化設計工具。

[為設計工具提供復原支援](../extensibility/supplying-undo-support-to-designers.md)\
說明如何為設計工具提供復原支援。

[自訂編輯器中的語法著色](../extensibility/syntax-coloring-in-custom-editors.md)\
說明核心編輯器和自訂編輯器中語法著色的差異。

[自訂編輯器中的檔資料和檔視圖](../extensibility/document-data-and-document-view-in-custom-editors.md)\
說明如何在自訂編輯器中執行檔資料和檔視圖。

## <a name="related-sections"></a>相關章節

[編輯器中的舊版介面](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)\
說明如何透過舊版 API 存取核心編輯器。

[開發舊版語言服務](../extensibility/internals/developing-a-legacy-language-service.md)\
說明如何執行語言服務。

[擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)\
說明如何建立符合其餘部分的 UI 元素 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
