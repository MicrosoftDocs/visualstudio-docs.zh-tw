---
title: 舊版語言服務的模型 |Microsoft Docs
description: 使用 Visual Studio 核心編輯器的最基礎語言服務模型，作為建立您專屬語言服務的指南。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2928d3c09a54ea8e9548f7751381279f153643e5
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876736"
---
# <a name="model-of-a-legacy-language-service"></a>舊版語言服務模型
語言服務會定義特定語言的元素和功能，並用來為編輯器提供該語言特定的資訊。 例如，編輯器必須知道語言的元素和關鍵字，才能支援語法色彩。

 語言服務與編輯器所管理的文字緩衝區以及包含編輯器的視圖緊密搭配運作。 Microsoft IntelliSense **Quick Info** 選項是語言服務所提供之功能的範例。

## <a name="a-minimal-language-service"></a>基礎語言服務
 最基本的語言服務包含下列兩個物件：

- *語言服務* 會實作為 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 介面。 語言服務包含語言的相關資訊，包括其名稱、副檔名、程式碼視窗管理員和著色器。

- *著色器* 會實作為 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 介面。

  下列概念繪圖顯示基礎語言服務的模型。

  ![語言服務模型圖形](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") 基礎語言服務模型

  文件視窗會主控編輯器的 *檔視圖* ，在此案例中為 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 核心編輯器。 檔視圖和文字緩衝區是由編輯器所擁有。 這些物件會 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 透過稱為程式 *代碼視窗* 的特製化文件視窗來運作。 程式碼視窗包含在 IDE 所 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 建立和控制的物件中。

  載入具有指定副檔名的檔案時，編輯器會找出與該副檔名相關聯的語言服務，然後藉由呼叫方法，將它傳遞至程式碼視窗 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> 。 語言服務會傳回程序 *代碼視窗管理員*，以執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 介面。

  下表提供模型中物件的總覽。

| 元件 | Object | 函數 |
|------------------| - | - |
| 文字緩衝區 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Unicode 讀取/寫入文字資料流程。 文字可能會使用其他編碼。 |
| 程式碼視窗 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | 包含一或多個文字視圖的文件視窗。 當 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 位於多重文件介面 (mdi) 模式時，程式碼視窗會是 mdi 子系。 |
| 文字視圖 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | 可讓使用者使用鍵盤和滑鼠流覽和觀看文字的視窗。 使用者會看到文字視圖作為編輯器。 您可以使用一般編輯器視窗、[輸出] 視窗和 [即時運算] 視窗中的文字流覽。 此外，您可以在程式碼視窗中設定一或多個文字視圖。 |
| 文字管理員 | 由服務管理 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> ，您可從中取得 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> 指標 | 此元件會維護先前所述所有元件所共用的通用資訊。 |
| 語言服務 | 執行相依;實現 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | 物件，為編輯器提供語言特定的資訊，例如語法醒目提示、語句完成和大括弧比對。 |

## <a name="see-also"></a>請參閱
- [自訂編輯器中的文件資料和文件檢視](../../extensibility/document-data-and-document-view-in-custom-editors.md)
