---
title: 屬性視窗的物件清單 |Microsoft Docs
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
ms.openlocfilehash: 751339d0e9f8d4dd6d43a1f786e08b57d0ac7555
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347804"
---
# <a name="properties-window-object-list"></a>屬性視窗的物件清單
在 [物件] 清單**屬性**視窗是下拉式清單，可讓您將選取範圍變更一或多個選取的 windows 中可用的其他物件。 選取這份清單內的不同物件從觸發程序呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>通知環境已選取新的物件。 中顯示的資訊**屬性**視窗再變更為顯示新選取的物件相關聯的屬性。

## <a name="the-object-list"></a>物件清單
 包含兩個欄位的物件清單: （以粗體顯示） 的物件名稱和物件類型。

 左邊的物件型別，以粗體顯示的物件名稱擷取自物件本身使用`Name`所提供的屬性<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>介面。 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>唯一的方法上<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>，傳回<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>針對該介面的 coclass。 **屬性** 視窗使用<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>取得 coclass，顯示為下拉式清單中的物件名稱的名稱。

 如果物件沒有`Name`屬性名稱不會顯示在 物件清單的 名稱 區域。 如果您想要顯示在 [物件] 清單中的名稱，您可以新增至物件的 Name 屬性。

 如果 COM 物件未實作<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>，則**屬性**視窗會顯示在左側的清單上的介面名稱來取代物件名稱。

## <a name="see-also"></a>另請參閱
- [擴充屬性](../../extensibility/internals/extending-properties.md)