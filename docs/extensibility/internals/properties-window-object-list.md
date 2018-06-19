---
title: 屬性視窗物件清單 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6b7d238f7ce64122ac18a52dab59afb063ce47e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130132"
---
# <a name="properties-window-object-list"></a>屬性視窗物件清單
中的物件清單**屬性**視窗是下拉式清單，可讓您可以在一或多個選取的 windows 中使用的其他物件變更選取範圍。 選取此清單內的不同物件觸發程序呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>通知環境已選取新的物件。 中顯示的資訊**屬性**視窗然後變更為顯示與新選取的物件相關聯的屬性。  
  
## <a name="the-object-list"></a>物件清單  
 包含兩個欄位的物件清單: （以粗體顯示） 的物件名稱和物件類型。  
  
 左側的物件類型，以粗體顯示的物件名稱擷取自物件本身使用`Name`屬性所提供<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>介面。 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>唯一的方法上<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>，傳回<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>為該介面的 coclass。 **屬性**視窗使用<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>取得 coclass，會顯示為下拉式清單中的物件名稱的名稱。  
  
 如果物件沒有`Name`屬性名稱不會顯示在 [名稱] 區域的物件清單。 如果您想要顯示物件清單中的名稱，您可以新增至物件的 Name 屬性。  
  
 如果 COM 物件未實作<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>、**屬性**視窗會顯示清單的左半部介面名稱來取代物件名稱。  
  
## <a name="see-also"></a>另請參閱  
 [擴充屬性](../../extensibility/internals/extending-properties.md)