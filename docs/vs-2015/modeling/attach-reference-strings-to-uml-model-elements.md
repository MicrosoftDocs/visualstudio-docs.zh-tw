---
title: 將參考字串附加至 UML 模型項目 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, reference strings
ms.assetid: 15dbed99-efce-42fe-a768-714a5804e7d1
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: cf8a9e7e023e9c75f61fdf9a6bfb608edc3a7123
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804575"
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
  
|方法呼叫|描述|  
|-----------------|-----------------|  
|`element.AddReference (nameString, valueString, duplicatesAllowed)`|以指定名稱和值字串建立 `IReference`，並將其連結至 `element`。 傳回 `IReference`。<br /><br /> 如果 `duplicatesAllowed` 為 false，而且已經有同名的 `IReference` 附加至 `element`，則擲回例外狀況。|  
|`element.GetReferences(name)`|傳回連結至 `IReference`，且有指定 `element` 的所有 `name` 物件。|  
|`element.DeleteAllReferences(name)`|刪除連結至有指定名稱項目的所有 `IReference` 物件。|  
|`reference.Delete()`|刪除這個 `IReference`。|  
|`ReferenceConstants.WorkItem`|用於命名工作項目參考的值。|  
  
## <a name="see-also"></a>另請參閱  
 [定義工作項目連結處理常式](../modeling/define-a-work-item-link-handler.md)   
 [定義與安裝模型擴充功能](../modeling/define-and-install-a-modeling-extension.md)   
 [使用 UML API 進行程式設計](../modeling/programming-with-the-uml-api.md)



