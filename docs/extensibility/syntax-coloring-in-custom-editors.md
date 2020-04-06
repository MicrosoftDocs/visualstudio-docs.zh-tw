---
title: 自訂編輯器中的語法著色 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6296c8451684a121ac42dbde6619c0ebbb421908
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699329"
---
# <a name="syntax-coloring-in-custom-editors"></a>自訂編輯器中的語法著色
Visual Studio 環境 SDK 編輯器(包括核心編輯器)使用語言服務來識別特定的語法專案,並顯示它們具有給定文件檢視的指定顏色。

## <a name="colorization-requirements"></a>著色要求
 實現語言服務著色器的所有編輯必須:

1. 使用物件實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>來管理要著色的文本和物件<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>實現 以提供文本的文件視圖。

2. 通過使用語言服務的標識 GUID 查詢 VSPackage 的服務提供者,獲取特定語言服務的介面。

3. 調用對<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>象<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>實現的方法。 此方法將語言服務與 VSPackage<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>用於管理要著色的文本的實現關聯。

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>語言服務著色器的核心編輯器使用
 當核心編輯器的實例獲得帶有著色器的語言服務時,語言服務的著色器會自動解析和呈現文本,而無需您進行任何進一步的干預。

 IDE 透明化:

- 根據需要調用著色器,以在中添加或修改文本時對其進行分析<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>和分析。

- 確保使用著色器返回的資訊更新和重新繪<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>製 實現提供的文檔檢視提供的顯示。

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>語言服務著色器的非核心編輯器使用
 非核心編輯器實例也可以使用語言服務的語法著色服務,但它們必須顯式檢索和應用服務的著色器,並重新繪製其文檔視圖本身。

 為此,非核心編輯器必須:

1. 獲取語言服務的著色器物件(實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>)。 VSPackage 通過在語言服務的介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>上 調用方法來實現此。

2. 調用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法以請求對特定文本範圍進行著色。

     該方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>返回一個值陣列,對於正在著色的文本範圍中的每個字母一個。 它還將文本範圍標識為特定類型的可著色項,如註釋、關鍵字或數據類型。

3. 使用返回<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>的著色資訊重新繪製和顯示其文本。

> [!NOTE]
> 除了使用語言服務的著色器外,VSPackage 還可以選擇使用通用的可視化工作室環境 SDK 文本著色機制。 有關此機制的詳細資訊,請參閱[使用字型和顏色](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)。

## <a name="see-also"></a>另請參閱

- [舊版語言服務中的語法著色](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [實作語法著色](../extensibility/internals/implementing-syntax-coloring.md)
- [如何︰使用內建可設定色彩的項目](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [自訂可設定色彩的項目](../extensibility/internals/custom-colorable-items.md)
