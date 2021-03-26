---
title: 如何：識別程式庫中的符號 |Microsoft Docs
description: 瞭解如何在程式庫中找出符號，方法是執行將流覽資訊從符號庫傳遞至 Visual Studio 物件管理員的方法。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6c897801b98857f4a310323d4e00583c98245d5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078873"
---
# <a name="how-to-identify-symbols-in-a-library"></a>如何：識別程式庫中的符號
符號流覽工具會顯示符號的階層式觀點。 符號代表命名空間、物件、類別、類別成員和其他語言專案。

 階層中的每個符號都可透過下列介面，由符號連結庫傳遞至物件管理員的導覽資訊來識別 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ：

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 符號在階層中的位置會區分符號。 它可讓符號流覽工具流覽至特定符號。 符號的唯一、完整路徑會決定位置。 路徑中的每個元素都是一個節點。 路徑是以最上層節點開頭，並以特定符號結尾。 例如，如果 M1 方法是 C1 類別的成員，而 C1 是在 N1 命名空間中，M1 方法的完整路徑就是 N1。低耗.M1. 此路徑包含三個節點： N1、C1 和 M1。

 導覽資訊可讓 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 物件管理員尋找、選取及保留選取階層中的符號。 它可讓您從一個流覽工具流覽至另一個。 使用 **物件瀏覽器** 流覽專案中的符號時 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ，您可以用滑鼠右鍵按一下方法，然後啟動 **呼叫瀏覽器** 工具，以在呼叫圖形中顯示該方法。

 有兩種形式描述項號位置。 標準格式是以符號的完整路徑為基礎。 它代表階層中符號的唯一位置。 它與符號流覽工具無關。 為了取得標準格式資訊， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 物件管理員會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> 方法。 簡報表單描述項號在特定符號流覽工具中的位置。 符號的位置相對於階層中其他符號的位置。 給定的符號可以有數個呈現路徑，但只能有一個標準路徑。 例如，如果 C1 類別繼承自 C2 類別，而且這兩個類別都在 N1 命名空間中，則 **物件瀏覽器** 會顯示下列階層式樹狀結構：

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 C2 類別的標準路徑（在此範例中為 N1 + C2）。 C2 的展示路徑包含 C1 和「基底和介面」節點： N1 + C1 + 「基底和介面」 + C2。

 為了取得簡報表單資訊，物件管理員會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> 方法。

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>取得標準和呈現表單資訊

1. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> 方法。

     物件管理員會呼叫這個方法，以取得符號的標準路徑中包含的節點清單。

    ```vb
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)
        Return 0
    End Function
    ```

    ```csharp
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)
    {
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =
            new CallBrowserEnumNavInfoNodes(m_strMethod);
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);
        return 0;
    }

    ```

2. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> 方法。

     物件管理員會呼叫這個方法，以取得符號呈現路徑中包含的節點清單。

## <a name="see-also"></a>另請參閱
- [支援符號流覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [如何：使用物件管理員註冊程式庫](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [如何：將程式庫提供的符號清單公開至物件管理員](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
