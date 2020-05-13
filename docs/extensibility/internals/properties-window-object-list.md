---
title: 屬性視窗物件清單 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffe11ae6ebb4e692686c884b663a4f93d1466535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706142"
---
# <a name="properties-window-object-list"></a>屬性視窗的物件清單
**屬性**視窗中的物件清單是一個下拉清單,允許您將選取內容更改為一個或多個選定視窗中可用的其他物件。 從此清單中選擇其他物件將觸發調用,以<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>通知環境已選擇新物件。 然後更改「**屬性」** 視窗中顯示的資訊以顯示與新選擇的物件關聯的屬性。

## <a name="the-object-list"></a>物件清單
 物件清單由兩個字段組成:物件名稱(以粗體顯示)和物件類型。

 使用`Name`<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>介面提供的屬性從物件本身檢索以粗體顯示的物件類型左側的物件名稱。 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>,上<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>的唯一方法<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>返回 該介面的 coclass。 屬性**Properties**視窗<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>用於獲取 coclass 的名稱,該名稱在下拉清單中顯示為物件名稱。

 如果物件沒有`Name`屬性,則名稱不會顯示在物件清單的"名稱"區域中。 如果希望物件清單中顯示的名稱,則可以向物件添加Name 屬性。

 如果 COM 物件<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>未實現 ,**則屬性**視窗將介面名稱顯示在列表左側的物件名稱中。

## <a name="see-also"></a>另請參閱
- [擴充屬性](../../extensibility/internals/extending-properties.md)
