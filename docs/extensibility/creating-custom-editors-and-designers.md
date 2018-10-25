---
title: 建立自訂編輯器和設計工具 |Microsoft Docs
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
ms.openlocfilehash: 05eeae4901af8780927e0ce0577b385ee9ffa371
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950897"
---
# <a name="create-custom-editors-and-designers"></a>建立自訂編輯器和設計工具
Visual Studio 整合式的開發環境 (IDE) 可裝載不同類型的編輯器：  
  
- Visual Studio 核心編輯器  
  
- 自訂編輯器  
  
- 外部編輯器  
  
- 設計工具  
  
  下列資訊可協助您選擇的編輯器，您需要的類型。  
  
## <a name="types-of-editor"></a>類型的編輯器  
 Visual Studio 核心編輯器的相關資訊，請參閱[編輯器和語言服務延伸](../extensibility/extending-the-editor-and-language-services.md)。  
  
### <a name="custom-editors"></a>自訂編輯器  
 自訂編輯器是設計用於在特殊情況下。 例如，您可以建立函式會讀取和寫入資料至特定的儲存機制，例如 Microsoft Exchange server 的編輯器。 如果您希望您的專案類型只適用於編輯器，或如果您希望編輯器具有只有幾個特定的命令，請選擇自訂編輯器。 請注意，不過，使用者不能使用自訂的編輯器編輯標準[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案。  
  
 自訂編輯器可以使用編輯器處理站，並在登錄中新增編輯器的相關資訊。 不過，自訂編輯器相關聯的專案型別可以具現化中的其他方法的自訂編輯器。  
  
 自訂編輯器，可以使用就地啟用或簡化內嵌實作檢視。  
  
### <a name="external-editors"></a>外部編輯器  
 外部編輯器是不會整合至 Visual Studio 中，例如 Microsoft Word 中，[記事本] 或 Microsoft FrontPage 的編輯器。 如果，比方說，您傳遞文字給它的 VSPackage，您可能會呼叫這類編輯器。 外部編輯器自行註冊，並可以在 Visual Studio 外部使用。 當您呼叫外部編輯器，且它可以內嵌在主視窗中時，會出現在 IDE 中的視窗。 如果沒有，IDE 然後為其建立另一個視窗。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>方法會設定文件的優先順序，使用<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列舉型別。 如果`DP_External`值指定，則可以透過外部編輯器開啟檔案。  
  
## <a name="editor-design-decisions"></a>編輯器的設計決策  
 下列的設計問題將協助您選擇適合您的應用程式的最佳的編輯器類型：  
  
- 將您的應用程式儲存其資料檔案中或不嗎？ 當它會將其資料儲存在檔案中，將其自訂或標準的格式？  
  
   如果您使用標準檔案格式，除了您的專案以外的其他專案類型可以開啟和讀取/寫入資料到它們。 如果您使用自訂檔案格式，不過，只有您的專案類型能夠開啟和讀取/寫入資料到它們。  
  
   如果您的專案使用的檔案，您應該自訂的標準編輯器。 如果您的專案不會使用檔案，但使用資料庫或其他存放庫中的項目，您應該建立自訂編輯器。  
  
- 您的編輯器需要裝載 ActiveX 控制項嗎？  
  
   如果您的編輯器裝載 ActiveX 控制項，然後實作就地啟用編輯器，在中所述[就地啟用](../extensibility/in-place-activation.md)。 如果它不會裝載 ActiveX 控制項，然後使用簡化的內嵌編輯器中，或是自訂[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]預設編輯器。  
  
- 將您的編輯器支援多個檢視嗎？ 如果您想要顯示的預設編輯器同時編輯器的檢視，您必須支援多個檢視。  
  
   如果您的編輯器需要支援多個檢視，文件資料和編輯器的文件檢視物件必須是不同的物件。 如需詳細資訊，請參閱 <<c0> [ 支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)。  
  
   如果您的編輯器支援多個檢視，您打算使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器的文字緩衝區實作 (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>物件) 的文件資料物件？ 您想要支援您編輯器檢視所並存的即[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器嗎？ 若要這樣做的功能表單設計工具的基礎...  
  
- 如果您要裝載外部編輯器時，編輯器可內嵌在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]嗎？  
  
   如果它可以內嵌，您應該針對外部編輯器建立主視窗，然後呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>方法和 set<xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列舉值，以`DP_External`。 如果編輯器無法內嵌，IDE 會自動為它建立另一個視窗。  
  
## <a name="in-this-section"></a>本節內容  
 [逐步解說： 建立自訂編輯器](../extensibility/walkthrough-creating-a-custom-editor.md)  
 說明如何建立自訂編輯器。  
  
 [逐步解說： 將功能加入至自訂編輯器](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 說明如何將功能加入至自訂編輯器。  
  
 [設計工具的初始設定和中繼資料組態](../extensibility/designer-initialization-and-metadata-configuration.md)  
 說明如何初始化設計工具。  
  
 [設計工具提供復原支援](../extensibility/supplying-undo-support-to-designers.md)  
 說明如何設計工具提供復原功能支援。  
  
 [自訂編輯器中的語法著色](../extensibility/syntax-coloring-in-custom-editors.md)  
 說明語法著色和自訂編輯器中核心編輯器之間的差異。  
  
 [文件資料和自訂編輯器中的文件檢視](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 說明如何實作自訂編輯器中的文件資料和文件檢視。  
  
## <a name="related-sections"></a>相關章節  
 [在編輯器中的舊版介面](../extensibility/legacy-interfaces-in-the-editor.md)  
 說明如何透過舊版 API 存取核心編輯器。  
  
 [開發舊版語言服務](../extensibility/internals/developing-a-legacy-language-service.md)  
 說明如何實作的語言服務。  
  
 [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)  
 說明如何建立比對的其餘的 UI 項目[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>