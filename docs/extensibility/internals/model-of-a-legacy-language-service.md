---
title: 傳統語言服務模型 |微軟文件
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
ms.openlocfilehash: 7f024a02641902843f673ce3ff8583a4bce3b135
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707040"
---
# <a name="model-of-a-legacy-language-service"></a>舊版語言服務模型
語言服務定義特定語言的元素和功能,並用於向編輯器提供特定於該語言的資訊。 例如,編輯器需要知道語言的元素和關鍵字,以支援語法著色。

 語言服務與編輯器管理的文字緩衝區和包含編輯器的檢視密切合作。 Microsoft IntelliSense**快速資訊**選項是語言服務提供的功能的範例。

## <a name="a-minimal-language-service"></a>最小語言服務
 最基本的語言服務包含以下兩個物件:

- *語言服務*實<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>作介面 。 語言服務包含有關該語言的資訊,包括其名稱、檔名擴展名、代碼視窗管理員和著色器。

- *著色器*<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>實現 介面。

  以下概念圖顯示了基本語言服務的模型。

  ![語言服務模型圖形](../../extensibility/media/vslanguageservicemodel.gif "vs 語言服務模型")基礎語言服務模型

  文件視窗承載編輯器*的文檔檢視*,在這種情況下,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]則承載 核心編輯器。 文件檢視和文字緩衝區歸編輯器所有。 這些物件通過稱為[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]*代碼視窗*的專用文檔視窗進行使用。 代碼視窗包含在由 IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>創建和控制的物件中。

  載入具有給定副檔名的檔時,編輯器將查找與該擴展名關聯的語言服務,並透過調<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>用方法傳遞給它代碼視窗。 語言服務返回一個*代碼視窗管理員*,該管理器<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>實現 介面。

  下表概述了模型中的物件。

| 元件 | Object | 函式 |
|------------------| - | - |
| 文字緩衝區 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Unicode 讀/寫文字流。 文字可以使用其他編碼。 |
| 程式碼視窗 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | 包含一個或多個文字檢視的文件視窗。 當[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]處於多文檔介面 (MDI) 模式時,代碼視窗是 MDI 子視窗。 |
| 文字檢視 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | 允許使用者使用鍵盤和滑鼠導航和查看文本的視窗。 文字檢視以編輯器形式顯示給使用者。 您可以在普通編輯器視窗、「輸出」視窗和「立即」視窗中使用文字檢視。 此外,您還可以在代碼視窗中配置一個或多個文本檢視。 |
| 文字管理員 | 由<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>服務管理,從中<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>獲取指標 | 維護前面描述的所有元件共用的常見資訊的元件。 |
| 語言服務 | 依實施;實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | 向編輯器提供特定於語言的資訊的物件,如語法突出顯示、語句完成和大括弧匹配。 |

## <a name="see-also"></a>另請參閱
- [自訂編輯器中的文件資料和文件檢視](../../extensibility/document-data-and-document-view-in-custom-editors.md)
