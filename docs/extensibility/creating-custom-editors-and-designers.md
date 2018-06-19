---
title: 建立自訂編輯器和設計工具 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4c0dbc0db9d5116e372d96b43059a393ac8f4b5d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105287"
---
# <a name="creating-custom-editors-and-designers"></a>建立自訂編輯器和設計工具
Visual Studio 整合式的開發環境 (IDE) 可裝載編輯器的不同類型：  
  
-   Visual Studio 核心編輯器  
  
-   自訂編輯器  
  
-   外部編輯器  
  
-   設計工具  
  
 下列資訊可協助您選擇的編輯器，您需要的類型。  
  
## <a name="types-of-editor"></a>類型的編輯器  
 Visual Studio 核心編輯器的相關資訊，請參閱[擴充編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)。  
  
##### <a name="custom-editors"></a>自訂編輯器  
 自訂編輯器是一種為了在特定情況下運作。 例如，您可以建立函式是以讀取和寫入資料至特定的儲存機制，例如 Microsoft Exchange server 的編輯器。 如果您想要搭配您的專案類型只編輯器，或如果您想要編輯器具有少數的特定命令，請選擇自訂編輯器。 不過請注意，使用者不能使用自訂的編輯器編輯標準[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案。  
  
 自訂編輯器可以使用編輯器 factory，並將編輯器 中的相關資訊新增至登錄。 不過，使用自訂編輯器相關聯的專案類型可以具現化中的其他方法的自訂編輯器。  
  
 自訂編輯器可以使用就地啟用或簡化的嵌入實作檢視。  
  
##### <a name="external-editors"></a>外部編輯器  
 外部編輯器的不會整合至 Visual Studio 中，例如 Microsoft Word 中，[記事本] 或 Microsoft FrontPage 的編輯器。 如果比方說，您要將文字至它從您的 VSPackage，您可能會呼叫這類的編輯器。 外部編輯器自行註冊，並可以使用 Visual Studio 之外。 當呼叫外部編輯器，它可以內嵌在主控視窗中，會出現在 IDE 中的視窗。 如果沒有，則 IDE 然後為其建立個別的視窗。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>方法是使用來設定文件的優先順序<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列舉型別。 如果`DP_External`指定值，則可以透過外部編輯器開啟此檔案。  
  
## <a name="editor-design-decisions"></a>編輯器的設計決策  
 下列的設計問題將協助您選擇適合您的應用程式的最佳的編輯器類型：  
  
-   將您的應用程式儲存其資料檔案中或不嗎？ 如果它會將其資料儲存在檔案中，它們會以自訂或標準格式？  
  
     如果您使用標準檔案格式，除了您的專案的其他專案類型將能夠開啟和讀取/寫入資料到它們。 如果您使用自訂的檔案格式，不過，只有您的專案類型將能夠開啟和讀取/寫入資料到它們。  
  
     如果您的專案使用的檔案，您應該自訂標準編輯器。 如果您的專案不使用檔案，但而不是使用資料庫或其他儲存機制中的項目，您應該建立自訂編輯器。  
  
-   您的編輯器需要裝載 ActiveX 控制項嗎？  
  
     如果您的編輯器裝載 ActiveX 控制項，然後實作就地啟用編輯器中所述[就地啟用](../extensibility/in-place-activation.md)。 如果它未裝載 ActiveX 控制項，然後使用簡化的嵌入編輯器，或自訂[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]預設編輯器。  
  
-   將您的編輯器支援多個檢視？ 如果您想要檢視您在同一時間的預設編輯器是可見的編輯器，您必須支援多個檢視。  
  
     如果您的編輯器需要支援多個檢視，編輯器的文件檢視物件與文件資料必須是不同的物件。 如需詳細資訊，請參閱[支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)。  
  
     如果您的編輯器支援多個檢視，執行您打算使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器的文字緩衝區實作 (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件) 的文件資料物件嗎？ 您想要支援您編輯器檢視--與並存也就是[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器嗎？ 若要這樣做的功能是表單設計工具的基礎...  
  
-   如果您要裝載外部編輯器時，可以在編輯器會內嵌在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]嗎？  
  
     如果可以內嵌，建立主應用程式視窗外部編輯器中，然後呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>方法並將<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列舉值，以`DP_External`。 如果編輯器無法內嵌，IDE 會自動為它建立個別的視窗。  
  
## <a name="in-this-section"></a>本節內容  
 [逐步解說︰建立自訂編輯器](../extensibility/walkthrough-creating-a-custom-editor.md)  
 說明如何建立自訂編輯器。  
  
 [逐步解說︰將功能加入至自訂編輯器](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 說明如何將功能加入至自訂編輯器。  
  
 [設計工具初始化和中繼資料組態](../extensibility/designer-initialization-and-metadata-configuration.md)  
 說明如何初始化設計工具。  
  
 [為設計工具提供復原支援](../extensibility/supplying-undo-support-to-designers.md)  
 說明如何設計工具提供復原支援。  
  
 [自訂編輯器中的語法著色](../extensibility/syntax-coloring-in-custom-editors.md)  
 說明自訂編輯器和核心編輯器中著色的語法差異。  
  
 [自訂編輯器中的文件資料和文件檢視](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 說明如何實作自訂編輯器中的文件資料和文件的檢視。  
  
## <a name="related-sections"></a>相關章節  
 [在編輯器中的傳統介面](../extensibility/legacy-interfaces-in-the-editor.md)  
 說明如何透過舊版 API 存取核心編輯器。  
  
 [開發舊版語言服務](../extensibility/internals/developing-a-legacy-language-service.md)  
 說明如何實作語言服務。  
  
 [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)  
 說明如何建立符合的其餘部分的 UI 項目[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>