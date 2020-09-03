---
title: 自訂元素工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6b35bbb0592f7ec9f8defcd9d78dbba5a6a47a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655015"
---
# <a name="customizing-element-tools"></a>自訂項目工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在某些 DSL 定義中，您可以將單一概念表示為元素群組。 例如，如果您建立一個模型，其中元件有一組固定的通訊埠，您一定會想要在其父元件的相同時間建立埠。 因此，您必須自訂專案建立工具，以建立一組專案，而不是只有一個元素。 若要達成此目的，您可以自訂專案建立工具的初始化方式。

 您也可以覆寫工具拖曳至圖表或元素時所發生的情況。

## <a name="customizing-the-content-of-an-element-tool"></a>自訂元素工具的內容
 每個元素工具都會儲存 <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP) 的實例，其中包含一個或多個模型專案和連結的序列化版本。 根據預設，元素工具的 EGP 會包含您為工具指定的一個類別實例。 您可以藉由覆寫*YourLanguage*來變更此項 `ToolboxHelper.CreateElementToolPrototype` 。 當 DSL 套件載入時，會呼叫這個方法。

 方法的參數是您在 DSL 定義中指定之類別的識別碼。 使用您感興趣的類別來呼叫方法時，您可以在 EGP 中新增額外的元素。

 EGP 必須包括將一個主要元素的連結內嵌到附屬元素。 它也可以包含參考連結。

 下列範例會建立一個主要元素和兩個內嵌元素。 主要類別稱為「電阻」，其具有兩個與名為 Terminal 的專案之間的內嵌關聯性。 內嵌角色屬性的名稱為 Terminal1 和 Terminal2，而且兩者的多重性為 1 ..1。

```
using Microsoft.VisualStudio.Modeling; ...
public partial class CircuitDiagramToolboxHelper
{
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)
  {
    // A case for each tool to customize:
    if (domainClassId == Resistor.DomainClassId)
    {
      // Set up the prototype elements and links:
      Resistor resistor = new Resistor(store);
      resistor.Terminal1 = new Terminal(store);
      resistor.Terminal2 = new Terminal(store);
      resistor.Terminal1.Name = "T1"; // embedding
      resistor.Terminal2.Name = "T2"; // embedding
      // We could also set up reference links.

      // Create an element group prototype for the toolbox:
      ElementGroup egp = new ElementGroup(store.DefaultPartition);
      egp.AddGraph(resistor, true);
      // We do not have to explicitly include embedded children.
      return egp.CreatePrototype();
    }
    // Element tools for other classes:
    else
      return base.CreateElementToolPrototype(store, domainClassId);
  }
}
```

## <a name="see-also"></a>另請參閱
 [自訂項目的建立和移動](../modeling/customizing-element-creation-and-movement.md)
