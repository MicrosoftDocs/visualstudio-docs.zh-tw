---
title: 預設命令、 群組及工具列位置 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7fc877332f7db7b27c4a30c23f1ac395a4fc22e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196887"
---
# <a name="default-command-group-and-toolbar-placement"></a>預設的命令、群組及工具列放置
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

如需產品的一致性和穩定性，UI 預設會顯示特定命令群組，和[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]提供命令和命令群組的定義。 Vspackage 也可以使用標準命令和命令群組。  
  
 預設命令群組分成三個類別：IDE 命令、 產品命令和編輯器命令。  
  
## <a name="default-ide-commands"></a>預設 IDE 命令  
 預設 IDE 工具列中包含共用的所有產品中包含的命令[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 其中包括與相關的命令一般專案作業，例如**儲存**命令並**加入項目**命令。 Vspackage 不應該加入或減去此工具列，有一個例外狀況：如果 VSPackage 的產品加入新的工具視窗中，則視窗應該新增至可用的工具視窗的清單上**檢視**功能表。 新的產品或 Vspackage 可以新增自己的工具列。  
  
## <a name="default-product-commands"></a>預設產品命令  
 每項產品可以提供自己預設工具列包含重要且常用命令的 IDE。 它是最佳方法，不過，若要使用現有的功能表和工具列，可能的話，並補充它們與其他工作特定的工具列，視。  
  
 工具列的 [優先順序] 欄位會決定它的資料列位置。 零優先順序置於第三個資料列 （資料列 3），功能表列下方工具列 （資料列 1） 和**標準**工具列 （資料列 2）。 因此，其他工具列會出現在資料列 （優先順序 + 3）。 後續的工具列會放在相同的資料列，如果有足夠的空間;否則，它們會自動移至下一個資料列。  
  
## <a name="default-editor-commands"></a>預設編輯器命令  
 VSPackage 提供的自訂編輯器應該提供預設的工具列，包含最重要的而且在該編輯器中常用命令。 當編輯器為作用中且編輯器不是作用中時，應該隱藏時，應該會出現 [編輯器] 工具列。 此可見性會控制`VisibilityConstraints Element`.vsct 檔。  
  
 編輯器工具列應該放下方 IDE 和 產品 工具列中。  
  
## <a name="see-also"></a>另請參閱  
 [IDE 定義的命令、 功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
