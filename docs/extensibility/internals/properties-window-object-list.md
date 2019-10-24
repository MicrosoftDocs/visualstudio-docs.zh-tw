---
title: 屬性視窗物件清單 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e50b3fe46edb8d14cad9a03a45bc8650cb9713ab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725192"
---
# <a name="properties-window-object-list"></a>屬性視窗的物件清單
[**屬性**] 視窗中的 [物件] 清單是下拉式清單，可讓您將選取範圍變更為一個或多個所選視窗內可用的其他物件。 從這份清單中選取不同的物件，會觸發對 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> 的呼叫，以通知環境已選取新的物件。 接著會變更 [**屬性**] 視窗中顯示的資訊，以顯示與新選取物件相關聯的屬性。

## <a name="the-object-list"></a>物件清單
 物件清單是由兩個欄位所組成：物件名稱（以粗體顯示）和物件類型。

 以粗體顯示在物件類型左邊的物件名稱，會使用 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> 介面所提供的 `Name` 屬性從物件本身抓取。 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>，<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> 的唯一方法會傳回該介面的 coclass <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>。 [**屬性**] 視窗會使用 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> 來取得 coclass 的名稱，這會顯示為下拉式清單中的物件名稱。

 如果物件沒有 `Name` 屬性，就不會在物件清單的 [名稱] 區域中顯示名稱。 如果您想要在 [物件清單] 中顯示名稱，可以將名稱屬性加入至物件。

 如果 COM 物件不會執行 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>，[**屬性**] 視窗會顯示介面名稱，以取代清單左邊的物件名稱。

## <a name="see-also"></a>請參閱
- [擴充屬性](../../extensibility/internals/extending-properties.md)