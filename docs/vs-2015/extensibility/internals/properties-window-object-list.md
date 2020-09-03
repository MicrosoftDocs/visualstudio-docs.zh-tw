---
title: 屬性視窗物件清單 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95ef509491e05daf575e211ae479c815994eb3d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148336"
---
# <a name="properties-window-object-list"></a>屬性視窗的物件清單
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[ **屬性** ] 視窗中的 [物件清單] 是一個下拉式清單，可讓您將選取範圍變更為一或多個選取視窗內可用的其他物件。 從這份清單中選取不同的物件會觸發呼叫， <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> 以通知環境已選取新的物件。 接著會變更 [ **屬性** ] 視窗中顯示的資訊，顯示與新選取之物件相關聯的屬性。  
  
## <a name="the-object-list"></a>物件清單  
 物件清單包含兩個欄位：物件名稱 (以粗體顯示) 和物件類型。  
  
 以粗體顯示于物件類型左邊的物件名稱，會使用介面所提供的屬性從物件本身取出 `Name` <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> 。 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>，唯一的方法是傳回 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> 該介面的 coclass。 [ **屬性** ] 視窗 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> 會使用來取得 coclass 的名稱，該 coclass 會顯示為下拉式清單中的物件名稱。  
  
 如果物件沒有 `Name` 屬性，就不會在 [物件清單] 的 [名稱] 區域中顯示名稱。 如果您想要在 [物件清單] 中顯示名稱，您可以將 [名稱] 屬性加入物件中。  
  
 如果 COM 物件未執行 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> ，[ **屬性** ] 視窗就會顯示介面名稱，取代清單左邊的物件名稱。  
  
## <a name="see-also"></a>另請參閱  
 [擴充屬性](../../extensibility/internals/extending-properties.md)
