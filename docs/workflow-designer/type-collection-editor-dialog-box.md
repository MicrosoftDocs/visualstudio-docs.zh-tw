---
title: 工作流程設計工具型別集合編輯器對話方塊
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0a9bf604749524d76b8046d60de75d4b5844cc4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649786"
---
# <a name="type-collection-editor-dialog-box"></a>型別集合編輯器對話方塊

[**型別集合編輯器**] 對話方塊是用來將已知型別加入至**傳送**和**接收**活動。 這個對話方塊也用來將泛型型別引數加入至**InvokeMethod**活動。 當用於**傳送**和**接收**活動以加入已知型別時，[**型別集合編輯器**] 對話方塊會要求類型新增必須是唯一的。 如果加入重複的類型，並按一下 **[確定]** 來認可變更，則會傳回錯誤訊息。 當用於**InvokeMethod**活動以加入泛型型別引數時，[**型別集合編輯器**] 對話方塊可讓您新增重複的類型。

如需詳細資訊，請參閱[資料合約已知類型](/dotnet/framework/wcf/feature-details/data-contract-known-types)。

下表描述 [**型別集合**] 對話方塊的使用者介面（UI）元素。

|UI 項目|描述|
|-|-----------------|
|**類型清單**|已加入或已移除之型別的清單。|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>若要顯示 Send  與 Receive 活動的型別集合編輯器

1. 在設計檢視中，選取 [**傳送**] 或 [**接收**] 活動。

2. 按**F4**以顯示 [**屬性**] 視窗。

3. 在 [**屬性**] 視窗中，按一下 [ **KnownTypes** ] 屬性旁邊的省略號按鈕。

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>若要顯示 InvokeMethod 活動的型別集合編輯器

1. 在設計檢視中選取 [ **InvokeMethod** ] 活動。

2. 按**F4**以顯示 [**屬性**] 視窗。

3. 在 [**屬性**] 視窗中，按一下 [ **GenericTypeArguments** ] 屬性旁邊的省略號按鈕。