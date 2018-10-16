---
title: 自訂項目工具 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: cf2d48ee0ec4c8f2f9986f4655eb98b44583beef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220502"
---
# <a name="customizing-element-tools"></a>自訂項目工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

某些在 DSL 定義中，在中，您可以表示單一的概念為一組項目。 比方說，如果您建立的模型，其中一個元件都有一組固定的連接埠，您一定想要在其父元件的相同時間建立的連接埠。 因此，您必須自訂項目建立工具，因此它會建立一組項目，而不是其中一個。 若要這麼做，您可以自訂初始化項目建立工具的方式。  
  
 此外，您也可以覆寫工具拖曳到圖表或項目時，會發生什麼事。  
  
## <a name="customizing-the-content-of-an-element-tool"></a>自訂項目工具的內容  
 每個項目工具會將儲存的執行個體<xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>(EGP)，其中包含一或多個模型項目和連結的序列化的版本。 根據預設，項目工具 EGP 會包含一個執行個體的類別，以您指定的工具。 您可以覆寫來變更這*YourLanguage*`ToolboxHelper.CreateElementToolPrototype`。 載入 DSL 封裝時，會呼叫這個方法。  
  
 方法的參數是您在 DSL 定義中指定之類別的識別碼。 當這個方法會呼叫您感興趣的類別時，您可以新增額外的項目到 EGP。  
  
 EGP 必須包含內嵌的附屬項目從一個主要的項目連結。 它也可以包含參考連結。  
  
 下列範例會建立主要的項目和兩個內嵌的項目。 主要的類別稱為電阻，而且具有兩個項目，名為終端機的內嵌關聯性。 內嵌的角色屬性具名 Terminal1 和 Terminal2，並且兩者都有多重性為 1..1。  
  
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



