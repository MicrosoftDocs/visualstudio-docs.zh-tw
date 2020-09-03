---
title: 將參考字串附加至 UML 模型元素 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending, reference strings
ms.assetid: 15dbed99-efce-42fe-a768-714a5804e7d1
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7726379258ef474b57f1ca4a924413cd93cf80bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672797"
---
# <a name="attach-reference-strings-to-uml-model-elements"></a>將參考字串附加至 UML 模型項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以撰寫程式碼，將任意字串附加至模型項目。 例如，字串可能是 URI、快取的計算結果，或另一個模型項目的 ModelBus 參考。 每個字串都包含在 IReference 物件中。 任何數目的 IReference 物件都可以附加至每個模型項目。

 每個 IReference 物件都具有名稱。 您可以使用這個名稱指示參考值應有的解譯方式。 例如，您可以將名稱設為 "URI"，指示此值應解譯為 URI。 有些預先定義的參考名稱值已為模型工具所用。

## <a name="attaching-a-reference-to-an-ielement"></a>將參考附加至 IElement
 若要使用下列方法，您必須將參考加入：

 Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll

 您應該在程式碼中插入此指示詞：

 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

|方法呼叫|說明|
|-----------------|-----------------|
|`element.AddReference (nameString, valueString, duplicatesAllowed)`|以指定名稱和值字串建立 `IReference`，並將其連結至 `element`。 傳回 `IReference`。<br /><br /> 如果 `duplicatesAllowed` 為 false，而且已經有同名的 `IReference` 附加至 `element`，則擲回例外狀況。|
|`element.GetReferences(name)`|傳回連結至 `IReference`，且有指定 `element` 的所有 `name` 物件。|
|`element.DeleteAllReferences(name)`|刪除連結至有指定名稱項目的所有 `IReference` 物件。|
|`reference.Delete()`|刪除這個 `IReference`。|
|`ReferenceConstants.WorkItem`|用於命名工作項目參考的值。|

## <a name="see-also"></a>另請參閱
 [定義工作專案連結處理常式](../modeling/define-a-work-item-link-handler.md)[使用 UML API](../modeling/programming-with-the-uml-api.md) [定義和安裝模型擴充](../modeling/define-and-install-a-modeling-extension.md)功能程式設計
