---
title: 舊語言服務中的語法著色 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2589ec24f230287306e0ff7e802d381fb6ab18b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704763"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>舊版語言服務中的語法著色

Visual Studio 使用著色服務來標識語言的元素,並在編輯器中使用指定的顏色顯示它們。

## <a name="colorizer-model"></a>著色器模型
 語言服務實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>介面,然後由編輯器使用。 此實現是語言服務中的單獨物件,如下圖所示:

 ![SVC 色彩標示器圖形](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> 語法著色服務與用於著色文本的一般 Visual Studio 機制是分開的。 有關支援著色的一般[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]機制的詳細資訊,請參閱[使用字型和顏色](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)。

 除了著色器之外,語言服務還可以通過通告提供自定義可著色專案來提供編輯器使用的自定義可著色專案。 可以通過在<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems><xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>實現 介面的同一對象上實現介面來實現此目的。 當編輯器調用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>方法時,它返回自定義可著色項的數量,並在編輯器調<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>用 方法時返回單個自定義可著色項。

 該方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>返回實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>介面的物件。 如果語言服務支援 24 位元或高顏色值,則必須在<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>介面的同<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>一對象上實現介面。

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>VS 套件如何使用語言服務著色器

1. VSPackage 必須獲得適當的語言服務,這需要語言服務 VSPackage 執行以下操作:

    1. 使用實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>介面的物件使文本著色。

         文字通常使用一個介面的物件<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>顯示 。

    2. 通過查詢語言服務 GUID 的 VSPackage 的服務提供者來獲取語言服務。 語言服務在註冊表中通過檔擴展名標識。

    3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>通過調用語言<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>服務的方法將語言服務與關聯。

2. VSPackage 現在可以獲取和使用著色器物件,如下所示:

    > [!NOTE]
    > 使用核心編輯器的 VS 套件不必顯式獲取語言服務的著色器物件。 一旦核心編輯器的實例獲得適當的語言服務,它將執行此處顯示的所有著色任務。

    1. 通過在<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>語言服務<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2><xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A><xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>的物件上調用方法,獲取實現和介面的語言服務的著色器物件。

    2. 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法以獲取特定文本範圍的著色器資訊。

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>返回一個值陣列,對於著色的文本範圍中的每個字元,一個。 這些值是索引到可著色項清單,該清單是核心編輯器維護的預設可著色項清單,或者由語言服務本身維護的自定義可著色項清單。

    3. 使用 方法返回<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>的 著色信息顯示所選文本。

> [!NOTE]
> 除了使用語言服務著色器外,VSPackage 還可以使用通用視覺工作室文本著色機制。 有關此機制的詳細資訊,請參閱[使用字型和顏色](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)。

## <a name="in-this-section"></a>本節內容
- [實作語法著色](../../extensibility/internals/implementing-syntax-coloring.md)

 討論編輯器如何存取語言服務的語法著色,以及語言服務必須實現什麼來支援語法著色。

- [如何︰使用內建可設定色彩的項目](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 演示如何使用語言服務中的內置可著色項。

- [自訂可設定色彩的項目](../../extensibility/internals/custom-colorable-items.md)

 討論如何實現自定義可著色項。
