---
title: 建立自訂編輯器和設計工具 |Microsoft Docs
description: 深入瞭解可由 Visual Studio IDE 裝載的不同編輯器類型：核心編輯器、自訂編輯器、外部編輯器和設計工具。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2882cfa103627672e5c96a0e3d4b2a23b4b4ba9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055774"
---
# <a name="create-custom-editors-and-designers"></a>建立自訂編輯器和設計工具

Visual Studio 整合式開發環境 (IDE) 可以裝載不同類型的編輯器：

- Visual Studio 核心編輯器

- 自訂編輯器

- 外部編輯器

- 設計工具

下列資訊可協助您選擇所需的編輯器類型。

## <a name="types-of-editor"></a>編輯器的類型

如需 Visual Studio core 編輯器的詳細資訊，請參閱 [擴充編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)。

### <a name="custom-editors"></a>自訂編輯器
 自訂編輯器是設計來在特殊情況下工作的編輯器。 例如，您可以建立編輯器，其函式會將資料讀取和寫入至特定儲存機制（例如 Microsoft Exchange server）。 如果您只想要搭配您的專案類型使用的編輯器，或只想要有一些特定命令的編輯器，請選擇自訂編輯器。 不過請注意，使用者將無法使用自訂編輯器來編輯標準 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案。

 自訂編輯器可以使用編輯器 factory，並將編輯器的相關資訊新增至登錄。 不過，與自訂編輯器相關聯的專案類型可以透過其他方式將自訂編輯器具現化。

 自訂編輯器可以使用就地啟用或簡化內嵌來執行視圖。

### <a name="external-editors"></a>外部編輯器
 外部編輯器是未整合至 Visual Studio 的編輯器，例如 Microsoft Word、記事本或 Microsoft FrontPage。 例如，您可以呼叫這類編輯器，例如，從 VSPackage 將文字傳遞給它。 外部編輯器會自行註冊，而且可以在 Visual Studio 之外使用。 當您呼叫外部編輯器，而且可以內嵌于主視窗中時，它會顯示在 IDE 的視窗中。 如果沒有，則 IDE 會為它建立個別的視窗。

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>方法會使用列舉來設定檔優先權 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 。 如果 `DP_External` 指定了值，就可以透過外部編輯器來開啟檔案。

## <a name="editor-design-decisions"></a>編輯器設計決策
 下列設計問題將協助您選擇最適合您應用程式的編輯器類型：

- 您的應用程式是否會將其資料儲存在檔案中？ 如果它會將其資料儲存在檔案中，它們會採用自訂或標準格式嗎？

   如果您使用標準檔案格式，則除了專案以外，其他專案類型也可以開啟和讀取/寫入資料。 但是，如果您使用自訂檔案格式，則只有您的專案類型可以開啟和讀取/寫入資料。

   如果您的專案使用檔案，則您應該自訂標準編輯器。 如果您的專案不使用檔案，而是使用資料庫或其他存放庫中的專案，則您應該建立自訂編輯器。

- 您的編輯器是否需要裝載 ActiveX 控制項？

   如果您的編輯器裝載 ActiveX 控制項，請依照就地 [啟用](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015)的說明，執行就地啟用編輯器。 如果未裝載 ActiveX 控制項，則請使用簡化的內嵌編輯器，或自訂 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 預設編輯器。

- 您的編輯器是否支援多個視圖？ 如果您想要讓編輯器的查看與預設編輯器同時顯示，您必須支援多個視圖。

   如果您的編輯器需要支援多個視圖，則編輯器的檔資料和檔視圖物件必須是個別的物件。 如需詳細資訊，請參閱 [支援多個檔的觀點](../extensibility/supporting-multiple-document-views.md)。

   如果您的編輯器支援多個視圖，您是否打算 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 針對您的檔資料物件使用核心編輯器的文字緩衝區執行 (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 物件) ？ 也就是，您是否想要與核心編輯器並存支援您的編輯器視圖 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ？ 執行這項作業的能力是表單設計工具的基礎。

- 如果您需要裝載外部編輯器，編輯器是否可以內嵌在內部 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ？

   如果可以內嵌，您應該建立外部編輯器的主控制項視窗，然後呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 方法並將 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 列舉值設定為 `DP_External` 。 如果無法內嵌編輯器，IDE 會自動為它建立一個不同的視窗。

## <a name="in-this-section"></a>本節內容

[逐步解說：建立自訂編輯器](../extensibility/walkthrough-creating-a-custom-editor.md)\
說明如何建立自訂編輯器。

[逐步解說：將功能新增至自訂編輯器](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
說明如何將功能加入至自訂編輯器。

[設計工具初始化和中繼資料設定](../extensibility/designer-initialization-and-metadata-configuration.md)\
說明如何初始化設計工具。

[為設計工具提供復原支援](../extensibility/supplying-undo-support-to-designers.md)\
說明如何為設計工具提供復原支援。

[自訂編輯器中的語法著色](../extensibility/syntax-coloring-in-custom-editors.md)\
說明核心編輯器和自訂編輯器中的語法著色之間的差異。

[自訂編輯器中的檔資料和檔查看](../extensibility/document-data-and-document-view-in-custom-editors.md)\
說明如何在自訂編輯器中執行檔資料和檔查看。

## <a name="related-sections"></a>相關章節

[編輯器中的舊版介面](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015)\
說明如何透過舊版 API 來存取核心編輯器。

[開發舊版語言服務](../extensibility/internals/developing-a-legacy-language-service.md)\
說明如何執行語言服務。

[延伸 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)\
說明如何建立符合其餘部分的 UI 元素 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
