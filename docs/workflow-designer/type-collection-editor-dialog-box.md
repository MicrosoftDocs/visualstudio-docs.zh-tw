---
title: "型別集合編輯器對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 8e4b794a623c3a0218e44773da6bdb6c76612816
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="type-collection-editor-dialog-box"></a>型別集合編輯器對話方塊
**型別集合編輯器**對話方塊用來新增至已知型別的**傳送**和**接收**活動。 也使用此對話方塊來加入泛型型別引數**InvokeMethod**活動。 當用於**傳送**和**接收**活動，以加入已知型別，**型別集合編輯器**對話方塊會要求附加唯一的型別。 如果加入重複的型別，並認可變更，即可**確定**，會傳回錯誤訊息。 當用於**InvokeMethod**活動，將泛型型別引數，**型別集合編輯器** 會允許附加重複的型別。  
  
> [!NOTE]
>  [!包含[crabout](/dotnet/framework/wcf/feature-details/data-contract-known-types)。  
  
 下表描述的使用者介面 (UI) 項目**型別集合** 對話方塊。  
  
|UI 項目|描述|  
|----------------|-----------------|  
|**類型清單**|已加入或已移除之型別的清單。|  
  
## <a name="to-bring-up-the-type-collection-editor"></a>顯示型別集合編輯器  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>若要顯示 Send  與 Receive 活動的型別集合編輯器  
  
1.  選取**傳送**或**接收**[設計] 檢視中的活動。  
  
2.  按**F4**啟動**屬性**視窗。  
  
3.  在**屬性**視窗中，按一下省略符號按鈕下, 一步 **KnownTypes**屬性。  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>若要顯示 InvokeMethod 活動的型別集合編輯器  
  
1.  選取**InvokeMethod** [設計] 檢視中的活動。  
  
2.  按**F4**啟動**屬性**視窗。  
  
3.  在**屬性**視窗中，按一下省略符號按鈕下, 一步 **GenericTypeArguments**屬性。