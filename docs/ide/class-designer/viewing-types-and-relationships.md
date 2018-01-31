---
title: "檢視類型和關聯性 (類別設計工具) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- class diagrams
- types [Visual Studio], visualizing
- relationships, class diagrams
- types [Visual Studio], class diagrams
- relationships, visualizing
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e9ca80f3a3feb9655d53c6ee292f84c7c567d166
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="viewing-types-and-relationships-class-designer"></a>檢視類型和關聯性 (類別設計工具)

[類別設計工具] 使用類別圖表來顯示類型的詳細資料 (例如其構成成員)，以及類型共有的關聯性。 這些實體在視覺化後，實際上就是程式碼中的動態檢視。 這表示您可以在設計工具上編輯類型，然後就能看到編輯的結果反映在實體的原始程式碼中。 同樣地，類別圖表會與您對程式碼中的實體所做的變更保持同步。

> [!NOTE]
> 如果您的專案包含類別圖表，而且參考了其他專案中的類型，則除非您建置該類型的專案，否則類別圖表不會顯示參考的類型。 同樣地，除非您重建外部實體的專案，否則此圖表不會顯示該實體的程式碼變更。

## <a name="see-also"></a>另請參閱

[設計類別和類型](designing-classes-and-types.md)  
[重構類別與類型](refactoring-classes-and-types.md)  
[如何：自訂類別圖表](how-to-customize-class-diagrams.md)  
[使用類別圖表](working-with-class-diagrams.md)