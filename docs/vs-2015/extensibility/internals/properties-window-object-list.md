---
title: 屬性視窗的物件清單 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6fd821da5d54afdb7ea8b3d16dc32f818222a961
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183101"
---
# <a name="properties-window-object-list"></a>屬性視窗的物件清單
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在 [物件] 清單**屬性**視窗是下拉式清單，可讓您將選取範圍變更一或多個選取的 windows 中可用的其他物件。 選取這份清單內的不同物件從觸發程序呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>通知環境已選取新的物件。 中顯示的資訊**屬性**視窗再變更為顯示新選取的物件相關聯的屬性。  
  
## <a name="the-object-list"></a>物件清單  
 包含兩個欄位的物件清單: （以粗體顯示） 的物件名稱和物件類型。  
  
 左邊的物件型別，以粗體顯示的物件名稱擷取自物件本身使用`Name`所提供的屬性<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>介面。 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>唯一的方法上<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>，傳回<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>針對該介面的 coclass。 **屬性** 視窗使用<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>取得 coclass，顯示為下拉式清單中的物件名稱的名稱。  
  
 如果物件沒有`Name`屬性名稱不會顯示在 物件清單的 名稱 區域。 如果您想要顯示在 [物件] 清單中的名稱，您可以新增至物件的 Name 屬性。  
  
 如果 COM 物件未實作<xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>，則**屬性**視窗會顯示在左側的清單上的介面名稱來取代物件名稱。  
  
## <a name="see-also"></a>另請參閱  
 [擴充屬性](../../extensibility/internals/extending-properties.md)

