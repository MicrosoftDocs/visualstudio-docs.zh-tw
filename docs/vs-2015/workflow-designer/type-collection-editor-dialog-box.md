---
title: 型別集合編輯器對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: c33049c264041495041798ab98c4223ebe0ed6f7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298560"
---
# <a name="type-collection-editor-dialog-box"></a>型別集合編輯器對話方塊
**型別集合編輯器** 對話方塊用來新增至已知型別的**傳送**並**接收**活動。 此對話方塊也會用來加入泛用型別引數**InvokeMethod**活動。 當用於**傳送**並**接收**活動，以加入已知型別，**型別集合編輯器**對話方塊需要是唯一的型別新增項目。 如果加入重複的型別，並認可變更，即可**確定**，會傳回錯誤訊息。 當用於**InvokeMethod**活動，將泛型型別引數**型別集合編輯器**對話方塊允許重複的型別。  
  
> [!NOTE]
>  [!INCLUDE[crabout](../includes/crabout-md.md)] 如需已知型別的詳細資訊，請參閱 [Data Contract Known Types](http://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337)就會將 CLR 型別對應至 XSD。  
  
 下表描述的使用者介面 (UI) 項目**型別集合** 對話方塊。  
  
|UI 項目|描述|  
|----------------|-----------------|  
|**類型清單**|已加入或已移除之型別的清單。|  
  
## <a name="to-bring-up-the-type-collection-editor"></a>顯示型別集合編輯器  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>若要顯示 Send  與 Receive 活動的型別集合編輯器  
  
1.  選取 **傳送**或是**接收**設計 檢視中的活動。  
  
2.  按下**F4**即可啟動**屬性**視窗。  
  
3.  在 **屬性**視窗中，按一下 下的一步 的省略符號按鈕**KnownTypes**屬性。  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>若要顯示 InvokeMethod 活動的型別集合編輯器  
  
1.  選取  **InvokeMethod** 設計 檢視中的活動。  
  
2.  按下**F4**即可啟動**屬性**視窗。  
  
3.  在 **屬性**視窗中，按一下 下的一步 的省略符號按鈕**GenericTypeArguments**屬性。