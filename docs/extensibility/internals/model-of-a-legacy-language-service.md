---
title: 舊版語言服務的模型 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b87106060d3fd66b3659f5d49159ebbb9be9ef6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726380"
---
# <a name="model-of-a-legacy-language-service"></a>舊版語言服務模型
語言服務會定義特定語言的專案和功能，並用來提供該語言特定資訊的編輯器。 例如，編輯器必須知道語言的元素和關鍵字，才能支援語法著色。

 語言服務會與編輯器所管理的文本緩衝區和包含編輯器的視圖緊密搭配運作。 Microsoft IntelliSense**快速**諮詢選項是語言服務所提供之功能的範例。

## <a name="a-minimal-language-service"></a>最小語言服務
 最基本的語言服務包含下列兩個物件：

- *語言服務*會實行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 介面。 語言服務包含該語言的相關資訊，包括其名稱、副檔名、程式碼視窗管理員和著色器。

- *著色器*會執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 介面。

  下列概念圖顯示基礎語言服務的模型。

  ![語言服務模型圖形](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")基礎語言服務模型

  文件視窗會主控編輯器的*檔視圖*，在此案例中為 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 核心編輯器。 檔視圖和文本緩衝區是由編輯器所擁有。 這些物件會透過稱為程式*代碼視窗*的特殊文件視窗，與 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 搭配使用。 [程式碼] 視窗包含在 IDE 所建立和控制的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 物件中。

  載入指定之副檔名的檔案時，編輯器會尋找與該延伸模組相關聯的語言服務，並藉由呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> 方法，將其傳遞至程式碼視窗。 語言服務會傳回程序*代碼視窗管理員*，它會執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 介面。

  下表提供模型中物件的總覽。

| 元件 | Object | 功能 |
|------------------| - | - |
| 文字緩衝區 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Unicode 讀取/寫入文字資料流程。 文字可能會使用其他編碼。 |
| 程式碼視窗 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | 包含一或多個文字流覽的文件視窗。 當 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 在多重文件介面（MDI）模式時，程式碼視窗為 MDI 子系。 |
| 文字視圖 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | 一個視窗，可讓使用者使用鍵盤和滑鼠來流覽和觀看文字。 使用者會看到文字視圖做為編輯器。 您可以在一般編輯器視窗、[輸出] 視窗和 [即時運算] 視窗中使用文字流覽。 此外，您可以在程式碼視窗內設定一或多個文字流覽。 |
| 文本管理員 | 由 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> 服務管理，您可以從中取得 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> 指標 | 此元件會維護先前所述之所有元件共用的通用資訊。 |
| 語言服務 | 相依于執行;執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | 物件，提供編輯器語言特定的資訊，例如語法反白顯示、語句完成和括弧對稱。 |

## <a name="see-also"></a>請參閱
- [自訂編輯器中的文件資料和文件檢視](../../extensibility/document-data-and-document-view-in-custom-editors.md)