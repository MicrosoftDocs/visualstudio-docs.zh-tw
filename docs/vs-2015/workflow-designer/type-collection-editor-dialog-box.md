---
title: 型別集合編輯器對話方塊 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dae99166b8b811df75f2e2777d176e6778b60c7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670154"
---
# <a name="type-collection-editor-dialog-box"></a>型別集合編輯器對話方塊
[ **型別集合編輯器** ] 對話方塊是用來將已知型別加入至 **傳送** 和 **接收** 活動。 這個對話方塊也會用來將泛型型別引數加入至 **InvokeMethod** 活動。 當用於 **傳送** 和 **接收** 活動以加入已知型別時，[ **型別集合編輯器** ] 對話方塊會要求新增類型必須是唯一的。 如果加入重複的類型，且按一下 **[確定]** 來認可變更，則會傳回錯誤訊息。 當用於 **InvokeMethod** 活動以加入泛型型別引數時，[ **型別集合編輯器** ] 對話方塊可讓您加入重複的類型。

> [!NOTE]
> [!INCLUDE[crabout](../includes/crabout-md.md)] 如需已知型別的詳細資訊，請參閱 [Data Contract Known Types](https://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337)。

 下表說明 [ **型別集合** ] 對話方塊中， (UI) 元素的使用者介面。

|UI 元素|描述|
|----------------|-----------------|
|**Type List**|已加入或已移除之型別的清單。|

## <a name="to-bring-up-the-type-collection-editor"></a>顯示型別集合編輯器

#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>若要顯示 Send  與 Receive 活動的型別集合編輯器

1. 選取設計檢視中的 [ **傳送** ] 或 [ **接收** ] 活動。

2. 按 **F4** 顯示 [ **屬性** ] 視窗。

3. 在 [ **屬性** ] 視窗中，按一下 [ **KnownTypes** ] 屬性旁邊的省略號按鈕。

#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>若要顯示 InvokeMethod 活動的型別集合編輯器

1. 在設計檢視中選取 [ **InvokeMethod** ] 活動。

2. 按 **F4** 顯示 [ **屬性** ] 視窗。

3. 在 [ **屬性** ] 視窗中，按一下 [ **GenericTypeArguments** ] 屬性旁邊的省略號按鈕。