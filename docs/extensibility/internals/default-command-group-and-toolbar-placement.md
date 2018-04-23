---
title: 預設命令、 群組及工具列位置 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0753a29e323f18ad40bcc62a70cf8e9b1123b728
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="default-command-group-and-toolbar-placement"></a>預設的命令、 群組及工具列位置
產品的一致性與穩定性，UI 預設會顯示特定命令的群組，和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令和命令群組提供定義。 Vspackage 也可以使用標準命令和命令群組。  
  
 預設命令群組分成三個類別： IDE 命令、 產品命令和編輯器命令。  
  
## <a name="default-ide-commands"></a>預設 IDE 命令  
 預設 IDE 工具列包含共用的所有產品中所包含的命令[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 其中包括與泛型專案作業，例如相關的命令**儲存**命令和**加入項目**命令。 Vspackage 不應該加入或減去此工具列，有一個例外狀況： 如果產品或 VSPackage 將加入新的工具視窗中，則視窗應該加入至可用的工具視窗的清單上**檢視**功能表。 新產品或 Vspackage 可以加入自己的工具列。  
  
## <a name="default-product-commands"></a>預設產品指令  
 每個產品可以提供自己預設工具列，其中包含重要並經常使用的命令與 IDE。 所以最好，不過，使用現有的功能表和工具列盡可能並視需要以特定工作的其他工具列補充它們。  
  
 工具列的 [優先順序] 欄位會決定它的資料列位置。 零優先順序置於功能表列下方的第三個資料列 （資料列 3），工具列 （資料列 1） 和**標準**工具列 （資料列 2）。 因此，其他工具列會出現在資料列 （優先順序 + 3）。 後續工具列位於同一個資料列中，如果有足夠的空間;否則，它們會自動移至下一個資料列。  
  
## <a name="default-editor-commands"></a>預設編輯器命令  
 VSPackage 提供的自訂編輯器應該提供預設工具列，其中包含最重要的並在該編輯器中常用命令。 當編輯器 為作用中且編輯器不在作用中時，應該隱藏時，應該會出現 編輯器 工具列。 此可見性進行控制`VisibilityConstraints Element`.vsct 檔。  
  
 IDE 和產品工具列下方應放編輯器工具列。  
  
## <a name="see-also"></a>另請參閱  
 [IDE 定義命令、 功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)